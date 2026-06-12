---
title: "No 3D acceleration with Intel 945 on Gutsy"
date: 2008-02-03
forum: Dell  Ubuntu Support
---

### Post by Monkey_Tales on 2008-02-03
I have upgraded to Gutsy and many programs using 3D acceleration dont work any more . Google Earth dont work, Nexuiz dont work Open Arena dont work and Second life and some other progs wont work any more!
When i was using Feisty, they all worked fine, but in Gutsy they dont work any more and i dont want to downgrade to Feisty.
Who can help me?:confused:

---

### Post by grimdestripador on 2008-02-08
i'm researching this myself, i believe that you need xgl support in your /etc/X11/xorg.conf

but i'm unsure, how to enable the chipset. possibly do a
sudo dpkg-reconfigure xserver-xorg

---

### Post by RedRat on 2008-02-11
Since you have not given any info about your graphics card you may need a proprietary driver, for example from NVidia in order to get 3d capability. I am using a Nvidia 8600GTS on Dell and Google Earth works fine, but I am using the restricted NVida driver.

---

### Post by Monkey_Tales on 2008-02-12
Thanks for the reply's.

The last configuration i have done is the sudo dpkg-reconfigure xserver-xorg.
I selected the i810 intel driver and some the 3D programs work, but not all.
I have tried also the intel graphics driver with the dpkg-reconfigure xserver-xorg, but still not all 3D applications work.
Google earth refuses to work and Nexuis gives a strange pixel effect that looks  like a 8bit envoirment from the 1980's.
The best driver so far is the i810 (intel) driver. it give's the least problems, but i am not satisfied, because when i was using Feisty, everthing worked fine...
I have a Dell 6400 laptop duo core 1,73 Ghz with the intel 945 graphics card with 256mb shared memory.
Is there maybe someone with the same laptop and problems or solutions?

---

### Post by overdrank on 2008-02-12
> **Monkey_Tales said:**
> Thanks for the reply's.

The last configuration i have done is the sudo dpkg-reconfigure xserver-xorg.
I selected the i810 intel driver and some the 3D programs work, but not all.
I have tried also the intel graphics driver with the dpkg-reconfigure xserver-xorg, but still not all 3D applications work.
Google earth refuses to work and Nexuis gives a strange pixel effect that looks  like a 8bit envoirment from the 1980's.
The best driver so far is the i810 (intel) driver. it give's the least problems, but i am not satisfied, because when i was using Feisty, everthing worked fine...
I have a Dell 6400 laptop duo core 1,73 Ghz with the intel 945 graphics card with 256mb shared memory.
Is there maybe someone with the same laptop and problems or solutions?

HI and adding the 915 resolution via synaptic has helped some users. Good luck!

---

### Post by vambo on 2008-02-12
What's the output of?
```
glxinfo | grep direct
```

---

### Post by Monkey_Tales on 2008-02-12
Hi,
- 915 resolution is already installed on the system.
- glxinfo | grep direct gives: 
$ glxinfo | grep direct direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
what can i do with this info?

Thanks for the quick reply

---

### Post by vambo on 2008-02-12
> **Monkey_Tales said:**
> Hi,
- 915 resolution is already installed on the system.
- glxinfo | grep direct gives: 
$ glxinfo | grep direct direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
what can i do with this info?

Thanks for the quick reply

Do as it asks, i.e.

```
export LIBGL_DEBUG=verbose
```

Then run
```
glxinfo | grep direct

```
again.

If it complains about missing a library <something>-dri (I forget exactly what), then you'll need get the following from the repos.

```
sudo apt-get install libgl1-mesa-dri
```

With a bit of luck, logging out then back in should have you set

---

### Post by ItalOz on 2008-02-12
I did what you said to (I have a  Radeon X1550 64-bit) and same problem as Monkey_Tales
the answer to:
glxinfo | grep direct
was:
XF86DRIQueryDirectRenderingCapable

I tried to run
sudo apt-get install libgl1-mesa-dri

And I got
libgl1-mesa-dri is already the newest version

Any Idea?!?

---

### Post by vambo on 2008-02-12
> **ItalOz said:**
> I did what you said to (I have a  Radeon X1550 64-bit) and same problem as Monkey_Tales
the answer to:
glxinfo | grep direct
was:
XF86DRIQueryDirectRenderingCapable

I tried to run
sudo apt-get install libgl1-mesa-dri

And I got
libgl1-mesa-dri is already the newest version

Any Idea?!?

