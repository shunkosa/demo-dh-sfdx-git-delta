A simple GitHub Actions demo based on [@traiheadapps/dreamhouse-lwc](https://github.com/trailheadapps/dreamhouse-lwc) and [@scolladon/sfdx-git-delta](https://github.com/scolladon/sfdx-git-delta).

| Branches     | Event        | Action                                                                                                                                                                                                       |
| ------------ | ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| develop/full | Pull Request | 1. Validate (`sfdx:force:source:deploy -p force-app -c --testlevel RunLocalTests`)                                                                                                                           |
| develop/diff | Pull Request | 1. SGD (`sgd:source:delta --from develop/diff --to HEAD --output .`) <br/> 2. Validate (`sfdx:force:source:deploy -x package.xml --checkonly --testlevel RunLocalTests`)                                         |
| develop/diff | Merge        | 1. SGD (`sgd:source:delta --from develop/diff --to HEAD --output .`) <br/> 2. Deploy(`sfdx:force:source:deploy -x package.xml`) <br/> 3. Destruct (`sfdx force:mdapi:deploy -d destructiveChanges`) |
