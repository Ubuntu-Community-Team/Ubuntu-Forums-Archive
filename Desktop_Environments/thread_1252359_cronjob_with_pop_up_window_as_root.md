---
title: "cronjob with pop up window as root"
date: 2009-08-28
forum: Desktop Environments
---

### Post by emkersyt on 2009-08-28
Hi, anybody can tell me if it's possible to execute a graphical app from a root cronjob?
I am trying to run a script which uses the command gmessage in order to pop up a window with a warning when the battery runs low.
I choose to edit root's crontab because my machine needs root permissions to shut down which is the last step in that script when the battery falls below 4% capacity. I don't want to change the permissions for shutting down. I just want that cronjob to come up with that little window under root (because it is necessary for the script to terminate). The script works if I let it run under the user's crontab except that the machine won't shut down.

That is the enty in root's crontab (not /etc/crontab)
```
*/5 * * * * env DISPLAY=:0.0 /root/scripts/batpowershutdown
```
"batpowershutdown" is the script as you might have guessed:

```
#!/bin/sh

# little script to shut down the machine when battery power reaches a critical
# level


battperc=$(acpi -b | cut -d , -f 2 | cut -d % -f 1)

case $battperc in
10)
  gmessage -display :0.0 -geometry 400x30 -timeout 300 -name ALERT -bg "#c90" "Battery power is critical!! Please plug in soon!!"
;;
6)
  gmessage -display :0.0 -geometry 400x30 -timeout 120 -name ALERT -bg "#c90" "Battery power is critical!! Forced shutdown in 2 minutes!!"
;;
4)
  shutdown -h now "Sorry, I am out of energy. Goodbye!"
;;
esac
```

Btw: I know this is a Ubuntu forum, my machine runs Debian, but that shouldn't make much of a difference. Maybe there is one in terms of larger security restrictions, though, not sure in that case.

---

### Post by emkersyt on 2009-08-28
I just realized I got the display parameter twice but I tried before with and without it in the script as well as in the crontab. The scripts starts running: if I put an echo command at the beginning for debugging it returns the output from it. It's just the GUI part which makes trouble.

---