Not sure about this one, as you have direct rendering (the XF86 bit). Also I have no experience with Radeon graphics. I assume you have the right drivers?

---

### Post by ItalOz on 2008-02-12
I think I have, I've selected the restricted ATI drivers, I run at the proper resolution, I have beatiful and fast working desktop effects (rotate cube and everything).

I stepped into this direct rendering thing because I am trying to run some applications under wine. And I found on the help files that I need direct rendering to run... but seems it does not.

---

### Post by Monkey_Tales on 2008-02-12
Hello Vambo,

The result is:

~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
~$ export LIBGL_DEBUG=verbose
~$ glxinfo | grep direct
libGL: XF86DRIGetClientDriverName: 1.7.4 i915 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/i915_dri.so
libGL error: dlopen /usr/lib/dri/i915_dri.so failed (/usr/lib/dri/i915_dri.so: undefined symbol: _glapi_add_dispatch)
libGL error: unable to find driver: i915_dri.so
libGL: XF86DRIGetClientDriverName: 1.7.4 i915 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/i915_dri.so
libGL error: dlopen /usr/lib/dri/i915_dri.so failed (/usr/lib/dri/i915_dri.so: undefined symbol: _glapi_add_dispatch)
libGL error: unable to find driver: i915_dri.so
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

I tried also 915resolution:
~$ sudo 915resolution 5c 1280 800 32
Intel 800/900 Series VBIOS Hack : version 0.5.3

Chipset: 945GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Patch mode 5c to resolution 1280x800 complete

But still Google earth and others won't work.

---

### Post by vambo on 2008-02-12
Did you install libgl?
i.e., the

```
sudo apt-get install libgl1-mesa-dri
```
bit.

As far as I'm aware that should resolve the error with not resolving i965_dri.so, which is the thing you need.

---

### Post by Monkey_Tales on 2008-02-12
Hi,

Yes i have installed  sudo apt-get install libgl1-mesa-dri
This is the result:

~$ sudo apt-get install libgl1-mesa-dri
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd
Reading state information... Klaar
libgl1-mesa-dri is reeds de nieuwste versie.
De volgende pakketten werden automatisch geïnstalleerd en zijn niet langer nodig:
  libglitz-glx1 libglitz1 libopal-2.2 libpt-plugins-alsa
Gebruik 'apt-get autoremove' om ze te verwijderen.
0 pakketten opgewaardeerd, 0 pakketten nieuw geïnstalleerd, 0 te verwijderen en 0 niet opgewaardeerd.
~$ glxinfo | grep direct
libGL: XF86DRIGetClientDriverName: 1.7.4 i915 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/i915_dri.so
libGL error: dlopen /usr/lib/dri/i915_dri.so failed (/usr/lib/dri/i915_dri.so: undefined symbol: _glapi_add_dispatch)
libGL error: unable to find driver: i915_dri.so
libGL: XF86DRIGetClientDriverName: 1.7.4 i915 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/i915_dri.so
libGL error: dlopen /usr/lib/dri/i915_dri.so failed (/usr/lib/dri/i915_dri.so: undefined symbol: _glapi_add_dispatch)
libGL error: unable to find driver: i915_dri.so
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
~$ export LIBGL_DEBUG=verbose
~$ glxinfo | grep direct
libGL: XF86DRIGetClientDriverName: 1.7.4 i915 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/i915_dri.so
libGL error: dlopen /usr/lib/dri/i915_dri.so failed (/usr/lib/dri/i915_dri.so: undefined symbol: _glapi_add_dispatch)
libGL error: unable to find driver: i915_dri.so
libGL: XF86DRIGetClientDriverName: 1.7.4 i915 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/i915_dri.so
libGL error: dlopen /usr/lib/dri/i915_dri.so failed (/usr/lib/dri/i915_dri.so: undefined symbol: _glapi_add_dispatch)
libGL error: unable to find driver: i915_dri.so
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

I am doing something wrong but i don't know what?

---

### Post by vambo on 2008-02-12
What's inside /usr/lib/dri?

```
ls -al /usr/lib/dri
```

---

### Post by Monkey_Tales on 2008-02-12
Hello Vambo,

