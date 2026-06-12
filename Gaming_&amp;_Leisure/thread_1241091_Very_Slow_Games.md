---
title: "Very Slow Games"
date: 2009-08-15
forum: Gaming &amp; Leisure
---

### Post by Gregz on 2009-08-15
ok   I downloaded some games to play, and they all installed without a hitch but, They run real slow choppy. I downloaded from playdeb and it seems only one will work, UFO does work no problems. The rest like Nexuiz, will not load single player locks up on dos screen(can access games it loads but locks up on 1on1 freezes at dos screen. Sauerbraten, is so slow enemy is on me killing and I didn't even see them enter room. Now thats slow the mouse moves slow and jumpy. It takes for ever to sswitch weapons or shoot WHATS UP????

The rest run so slowly you can't play them. I have nvidia card:


james@Catfish:~$ glxinfo | grep vendor
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation

Driver is 185.18.14

any ideas

To be honest this is the only reason I still have windows to play games why can't they fix this??

---

### Post by 569874123 on 2009-08-15
U can try playing nexuiz with the zip file from their site.
What are the other games u want to play?

---

### Post by Gregz on 2009-08-15
Nexuiz, Sauerbraten, There's more but scared to try them...

---

### Post by 569874123 on 2009-08-15
I would recommend to stick to windows for gaming, at least for now, until getdeb gets their bugs fixed.
It is what i do :)

---

### Post by Gregz on 2009-08-15
Yep, I have been using windows since windows 95. I went through all the growing pains like 98 to xp xp to vista guess this is my linux growing pain  lol

---

### Post by Bölvaður on 2009-08-15
What card do you have?
You might be using the wrong driver.

Also, as a quick test. what do you get from (if you open your terminal) glxgears, it's not a benchmark, but good to do quick estimates.

---

### Post by Gregz on 2009-08-15
I did it three times and each time i got  a red,blue,green gears spinning. after I closed small window it said this:

 ```
james@Catfish:~$ glxgears
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
17218 frames in 5.0 seconds = 3439.571 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 44436 requests (39 known processed) with 0 events remaining.
james@Catfish:~$ glxgears
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 25476 requests (39 known processed) with 0 events remaining.
james@Catfish:~$ glxgears
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 18476 requests (39 known processed) with 0 events remaining.

```  card is a nvidia nx7600gs

---

### Post by tgalati4 on 2009-08-15
In a terminal:

sudo chmod 777 /dev/nvidiactl

Then run glxgears.

---

### Post by Gregz on 2009-08-15
I got the same thing

james@Catfish:~$ glxgears
NVIDIA: could not open the device file /dev/nvidia0 (Permission denied).
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 20756 requests (39 known processed) with 0 events remaining.
james@Catfish:~$

no sorry it's different

---

### Post by Gregz on 2009-08-15
I also did a chmod on /dev/nvidia0 and it took off frame rates list a mile long. no errors.

---

### Post by Gregz on 2009-08-15
I started Sauerbraten and wow thats what it like  :P. fps 200+ love it smooth. I must say Thank You. I have not tried on Nexuiz yet.

Again thank you

---

### Post by tgalati4 on 2009-08-16
So did the chmod fix the problem?  If so, you will need to do it for each reboot, since /dev devices get created upon boot.  Put that line (without the sudo) in /etc/rc.local.

Looks like the nVidia installer has a permissions problem or you need to add your username to the group video or something like that.

ls -la /dev/nvidiactl

this will show who owns it and what group can access it.

---

### Post by Gregz on 2009-08-16
It says root is owner

james@Catfish:~$ ls -la /dev/nvidiactl
crwxrwxrwx 1 root video 195, 255 2009-08-16 11:09 /dev/nvidiactl

---

### Post by tgalati4 on 2009-08-17
And video is the group, as I suspected.  Perhaps you need to add your username to group video.

---

### Post by Gregz on 2009-08-17
Whats the easiest way to do that???

---

### Post by tgalati4 on 2009-08-17
man adduser
sudo adduser gregz video

---

