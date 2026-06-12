---
title: "No graphical boot without my monitor plugged :)"
date: 2012-11-23
forum: Desktop Environments
---

### Post by leslipsale on 2012-11-23
Hi !
My config :
lubuntu 12.04 ,with default installation + Ati radeon x1950gt + old crt monitor
 
I put autologin and x11vnc server with autostart and it works!
 
Problem :
 
If i plug off my crt monitor and if i restart my computer, i have no more graphical interface and my x11vncserver cant work :(
 
i read that's xorg11.conf problem but i cant find it.
 
PS : i m not using ati driver and i dont know my interface type (lxde does not  seem to work)
 
if someone could help me please

---

### Post by cybergalvez on 2012-11-23
> **leslipsale said:**
> Hi !
My config :
lubuntu 12.04 ,with default installation + Ati radeon x1950gt + old crt monitor
 
I put autologin and x11vnc server with autostart and it works!
 
Problem :
 
If i plug off my crt monitor and if i restart my computer, i have no more graphical interface and my x11vncserver cant work :(
 
i read that's xorg11.conf problem but i cant find it.
 
PS : i m not using ati driver and i dont know my interface type (lxde does not  seem to work)
 
if someone could help me please

I remember having similar issues years ago when I tried this with redhat. The issues is (if I remember correctly) that VNC really requires a screen buffer to read, so you need to have the screen plugged in for your vid card to interact with. If you can use something other than VNC I would recomend that you use something which is not dependent on the actual screen buffer. I use x2go for this type of stuff, becuase if is very easy to use. main draw back is you will have to use their client.

---

### Post by steeldriver on 2012-11-23
I've not done this myself so I'll avoid giving specific advice but from what I've read you may need a dummy xserver package (xserver-xorg-video-dummy) and possibly a corresponding /etc/xorg.conf file to get x11vnc to work in a truly 'headless' configuration. That info may be out of date or plain wrong though.

---

### Post by leslipsale on 2012-11-23
> **cybergalvez said:**
> I remember having similar issues years ago when I tried this with redhat. The issues is (if I remember correctly) that VNC really requires a screen buffer to read, so you need to have the screen plugged in for your vid card to interact with. If you can use something other than VNC I would recomend that you use something which is not dependent on the actual screen buffer. I use x2go for this type of stuff, becuase if is very easy to use. main draw back is you will have to use their client.
 
hi & thx :)
 
its not realy vnc problem because when i disconnect my monitor and then i push the "reset button" and if i let linux loads and then i plug back my monitor to see what my pc does, i see a black screen , (maybe one console) and linux seems to work well but no interface has been started, if i type startx it works well...
 
the lxde environement dosent starts if there is no monitor :(
 
i saw  multiple people in the same case i have to modify my xorgconf files to add a fake or forced monitor

---

### Post by leslipsale on 2012-11-23
> **steeldriver said:**
> I've not done this myself so I'll avoid giving specific advice but from what I've read you may need a dummy xserver package (xserver-xorg-video-dummy) and possibly a corresponding /etc/xorg.conf file to get x11vnc to work in a truly 'headless' configuration. That info may be out of date or plain wrong though.
 
 
its seems to match with my problem, i will see tomorow
 
thx

---