~$ ls -al /usr/lib/dri
totaal 45008
drwxr-xr-x   2 root root    4096 2008-02-04 02:32 .
drwxr-xr-x 244 root root  110592 2008-02-12 20:09 ..
-rw-r--r--   1 root root 9274776 2007-11-02 02:22 fglrx_dri.so
-rw-r--r--   1 root root 2236104 2007-10-13 02:38 i810_dri.so
-rw-r--r--   1 root root 2350792 2007-10-13 02:38 i915_dri.so
-rw-r--r--   1 root root 2342604 2007-10-13 02:38 i915tex_dri.so
-rw-r--r--   1 root root 2402568 2007-10-13 02:38 i965_dri.so
-rw-r--r--   1 root root 2334476 2007-10-13 02:38 mach64_dri.so
-rw-r--r--   1 root root 2375368 2007-10-13 02:38 mga_dri.so
-rw-r--r--   1 root root 2240200 2007-10-13 02:38 r128_dri.so
-rw-r--r--   1 root root 2317896 2007-10-13 02:38 r200_dri.so
-rw-r--r--   1 root root 2249000 2007-10-13 02:38 r300_dri.so
-rw-r--r--   1 root root 2282412 2007-10-13 02:38 radeon_dri.so
-rw-r--r--   1 root root 2207304 2007-10-13 02:38 s3v_dri.so
-rw-r--r--   1 root root 2289804 2007-10-13 02:38 savage_dri.so
-rw-r--r--   1 root root 2293608 2007-10-13 02:38 sis_dri.so
-rw-r--r--   1 root root 2294408 2007-10-13 02:38 tdfx_dri.so
-rw-r--r--   1 root root 2150124 2007-10-13 02:38 trident_dri.so
-rw-r--r--   1 root root 2223888 2007-10-13 02:38 unichrome_dri.so

---

### Post by vambo on 2008-02-12
This is getting a bit odd.

Can you check you have
libgl1-mesa-dev and libgl1-mesa-glx  installed

This basically mirrors my set up and it's okay.

---

### Post by Monkey_Tales on 2008-02-12
I looked in adept manager and the following are installed:

-libgl1-mesa-dev
-libgl1-mesa-dri
-libgl1-mesa-glx
-libgl1-mesa-glx-dbg

What am i missing?

---

### Post by vambo on 2008-02-12
You're not missing anything as far as I'm concerned.
For some reason it appears to be having trouble with i915_dri.so

What does 
```
xdriinfo
``` give?

Also, have you tried an old fashioned reboot?

---

### Post by Monkey_Tales on 2008-02-12
This is xdriinfo:

~$ xdriinfo
libGL: XF86DRIGetClientDriverName: 1.8.0 i915 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/i915_dri.so
libGL error: dlopen /usr/lib/dri/i915_dri.so failed (/usr/lib/dri/i915_dri.so: undefined symbol: _glapi_add_dispatch)
libGL error: unable to find driver: i915_dri.so
libGL: XF86DRIGetClientDriverName: 1.8.0 i915 (screen 0)
Screen 0: i915

I restarted kubuntu about 7 times
The problem seems to be with libGL and the i915_dri.so.
In Feisty i did not have this problem.

---

### Post by vambo on 2008-02-12
All I can suggest is to uninstal then reinstall libgl1-mesa-dri, as it seems to be that that's causing the trouble. Other than that I'm afraid I'm out of ideas.

---

### Post by Monkey_Tales on 2008-02-12
I deleted the libgl1-mesa-dri and reinstalled it with no result.

~$ glxinfo | grep direct
libGL: XF86DRIGetClientDriverName: 1.8.0 i915 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/i915_dri.so
libGL error: dlopen /usr/lib/dri/i915_dri.so failed (/usr/lib/dri/i915_dri.so: undefined symbol: _glapi_add_dispatch)
libGL error: unable to find driver: i915_dri.so
libGL: XF86DRIGetClientDriverName: 1.8.0 i915 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/i915_dri.so
libGL error: dlopen /usr/lib/dri/i915_dri.so failed (/usr/lib/dri/i915_dri.so: undefined symbol: _glapi_add_dispatch)
libGL error: unable to find driver: i915_dri.so
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

The i915_dri.so driver is in the correct directory but gives an error that it cant be found? strange...

Vambo, thank you very much for your advice and time into this problem. I am also out of solutions,

---

### Post by f03el on 2008-03-13
This worked for me:

