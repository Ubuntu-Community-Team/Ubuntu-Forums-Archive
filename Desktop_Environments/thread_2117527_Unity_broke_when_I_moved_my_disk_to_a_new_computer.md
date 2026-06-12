---
title: "Unity broke when I moved my disk to a new computer"
date: 2013-02-18
forum: Desktop Environments
---

### Post by ClarenceD on 2013-02-18
I moved my "Ubuntu 12.04.2 LTS" boot drive to a new computer.
The desktop login still looks okay, but if I connect via VNC, I get a blank screen instead of my Unity desktop.
syslog has some errors, that seem to start with this one
"x-session-manager[6235]: Gdk-WARNING: x-session-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :25.#012"

My VNC session is "25" deliberately, but I have tried other numbers.

"compiz[9406]: segfault at 3c ip b6113057 sp bfdaf810 error 4 in libcomposite.so[b6108000+21000]"

.xsession-errors has some error messages, like
(gnome-settings-daemon:4692): color-plugin-WARNING **: unable to get EDID for xrandr-default: unable to get EDID for output

I/O warning : failed to load external entity "/home/clarence/.compiz/session/10301235a14df254bb136120456075273800000046400036"

X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  109 (X_ChangeHosts)
  Value in failed request:  0x5

----------------------------------------------------------
I moved the disk from a desktop with an unsupported old NVidia card 
model name      : Intel(R) Pentium(R) 4 CPU 2.80GHz
01:00.0 VGA compatible controller: NVIDIA Corporation NV18GL [Quadro NVS 280 SD] (rev c1) (prog-if 00 [VGA controller])

to a Lenovo T61p laptop with model name      : Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz
01:00.0 VGA compatible controller: NVIDIA Corporation G84M [Quadro FX 570M] (rev a1) (prog-if 00 [VGA controller])

I have tried with nouveau and NVidia drivers, using either "display" or the NVidia tool to configure for external display only, or dual.
It just occured to me that I haven't tried with the external dsiplay disconnected.

I have tried to follow various "reset unity" and "reset compiz" threads, to no avail.

Should I uninstall and reinstall a few packages?

-- clarence

---

### Post by Bashing-om on 2013-02-18
ClarenceD; Hi ! Welcome to the forum.

With the disk swap definitely need to at least change the drivers, in particular the graphics driver. This code will remove the Nvida stuff and install the nouveau driver. If you do not want the nouveau driver, see below. 
```

  sudo nvidia-settings --uninstall
  sudo apt-get remove --purge nvidia*
  sudo apt-get remove --purge xserver-xorg-video-nouveau xserver-xorg-video-nv
  sudo apt-get install nvidia-common
  sudo apt-get install xserver-xorg-video-nouveau
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
```Then reboot your system and when it comes up it will be running with nouveau.

else: if ya want to run the Nvidia driver:
do all the above 'till apt-get install; do to install Nvidia:

```

sudo apt-get install linux-headers-generic
sudo apt-get install nvidia-current nvidia-settings
```[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by ClarDold on 2013-02-19
> **Bashing-om said:**
> ClarenceD; Hi ! Welcome to the forum.

With the disk swap definitely need to at least change the drivers, in particular the graphics driver. This code will remove the Nvida stuff and install the nouveau driver. If you do not want the nouveau driver, see below. 


My monitor works fine, it's just VNC that doesn't work.
I used the "proprietary drivers" tool to enable NVidia, which wasn't enabled on the old machine, and then back to noveau, and back to NVidia, so the hardware portion of the drivers should have updated.

I'll try the packages as you listed them, and see what happens.

---

### Post by ClarDold on 2013-02-19
> **Bashing-om said:**
> ClarenceD; Hi ! Welcome to the forum.


I've been lurking for a while.  I've been a Redhat guy, and stumbled onto Ubuntu while rescuing a trashed Windows disk via LiveCD, which RHEL didn't have at the time.

Since then, I've been an Ubuntu fan, and this is the first time I've needed to post a question, since everything else seems to already be answered here ;)

