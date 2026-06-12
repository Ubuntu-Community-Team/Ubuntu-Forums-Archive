---
title: "Firewall recommendations?"
date: 2005-12-17
forum: General Help
---

### Post by DJiNN on 2005-12-17
Hi there.

Been using "Firestarter" on Breezy, which is OK, but not sure how to get it to start when i Boot. Can anyone point me towards a solution & also any recommendations on other firewalls? I would love to know what's available & what people are using. I've heard of one called "Bulldog" (Or is it Guardog?) but have never tried it.

Any info or help would be much appreciated.

DJiNN

---

### Post by hajk on 2005-12-17
If you have installed the Ubuntu Firestarter package, then it runs automatically at boot. Starting the Firestarter window in Applications/System Tools is independent of its running, and allows you to modify the firewall rules, check for  "events", etc.

---

### Post by zekolas on 2005-12-17
I think most linux firewalls are just gui front ends to iptables if I am not mistaken so use what ever firewall has the best interface. I myself do not run any firewall, I don't see the need because I don't run any servers from my machine. I am however behind a router.

---

### Post by jamesford on 2005-12-17
how to make the gui run at startup: [http://fs-security.com/docs/faq.php](http://fs-security.com/docs/faq.php)

---

### Post by ykpaiha on 2005-12-17
[QUOTE=DJiNN]Hi there.

Been using "Firestarter" on Breezy, which is OK, but not sure how to get it to start when i Boot. Can anyone point me towards a solution & also any recommendations on other firewalls? I would love to know what's available & what people are using. I've heard of one called "Bulldog" (Or is it Guardog?) but have never tried it.

Any info or help would be much appreciated.

DJiNN[/QUOTE]
I personnaly rather prefer guarddod as firewall to manage easly my system
You just add your own config and validate it 
It comes as well with some preconfiguration that you just have to check.
[http://www.simonzone.com/software/guarddog/#screenshots](http://www.simonzone.com/software/guarddog/#screenshots)

---

### Post by DJiNN on 2005-12-17
Many thanks to all those who have replied. It's much appreciated. I have been using Firestarter but (& i don't know why) it's not loaded at boot time for some reason. I have to do it manually & when i try & save the current session (Which, i must admit has been less & less because Linux stays up & running longer & stronger than XP) .... :) it say's that you can't do this with FireStarter, and that it must be started manually each boot time.

Anyway, no real problems, i'm sure that i will get it sorted eventually.... just wanted to say "Huge Thanks!" to all the people that have helped me so far.... this place is incredible for help & advice. I'm so glad that i chose Ubuntu! :)

DJiNN

---

### Post by Toxicity on 2005-12-17
1. On your dropdowns System>Preferences>Sessions
2. Navigate to the Startup tab
3. add whatever you want, I would say leave it at order 50 unless you have a custom layout order.

Here just add:
Command: gksudo /usr/sbin/firestarter 
(It must be that exact string as firestarter is a root application you need to run it as a superuser, since you dont want to have to give password input you use gksudo (as used it many menu items.))

If your method works great, but this might make things simpler for future wants like this. It's convenient having gaim start right up.

---

### Post by linrasta on 2005-12-18
i tried gksudo and it still asked for a password!  What am I doing wrong?

---

### Post by duminas on 2005-12-18
Make sure you added the required line in sudoers?
```
$ sudo gedit /etc/sudoers
```
If you don't have it in there, add this, replacing the bolded things with your username:
```
**username** ALL= NOPASSWD: /usr/sbin/firestarter
```
That should make it not prompt for a password.

Such being said, random technical question time. Is iptables always starting at bootup, if anyone might know? Not the Firestarter GUI.

---

### Post by DJiNN on 2005-12-18
[QUOTE=Toxicity]1. On your dropdowns System>Preferences>Sessions
2. Navigate to the Startup tab
3. add whatever you want, I would say leave it at order 50 unless you have a custom layout order.

