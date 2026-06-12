---
title: "Screen Resolutions Disappear-Login Screen Messed Up"
date: 2007-02-08
forum: Desktop Environments
---

### Post by Dylnuge on 2007-02-08
My current resolution is 800x600. I used to have a large number of options, including 1900x1200 (widescreen), which I used. Now they are all gone. I have three options: 800x600, 640x480, and 2046x1536 (sounds like dual-screen, but it looks like 800x600 stretched out too much, so something tells me it won't help).

Recent Changes:
Installed StartUp Manager, have rebooted 3 times without problem
Installed Kubuntu, have used KDE without problem, but not extensively.

I just was in KDE and using extensivly for first time (changed settings and the like). Logged out, noticed GDM was running at a 1900x1200 resolution centered on a 800x600 screen (i.e, I could see the login and password box but it was too big to see anything else but the letters UNT (part of ubUNTu).

I might have done something in KDE, but it is not my default environment, so I can't get into it (cant see the switch session button, its below the visible portion).

I need to get the computer up and running ASAP.

Thanks,
Dylan

PS: really needs to be an emotion of someone ripping their hair out, not just this crying one.

---

### Post by Dylnuge on 2007-02-09
Can someone please help with this? I really need to get back into my system.

---

### Post by Dylnuge on 2007-02-09
Somebody, Please!!!!! I might have to reinstall my whole system. Please help!

---

### Post by shareMenaPeace on 2007-02-09
Did you tried login with failsafe session?

---

### Post by Dylnuge on 2007-02-09
No, because I cannot. GDM is displaying at a 1900x1200 resolution, but only 800x600 pixels of it are displaying.

In other words, I cannot switch session or anything like that from GDM. All I can see is the login box and a shaved off Ubuntu logo.

Thanks, however.

---

### Post by shareMenaPeace on 2007-02-09
Than hit ALT + F2 and login and type

startx

---

### Post by Dylnuge on 2007-02-09
Actually, I just found that I can move the mouse to the edge of the gigantic screen, and it moves me around the giant desktop. I loaded in failsafe, and got a huge screen on the desktop. It turned out it was one of the three options, the 2046x1536 one. I switched to 800x600, my only other option besides 640x480. I also got a GNOME Settings Daemon startup error. I remember reading something about that a few minutes ago.

Any suggestions, or should I reinstall the OS.

---

### Post by Dylnuge on 2007-02-09
I am afraid I have no choice anymore. All of the packages I have installed will be lost, but maybe its for the better. For that matter, maybe a new installation won't be so bad.

Unfortunatly, I have no plans to download the Edgy LiveCD just to reinstall. I guess I will be upgrading from Dapper.

---

### Post by Dylnuge on 2007-02-09
Looks like a system reinstall is nessicary. I will begin tomorrow morning.

If anyone can help, I also was trying to get my back button on my mouse to work and was using the xorg.conf file's buttonmapping feature.

-Dylan

---

### Post by shareMenaPeace on 2007-02-09
What is the problem now again?

You can login 

Did you cahnged the screen resolution?

Did you changed the mouse theme?

And please post the content of the error message -someone might know this.

---

### Post by Dylnuge on 2007-02-09
My first reply did not go through, for some odd reason.

I was always able to login. I just can't see any portion of the login screen but the login box without scrolling through it.

My system does not change the screen resolution: The only options are listed in my first post. Anything bigger then 800x600 displays at 800x600 with a large majority of the screen hidden.

Confused on what you mean by mouse theme.

Error message went by to fast-but it only appeared in failsafe mode. It said that the GNOME Settings Dameon failed to start. This does not appear in regular, non failsafe mode.

PS: Tried KDM and startx using the recovery mode. No avail.

---

### Post by shareMenaPeace on 2007-02-09
Dou you have kdm or gdm as desktop?

---

### Post by shareMenaPeace on 2007-02-10
You need to reconfigure the xserver maybe

try
[HTML]sudo dpkg-reconfigure xserver-xorg[/HTML]

---

