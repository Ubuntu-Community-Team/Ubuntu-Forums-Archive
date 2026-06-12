---
title: "Terrible X-Server Crash"
date: 2006-02-15
forum: Desktop Environments
---

### Post by WelterPelter on 2006-02-15
Something awful is going on with my x server. It was working fine, and then I logged out. After that, all hell broke loose. When I try to log in, it keeps crashing. I'm writing this from a nearby laptop. Here is an approximation of the error messages it's giving me:

/etc/gdm/Xsession: Beginning session setup
IceTransTransNoListen:unable to find transport tcp
IceTransmkdir: ERROR! euid != 0 /dev/X will not be created
IceTransmkdir: ERROR! cannot create /dev/X
IceTransPTSOpenServer: mkdir /dev/X failed error = 13


Anybody have any idea what's going on here? The computer seems fine if I log in on a shell. How do I fix this and get back to work? :confused:


---ARRGGHHH.... Since writing this post, I found some advice in a forum thread that showed me how to reconfigure my Xserver. Now the thing is completely verklempt. Utterly kaput. "Failed to start X server..." Etc. 

Is there some way to restore the system without going back to scratch?

---

### Post by NewWithoutClue on 2006-02-15
"ERROR! euid != 0 /dev/X will not be created"
Error user is not root.. cannot create /dev/x

dont know if this helps.. just incase you didnt know

---

### Post by anirban.sam on 2006-02-15
sudo dpkg-reconfigure xserver-xorg

---

### Post by WelterPelter on 2006-02-15
>sudo dpkg -reconfigure xserver-xorg


I have tried this at least 35 times already. No configuration I attempt works. Ubuntu auto-detected everything just fine when I installed. So apparently this reconfigure thing isn't going to work.


Is there a way to re-install the system, or rescue it, that won't overwrite everything I have there? I've saved the vital data already, but would like to not have to re-setup my entire setup.

-- Never mind. Couldn't wait any longer. Just doing a fresh install.

---

