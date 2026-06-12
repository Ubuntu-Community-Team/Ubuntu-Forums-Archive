---
title: "admin access?"
date: 2006-08-06
forum: Desktop Environments
---

### Post by Chase48 on 2006-08-06
i installed linux as a dual-boot with Windows XP, and i currently have Ubuntu 6.06 LTS (Dapper Drake), so my point is, HOW can I make it so i have administrative access, instead of not being able to do anything, or having to enter the password every time i type in an important command?

---

### Post by ardchoille on 2006-08-06
Use sudo for command line apps and gksudo for gui apps.. this will give you admin asscess to the system providing you are the system admin user.

The root account is disabled in Ubuntu 6.06LTS for security reasons and, in my opinion, should not be enabled. When someone tries to break into your computer, they know there is a root account. If the root account is disabled, it's much harder to break into it and they can't break into the user accounts because they don't know the which users to break into. The root policy in Ubuntu is an added security measure.

---

### Post by Chase48 on 2006-08-06
all i want is to be able to put things into my file folder so they dont overflow the desktop.. i want to have write access to my file system folder, and i am the only one who uses this computer so i should be admin shouldnt i?, im using linux as a personal thing

and one small side question, how do i run programs or MIDIS or mp3s?

---

### Post by petersjm on 2006-08-06
You should already have write privilages to your file system folders like /home/USER. If not, open the terminal (command line) and type gksudo nautilus (enter your password when prompted). Now navigate to the folder you want write privileges for and right-click it, then select PROPERTIES. Select the "Permissions" tab and click WRITE under "Owner" (make sure "file owner" is selected as you).

EDIT: As for running programs, it's just like Windows: Click it from the Applications menu on the top panel. Double-clicking an mp3 should run it automatically. I suggest you install Automatix from Synaptic (Applications > Add/Remove Programs) and then choose everything you need from that. Lots of useful things for newbies to install - I wouldn't be here without it! :)

---

### Post by Chase48 on 2006-08-06
do you have AIM or MSN?, your post was the most helpful, BUT when i typed gksudo nautilus i got this:

"GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed."

---

### Post by petersjm on 2006-08-06
I get the same warning, but does it not ask you for your password? If it does, enter it, click okay and give it a couple of seconds to work. Nautilus (file manager) should open up. Then you can do as I suggested above. Hope it works for you. I've only been on Linux for a few weeks, maybe a month at most. You'll soon get the hang of it.

---

### Post by Chase48 on 2006-08-06
do you have gaim or aim, msn, or whatever?

and it didnt ask me for my password after i got the error, it asked for it right before i got the error,

and when i click okay, the file browser comes up with a window and 1 folder, "root" in there

---

### Post by aysiu on 2006-08-06
Read these two links:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Chase48 on 2006-08-06
i read and im STILL confused.. what should i do?

---

### Post by aysiu on 2006-08-06
Want to fix yourself some dinner? Walk into the kitchen.

Want to take a nap? Go to bed.

Want to withdraw some money from your bank? Well, make sure you have your ATM card with you. Then find an ATM for your bank. Wait in line. Put your card in and enter your password (PIN) and specify what amount you want to withdraw.

It's called **security**.

You put obstacles in the way of doing certain things because the obstacles are easy for you to overcome (put in a password) and hard for others to overcome (figure out the password).

Same thing in Ubuntu and Mac OS X--it's called *sudo*.

Anyone with administrator capabilities runs as a regular user almost all the time (kitchen, bed). When she needs to do change system-wide settings or files, she needs to temporarily gain full administrative privilege (money from bank) and use a password to do so.

---

### Post by petersjm on 2006-08-07
I'm not on my Linux box at the minute so I can't post a screenshot, but when the file browser opens up, you should have folders listed on the left-hand side (like your username folder or "Home" as well as "File System" etc). Can't you navigate to the folder you want?

---