Previously I had this error:
```
erik@fox:~$ export LIBGL_DEBUG=verbose
erik@fox:~$ glxinfo | grep direct
libGL: XF86DRIGetClientDriverName: 1.8.0 i915 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/i915_dri.so
libGL error: dlopen /usr/lib/dri/i915_dri.so failed (/usr/lib/dri/i915_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: i915_dri.so
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```
I looked for /usr/lib/dri, but for some reason it wasn't there. Earlier I had noticed that 3D acceleration worked on the live cd, so I booted up an ubuntu 7.10 live cd and copied the /usr/lib/dri to a usb stick (probably it would have worked writing it directly to the hard disk). Then I booted into my installed system, got the folder in place and had to adjust owner and permissions:
```
erik@fox:~$ sudo chown -R root:root /usr/lib/dri
erik@fox:~$ sudo chmod 755 /usr/lib/dri/
erik@fox:~$ sudo chmod 644 /usr/lib/dri/*

```
Now glxinfo gives
```
erik@fox:~$ glxinfo | grep direct
libGL: XF86DRIGetClientDriverName: 1.8.0 i915 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/i915_dri.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
libGL warning: 3D driver claims to not support visual 0x56
libGL error: 
Can't open configuration file /etc/drirc: No such file or directory.
libGL error: 
Can't open configuration file /home/erik/.drirc: No such file or directory.
direct rendering: Yes

```
There are some errors due to the missing rc-files, but they doesn't exist on the live cd either. Anyway, glxgears runs without any problem now.

---

### Post by fragos on 2008-03-13
My 1420n came with 7.04 and I've upgraded to the Dell 7.10 DVD. In both cases, glxinfo indicates direct rendering as yes.  glxgears gives me over 1100 frames per second which couldn't be achieved without 3D rendering.  Compiz blacklists the Intel chip because some unspecific video output doesn't work when running Compiz.  You can overide the blacklist check and Compiz will work with the 1420n's LCD.  Check out [http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10)

---

### Post by Warprunner on 2008-03-13
> **Monkey_Tales said:**
> I have upgraded to Gutsy and many programs using 3D acceleration dont work any more . Google Earth dont work, Nexuiz dont work Open Arena dont work and Second life and some other progs wont work any more!
When i was using Feisty, they all worked fine, but in Gutsy they dont work any more and i dont want to downgrade to Feisty.
Who can help me?:confused:

I have an HP nc6320 with a 945 Intel. I went through the same issues. I have found out something from trying to get Compiz to run correctly to getting my ViewSonic VA1912wb 1440x900 widescreen monitor to work...
**_*DO NOT USE THE 810 drivers!!!!!!*_** Use the Intel Experimental.

I have reformatted 10 times playing around and finally...finally have EVERYTHING working. I even went to a hexagon in Compiz.

I could NEVER get the Intel Experimental to load without reloading Ubuntu. Sorry but that is my experience. But the upside is I have Google Earth, Compiz, Emerald Themes, etc...all work...no glitches.

---

### Post by stumbleUpon on 2008-04-02
Similar problem. I was able to run OpenGL programs in Fiesty. I did not upgrade directly but backed up my data and did a fresh install of gutsy from the CD.

I have an Intel 82G965 on an Intel Core 2 Duo. 


my output of 'glxinfo | grep direct'

```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```

and after 'export LIBGL_DEBUG=verbose'

```
libGL: XF86DRIGetClientDriverName: 1.8.0 i965 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/i965_dri.so
libGL error: dlopen /usr/lib/dri/i965_dri.so failed (/usr/lib/dri/i965_dri.so: undefined symbol: _glapi_get_dispatch)
libGL error: unable to find driver: i965_dri.so
libGL: XF86DRIGetClientDriverName: 1.8.0 i965 (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/i965_dri.so
libGL error: dlopen /usr/lib/dri/i965_dri.so failed (/usr/lib/dri/i965_dri.so: undefined symbol: _glapi_get_dispatch)
libGL error: unable to find driver: i965_dri.so
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
```

And 'xdriinfo' gives

```

Screen 0: i965
```


I have both 'libgl1-mesa-dev' and 'libgl1-mesa-glx' installed.

Output of 'ls -al /usr/lib/dri'

