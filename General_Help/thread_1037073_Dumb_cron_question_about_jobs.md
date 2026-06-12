---
title: "Dumb cron question about jobs"
date: 2009-01-11
forum: General Help
---

### Post by matthewboh on 2009-01-11
I've got Amanda up and running my backups, but I need to split apart some of the jobs.  What I would like to do is to run one job after another since only one backup job can be run at a time.  How would I set that up?  For example, I need to run the following jobs:

amdump music
amdump musiccd

Thanks!

---

### Post by andrewc6l on 2009-01-12
Write a script which does what you want.

```
#!/bin/bash
/path/to/amdump music
/path/to/amdump musiccd
```

Then run the script in your cron job instead of individual backup commands. (Obviously, replace /path/to with the real path to amdump :-) )

---

