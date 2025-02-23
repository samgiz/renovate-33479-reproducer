# renovate-33479-reproducer

Running `renovate@39.177.1` on this repo produces the following error message:

```json
"config": {
         "git-submodules": [
           {
             "deps": [
               {
                 "depName": "renovate-34101-reproducer",
                 "packageName": "https://github.com/samgiz/renovate-34101-reproducer",
                 "currentValue": "main",
                 "currentDigest": "f081d04a38c0a204c0563a19f262951321dddfff",
                 "updates": [],
                 "versioning": "git",
                 "warnings": [
                   {
                     "message": "Could not determine new digest for update (custom.dummy package https://github.com/samgiz/renovate-34101-reproducer)",
                     "topic": "https://github.com/samgiz/renovate-34101-reproducer"
                   }
                 ]
               }
             ],
             "datasource": "git-refs",
             "packageFile": ".gitmodules"
           }
         ]
       }
```

Reverting [this commit](https://github.com/samgiz/renovate-33479-reproducer/commit/61198ecc543775276ea7ef3c2340d2082d9068b5) is a workaround for the issue (note that the `1.0.0` branch doesn't need to exist and isn't used in the end, it just needs to follow a semver format):

```
DEBUG: branches info extended (repository=samgiz/renovate-33479-reproducer)
       "branchesInformation": [
         {
           "branchName": "renovate/renovate-34101-reproducer-digest",
           "prNo": null,
           "prTitle": "Update renovate-34101-reproducer digest to 883dead",
           "result": "no-work",
           "upgrades": [
             {
               "datasource": "custom.dummy",
               "depName": "renovate-34101-reproducer",
               "displayPending": "",
               "fixedVersion": "1.0.0",
               "currentVersion": "1.0.0",
               "currentValue": "1.0.0",
               "currentDigest": "f081d04a38c0a204c0563a19f262951321dddfff",
               "newValue": "1.0.0",
               "newDigest": "883deadc7186bb1ad00f98cd46d16a52419b7368",
               "packageFile": ".gitmodules",
               "updateType": "digest",
               "packageName": "https://github.com/samgiz/renovate-34101-reproducer"
             }
           ]
         }
       ]
```

More context [in the Renovate discussion](https://github.com/renovatebot/renovate/discussions/33479#discussioncomment-11994587).
