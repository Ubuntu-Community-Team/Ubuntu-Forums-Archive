---
title: "What is the current default of Ubuntu 23.04? Xorg or Wayland?"
date: 2023-10-12
forum: Desktop Environments
---

### Post by sblantipodi on 2023-10-12
As title.

What is the current default of Ubuntu 23.04? Xorg or Wayland?

Thanks

---

### Post by ian-weisser on 2023-10-12
Wayland.

---

### Post by Rubi1200 on 2023-10-12
At the login screen you can choose to switch between them. Bear in mind that whichever one you choose will then be the default the next time you boot/restart the computer.

---

### Post by sblantipodi on 2023-10-12
> **Rubi1200 said:**
> At the login screen you can choose to switch between them. Bear in mind that whichever one you choose will then be the default the next time you boot/restart the computer.

default is wayland on every kind of hardware?

---

### Post by sblantipodi on 2023-10-12
ok I installed Ubuntu 23.10.

the default is X11... 
why people says that it's wayland?

I simply installed Ubuntu with a usb key with the latest 23.10 iso.

as soon as the os is started this is the output of this command.

 echo $XDG_SESSION_TYPE
X11

why people says that the default is wayland and I have X11 as default?

---

### Post by grahammechanical on 2023-10-12
This could be the reason

[https://forums.developer.nvidia.com/t/nvidia-graphics-card-not-being-used-on-ubuntu-22-10/237489](https://forums.developer.nvidia.com/t/nvidia-graphics-card-not-being-used-on-ubuntu-22-10/237489)

It is possible that on Nvidia video adapters Ubuntu will default to Xorg. I remember hearing something of the sort some months back. I cannot find a link for it. You can use Software and Updates>Additional Drivers tab to disable the Nvidia driver. It might be possible to run the Wayland compositor when using the open source video driver.

Regards

---

### Post by sblantipodi on 2023-10-12
I have no problem in enabling wayland with nvidia driver,
my only doubts was why everyone says that wayland is the default when my default is X11.

Running an RTX4090 here...

---

### Post by #&amp;thj^% on 2023-10-12
+1 to the above, "You can only make use of the nvidia gpu using offloading with Xwayland."
```
Graphics:
  Device-1: NVIDIA TU117M [GeForce GTX 1650 Ti Mobile] vendor: Lenovo
    driver: nvidia v: 535.113.01 arch: Turing pcie: speed: 2.5 GT/s lanes: 8
    bus-ID: 01:00.0 chip-ID: 10de:1f95 class-ID: 0300
  Device-2: Syntek Integrated Camera driver: uvcvideo type: USB rev: 2.0
    speed: 480 Mb/s lanes: 1 bus-ID: 1-3:2 chip-ID: 174f:244c class-ID: 0e02
    serial: 0001
 [COLOR="#FF0000"] Display: wayland server[/COLOR]: X.Org v: 23.2.1 with:[COLOR="#FF0000"] Xwayland v: 23.2.1[/COLOR]
    compositor: gnome-shell v: 45.0 driver: X: loaded: modesetting,nvidia
    dri: swrast gpu: nvidia display-ID: :0 screens: 1

```
```
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|  [COLOR="#FF0000"]  0   N/A  N/A      1390      G   /usr/bin/gnome-shell                          1MiB |[/COLOR]
+---------------------------------------------------------------------------------------+

```

---

### Post by #&amp;thj^% on 2023-10-12
> **sblantipodi said:**
> I have no problem in enabling wayland with nvidia driver,
my only doubts was why everyone says that wayland is the default when my default is X11.

Running an RTX4090 here...

Have a look: [https://www.omgubuntu.co.uk/2021/01/ubuntu-21-04-will-use-wayland-by-default](https://www.omgubuntu.co.uk/2021/01/ubuntu-21-04-will-use-wayland-by-default)
If your using the nvidia driver now and on Wayland session, please show me this:
```
nvidia-smi | grep /usr/bin/gnome-shell
```

---

### Post by ian-weisser on 2023-10-12
> **sblantipodi said:**
> default is wayland on every kind of hardware?

No. Some hardware has historically been incompatible with Wayland.
A new install on hardware that is compatible with Wayland will default to Wayland.

If your hardware is currently incompatible with Wayland, then you won't be offered the choice (gear icon on the password screen). You will have only X options.

If your hardware was incompatible with Wayland in the past, but is now compatible in the present, then the old default to use X can be changed using the gear icon on the password screen.

The choice between X and Wayland is persistent. Only you can change it. It is not changed by a release-upgrade. So older systems that have been release-upgraded may simply be carrying on with X from the pre-choice era. Or perhaps the admin forgot that they made the choice years ago. Easy enough to change at the login screen.

If you discover hardware that is compatible with Wayland, but that compatibility is not shown among the options on the password screen of the current development release, then please file a bug report. Don't file bug reports for old releases or old kernels -- test the development release.

---

### Post by sblantipodi on 2023-10-13
> **1fallen said:**
> Have a look: [https://www.omgubuntu.co.uk/2021/01/ubuntu-21-04-will-use-wayland-by-default](https://www.omgubuntu.co.uk/2021/01/ubuntu-21-04-will-use-wayland-by-default)
If your using the nvidia driver now and on Wayland session, please show me this:
```
nvidia-smi | grep /usr/bin/gnome-shell
```

vidia-smi | grep /usr/bin/gnome-shell
|    0   N/A  N/A      7028      G   /usr/bin/gnome-shell                        397MiB |

---

### Post by sblantipodi on 2023-10-13
> **ian-weisser said:**
> No. Some hardware has historically been incompatible with Wayland.
A new install on hardware that is compatible with Wayland will default to Wayland.

If your hardware is currently incompatible with Wayland, then you won't be offered the choice (gear icon on the password screen). You will have only X options.

If your hardware was incompatible with Wayland in the past, but is now compatible in the present, then the old default to use X can be changed using the gear icon on the password screen.

The choice between X and Wayland is persistent. Only you can change it. It is not changed by a release-upgrade. So older systems that have been release-upgraded may simply be carrying on with X from the pre-choice era. Or perhaps the admin forgot that they made the choice years ago. Easy enough to change at the login screen.

If you discover hardware that is compatible with Wayland, but that compatibility is not shown among the options on the password screen of the current development release, then please file a bug report. Don't file bug reports for old releases or old kernels -- test the development release.

this is true, I haven't the icon to switch to wayland, I had to enable it editing the 
/etc/gdm3/custom.conf

Most of my apps doesn't work on wayland, at this point what is the point of wayland if devs doesn't want to support it?

---

### Post by ian-weisser on 2023-10-13
> **sblantipodi said:**
> this is true, I haven't the icon to switch to wayland, I had to enable it editing the 
/etc/gdm3/custom.conf

This strongly suggests that you have incompatible hardware. Thus your Wayland problems seem to be expected behavior.

Your experience is not universal. Wayland is well-supported. I have used Wayland since 2017 with no serious problems. No problems at all since 2019.

---

### Post by #&amp;thj^% on 2023-10-13
> **ian-weisser said:**
> This strongly suggests that you have incompatible hardware. Thus your Wayland problems seem to be expected behavior.

Your experience is not universal. Wayland is well-supported. I have used Wayland since 2017 with no serious problems. No problems at all since 2019.

+1 and to add your card is seen by Wayland just not used, shown by:
> **sblantipodi said:**
> vidia-smi | grep /usr/bin/gnome-shell
|    0   N/A  N/A      7028      G   /usr/bin/gnome-shell                        397MiB |
When it's used it will populate something like:
```
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A      4290      G   /usr/lib/xorg/Xorg                          198MiB |
|    0   N/A  N/A      5408      G   xfwm4                                         2MiB |
|    0   N/A  N/A     54790      G   /usr/bin/python                              11MiB |
|    0   N/A  N/A     76310      G   /usr/lib/firefox/firefox                    144MiB |
+---------------------------------------------------------------------------------------+

```
And It's nVidia's job to help fix all this, and not Ubuntus...

---

### Post by sblantipodi on 2023-10-13
> **ian-weisser said:**
> This strongly suggests that you have incompatible hardware. Thus your Wayland problems seem to be expected behavior.

Your experience is not universal. Wayland is well-supported. I have used Wayland since 2017 with no serious problems. No problems at all since 2019.

I sincerely never seen so much people that likes Wayland... 
wayland is too distruptive, there are too many apps that doesn't work with wayland after years... 
I sincerely don't think that wayland will be the future for the desktop environment...

---

### Post by #&amp;thj^% on 2023-10-13
weather plenty of people or few people like it, It's here to stay.
Embrace the future and you'll be much better off.
"resistance is futile" :P

---

### Post by TheFu on 2023-10-16
I installed Ubuntu-Mate 23.10 a few days ago into a VM with virtio for the GPU and it didn't have Wayland.  I considered it a feature NOT to use Wayland, since it breaks a number of my workflows, still.  There doesn't seem to be any movement on Wayland bugs brought up in 2018. Guess they decided such a small number of people are impacted so it isn't worth their time to attempt fixes.  To be fair, some of those things take advantage of X11 security issues, so I can understand why some of them wouldn't be addressed.

I don't see why it would matter which display server people use unless they have a specific requirement for one or the other.

My hardware is an AMD APU (Ryzen 5600g), so it should be well supported by Wayland.

I hope Gnome doesn't cut off X11 support. That will drastically impact me and how I work.  Plus, Gnome is used on non-Linux platforms that don't have Wayland, so it would impact other F/LOSS communities.

---

### Post by sblantipodi on 2023-10-17
wayland it's rubbish in its current state, if ubuntu cuts it, people will cut ubuntu

---

### Post by TheFu on 2023-10-17
> **sblantipodi said:**
> wayland it's rubbish in its current state, if ubuntu cuts it, people will cut ubuntu

There is another group just as happy about Wayland because it is significantly faster and more secure than X11, at the cost of a few seldom-used capabilities. Can't make everyone happy. That's the nature of change.

Anyway, seems that Wayland is generally preferred at installation, but not not always possible. Different Ubuntu Flavors install or don't install Wayland based on their needs too.  

I remember a 20.04 install that tried to force Wayland onto everyone.  That crashed and burned on systems with nVidia GPUs.  Back then, for people who use screen recorders, the only tool that halfway worked with Wayland was from Gnome. It was part of the gstreamer crap-fest. Throwing Wayland into the world and seeing how few screen recording tools supported it did make those projects take note and start making their software compatible.  For example, OBS didn't support Wayland at all.  6 months later, they had some level of support and a year later, I get the feeling Wayland support in OBS was good.  OBS is a little heavy for my needs and fairly complex to setup for most people.

I've been using SimpleScreenRecorder for about a decade now.  Prior to that, I used an X/windows tool from the mid-1990s for screen captures, but getting the location to capture was 100% manual and a pain.  Just looked for a SimpleScreenRecorder option on AlternativeTo.net.  Only 1 in the list met my F/LOSS and Linux requirements and it was using gstreamer.  Uuuuug.

Perhaps gstreamer isn't as bad as it was 10 yrs ago. I just know that it was slow and bloated. SimpleScreenRecorder does have a number of options that do work for my needs, like control over which video and audio codecs are used for recording. Most of the others only support 1 video recording codec and the mandated container file type it is one I prefer to avoid too.

Definitely very unimportant problems, compared to all the problems in the world today.

---

### Post by den_ on 2023-12-31
> **grahammechanical said:**
> This could be the reason

[https://forums.developer.nvidia.com/t/nvidia-graphics-card-not-being-used-on-ubuntu-22-10/237489](https://forums.developer.nvidia.com/t/nvidia-graphics-card-not-being-used-on-ubuntu-22-10/237489)

It is possible that on Nvidia video adapters Ubuntu will default to Xorg. I remember hearing something of the sort some months back. I cannot find a link for it. You can use Software and Updates>Additional Drivers tab to disable the Nvidia driver. It might be possible to run the Wayland compositor when using the open source video driver.

Regards

Wayland works with proprietary drivers as well, question is only how well. At the beginning with 23.04 it was quite bad. E.g. it was basically impossible to watch videos (Browsers and players).
Situation later improved after I have upgraded to 23.10. However there are still some issues, and I also have some weird sound issues occasionally. Can't say if this is related to wayland. I did install some pulse audio stuff to be able to use pavucontrol. and the GPU is quite old (970GTX).
But the sound issues mainly started after I had installed Fallout New Vegas. Aside from that the only problem I have noticed with wayland was the system wasn't able to recover from suspend.

Anyhow, my new system with new 23.10 install works much better. Components and the GPU are brand new, and nvidia drivers for 40 series are better, but the *_interesting part is that the system didn't come with wayland. Installer only installed Xorg and I chose the proprietary driver._*

It is crazy how well everything works. If you have a system like this (Where everything works.) and you need it for productivity work, and don't feel like experimenting, troubleshooting, reinstalling, my advice is leave it and forget about wayland for now, then try again after 24.04 or the next release.

I have never had a system where everything works this well without me having to mess with it. Re games, I installed Cyberpunk and New Vegas, both work amazing (No tweaking involved. Simply installed steam, then game). Vegas crashed only once (What's pretty good compared to windows), I didn't have to install any mods to prevent game from freezing on load etc.

Cyberpunk also froze once, only after me spending a half an hour, trying out a bunch of different graphic settings.

---

