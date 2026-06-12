---
title: "How to login with user-environment set to Bash shell then automatically change path"
date: 2018-02-01
forum: Desktop Environments
---

### Post by abdulbadii on 2018-02-01
[COLOR=#000000][FONT=Verdana]How do a user login with full user-environment preset to Bash shell then automatically do path modification with few script codes, either on command-line or put it in a script file.
what i tried:

bash --login -c PATH="/ANewPath:${PATH}"
bash --login -c 'PATH="/ANewPath:${PATH}"; export PATH'
bash --login -c 'export PATH="/ANewPath:${PATH}"'
bash --login ~/ChangePath.sh

with no avail

Anybody please usefully and sincerely help me...
Thanks in advance[/FONT][/COLOR]

---

