---
title: "Bypass Ubuntu Login Screen &quot;Safetly&quot;"
date: 2007-11-28
forum: Desktop Environments
---

### Post by clark.peter on 2007-11-28
Hi there.

I wanted to bypass the login screen each time I boot up the computer and I found this:

[I]   1. First go to System,Administration. Select Login Window
   2. A dialog will appear, Select Security Tab
   3. Check Enable Automatic Login, then select the name of the default user
   4. You're done, the next time your Ubuntu boots, you will be automatically be logged in as the default user.
[/I]

Everything is OK, but I am wondering if it is possible to Lock the session automatically after the automatic login. Let me explain you:

- I want the computer to boot up when I am not at home (configuring the BIOS settings) 
- I want Ubuntu to start automatically and login as my user.
- But I want to lock the screen so nobody can use the computer unless he knows the password.
- I want to do that because I want to use p2p at a range of time when I am not at home but I don't want anybody to access my computer. I also do not want anybody to start my computer manually and be logged automatically in Ubuntu.

Is there any way of get this?

Thank's in advance. Ubuntu 4ever

---

### Post by HJB on 2007-11-28
Hi there.
It is only the gui which is not 'logged in' when your system boots up.
You dont need to log into the gui to start a p2p application
If you use rtorrent (best one I found), its even possible to start it remotely.
All you need to start a program is a script. Either in crontab or at the bootup process, which thrn starts you program.
example:
crontab -e

05 08,12,22 * * * sh ~/MyDocuments/scripts/start_my_appy..sh
Then in that folder place the script start_my_appy..sh, and make it executable

example:
nano start_my_appy..sh
#!/bin/bash
screen rtorrent

Hope this helps
Bye

---

### Post by Prospero2006 on 2007-11-28
I would tend to agree with the second poster. 
You can also add lines to /etc/rc.local 
These commands are executed right before the gdm or kdm
manager fires up and presents login info. 
You really don't need the gui for remote services.

Ok, having said that I'm sure there is a way to lock the screen right away.
The keyboard sequence to do it is ctrl-alt-L

Pros

---

### Post by clark.peter on 2007-11-28
Thanks a million for the answers. 

As you said I can start a p2p program (i.e. azureus) without logging in Gnome but,
will it use the settings that are on my gnome profile or will it start the application with the default options?

Anyways, I will still prefer to login in Gnome and lock the screen automatically, so my session is ready when I arrrive home and I don't need to login, I just need to unlock it. Any trick to lock the screen automatically?

Cheers.

---

### Post by Znort_Ubern00b on 2007-11-28
you could always set up your screensaver to lock after 1 min of inactivity and this requires password to get back to desktop...

---

### Post by clark.peter on 2007-11-28
> **Znort_Ubern00b said:**
> you could always set up your screensaver to lock after 1 min of inactivity and this requires password to get back to desktop...

Yes, but in this case some could start the computer and access my desktop before the screensaver is activated

---

### Post by Znort_Ubern00b on 2007-11-28
thing is if you set it up to log in automatically then anyone else that turns on PC will log in as you...so if its on and locked then they could just power off using button turn on and log in as you...you would be best using the other option in first reply.

---

### Post by bingoUV on 2007-11-28
install xscreensaver.
Run xscreensaver -lock in your gnome session startup programs
Set gdm to log you into gnome automatically

---

### Post by clark.peter on 2007-11-28
> **bingoUV said:**
> install xscreensaver.
Run xscreensaver -lock in your gnome session startup programs
Set gdm to log you into gnome automatically

Yes!!! I think that is gonna solve my problem. I will tell you if it works. 

Cheers.

---

### Post by clark.peter on 2007-11-28
I installed xscreensaver and used the command "xscreensaver-command -lock" to solve my problem.

Thanks everybody for your help

---