-- clarence

---

### Post by Bashing-om on 2013-02-19
ClarDold;

Looks like you have properly set the graphics driver. As the "desktop" is fully functional, must be a disparity in the protocol to implement the VNC connection.
I have never ran VNC so have no experience/knowledge and must now bow out of advisement. I will monitor this thread for my education !
I expect others more knowledgeable in this area will pick up on this thread.

[INDENT]best regards.
[/INDENT]

---

### Post by ClarenceD on 2013-02-20
> **Bashing-om said:**
> 
With the disk swap definitely need to at least change the drivers, in particular the graphics driver. 

I ran all of those, with no effect.
I still had a segfault from compiz, so I uninstalled and reinstalled compiz.
That made a difference ):P

Now, my console was blank, just like my VNC session. :(

So I uninstalled compiz and rebooted.
The console looks good, and the VNC looks good.
Compiz must not like something about the new computer.

```

apt-get remove --purge compiz\* libcompizconfig0

```

---

### Post by Bashing-om on 2013-02-20
ClarenceD;

Wow, As I live and learn. Look and see how your card likes unity:
Terminal command:
```
/usr/lib/nux/unity_support_test -p
```all responses should be "yes".
[INDENT][INDENT]what can I say 
[/INDENT][/INDENT]

---

### Post by ClarenceD on 2013-02-20
> **Bashing-om said:**
> ClarenceD;

Wow, As I live and learn. Look and see how your card likes unity:
Terminal command:
```
/usr/lib/nux/unity_support_test -p
```all responses should be "yes".[INDENT][INDENT]what can I say 
[/INDENT][/INDENT]

Well, that tells a tale, although I'm not sure what...
It fails on VNC, and runs on the console.
I'm happy without Compiz, so I am good to go with the current configuration anyway.


```
VNC $ /usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":25".
Error: GLX is not available on the system 
```
```
Console $ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: Quadro FX 570M/PCIe/SSE2
OpenGL version string:  3.3.0 NVIDIA 295.40

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

---

### Post by Bashing-om on 2013-02-21
ClarenceD;

IDK, I am sorta chasing my own tail now. Need to get some direction.
Let's do this ...let's look at the X.org.0.log file, both on the host prior to starting the VNC connection and afterward, see what the system tells us.
```
cat /var/log/Xorg.0.log | grep glx
```Maybe there is a miss link to the libraries on vnc ?

And on a similar thought,  do you have a vnc connection log ?

Also ran across a thread that how one connects might be an issue:
[http://serverfault.com/questions/174003/how-can-opengl-graphics-be-displayed-remotely-using-vnc](http://serverfault.com/questions/174003/how-can-opengl-graphics-be-displayed-remotely-using-vnc)
[INDENT][INDENT]which way did he go, George

[/INDENT][/INDENT]

---

### Post by ClarenceD on 2013-02-21
> **Bashing-om said:**
> 

```
cat /var/log/Xorg.0.log | grep glx
``` 

It doesn't seem that VNC plays at all in that log.
The result from that grep is
```
 [    12.807] (II) LoadModule: "glx"
[    12.808] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    12.868] (II) Module glx: vendor="NVIDIA Corporation"

```which I think was at boot time.
-i lets me see 
```
[    12.868] (II) NVIDIA GLX Module  295.40  Thu Apr  5 21:49:54 PDT 2012

```> 
And on a similar thought,  do you have a vnc connection log ?

Also ran across a thread that how one connects might be an issue:
I don't have my particular vnc.log, which gets recreated on each login.  Scouring around, I have a couple on other users from days gone by, but neither glx nor compiz appears in any of them.

I wonder if some other set of dependencies caused glx or compiz not to load on the old system, and they do load on the new system.

I think I'm going to live without compiz until such time as I upgrade Ubuntu levels.
That other URL you gave doesn't seem encouraging.  that was from someone that needed GLX.  I don't seem to need it so far.

(I moved a disk drive from an old 32 bit P4 to a 64 bit Core 2 Duo T7700)

-- clarence

---