```
total 47892
drwxr-xr-x   2 root root    4096 2008-04-02 19:46 .
drwxr-xr-x 203 root root   69632 2008-04-02 19:26 ..
-rw-r--r--   1 root root 9829144 2007-11-01 13:51 fglrx_dri.so
-rw-r--r--   1 root root 2396936 2007-10-13 06:15 i810_dri.so
-rw-r--r--   1 root root 2500680 2007-10-13 06:15 i915_dri.so
-rw-r--r--   1 root root 2500552 2007-10-13 06:15 i915tex_dri.so
-rw-r--r--   1 root root 2526792 2007-10-13 06:15 i965_dri.so
-rw-r--r--   1 root root 2471144 2007-10-13 06:15 mach64_dri.so
-rw-r--r--   1 root root 2543272 2007-10-13 06:15 mga_dri.so
-rw-r--r--   1 root root 2384680 2007-10-13 06:15 r128_dri.so
-rw-r--r--   1 root root 2485384 2007-10-13 06:15 r200_dri.so
-rw-r--r--   1 root root 2388968 2007-10-13 06:15 r300_dri.so
-rw-r--r--   1 root root 2436008 2007-10-13 06:15 radeon_dri.so
-rw-r--r--   1 root root 2351592 2007-10-13 06:15 s3v_dri.so
-rw-r--r--   1 root root 2439016 2007-10-13 06:15 savage_dri.so
-rw-r--r--   1 root root 2462408 2007-10-13 06:15 sis_dri.so
-rw-r--r--   1 root root 2450504 2007-10-13 06:15 tdfx_dri.so
-rw-r--r--   1 root root 2298792 2007-10-13 06:15 trident_dri.so
-rw-r--r--   1 root root 2376752 2007-10-13 06:15 unichrome_dri.so
```

Any help is greatly appreciated....!!!

---

### Post by Warprunner on 2008-04-03
I upgraded to Hardy.  Everything loaded fine and I have the cube, etc..

I haven't got the Emerald themes working yet or haven't stopped Counter Strike to stop freezing, but I am well happy.

Maybe try that? 

I am too much of a Noob to help any other way. Sorry

---

### Post by stumbleUpon on 2008-05-08
Problem solved....!

I now have direct rendering in Hardy. I did a fresh install of Ubuntu 8.04 and direct rendering is now enabled.

I do not know what was wrong earlier.

Now my output of 'glxinfo | grep direct'

```
direct rendering: Yes
```

'xdriinfo' gives

```
Screen 0: i965
```

Now 'ls -al /usr/lib/dri' gives

```
total 37664
drwxr-xr-x   2 root root    4096 2008-04-22 23:41 .
drwxr-xr-x 179 root root   69632 2008-05-08 08:44 ..
-rw-r--r--   1 root root 2359048 2008-04-06 03:35 i810_dri.so
-rw-r--r--   1 root root 2464328 2008-04-06 03:35 i915_dri.so
-rw-r--r--   1 root root 2460136 2008-04-06 03:35 i915tex_dri.so
-rw-r--r--   1 root root 2475432 2008-04-06 03:35 i965_dri.so
-rw-r--r--   1 root root 2434920 2008-04-06 03:35 mach64_dri.so
-rw-r--r--   1 root root 2507624 2008-04-06 03:35 mga_dri.so
-rw-r--r--   1 root root 2345832 2008-04-06 03:35 r128_dri.so
-rw-r--r--   1 root root 2448008 2008-04-06 03:35 r200_dri.so
-rw-r--r--   1 root root 2353480 2008-04-06 03:35 r300_dri.so
-rw-r--r--   1 root root 2399464 2008-04-06 03:35 radeon_dri.so
-rw-r--r--   1 root root 2315240 2008-04-06 03:35 s3v_dri.so
-rw-r--r--   1 root root 2403400 2008-04-06 03:35 savage_dri.so
-rw-r--r--   1 root root 2421576 2008-04-06 03:35 sis_dri.so
-rw-r--r--   1 root root 2410248 2008-04-06 03:35 tdfx_dri.so
-rw-r--r--   1 root root 2260872 2008-04-06 03:35 trident_dri.so
-rw-r--r--   1 root root 2337584 2008-04-06 03:35 unichrome_dri.so
```

Notice the only difference is the 'fglrx_dri.so' library compared to my earlier post. Both 'libgl1-mesa-dev' and 'libgl1-mesa-glx' are installed in my system though.

Hopefully this helps someone.

---

### Post by Monkey_Tales on 2008-05-08
**Hardy Heron solved my 3D problem**
 
Since using Hardy Heron the 3D problem seems to be gone...
All aplications that didn't work anymore, do work under Hardy.
The 3D acceleration problem must be a Gusty problem, and very hard to find.
I am not going to look for Gutsy solutions, because i like and stick to Hardy Heron.
Sorry to say this, but Gutsy was an inbetween solution (for me).
 
:guitar:

---

### Post by demmsnt on 2008-06-02
In my box same problem. But in Hardy. I found, 

LD_LIBRARY_PATH=/usr/lib/xorg

Who set this variable?

if i unset LD_LIBRARY_PATH all work

But renaming libGL* in /usr/lib/xorg/ solve problem

---

