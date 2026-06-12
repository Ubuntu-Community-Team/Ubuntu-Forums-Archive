---
title: "Very happy with Wayland in Ubuntu 21.04 on nVIDIA hardware"
date: 2021-04-26
forum: Desktop Environments
---

### Post by bert.ram.aerts on 2021-04-26
I have a Dell Inspiron 7577 laptop with nVIDIA GeForce GTX 1060 with max-Q design running Ubuntu 21.04.
It has a HiDPI screen 3840x2160 and I use fractional scaling at 175% with Gnome.
nVIDIA driver is latest 465.24.02 from
[https://launchpad.net/~oem-solutions-group/+archive/ubuntu/nvidia-driver-staging?field.series_filter=hirsute](https://launchpad.net/~oem-solutions-group/+archive/ubuntu/nvidia-driver-staging?field.series_filter=hirsute)
Up to now I was using Xorg. But I changed to Wayland a few days ago.
Matlab and VMWare Workstation Player complain about missing OpenGL hardware acceleration.
But overall I am very happy with Wayland.
No special tricks needed for many applications like Spotify and Matlab which previously did not scale in Xorg.
With Wayland Matlab scales perfectly out of the box.
Also resume from suspend to RAM now works for the first time on this laptop.
Though it takes 1 minute 45 seconds from power button to lock screen.
VLC full screen also works great, previously not possible in Xorg.
Waiting for nVIDA 470 series to have OpenGL hardware acceleration...
[https://www.phoronix.com/scan.php?page=news_item&px=NVIDIA-470-Wayland-Friendly](https://www.phoronix.com/scan.php?page=news_item&px=NVIDIA-470-Wayland-Friendly)

---

### Post by ActionParsnip on 2021-04-26
Nice to hear a success story :)

---

### Post by yaminb on 2021-04-28
Not to sound like an idiot but how did you enable Wayland?

I upgraded to 21.04 and have an nvidia card (Driver 460). 
I don't see the option to use wayland in the login screen.

---

### Post by TheFu on 2021-04-28
FYI, x2go does not work with gnome [s]wayland[/s] and probably never will.  It does work with wayland using fvwm and I bet most other DEs.
For kvm+libvirt VMs using the Spice protocol, wayland does work. I only use spice on a secured LAN, so need a new solution for internet use, which is what x2go does very well.

---

### Post by grahammechanical on 2021-04-28
Just passing on some information. 

In Ubuntu 21.04 Wayland is default. No option to login to X server.

Regards

---

### Post by TheFu on 2021-04-28
> **grahammechanical said:**
> Just passing on some information. 

In Ubuntu 21.04 Wayland is default. No option to login to X server.

Regards

/etc/gdm3/custom.conf has a settling to disable wayland, at least in 21.04 gnome.
```
$ sudoedit /etc/gdm3/custom.conf

# Uncomment the line below to force the login screen to use Xorg
# WaylandEnable=false
```
Then either restart gdm3 or reboot.

---

### Post by dddman on 2021-04-28
I am running 21.04.  This is not the xorg option??

[ATTACH=CONFIG]288388[/ATTACH]

---

### Post by TheFu on 2021-04-28
> **dddman said:**
> I am running 21.04.  This is not the xorg option??

That isn't offered to everyone.  See - no gear anywhere ... update: seems we have to enter/select a userid before the gear is displayed.
[ATTACH=CONFIG]288389[/ATTACH]

---

### Post by grahammechanical on 2021-04-28
On your system yes but not on my system. How did you get 21.04. I installed 20.10 and then upgraded to the 21.04 development version which has recently updated to 21.04 as officially released. It has no cog icon in the bottom right hand corner of the log in screen. I am sure that it had a cog icon during the 26 week development period. Will not swear to it, though.

Wayland is not a problem for me. It works to my satisfaction. I have just upgraded this 21.04 install to 21.10 development version. I plan to continue this way until it gets to 22.04 LTS. Then I will do a fresh install of 22.04 LTS over my present main working installation of 20.04 LTS. I like to see how things are developing.

Regards

---

### Post by ajgreeny on 2021-04-28
The option for xorg or wayland appears only after you have accepted a username by hitting Enter with that user showing in the box.

---

### Post by dddman on 2021-04-28
My bad...
I'm running 20.04...
I'll shut up now  :oops:

---

### Post by TheFu on 2021-04-28
> **ajgreeny said:**
> The option for xorg or wayland appears only after you have accepted a username by hitting Enter with that user showing in the box.

Ah ... I have to pick a userid first?  Anyway, I don't know how to capture a screen with that popup open, but it shows 2 options: **Ubuntu and fvwm**. Let me try something ... 
Ok, I have 3 options now:  **fvwm, Ubuntu and Ubuntu on Xorg**. I had Wayland disabled in the gdm3/custom.conf file.
```
# WaylandEnable=false
```
x2go doesn't like gnome. 
I see an "Oh no. Something has gone wrong" error inside the new GUI window if gnome is used, regardless of the Wayland or Xorg option.
OTHO, x2go connecting to an fvwm WM with either Wayland or Xorg both work.  Interesting.  I'll try to clean up my posts above to ensure Gnome + x2go are clearly shown as the problem, not Wayland.
If anyone cares, Spice works with both Wayland or Xorg too, even if Gnome is used.

I pulled 
```
2715254784 May  2  2020 ubuntu-20.04-desktop-amd64.iso
``` from a mirror and validated the sha256sums.
Also pulled the server version, but haven't played with it at all, yet.

So, basically, ignore all my posts in this thread. I was working two issues today - x2go and wayland. Got issues with x2go+Gnome mixed up with Wayland.  I've been seeing some other GUI funkiness, but don't know what is the cause. Select/paste got broken on one of my desktop systems, but not all of them. No clue about that. Plus 2-finger scrolling got reversed around the same time.  All OT for this thread.

---

### Post by bert.ram.aerts on 2021-04-29
I described the needed steps in [https://askubuntu.com/questions/1334825/what-are-the-steps-to-run-wayland-on-21-04-with-nvidia](https://askubuntu.com/questions/1334825/what-are-the-steps-to-run-wayland-on-21-04-with-nvidia)

---

### Post by yaminb on 2021-04-29
For what it's worth, I tried the above steps and I couldn't get the login screen.

It was the modeset line.

add to /etc/modprobe.d/nvidia-graphics-drivers.conf:
options nvidia_drm modeset=1


It kept saying something like Nvidia probe routine failed for 1 device...

So, I removed that configuration from /etc/modprobe.d/nvidia-graphics-drivers.conf
Back to xorg and working again.

---

### Post by rbmorse on 2021-04-29
FWIW, it works better on the Hippo than it does for Fedora 34 where there is a definite lack of hardware video acceleration with Nvidia for Youtube and other sites using VP9 format video. 

 Works fine on Ubuntu, though.  EDIT:  The Ubuntu installation here is a VMWare virtual machine on a Win 10 host.  That may make a difference.

---

### Post by irv on 2021-07-09
The day before last I upgraded from 20.04 to 20.10 and then 21.04 and everything went well. Took about 40 to 45 minutes to complete. (I have a fast Internet.)
It seemed like most things I did were giving me problems. Take for example drag and drop uploads. Sometimes it would take 5 or 6 tries. Then I use OBS all the time for my podcast. (OBS is not supporting Wayland yet.) The screen capture (XSHM) won't work in OBS. I had to switch back to xorg. And yes, you have to select your login name before the gear appears. My thoughts are we need to wait for things to catch up to Wayland before using it on a daily basis. It appears everything is back to normal now that I am back on xorg.

---

### Post by TheFu on 2021-07-09
I recall something about OBS supporting Wayland recently.   [https://obsproject.com/forum/threads/obs-and-wayland.138576/](https://obsproject.com/forum/threads/obs-and-wayland.138576/)  I'm not that versed in OBS - I dabble, but only use it about once a quarter.  Something about Wayland and Pipeline being required.

---

### Post by irv on 2021-07-09
> **TheFu said:**
> I recall something about OBS supporting Wayland recently.   [https://obsproject.com/forum/threads/obs-and-wayland.138576/](https://obsproject.com/forum/threads/obs-and-wayland.138576/)  I'm not that versed in OBS - I dabble, but only use it about once a quarter.  Something about Wayland and Pipeline being required.

Your right on this, but it requires a plugin. And even if I install it, it will not fix the drag and drop issue. Thank for the link, but for now, I will stay with xorg until OBS supports Wayland out of the box.

---

### Post by monkeybrain20122 on 2021-07-09
> **grahammechanical said:**
> Just passing on some information. 

In Ubuntu 21.04 Wayland is default. No option to login to X server.

Regards

I just made a fresh install of 21.04 on kvm and here is a screenshot of the login screen, the xorg option is clearly there (first time login ever, have not modified anything)

---

