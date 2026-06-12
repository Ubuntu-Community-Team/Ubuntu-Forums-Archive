---
title: "Ubuntu 22.04, problems with wayland"
date: 2022-09-20
forum: Desktop Environments
---

### Post by Dedalo on 2022-09-20
Hi there. I've been having problems since I've installed ubuntu 22.04. One of those problems is related to wayland. When wayland is enabled, after logging in into ubuntu, it takes like a lot to load, showing only a black screen, which makes look like the monitor were turned off. After it finally loads the system, a popup shows, with the message "The login keyring did not get unlocked when you logged into your computer.", and I have to put my login key again. 

This problem is solved if I set Waylandenable=false in the "/etc/gdm3/custom.conf" file. However, that causes other problems. I'm not able to share my screen in skype for instance, and my webcam doesn't work in cheese. 

I also had some trouble with mpi, which I'm not sure if those work when wayland is enabled, I should check that, but I'm pretty sure those problem appear when wayland is turned off. 

How can I solve all these issues? 

Thank you in advance.

---

### Post by grahammechanical on 2022-09-20
> This problem is solved if I set Waylandenable=false in the "/etc/gdm3/custom.conf" file.

If I do not want to use the Wayland compositor on 22.04 I press Enter at the login screen and then click the gear icon in the bottom right hand corner and select Ubuntu on Xorg. No need to edit a configuration file. To switch back to using Wayland I repeat the process and select Ubuntu. Wayland is default on Ubuntu 22.04.

Try using Advanced Options for Ubuntu and selecting an older Linux kernel. It might also be an issue with the video driver. What video card do you have? Are you using a proprietary video driver?

Regards

---

### Post by Dedalo on 2022-09-20
Hi. Thank you for your feedback. I have an nvidia gtx 1060, 3gb. I haven't installed any drivers. However, when I set waylandenable=true in the config file, the webcam works fine with cheese, but I have that issue, with the system taking too long when login in, with a totally black screen (looking like if turned off), and the popup message "The login keyring did not get unlocked when you logged into your computer.", where I have to put my login key again to use chrome. When I put  waylandenable=false in the config file, the login is fast, with no popup message regarding the keyring, but the webcam stop working with cheese, and I can't share my screen in skype.

---

### Post by TheFu on 2022-09-20
Wayland is KNOWN not to work well with nvidia. 2 weeks after the 22.04 release, Canonical changed the installation so that systems with nvideo GPUs would use Xorg, not Wayland.  You can check the release notes for more information.

Wayland has lots of problems for some specific workflows. Usually people with those workflows learned this years ago and have been quietly waiting for fixes.  They will come, hopefully.

To be fair, it is hard to replace a solution with 40 yrs of history, features, and fixes, for one with 10 yrs, no matter how excited the development team is about the new stuff.  It will take some time.  Wayland is preventing a number of X/Windows security failures that have been around for decades. Some of those failures allow some key workflows used by many people.

Nvidia drivers on Linux aren't open enough for the world to fix stuff as they go, so we are stuck waiting for that company to decide if a fix is needed or not, then wait for it to arrive in a driver, then wait for the driver to be tested with our much loved Ubuntu and made accessible through the ubuntu-drivers tool.  

I like the ubuntu-drivers tool, it has simplified getting solid GPU drivers that are known to work with the Canonical kernels greatly.

---

### Post by Dedalo on 2022-09-27
> **TheFu said:**
> Wayland is KNOWN not to work well with nvidia. 2 weeks after the 22.04 release, Canonical changed the installation so that systems with nvideo GPUs would use Xorg, not Wayland.  You can check the release notes for more information.

Wayland has lots of problems for some specific workflows. Usually people with those workflows learned this years ago and have been quietly waiting for fixes.  They will come, hopefully.

To be fair, it is hard to replace a solution with 40 yrs of history, features, and fixes, for one with 10 yrs, no matter how excited the development team is about the new stuff.  It will take some time.  Wayland is preventing a number of X/Windows security failures that have been around for decades. Some of those failures allow some key workflows used by many people.

Nvidia drivers on Linux aren't open enough for the world to fix stuff as they go, so we are stuck waiting for that company to decide if a fix is needed or not, then wait for it to arrive in a driver, then wait for the driver to be tested with our much loved Ubuntu and made accessible through the ubuntu-drivers tool.  

I like the ubuntu-drivers tool, it has simplified getting solid GPU drivers that are known to work with the Canonical kernels greatly.

Hi. Thank you. I haven't installed any drivers for the GPU. Should I? everything worked fine with ubuntu 20.04, but I think I had installed the gpu drivers after installing ubuntu 20.04. 

I am also having problems with mpi, and I don't know why. I have installed the gfortran and the intel fortran compilers. I have realized like two months ago, when I installed ubuntu 22.04 that I can install the intel fortran compiler for non commercial use. As I use the intel compiler in a cluster, I thought it was a good idea to have it on my desktop computer. I think MPI worked fine before I've installed the intel API, mkl and all that stuff. I don't know if I should create a different topic for this issue. I wrote a post about this here: [https://askubuntu.com/questions/1423120/problem-with-mpi-on-ubuntu-22-04](https://askubuntu.com/questions/1423120/problem-with-mpi-on-ubuntu-22-04)

Thanks for your help.

