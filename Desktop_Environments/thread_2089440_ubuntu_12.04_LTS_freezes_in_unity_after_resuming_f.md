---
title: "ubuntu 12.04 LTS freezes in unity after resuming from Lock, Suspend, and Hibernate"
date: 2012-11-29
forum: Desktop Environments
---

### Post by acerbuntu on 2012-11-29
Hi guys,

I am running ubuntu 12.04LTS and Iam having system freeze problems every time when I resume from lock, suspend, and hibernate.

This problem comes up only in unity (ubuntu) desktop not in unity 2D (ubuntu 2D) or Gnome Classic.

I don't have complete idea about it, but when click on ubuntu logo in my login box I can see 4 options such as **Ubuntu, Ubuntu 2D, Gnome Classic and Gnome Classic (No effects).**
My System freezes when I use it in Ubuntu environment.

Is Ubuntu environment unity 3D? 

Please help.

Thanks in Advance.

---

### Post by BlinkinCat on 2012-11-29
Hi,

Copy and paste and run -

```
/usr/lib/nux/unity_test -p
```Results will show if your hardware supports Unity.

Cheers - :P

Edit - yes Unity is 3D

---

### Post by acerbuntu on 2012-11-29
> **BlinkinCat said:**
> Hi,

Copy and paste and run -

```
/usr/lib/nux/unity_test -p
```Results will show if your hardware supports Unity.

Cheers - :P

Edit - yes Unity is 3D
Hi BlinkinCat,

Do you want me to login to Unity 3D and do that?

I tried in unity 2D it says "No such file or directory".

BDW My System Specs are as follows:

Screen Size 15.6 inches
Processor Type Intel Core i5 
Processor Speed 2.5 GHz (Turbo boost upto 3.1GHz)
Memory RAM Size 8 GB
Computer Memory Type DDR3 SDRAM
Hard Drive Size 750 GB
Graphics Card DescriptionNVIDIA GeForce GT 630M
Graphics Card Ram Size 1 GB VRAM
Pioneer DVD Super Multi DL Drive
HDMI out
USB 3.0
Audio Combo Jack
Acer Crystal HD Webcam
Average Battery Life (in hours)4.5 hours

thanks.

---

### Post by BlinkinCat on 2012-11-29
Hi,

Enter command into 2d terminal and post results back here.

Make sure you copy and paste command.

- :)

---

### Post by acerbuntu on 2012-11-29
Tried in 3D...No luck

> bash: /usr/lib/nux/unity_test: No such file or directory

Sorry I forgot to mention that I am using integrated graphics (HD 3000) not the NVidia.

Do the graphics need to be Nvidia? If so I don't have any idea how to make Nvidia work!

---

### Post by BlinkinCat on 2012-11-29
Specs look pretty good to me but I'm no expert.

It may have something to do with your graphics card.

---

### Post by acerbuntu on 2012-11-29
> **BlinkinCat said:**
> Hi,

Enter command into 2d terminal and post results back here.

Make sure you copy and paste command.

- :)
u mean in Ctrl+Alt+F1 or Alt+F1?

---

### Post by BlinkinCat on 2012-11-29
Hi-

You need to enter a space and then -p after test

---

### Post by BlinkinCat on 2012-11-29
It may be easier to download a terminal from Software Center

I have integrated graphics and Unity 12.04 is fine for me.

---

### Post by acerbuntu on 2012-11-29
> **BlinkinCat said:**
> Hi-

You need to enter a space and then -p after test
Hi,

Small change in command. Now it worked.

> /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string:  3.0 Mesa 8.0.4

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

---

### Post by BlinkinCat on 2012-11-29
Hi,

Result is good for Unity.

Suggest you wait for more qualified assistance to help solve your problem.

But cheerfully you are on the right track for Unity.

All the best - :P

---

### Post by acerbuntu on 2012-11-29
> **BlinkinCat said:**
> Hi,

Result is good for Unity.

Suggest you wait for more qualified assistance to help solve your problem.

But cheerfully you are on the right track for Unity.

All the best - :P
Thank you very much BlinkinCat.

I'm glad to know that I can use unity 3D.

Hope some one helps me.

Cheers. :)

---

### Post by BlinkinCat on 2012-11-29
> **acerbuntu said:**
> Thank you very much BlinkinCat.

I'm glad to know that I can use unity 3D.

Hope some one helps me.

Cheers. :)

Hi,

I'm glad to help - I'm only sorry that it took 10 posts to drag that out. Remember that if you don't get an immediate response you are entitled to bump you thread every 24 hours or so - hopefully you won't have to wait that long. There are many helpful members in the forums.

All the best and cheers - :P

---

### Post by BlinkinCat on 2012-11-29
Hi again,

There is a bug which may or may not be related to your issues -
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/989674](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/989674)

If the problems quoted sound familiar to yours you could register with Launchpad and add comments plus register that the bug affects you. In the meantime, perhaps someone on the forum can offer a solution.

All the best - :(

---

### Post by acerbuntu on 2012-11-29
> **BlinkinCat said:**
> Hi again,

There is a bug which may or may not be related to your issues -
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/989674](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/989674)

If the problems quoted sound familiar to yours you could register with Launchpad and add comments plus register that the bug affects you. In the meantime, perhaps someone on the forum can offer a solution.

All the best - :(
oic. The above bug remains quite similar symptoms but on the other-side I have to make my Nvidia work and then confirm.

Because in my case after resume I can view all my open windows freezed (not black/ white screen) and only mouse moving. 

And I don't remember what happened it was working until 2days before I started working with gnome 3 shell themes and cairo dock.And I also don't remember whether after installing ubuntu 12.04 it was on "Ubuntu" or "Ubuntu 2D" by default.

So now I have no idea how to find Nvidia installed or not? And what triggered my problem before 2days?

I installed bumblebee but don't know how to check nvidia.

Lets see if someone has any idea.

---

### Post by acerbuntu on 2012-11-30
I fixed this problem by doing a clean install. Now my sytem is running in Ubuntu, Ubuntu 2D and XBMC dektop (Hurray!!! I love this xbmc enjoyed couple of movies flawlessly:popcorn:).

With this my System Suspends, Hibernates and No more Freezes. 

I think something went wrong after messing with gnome shell and Cairo dock. However I did try both these desktops but I didn't enjoy them as much as i can do now in ubuntu desktop.Think they are not very reliable and stable desktops for ubuntu 12.04LTS.

However finally I am running 3D with integrated Intel graphics and I disabled NVIDIA in bios. As far as I know Nvidia is not required much unless you need it for gaming. And for Non Linear Video Editing and 3D design and other graphical apps intel HD 3000 should do.

My Sincere advice is not to mess up with other desktop environments unless you have good support.And also there are really some amazing features in ubuntu (unity 3D) to play:guitar: on, so please google it and try them.

Anyways this thread is [Solved] now. Thanks for BlinkinCat:)

---

### Post by BlinkinCat on 2012-11-30
Hi acerbuntu,

I'm so pleased that you were able to fix things yourself. 

We may run into each other again. All the best to you.

Cheers - :P

---

