---
title: "Inspiron 1420 webcam"
date: 2008-04-11
forum: Dell  Ubuntu Support
---

### Post by casfindad on 2008-04-11
I just did a fresh install of Gutsy onto a Dell Inspiron 1420 after shrinking the Vista partition. (This is NOT the 1420n, it came with Vista.) Strangely, the webcam worked on this machine when I ran the Live CD, but it is no longer detected after installing Ubuntu. Any suggestions to get my webcam detected and working (specifically for Ekiga) would be very much appreciated.

---

### Post by linuxwizard on 2008-04-11
You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.
To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If cam does not work post the results of the command > lsusb

---

### Post by casfindad on 2008-04-11
I found a clue to the problem. If I log in as the first user set up on this installation, (i.e. the user I created during installation), the webcam works! If I log in as another user, even if that user has administrator privileges, the webcam is not detected. I'm wondering if I need to be a member of the a special group that only the first user currently occupies, but I haven't been able to find the right group yet.

Here is the output of lsusb:
```
Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
```

---

### Post by sdennie on 2008-04-11
On my machine (almost certainly the same driver), /dev/video0 is read/write accessible via the video group.  Oddly enough, I don't see any way to add users to the video group via gui tools (in Hardy).  You may have to do something like: 

```

sudo adduser some_user video

```

---

### Post by casfindad on 2008-04-12
> **vor said:**
> On my machine (almost certainly the same driver), /dev/video0 is read/write accessible via the video group.  Oddly enough, I don't see any way to add users to the video group via gui tools (in Hardy).  You may have to do something like: 

```

sudo adduser some_user video

```
Thanks! That worked.

---

