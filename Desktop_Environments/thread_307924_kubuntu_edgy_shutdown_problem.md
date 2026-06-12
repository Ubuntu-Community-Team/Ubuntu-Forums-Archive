---
title: "kubuntu edgy shutdown problem"
date: 2006-11-27
forum: Desktop Environments
---

### Post by kebajonathan on 2006-11-27
Hi Guys,

I've already tried some solution, none worked... I'm running Kubuntu edgy (6.10) on a Thinkpad T22.

When I go to the Menu, click "log out", shutdown or reboot, I get into huge problems:
First, nothing happens for a few minutes! Then, suddenly, the title bars of the windows get away and if I'm lucky, it even closes the windows... Then, I'm left with a black screen showing only the mouse, and nothing happens until I issue Ctrl+Alt+F1 and reboot manually.

Do you know what I could do?

---

### Post by kebajonathan on 2006-11-28
Hey guys please!

My sister:twisted: 's gonna eat me up (she says so) if I don't get her pc to work....
:cry:
No really, if u know how to do it, please help...
:D

---

### Post by cmichaelboyd on 2006-11-28
sounds like it's waiting for a service to quit.....I'd start there.  Check out what daemons are running, and then kill'em one by one until the problem stops.  then figure out what was making the daemon so hateful.

---

### Post by kebajonathan on 2006-11-29
that's really painful... Don't u have another idea ?

---

### Post by cmichaelboyd on 2006-11-29
you could check your log files and see if you can find any messages about services exiting abnormally or with exit status 1 or anything that mentions exiting with an error.
 
If i can help anymore, let me know.
 
cheers

---

### Post by teyster2 on 2006-11-29
Try this - It worked for me. :-D 

Click on KMenu button
then "System Settings"
"Advanced Tab"
"Session Manager" button
"Default Shutdown Option"
Click on the "Turn off Computer"

Shutdown and restart work fine now.  I don't do hibernate.

---

### Post by cmichaelboyd on 2006-11-30
To narrow things down a bit, if kde is exiting abnormally, then it must be a service that relies upon kde's framework.  So start killing services that obviously are related to kde.  That's a good place to start.

---

### Post by kebajonathan on 2006-12-03
Strange, this only happens with one user: the one defined during the installation.

Anyway, I'll make a new user and hope it's going to work from now on

---

### Post by cmichaelboyd on 2006-12-03
well, i know that kde, by default, restores a session to it's previous state on startup.  If a person had run a kde program that was keeping the system from shutting down properly, it would probably continue to do it every time that user logged out.
To change the default behavior, open up your control center, and expand the "KDE Components" section, and click on "Session Manager".  Under the heading "On Login", the default setting will be "Restore Previous Session".  Change it to "Start with an Empty Session", and click apply.  Then reboot.

Maybe that'll help.

Cheers

---

### Post by towync on 2006-12-03
[SIZE="2"]I have similar but different shutdown problem, where I can clearly hear the harddrive shutting down, but the Kubuntu screen is still on, and I have to pull the plug to turn off everything. I tried the 2 Session Manager methods, but they're not working me =(. I also see the suggestion about damons and services, but I don't know how to open those to check, could someone post up command sequences to open those? (And some hints on how to kill of the bad services). Thanks very much :)[/SIZE]

---

### Post by cmichaelboyd on 2006-12-04
you can use 

ps -A

in a terminal window to list the services that are running, and to stop them immediately, you can type

killall *nameofservice*


if you need to disable a service so that it doesn't start at all on boot, you can:

apt-get install sysv-rc-conf

and then:

sysv-rc-conf

and un-x the service that you don't want to start, but BE CAREFUL, as you could easily disable a vital service.

hope that helps.

cheers,

chris

---

