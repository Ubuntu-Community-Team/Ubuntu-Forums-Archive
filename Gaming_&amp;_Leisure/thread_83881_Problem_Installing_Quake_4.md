---
title: "Problem Installing Quake 4"
date: 2005-10-29
forum: Gaming &amp; Leisure
---

### Post by Mantra Locust on 2005-10-29
Okay, I went out and bought Quake 4, hoping I'd have no problems installing it. I've read through the Linux Installation instructions, which tells you to copy files from the CDs and put them in the /usr/local/games/quake4/q4base folder. I can copy the files from the 1st CD with no problem, but the 2nd CD and on-ward, I get a dialog that states "You do not have permission to view files on this volume". I've changed my user privleges and placed myself under the root group with no success. If any one could help me, I'd be most greatful. Thanks.

---

### Post by Stampe^lol? on 2005-10-29
Have you tried to mount the cd after umount?
My installation went well - I've got the DVD edition.

---

### Post by Mantra Locust on 2005-10-29
How do I go about doing that?

---

### Post by dmn_clown on 2005-10-30
[QUOTE=Mantra Locust]I can copy the files from the 1st CD with no problem, but the 2nd CD and on-ward, I get a dialog that states "You do not have permission to view files on this volume".[/QUOTE]

```
sudo mount /dev/cdrom
```

---

### Post by Mantra Locust on 2005-10-30
[QUOTE=dmn_clown]```
sudo mount /dev/cdrom
```[/QUOTE]

When I do this, it states that the device is already mounted and I still get the dialog that "I do not have permission to view contents on this volume".

---

### Post by rseymour on 2005-10-30
I had the same problem on cds 2, 3, & 4.

finally gave root a non-random pw, logged in as root, copied the files, reset permissions, logged out, and logged back in under the user account.

---

### Post by dmn_clown on 2005-10-30
[QUOTE=rseymour]I had the same problem on cds 2, 3, & 4.

finally gave root a non-random pw, logged in as root, copied the files, reset permissions, logged out, and logged back in under the user account.[/QUOTE]

you could have just ```
sudo cp /path/to/cdrom/Setup/Data/q4base/*.pk4 /path/to/your/quake4/q4base
```

Accomplishes the same thing.

---

### Post by Mantra Locust on 2005-10-30
[QUOTE=rseymour]I had the same problem on cds 2, 3, & 4.

finally gave root a non-random pw, logged in as root, copied the files, reset permissions, logged out, and logged back in under the user account.[/QUOTE]

How do you go about giving root a non-random password? I'd like to log in as root, but I don't know how to go about setting that up. :P In most distros, you set up the root account at setup, but not in Ubuntu! :P

---

### Post by rseymour on 2005-10-30
> you could have just
Code:

sudo cp /path/to/cdrom/Setup/Data/q4base/*.pk4 /path/to/your/quake4/q4base


tried that - got the "you don't have permission" response/problem; googled and looked through the forum and didn't find a "fix"

> How do you go about giving root a non-random password? I'd like to log in as root, but I don't know how to go about setting that up. :P In most distros, you set up the root account at setup, but not in Ubuntu! :P

you can change by command (I think it's root passwd, but don't trust that; I'm sure someone else can help) ... since I can never remember commands you can go to system->administration->users and groups; select the root user; then properties; then set password by hand and then enter the password

obviously this negates the intent of ubuntu's superuser concept ... I personally like the sudo setup since my fingers are usually faster than my brain ... I avoid logging in as root except as a "last resort"

---

### Post by Mantra Locust on 2005-10-30
[QUOTE=rseymour]tried that - got the "you don't have permission" response/problem; googled and looked through the forum and didn't find a "fix"



you can change by command (I think it's root passwd, but don't trust that; I'm sure someone else can help) ... since I can never remember commands you can go to system->administration->users and groups; select the root user; then properties; then set password by hand and then enter the password

obviously this negates the intent of ubuntu's superuser concept ... I personally like the sudo setup since my fingers are usually faster than my brain ... I avoid logging in as root except as a "last resort"[/QUOTE]

I figured out how to change the root password right after I posted that reply above. You goto System > Administration > Users and Groups then Check "Show all Users and Groups".

But now I don't know how to log on as root, because you can't do it through the main login.

---

### Post by Mantra Locust on 2005-10-30
Alright, I finally found a fix.

I opened up a terminal window and entered the following
```
gksudo nautilus 
```

And accessed the cdrom from there. :)

---

### Post by krye on 2005-10-31
Altough it is not encouraged to use the root account, you can set it up by just entering the 'sudo passwd' command...

Then you will be able to use su - to switch to the superuser account, or log in as root.

---

### Post by Mantra Locust on 2005-10-31
I wasn't aware of that, but I'll keep that in mind for future reference. :)

The bad thing about it now is that I finally have it installed and running, but now my sound doesn't work right :P I've set the sound drivers to oss and changed it to 2 speakers, but then it gets to stuttering. :/

---

### Post by rseymour on 2005-10-31
> But now I don't know how to log on as root, because you can't do it through the main login.

system->administration->login screen setup->security tab->allow root to login with GDM

---

