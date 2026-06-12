---
title: "Helping create Firefox profile remotely (from Windows)"
date: 2012-06-14
forum: Desktop Environments
---

### Post by sccuser on 2012-06-14
Hi guys,
I'm trying to create Firefox profile from remotely (Windows) using "plink" tool, but it does not work in many cases.

First case
> 
plink.exe -l ***user_name*** -pw ***password*** ***user_name***@192.168.x.x DISPLAY=:0 firefox -createprofile "***user_name*** /home/***user_name***/Profiles/Firefox"


it's OK, but the target of profile folder is random (not expected target).

> 
Success: created profile '***user_name*** /home/***user_name***/Profiles/Firefox' at '/home/***user_name***/.mozilla/firefox/2titb3xh.***user_name***/prefs.js'


Second case: but when I wrapped the above command by ' mark (apostrophe mark)

> 
plink.exe -l ***user_name*** -pw ***password*** ***user_name***@192.168.x.x DISPLAY=:0 'firefox -createprofile "***user_name*** /home/***user_name***/Profiles/Firefox"'


it returns

> 
bash: firefox -createprofile ***user_name*** /home/***user_name***/Profiles/Firefox: No
such file or directory


Any help much appreciated!
Thanks so much!

---

