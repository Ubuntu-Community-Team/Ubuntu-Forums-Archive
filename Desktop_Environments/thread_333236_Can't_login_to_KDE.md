---
title: "Can't login to KDE"
date: 2007-01-07
forum: Desktop Environments
---

### Post by beow on 2007-01-07
I recently changed xorg.conf in order to get higher resolution on my screen and it works fine. I have two accounts, one for myself and one for my son. Now I can log into my account with correct resolution and all is hunky dory. But when I try to log into my sons account from kdm (or gdm, tested both) it is not possible and I ends up with the following .xsession-errors log:

```
Xsession: X session started for filip at sön jan  7 11:22:44 CET 2007
Traceback (most recent call last):
  File "/usr/bin/displayconfig-restore", line 297, in ?
    main()
  File "/usr/bin/displayconfig-restore", line 227, in main
    FixXorgDPI(dpi)
  File "/usr/bin/displayconfig-restore", line 84, in FixXorgDPI
    w_dpi = float(width)/(float(width_mm)/25.4)
ZeroDivisionError: float division
startkde: Starting up...
DCOP aborting call from 'anonymous-5492' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
startkde: Shutting down...
klauncher: Exiting on signal 1
startkde: Running shutdown scripts...
startkde: Done.
```

_I now wonder in which user configuration files settings about start up behaviour of KDE are_, so that I can compare my own that works, with my sons. Note that I have to fix his configuration from the shell since I can't do a graphical login.

---

### Post by obsidion on 2007-01-07
Can you log into his account from a terminal ?
ie from the login screen alt-ctrl-F2 and try to log in as him, this will check that his account is still valid. If this works check the .xsession-errors in his home folder, that may give you a pointer. You could try giving him a new account as administrator from Kuser and see if you can log in to that.  You could also try going to the tmp directory and deleting any directories referring to your son, making sure you sudo the command.

---

### Post by beow on 2007-01-07
Yes, his account is valid, I did "su filip" and took the .xsession-errors from his account. I'm sure it's a KDE configuration issue, because I can login alright to his account using a Gnome session. 

So the question is which KDE configurations files comes into play, so I can compare with my own KDE files. I'm hesitant to give him admin rights, I want to confine the problems to his account... :-|

---

### Post by ingo on 2007-01-07
Your problem appears to have something to do with kded - and you are not the first one to experience problems with that. Are you per chance running kat? If so, try uninstalling it (go for beagle & kerry) and update us.

---

### Post by obsidion on 2007-01-07
> **beow said:**
> Yes, his account is valid, I did "su filip" and took the .xsession-errors from his account. I'm sure it's a KDE configuration issue, because I can login alright to his account using a Gnome session. 

So the question is which KDE configurations files comes into play, so I can compare with my own KDE files. I'm hesitant to give him admin rights, I want to confine the problems to his account... :-|


  Not sure where to look unless since you can log in to gnome you set the display fro kde from there, don't have gnome on my computer so not sure if you can, try running systemsettings from alt-F2 and adjusting the display.
   Have you delteted his tmp files, I know when I was using fedora a few years ago, kysoca sometimes caused some problems. The other thing to do is to cd to his homefolder from a terminal as superuser and see if there are some .DCOPserver files and rm them. I'm shooting in the dark a little here as it has been a long time since I used Fedora and had this problem. It occured in that distro when I upgraded my kde.

---

### Post by beow on 2007-01-07
ingo & obsidion,

thanks for your tries. Nope "kat" is not installed. There is no .DCOP* flies on filip's account. 

Which KDE configuration files can i remove from his account to have KDE start from scratch?

---

### Post by beow on 2007-01-07
Problem solved. I just deleted his .kde directory and started over again... not the most scientific solution, but an easy fix in this case. Thanks for your help.

---

### Post by hal10000 on 2007-01-07
You should delete any of your sons files in /tmp directory **and** delete (or rename if there are configurations which you want to preserve) the /home/yourson/.kde folder. 
Upon new login, the .kde directory will be recreated.

---

### Post by ingo on 2007-01-07
> not the most scientific solution but it worked!!!

