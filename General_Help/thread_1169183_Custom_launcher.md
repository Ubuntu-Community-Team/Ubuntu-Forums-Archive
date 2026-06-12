---
title: "Custom launcher"
date: 2009-05-24
forum: General Help
---

### Post by BUSHYBOB on 2009-05-24
Is it possible to launch 2 seperate programs with a single launcher.

---

### Post by fermulator on 2009-05-24
I'm not sure.  I just tried with the following variations:

Command:
/usr/bin/vlc; /usr/bin/vlc <-- "/usr/bin/vlc;" isn't a valid command
/usr/bin/vlc /usr/bin/vlc <-- "this launches vlc with the arg "/usr/bin/vlc"
/usr/bin/vlc, /usr/bin/vlc <-- "/usr/bin/vlc," isn't a valid command
/usr/bin/vlc & /usr/bin/vlc <-- I'm not sure how that behaves...

Anyways, if you want a solution NOW .. you could simply create a script:

```
gedit ~/scripts/my_two_app_script.sh
```

```
#! /bin/bash
# My scrip to launch two apps
# Location: ~/scripts/my_two_app_script.sh

# Launch the first application and put it into the background
/usr/bin/app1 &

# Launch the second application and put it into the background
/usr/bin/app2 &
```

Save the file and close gedit.

Make it executable:
```
chmod u+x ~/scripts/my_two_app_script.sh
```

Created a custom application launcher and run the command:
> /home/my_user/scripts/my_two_app_script.sh

---

### Post by fermulator on 2009-05-24
NB: This thread ([http://ubuntuforums.org/showthread.php?t=862852](http://ubuntuforums.org/showthread.php?t=862852)) has a guy writing a generic "hackyscript" that fixes the problem.

Basically, in a terminal, if you execute
> /usr/bin/app1 & /usr/bin/app2
, it behaves as expected.

But in the custom application launcher, it doesn't.  This might be a bug?

---

### Post by BUSHYBOB on 2009-05-25
Yeah I've already done it the script way, I just wondered if there was a way that didn't require a script.

---