Here just add:
Command: gksudo /usr/sbin/firestarter 
(It must be that exact string as firestarter is a root application you need to run it as a superuser, since you dont want to have to give password input you use gksudo (as used it many menu items.))

If your method works great, but this might make things simpler for future wants like this. It's convenient having gaim start right up.[/QUOTE]

Toxicity.... that's exactly what i'm looking for.... thanks for that. I have just pasted it in so next time i start i shall check it out & see how it goes. That should make things a lot easier in future. :) I shall try a few other programs as well (Like Gaim, as you mentioned) just to see what happens. :)

Many thanks for your help, much appreciated.

DJiNN

---

### Post by DJiNN on 2005-12-18
[QUOTE=duminas]Make sure you added the required line in sudoers?
```
$ sudo gedit /etc/sudoers
```
If you don't have it in there, add this, replacing the bolded things with your username:
```
**username** ALL= NOPASSWD: /usr/sbin/firestarter
```
That should make it not prompt for a password.

Such being said, random technical question time. Is iptables always starting at bootup, if anyone might know? Not the Firestarter GUI.[/QUOTE]

Hi duminas.... thanks for that. I did that, and then went in again because i forgot to put in the username.... & i got this error.

>>> sudoers file: syntax error, line 22 <<<
sudo: parse error in /etc/sudoers near line 22

& couldn't get into the sudoers file again.... i must have done something wrong somewhere but i'm not sure what it is.... any ideas?

Thanks for your help.

DJiNN

---

### Post by Knomefan on 2005-12-18
First off, the easiest way to edit the sudoers file again is probably to boot into a LiveCD like Knoppix and edit the file from there. (You could also try to boot into rescue mode and see if this helps, though I can't really comment on this, as I never used it).

Second, some general comments.
As others have stated, firestarter is just a frontend to iptables, which runs as a daemon. So there is absolutely no need to have the firestarter gui running, your firewall (iptables) will work anyway. In fact, always having a program running as root in X is a rather bad idea.

Further, if you change the sudoers file, don't use gedit, but visudo. This way, before you save, the syntax of the file will be checked to prevent the troubles you are now experiencing.

Hope this helps.

---

### Post by DJiNN on 2005-12-18
[QUOTE=Knomefan]First off, the easiest way to edit the sudoers file again is probably to boot into a LiveCD like Knoppix and edit the file from there. (You could also try to boot into rescue mode and see if this helps, though I can't really comment on this, as I never used it).

Second, some general comments.
As others have stated, firestarter is just a frontend to iptables, which runs as a daemon. So there is absolutely no need to have the firestarter gui running, your firewall (iptables) will work anyway. In fact, always having a program running as root in X is a rather bad idea.

Further, if you change the sudoers file, don't use gedit, but visudo. This way, before you save, the syntax of the file will be checked to prevent the troubles you are now experiencing.

Hope this helps.[/QUOTE]

Thanks for that Knomefan.... it certainly does help, but not before i had to search for how to go into recovery mode & edit the sudoers fils from there. It was actually the Firestarter Stratup line that was put in there by going into SYSTEM>PREFERENCES>SESSIONS that caused the problem in the first place... :???:  

But there you go, at least i learnt something from it all, and to be honest, it didn't really take that long to fix (With the help of scouring these posts) & would have taken a lot longer for a similar problem on XP.... so it was fun. :)

I've a lot to learn that's for sure, & i think i really need to read some basic primers on the way that Linux operates etc. :)

I think the problem here is the whole "Windows Legacy Thinking" if you get what i mean? Using XP, i would have a firewall, several spyware progs, a couple of Virus checkers etc etc etc..... & this all behind a Netgear Firewall/Router!!  

So, scrap the "Legacy OS" in my head & start again..... & i'm REALLY enjoying it! :)

Thanks ever so much for the heads up, much appreciated.

DJiNN

---