---

### Post by obsidion on 2007-01-07
> **beow said:**
> Problem solved. I just deleted his .kde directory and started over again... not the most scientific solution, but an easy fix in this case. Thanks for your help.

  Must admit to having done the same in the past, however like you I want to find the actual cause, I suspect it was a stray tmp file in the .kde directory or a borked config file. I have been looking through mine trying to figure out which one it could be but haven't had any luck so far.

---

### Post by Abernard on 2007-01-14
I also have a problem with loging in to KDE and this seemed like a good place to ask for help.

I am running Kubuntu 6.10, recently installed and only one user. After changing some settings in the boot/grub/menu.lst  and xorg.conf files I can't log in to KDE. When I type in the password, screen goes blank as if loading the session (before the actual loading screen) and there is some hardware activity. But then it jumps back to the log in screen with my username and empty password field, with no error messages displayed.

I reverted the changes in menu.lst and xorg.conf (made backups before editing) just in case, but that didn't solve the problem. After doing that from the terminal mode I tried to run startx and got the following error messages

> Fatal server error:
Caught signal 11. Server abortin
xinit: connection to X server lost.


I can log in to terminal, use failsafe setting etc. so I suspect it's a KDE "thing".

What can be the problem at what are possible solutions?

(if you need aditional info just ask)

---

### Post by hal10000 on 2007-01-14
remove /tmp/.X0-lock: [COLOR="Red"]sudo rm /tmp/.X0-lock[/COLOR], then log in again

If this does not work, then try as I described in my upper  posting.

---

### Post by Abernard on 2007-01-14
No such file or directory.

But your previous advice - deleting the .kde directory in users home directory worked. Thank you for the advice. (Dismissd the solution previously due to own stupidity.)

To any other newbies with the same problem - the .kde directory wasn't shown in the home directory in terminal mode. I just took a leap of faith and run "sudo mv .kde kde_backup" command. Worked.


(still wondering what went wrong tho)

---

### Post by steevc on 2007-01-18
I have a similar problem. I seem to have broken my KDE startup after trying to get my old nvidia card working. Other accounts can log in fine, but mine just comes up with the KDE background and a Konsole window with no title bar. Running Kicker gets me the main menu, but I can't move windows or do much else. I've renamed my .kde with no change in the results.

Any ideas?

---

### Post by hal10000 on 2007-01-18
There's a file in your homedirectory called .xsession-errors. Remove it: [COLOR="Red"]rm .xsession-errors[/COLOR] Then log out an log in again. The .xsession-errors file will be recreated. Post the output.

---

### Post by steevc on 2007-01-20
This is what I got on the last log in, but it's different to what I had before. This time I got a pop-up complaining about DCOP, but the end effect was the same. I'll try it again later and report if it's any different.

```
Xsession: X session started for steve at Sat Jan 20 11:12:41 GMT 2007
DCOPClient::attachInternal. Attach failed Could not open network socket
Link points to "/tmp/ksocket-steve"
kdeinit: DCOPServer could not be started, aborting.
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket

```

---

### Post by hal10000 on 2007-01-20
@steevc:
remove /tmp/ksocket-steve, but NOT with sudo:
[COLOR="Red"]rm -r /tmp/ksocket-steve[/COLOR]
if this does'nt work, then remove all your files in tmp (NOT WITH SUDO):
[COLOR="Red"]rm -r /tmp/*[/COLOR]

---

### Post by steevc on 2007-01-20
> **hal10000 said:**
> @steevc:
remove /tmp/ksocket-steve, but NOT with sudo:
[COLOR="Red"]rm -r /tmp/ksocket-steve[/COLOR]
if this does'nt work, then remove all your files in tmp (NOT WITH SUDO):
[COLOR="Red"]rm -r /tmp/*[/COLOR]

Doing the first of those has fixed it! I have my old desktop back in it's full glory.

Thanks hugely.

---

### Post by hal10000 on 2007-01-20
It sometimes happens on an unclean shutdown that the /tmp files for the user can't be removed by the system, so you have to do this manually.

---

