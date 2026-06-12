---
title: "Desktop freezes every 4 seconds"
date: 2006-02-03
forum: Desktop Environments
---

### Post by VinceDee on 2006-02-03
This is about to drive me insane. Every 4 seconds whatever I'm doing freezes for about a 1/2 second. It's really frustrating because it's making my desktop feel almost unusable.

Breezy 5.1 install just done two days ago.
Installed Apache/MySQL/PHP via the awesome step-by-step instructions included in the Ubuntu help files.
Installed almost all of the Automatix program files.
Installed the 3D Desktop switcher.

It's as if some process is hogging up all the CPU every few seconds. What's the best way to check what it could be?:???: 

Thanks

Edit: Oh, I forgot to add that it's only been doing this today (that I've noticed), since before I installed the 3D Desktop (at least I'm pretty sure that's how it went).

---

### Post by jerome bettis on 2006-02-03
[quote=VinceDee]This is about to drive me insane. Every 4 seconds whatever I'm doing freezes for about a 1/2 second. It's really frustrating because it's making my desktop feel almost unusable.

Breezy 5.1 install just done two days ago.
Installed Apache/MySQL/PHP via the awesome step-by-step instructions included in the Ubuntu help files.
Installed almost all of the Automatix program files.
Installed the 3D Desktop switcher.

It's as if some process is hogging up all the CPU every few seconds. What's the best way to check what it could be?:???: 

Thanks

Edit: Oh, I forgot to add that it's only been doing this today (that I've noticed), since before I installed the 3D Desktop (at least I'm pretty sure that's how it went).[/quote]

you can type "top" from a terminal or you can goto applications > system > system monitor to see your cpu usage.  kinda like task manager in windows i guess.  the processes tab has the cpu column, sort it by that and see what the problem is.

---

### Post by VinceDee on 2006-02-03
[QUOTE=jerome bettis]you can type "top" from a terminal or you can goto applications > system > system monitor to see your cpu usage.  kinda like task manager in windows i guess.  the processes tab has the cpu column, sort it by that and see what the problem is.[/QUOTE]

I, for one, cannot believe how stupid I am for not thinking of the system monitor program myself ](*,) 

I started it and it showed the CPU pegged at 100%!  I don't know what was doing it, but I'm going to suspect the 3D desk program, since that was the last thing I installed before I really noticed the issue.

Thanks for the help \\:D/

---

### Post by toorima on 2006-02-03
It is 3ddesktop yes, to fix the freezing edit /etc/3ddesktop/3ddesktop.conf
add the line 
```
autoacquire 60
```
then it will "update" all desktops every 60 sec. Im not sure but if you set it to 0 it disables the update of desktops I think

---

### Post by jerome bettis on 2006-02-03
the 3ddesk thing is sweet

and what was suggested above might help, but there's a better way.

goto system > preferences > sessions .  click the startup programs tab, hit add and paste this into there: 3ddeskd --acquire=100 --fastest . set the order to like 51.

log out / log in again and try that.  if it still pegs the cpu remove the --fastest flag and try again.  still no luck with that, have a look at the config file, turn the texture down to 512 and maybe try some different views.

the cylinder thing took forever on my machine, but the bigmoney view is fast and pretty sweet as well.

---

