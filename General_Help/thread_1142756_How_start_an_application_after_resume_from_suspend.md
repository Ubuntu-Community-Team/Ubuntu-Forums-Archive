---
title: "How start an application after resume from suspend?"
date: 2009-04-29
forum: General Help
---

### Post by yellowman on 2009-04-29
I would like to kill an application when I suspend and start it when I resume from suspend.
What is the best way of doing that?

I have tried to add a file like: /etc/pm/sleep.d/06xbmc

```
#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
hibernate|suspend)
killall -9 xbmc.bin
;;
thaw|resume)
xbmc
;;
*)
;;

esac

exit $?
```

But that didn´t work, it seems to fail when resuming, var/log/pm-suspend.log says something about no display if I remember correctly.

---

### Post by kpkeerthi on 2009-04-29
You need to specify which display to use:

```

thaw|resume)
export DISPLAY=:0
export XAUTHORITY=/home/<your-user>/.Xauthority
xbmc
;;

```

* export XAUTHORITY is probably not required.
* export DISPLAY=:0.0 could also be used.
* you might want to use full path /usr/bin/xbmc
* acpi must be restarted.

---

### Post by kpkeerthi on 2009-04-29
Noticed that you might need to specify absolute path to xbmc. You can find that using ```
which xbmc
```

---

### Post by yellowman on 2009-04-29
Ok, thanks a lot! I´ll give it a try.

Btw. what do you mean by "acpi must be restarted"?

---

### Post by kpkeerthi on 2009-04-29
> **yellowman said:**
> Ok, thanks a lot! I´ll give it a try.

Btw. what do you mean by "acpi must be restarted"?

```
sudo /etc/init.d/acpid restart 
```

---

### Post by yellowman on 2009-04-29
I tried that now, but it didn't work. Maybe I did something wrong.

This is what the log looks like, if that  helps:
[http://pastebin.com/ma5b2506](http://pastebin.com/ma5b2506)

---

### Post by yellowman on 2009-05-02
While trying to debug this, I found out that if I run "sudo pm-suspend" from the console it resumes just fine and the script works, xbmc starts.

But if I run by clicking suspend in the gui, the script fails and xbmc does not start. So I wonder what the difference is?

Any ideas?

---

### Post by d98jh on 2009-05-11
Had any progress yet? I'm trying to do the same thing because of the mouse cursor bug in xbmc on jaunty. Is that what you're trying to work around as well?

---

### Post by yellowman on 2009-05-13
If you want to get rid of the mousecursor try installing "unclutter", hides the mouse after x seconds.

I was trying to get around that my remote didn´t work after resume, as xbmc wouldn´t reconnect to lirc.
I eventually worked around it by restarting gdm on resume.

---

### Post by mizunoX on 2009-05-14
> **yellowman said:**
> 
I was trying to get around that my remote didn´t work after resume, as xbmc wouldn´t reconnect to lirc.
I eventually worked around it by restarting gdm on resume.

Do you think you'd be able to provide instructions for restarting gdm on resume?  I have the same issue with lirc and xbmc in jaunty.

---

### Post by yellowman on 2009-05-14
> **mizunoX said:**
> Do you think you'd be able to provide instructions for restarting gdm on resume?  I have the same issue with lirc and xbmc in jaunty.

My script looked like this I think:
```
#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
hibernate|suspend)
if ps -ef|grep -v grep|grep -i xbmc.bin
then
# If it's running, kill it
killall -9 xbmc.bin
fi
;;
thaw|resume)
sudo /etc/init.d/gdm -restart
;;
*)
;;

esac

exit $?
```

Writing from memory, so I´m not sure it is correct. Then I started xbmc with the .profile file in my home folder.

Also have scripts for restarting lirc and lcdd, like desribed in this post: [http://www.xbmc.org/forum/showpost.php?p=248992&postcount=8](http://www.xbmc.org/forum/showpost.php?p=248992&postcount=8)

I´m running xfce as a window manager btw.

---

