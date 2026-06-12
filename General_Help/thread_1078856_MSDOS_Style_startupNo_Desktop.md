---
title: "MSDOS Style startup/No Desktop???"
date: 2009-02-23
forum: General Help
---

### Post by robertrod11 on 2009-02-23
I'm new to ubuntu and tried to install it to my desktop but when i start it up it looks like msdos and I cant seem to change it back to a regular desktop

it will prompt me like this after I log in

bob@bob-desktop:~$

I installed it on a partitioned part of my hard drive and made the partition ext3 or whatever I cant really remember 

Not sure if I chose the right format or if I just need to enter a simple lign to get my desktop back

---

### Post by cariboo on 2009-02-23
Your mistaken, it is a linux console. :) It seems that some how gdm isn't starting. at the prompt type:

```
sudo /etc/init.d/gdm start
```

If you haven't removed gdm you should get the login screen. If that doesn't work type:

```
startx
```

at the prompt. This will start up the desktop where you should be able to troubleshoot the rest of your problems.

Jim

---

### Post by robertrod11 on 2009-02-23
when i try the first one it says it cant find the command but when i do the second one it pops all this info and it looks fine but at the end it stops says the stuff below and waits for me to give it a command as before

(EE) No devices detected.

Fatal server error:
no screens foound
giving up.
Xinit: Connection refused (errno 111): unable to connect to X server
Xinit: no such process (errno 3): Server error.

thank you for helping me try and fix my problem :)

---

### Post by robertrod11 on 2009-02-23
I just typed in the first one and it strangly worked this time and gave me this before prompting 

* Starting GNOME Display Manager...                  [ OK ]

---

### Post by robertrod11 on 2009-02-23
a thing i forgot to mention is that when i first install it the gui comes up fine but i after i restart from updates it goes to the terminal only thing 

Please help me :)

---