PS: I have now installed the nvidia drivers, the problem persists. Moreover, I have set WaylandEnable=false, and WaylandeEnable=true in the config file, restarted the computer and everything, and nothing changes. It seems like, no matter how I set it, it continues to show, in the system configuration, to be using X11 (Xorg) as the window manager. I've tryied to use wayland selecting it in the cog wheel in the login screen, and it didn't work, the same problem persists, it shows the black screen and then returns to the login screen (it doesn't login at all). This is the buggiest ubuntu version I have ever seen, it was a total mistake to install this version, it is taking a lot of time to resolve issues that in ubuntu 20.04 wasn't a problem at all. I think ubuntu 22.04 shouldn't even exist.

---

### Post by TheFu on 2022-09-27
Just restore from the backup you made before attempting to replace the OS with newer.  Shouldn't be a big deal. 20.04 any DE has support until April. Gnome 3+ and Server have support until 2025. No hurry.

Millions of people are running 22.04 happily. They think is it better than 20.04 for different reasons. Perhaps their hardware is better supported or some issue they had with 20.04 got fixed?  Hard to say.

I wait to migrate important systems until I've migrated a few less important systems, to get comfortable with any new release.  Right now, only "play" systems are running 22.04.  Last Saturday, I moved an important system from 18.04 --> 20.04. Most everything is working, but a few things aren't. Only 1 remains that I miss, mpd. Other audio programs are working fine, just mpd isn't. Had the same issue with 18.04, that solution isn't working on 20.04.

---

### Post by Dedalo on 2022-09-27
> **TheFu said:**
> Just restore from the backup you made before attempting to replace the OS with newer.  Shouldn't be a big deal. 20.04 any DE has support until April. Gnome 3+ and Server have support until 2025. No hurry.

Millions of people are running 22.04 happily. They think is it better than 20.04 for different reasons. Perhaps their hardware is better supported or some issue they had with 20.04 got fixed?  Hard to say.

I wait to migrate important systems until I've migrated a few less important systems, to get comfortable with any new release.  Right now, only "play" systems are running 22.04.  Last Saturday, I moved an important system from 18.04 --> 20.04. Most everything is working, but a few things aren't. Only 1 remains that I miss, mpd. Other audio programs are working fine, just mpd isn't. Had the same issue with 18.04, that solution isn't working on 20.04.

Hi. Thank you. I think I will consider moving back to version 20.04. April seems too soon to lose support for the 20.04 if all these issues are not fixed in the 22.04 version. I don't really understand what happened with MPI. I don't know if its ubuntu or something messed up when I installed the intel fortran compiler, after gnu fortran.

---

### Post by TheFu on 2022-09-27
Ubuntu Gnome3 20.04 and Ubuntu Server get 5 yrs of support.  The other flavors get 3.  No surprise there. It is published and longer than many other distro releases.  That's April 2023 for 22.04 desktops.  
Non-LTS releases get 6-9 months of support, so 22.10 will be supported until around June/July 2023.
Loss of support means the repos are removed. Canonical stops maintaining the non-core programs/libraries and lots of attack vectors become possible.

I haven't touched Fortran since college. Think the last program I ran was on a Cray Y-MP there. I've never used Intel's Fortran. Played with a pirated MS-Fortran in the mid-80s, but it was too slow compared to the CDC servers we had.  I left a CFD program running on my PC at the time for 4 days and it crashed due to lack of RAM.  The Cray did that problem in 20 minutes ...  About a year ago, I looked up how a Ryzen 5600G would compare to that model of Cray - it is a little faster (the Ryzen). Not bad for the $140 price I've seen recently.

No clue what MPI is. It isn't a common term in Linux circles.

You should assume that something about your setup is odd, not that 22.04 is terrible.  It might be terrible for you, but that isn't the normal experience.

BTW, nobody here works for Canonical.  There are many things that I dislike in almost every release, but they also do 1000+ other things well.  You can ask for a refund, if you like.  Or you can switch to another distro, if Ubuntu-whatever doesn't fill your needs.  Linux Mint is very popular.

---

### Post by Dedalo on 2022-09-28
No refund for me, I haven't paid for anything :P

It's ok, I'll see what I can do. MPI is the message passing interface for parallel programming. Most clusters work on Linux, none I've seen uses ubuntu anyway. I think something broke when I installed the intel fortran compiller and the API, I've never installed it before, always used the GNU compilers. The cluster I work in uses intel fortran, so I thought it was a good idea to have the same compiler on my desktop computer because I have to change my codes a little bit when I run in the cluster. 

MPI should run the same program on different processors but under a single interface, each processor is assigned with a different task. I use it to decompose a big problem into little pieces to solve it in parallel. However, I think that after I installed the intel fortran compiler it started to run multiple programs on different processors, i.e. the same program runs multiple times in parallel, instead of running one single program under the same MPI environment (instead of breaking up the problem and solving each part in different processors, it executes exactly the same program in each processor, with no communication between them, which is awful and useless). I don't know what happened. I might format the disk and start all over again with another distro. Or maybe I'll try to delete the intel fortran compiler and re-install gfortran (I suspect there might be some conflict with the compilers because MPI can use either of them).

Thank you anyway. Hope these issues get solved soon, because it is discouraging for ubuntu users, and that might ultimately cause a migration to other Linux distributions.

---

### Post by Dedalo on 2022-09-29
I have one good news, the issue with MPI was fixed. MPI was using intel, and I was compiling with gnu. So, the only problem still being wayland, which is not working properly (not working at all actually for me). Even in Xorg, the system shows this black screen after logging in for a long time. And when it finally logs in, it asks for the key again when I try to open chrome.

I tried to take a picture in cheese. When I open cheese I can see the image from the webcam, but when I try to take the picture it delivers an error message, which says that there was an error playing video from the webcam. After I changed the picture resolution from 640x480 to 1024x768 it successfully took the picture.

---

