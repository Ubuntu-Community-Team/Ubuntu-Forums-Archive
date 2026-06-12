---
title: "shell_exec() using cron not executing"
date: 2009-06-12
forum: General Help
---

### Post by kauboy on 2009-06-12
Hi,

I am using Ubuntu 9.04 x86-64 and have some problem getting a php script to execute the shell_exec() command, when run using gnome-schedule. The php script performs the shell_exec('command') properly when run from a terminal but the same does not work when cron (gnome-schedule) runs the same php script. I'm sure that the php script gets executed by cron and also that the shell_exec() command within the php script is not executed. Is there any workaround? Thanks!

---

### Post by hal8000 on 2009-06-12
I'd be tempted to post your script. As well as cron there is at daemon and anacron which can run scripts for you, as well as /etc/init.d/rc.local
Hope that helps

---

### Post by lamego on 2009-06-12
Please note that there is a significant difference on running a script from a terminal or from cron, cron does not load your user profile, if the script you are calling depends on user's profile initialization (like setting variables, PATH, etc) it will not work correctly.
You will need to load your profile and then run the script:. 
```
$HOME/.profile ; php ./script.php
```

---

