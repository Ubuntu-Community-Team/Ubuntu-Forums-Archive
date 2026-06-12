---
title: "Vnc"
date: 2006-10-06
forum: Desktop Environments
---

### Post by DouglasAWh on 2006-10-06
I need some help setting up VNC.  My local Linux guru keeps telling me it's easy, and it was easy in WinXP, but I have no clue what I'm doing in ubuntu.  All I want to do is be able to access my ubuntu machine from my XP machine so I don't have to have two monitors taking up power and I don't have to have doubles of other things.  It's bed time over here...

---

### Post by Fully216 on 2006-10-06
The easiest way to do it is to use the remote desktop feature found under your applications menu.  If you need help, I would search for 'remote desktop' under the forums.  Installing a specific vnc client can be more trouble than you need if you simply want to connect to a XP computer.

---

### Post by DouglasAWh on 2006-10-06
I don't have a lot of time to deal with this before work (in fact, I've dealt too long with it).  Did you mean the Remote Desktop on the XP box or the Remote Desktop in ubuntu.  I typed the ubuntu IP address into the XP Remote Desktop and tried to connect with no luck.  Should I be connecting to the computer name instead of the IP address?  Thanks!

---

### Post by stalker145 on 2006-10-06
> **DouglasAWh said:**
> Did you mean the Remote Desktop on the XP box or the Remote Desktop in ubuntu.
You will be setting the Remote Desktop features on the Ubuntu box. Not being at my box, and still being kinda new, I'll say that it is under Administration and then Remote Desktop. Then allow users to take control, DO NOT require your input (since you said you're running this box headless) and you should be able to access it from your XP box after OK'ing out. It's probably best to put in a password for connection since this *is* a dangerous world that we play in ;)

---

### Post by ronmarley1 on 2006-10-06
EDIT: Sorry for the double post.  I got aced out again!
> **Fully216 said:**
> The easiest way to do it is to use the remote desktop feature found under your applications menu.  If you need help, I would search for 'remote desktop' under the forums.  Installing a specific vnc client can be more trouble than you need if you simply want to connect to a XP computer.

I think he actually wants to go the other way, from XP to Ubuntu.  On your Ubuntu box, go to System ->Preferences ->Remote Desktop.  Check "Allow other users to _v_iew your desktop.  You can allow users to control the desktop also.  Check the security features for how you want folks to connect.  Start VNC on your XP box, and type in the IP address or name of your Ubuntu box.

---

### Post by mjpatey on 2006-10-06
In Ubuntu, System -> Preferences -> check on both "Allow Other Users..." checkboxes, then set your password.

---

### Post by DouglasAWh on 2006-10-06
Ok, let me see if I've got this straight.  I use Remote Desktop on ubuntu and VNC in XP?  I believe I set up the remote desktop on ubuntu.  I'll give it a shot here in a bit.  I'm at work and don't remember if I left the ubuntu box on, but I am remotely connectly to my XP machine from here. :)

---

