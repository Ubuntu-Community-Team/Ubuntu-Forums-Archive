---
title: "FLUXBUNTU Installation failure...???"
date: 2008-10-21
forum: Desktop Environments
---

### Post by icanfly0307 on 2008-10-21
Hi everyone,
                        I am trying to install fluxbuntu on my old computer. However, when it comes to the installing base system step, it comes up with an error saying:

"Cannot find release candidate version..."

Does anyone know what this means and how I can solve this issue? Also, for some reason, the installer starts up in a text based installer instead of the graphical one. This is not an issue, but my system is currently unusable because it was left in the middle of the installation!!! :(

Thanks

---

### Post by snowpine on 2008-10-21
> **icanfly0307 said:**
> Hi everyone,
                        I am trying to install fluxbuntu on my old computer. However, when it comes to the installing base system step, it comes up with an error saying:

"Cannot find release candidate version..."

Does anyone know what this means and how I can solve this issue? Also, for some reason, the installer starts up in a text based installer instead of the graphical one. This is not an issue, but my system is currently unusable because it was left in the middle of the installation!!! :(

Thanks

Hi there I Can Fly, tech support for Fluxbuntu is kind of non-existent these days, but I'll do my best to help you out. A few questions to get started:

1. What are your system specs (processor, ram, hard disk, video, networking, etc)?
2. Where did you download the Fluxbuntu installer (here's where I got mine: [http://releases.fluxbuntu.org/7.10/rc/](http://releases.fluxbuntu.org/7.10/rc/))
3. Did you burn at a slow speed and check the disk's integrity to rule out the possibility of a bad burn?
4. Have you experimented with any other distros for older computers, such as Puppy, DSL, Debian Etch, Crunchbang, etc.?

I have never experienced that particular error message before ("Cannot find release candidate version..."). Fluxbuntu just doesn't boot right on many computers, as we discussed in this thread: [http://ubuntuforums.org/showthread.php?t=941481](http://ubuntuforums.org/showthread.php?t=941481)  There is an unofficial "fluxbuntu remix" that may solve your problem discussed here: [https://bugs.launchpad.net/fluxbuntu-project/+bug/157724](https://bugs.launchpad.net/fluxbuntu-project/+bug/157724)

ps It is normal for Fluxbuntu to have a text installer. It never had a graphic installer due to its support of low-spec systems.

---

### Post by icanfly0307 on 2008-10-21
Hi,
   Here are my system specs:
     --Pentium III 1 Ghz
     --Intel 82815 Onboard Graphics Controller
     --256 Megs of RAM
     --20 Gb Hard Drive
     --Intel Pro 100 Mbits Ethernet Controller

I downloaded the iso image from the same site that you did. And yes I did a slow burn. No, I haven't tested it on other computers. However, I can tell you this: My CD Drive is currently not functioning well. But I am sure that this is not causing the error. I'll try the alternative suggestion that you mentioned and try it.

Hope this helps.

---

### Post by snowpine on 2008-10-21
Hi there, I successfully ran Fluxbuntu for a while on a computer with simliar specs, so I am pretty sure your hardware is up to the task. Your faulty CD drive is my guess as the likely cause of the error message. One tip I've read on these forums, but never personally tried, is this: if you have another computer, try swapping the hard drives and installing on the other computer with the working CD drive, then switch the hard drives back. 

If you don't have any luck with Fluxbuntu, there are lots of other good options for that hardware (many good threads on that topic here on the forums). Personally I stopped using Fluxbuntu--despite liking a lot of things about it--because 1) it hasn't had any updates, bug fixes, or technical support for over a year now; 2) it only has 6 months left in its lifecycle (it's based on gutsy and gutsy's 18-month support cycle ends in April 2009); 3) in my personal and somewhat controversial opinion, Ubuntu is not a good "core" system for a lightweight distro. 

Good luck!

---

### Post by icanfly0307 on 2008-10-21
Hey, 
        just a quick question. My Cd Drive fails to spin the CD in the drive. It can make an initial spin but if the cd idles, it cant start the spin again. So, is there a way to remove the cd each time it fails to spin and then continue the installation process from the point where it left off?

In simple words:

--Installation in process, CD idles, cannot initiate spin again
--Remove CD (force unmounting), put it in again, remount CD
--Continue Installation

Thanks

---

### Post by snowpine on 2008-10-21
I just checked Newegg.com and they have several CD-ROM drives starting at $9.99. :)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16827134011](http://www.newegg.com/Product/Product.aspx?Item=N82E16827134011)

Seems to me your faulty CD drive will be an issue regardless of which distro you try to install, so your problem is not really specific to Fluxbuntu.

---

