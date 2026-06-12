---
title: "Login as root on Kubuntu, how?"
date: 2005-07-20
forum: Desktop Environments
---

### Post by ozzie123 on 2005-07-20
Hello,

I'm new to Kubuntu (although I've used Ubuntu before) and found it quite a difference if we are using GNOME. Is there anyway to login as root account since I have to set my firestarter setting?

Thank you

---

### Post by codejunkie on 2005-07-20
[QUOTE=ozzie123]Hello,

I'm new to Kubuntu (although I've used Ubuntu before) and found it quite a difference if we are using GNOME. Is there anyway to login as root account since I have to set my firestarter setting?

Thank you[/QUOTE]
yes enable the root user with this command if you havent already 
```
sudo passwd root
``` enter the new root password now do this >  sudo kate /etc/kde3/kdm/kdmrc
find "AllowRootLogin"
change the value to "true"
save, logout, log back in as ROOT! hope this helps...

---

### Post by ozzie123 on 2005-07-20
Hello,

Thank you so much, that does helps alot (although I have to edit it with vim, kate crashes my computer!)

---

### Post by earther on 2005-08-20
[QUOTE=codejunkie]yes enable the root user with this command if you havent already 
```
sudo kate /etc/kde3/kdm/kdmrc
find "AllowRootLogin"
change the value to "true"
``` enter the new root password now do this  hope this helps...[/QUOTE]This isn't working for me.  I am not able to save the file once I make the changes.  Plus Kate is crashing.  It was so easy to enable root using Gnome but I prefer the KDE interface.  Any suggestions?

---

### Post by codejunkie on 2005-08-20
[QUOTE=earther]This isn't working for me.  I am not able to save the file once I make the changes.  Plus Kate is crashing.  It was so easy to enable root using Gnome but I prefer the KDE interface.  Any suggestions?[/QUOTE]
if kate keeps crashing just use another text editor like "nano" or "gedit" if it's still installed.

---

### Post by earther on 2005-08-20
[QUOTE=codejunkie]if kate keeps crashing just use another text editor like "nano" or "gedit" if it's still installed.[/QUOTE]Thanks for responding.  Even when Kate doesn't crash, it won't let me save - permission denied.  I tried su which gave me root access but permission was still denied.  What's up with that?

---

### Post by OCPJaguar on 2005-08-20
Try "kdesu kate" instead of "sudo kate" if that doesnt work there is kwrite

---

### Post by earther on 2005-08-20
[QUOTE=OCPJaguar]Try "kdesu kate" instead of "sudo kate" if that doesnt work there is kwrite[/QUOTE]Thanks but I got really frustrated and decided to reinstall Ubuntu/Gnome.

---

### Post by amastronardi on 2005-08-20
Why???  [-X  Kubuntu rocks  :)

---

### Post by improverrr on 2005-08-20
One little trick I learned when I use the Konsole.  9 out of 10 times I need to be logged in as root.  I right clcked on the Konsole icon, chose properties, then the application tab, under command:  change to read KDESU KONSOLE and hit ok.  Now when you click the icon it prompts for password and konsole will open up as root.

---

### Post by Velox Letum on 2005-08-20
When I open up a terminal window and need root for an extended period (not just a command or two) I do *sudo -i*

After that, nano, gedit, vim, whatever you like.

---

### Post by Oxygene on 2005-08-20
In cases where I need root access for a longer period I usually do* sudo bash* and finish with ^D

---

### Post by earther on 2005-08-20
[QUOTE=Oxygene]In cases where I need root access for a longer period I usually do* sudo bash* and finish with ^D[/QUOTE]I actually needed to snag an icon that was installed on root Desktop so sudo wouldn't work.  :(

---

### Post by crt on 2005-08-20
I think Kubuntu rocks too, I just wish they would default to the root user when you install and let you decide later to make another user account with a password, I don't need a password for Kubuntu there is nothing that important on my puter to warrant any kind of user security. Maybe the admins will read this and consider the idea in breezy.

R

---

### Post by f1dave on 2005-08-20
I understand what you're saying, I don't really need any security either. But when it is so easy to use sudo with extra parameters to have the same effect as su, I don't see the point in them switching from sudo to su. I like sudo to be honest, and if you read the developer's discussion on it there are some very good reasons it was implemented.

Cheers,
Dave.

---

### Post by manicka on 2005-08-21
[QUOTE=crt]I think Kubuntu rocks too, I just wish they would default to the root user when you install and let you decide later to make another user account with a password, I don't need a password for Kubuntu there is nothing that important on my puter to warrant any kind of user security. Maybe the admins will read this and consider the idea in breezy.

R[/QUOTE]
 Everyone needs some level of security. If we all logged in with root priviliges, then in no time we'd have another windows on our hands. 
Being asked for permission to install or run certain things is your greatest security blanket in Linux and prevents the sort of problems that windows users experience.

---

### Post by lotech on 2005-08-21
Hi there,

I got exactly the same problem, and I use PICO for editing and it works. Btw, this is little off topic but still related to root logon. I need to sync. my PC clock via the internet, and I right click on the clock and select adjust date and time, it asked for password but I haven't created one for root yet, now that I have the password and try again, but the box does not come out anymore, it seems the the app. is locked, how do I release it ?

Thanks a lot !

---

### Post by GeneralZod on 2005-08-21
[QUOTE=manicka]Everyone needs some level of security. If we all logged in with root priviliges, then in no time we'd have another windows on our hands. 
Being asked for permission to install or run certain things is your greatest security blanket in Linux and prevents the sort of problems that windows users experience.[/QUOTE]

Couldn't agree more - every desktop Linux distribution should *always* be as secure as possible by default.  If someone wishes to trade some security for convenience then that's their call to make (although I genuinely cannot fathom why someone would want to run KDE as root - still, takes all sorts, I guess :)) but it should never, ever be the default else we'll have a spyware epidemic just as bad as that currently afflicting Windows users.

---

### Post by earther on 2005-08-22
[QUOTE=OCPJaguar]Try "kdesu kate" instead of "sudo kate" if that doesnt work there is kwrite[/QUOTE]I reinstalled Kubuntu on another box and tried your suggestion.  It worked!  Kate didn't crash and allowed me to save the setting.  I can now login as root.  Thank you!

---

