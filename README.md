# Brreg

Library for connecting to Brreg api





## Installation


Install using composer:

    composer require helgesverre/brreg:dev-master

Add the service provider in `config/app.php`:

    HelgeSverre\Brreg\Providers\BrregDataServiceProvider::class,

Usage
-----


```php

Route::get("/companies", function (Request $request, \HelgeSverre\Brreg\Services\BrregDataService $brreg) {

    $searchTerm = $request->input("q");
    
    
    $companies = $brreg->searchByName($searchTerm);

    return new Jsonresponse($companies["data"]);
});

```

By default, only 10 results are returned, however this can be changed as such:

```php
// Show 20 results, start on page 0
$companies = $brreg->searchByName("Acme", 0, 20);

// Get the 20 next entries
$companies = $brreg->searchByName("Acme", 1, 20);
```



You can also fetch company data by the Registration number (Org Nr):


```php

$companyData = $brreg->getCompanyData(814114562);
```
