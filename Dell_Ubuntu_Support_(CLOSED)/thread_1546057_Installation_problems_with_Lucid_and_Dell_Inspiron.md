---
title: "Installation problems with Lucid and Dell Inspiron 15R/Athlon II"
date: 2010-08-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by timnugent on 2010-08-04
This post is a bit long, but I'm putting my questions up front and numbering them. I hope someone will peruse the questions and then, if a question pops out as something you can address, kindly look at my correspondingly numbered explanation and post an answer.  No need to read everything unless you have the time and inclination.

I'm a graduate student about to start classes in 2 weeks, and an unabashed fan of Linux in general and Ubuntu in particular. I had a budget of $500 (US) and need a laptop to use for school for the coming years. I bought a Dell Inspiron 15R with an AMD Athlon II Dual Core 64 bit processor running at something just over 2 Ghz. It has 4 GB RAM and a 320 GB hard drive. Windows 7 Home Premium was installed.

I've tried to run and load Ubuntu 10.04 on the machine with very limited success indeed.

Here are my questions:

1) Does Ubuntu 10.04 run with my chip (AMD P320, I believe)?

2) Do I need to install special firmware first to make Ubuntu work on this system?

3) Should I return this system to the store and buy an Intel-based laptop instead?

4) Why does the 64 bit system on the Ubuntu download pages say it isn't for everyday use? Is this going to be made ready for everyday use eventually?

5) If the 32 bit system is the only stable one, will it employ both processors?

6) Should I be looking at another distribution of Linux such as Slackware or Debian or Knoppix maybe?

7) Why is Lucid Lynx 64 bit so sluggish on my laptop?

08) Why won't Lucid 32 bit boot up once installed?

9) If this installation can't be resolved, how do I avoid it again? What laptop should I buy in order to use Ubuntu 10.04 successfully and *reliably* for school?

OK, some explanations:

1) Everything I read suggests that Ubuntu (Including 10.04) should work with AMD dual core chips. Is this one too new to work? I tried  installing Lucid for AMD 64 but the system was sluggish and choppy. I tried downgrading to Lucid for 32 bit and while the system appeared to install successfully from the installation media, upon rebooting from the hard drive with the CD removed, I got the login panel asking for the user name along with 4 successive log-in drum sounds and a frozen screen from which I had to reboot, with the same results.

Linux Mint 9 had similar results as did Lubuntu 10.04--actually Lubuntu stalled at a splash screen before coming up at all.

2) I read here: [https://help.ubuntu.com/10.04/installation-guide/amd64/hardware-firmware.html](https://help.ubuntu.com/10.04/installation-guide/amd64/hardware-firmware.html) that firmware might need to be installed to get Ubuntu to work right in some circumstances. Looking over this process, it looks daunting, but it is the last thing I'm going to be able to try before giving up and getting a new system.

3) Is it common to have these kinds of problems with AMD? Is it that the system is too new and doesn't have proper drivers yet? If so, why does the 64 bit AMD version of Ubuntu fail to boot? Although it's sluggish, it does boot. At any rate, I don't have much time to mess around with a system that might or might not boot at the end of the process. I start school in 2 weeks and have lots on my plate before then... shall I return my dell and get something else?

4) Is the 64 bit installer labeled as not ready for prime-time because of bugs or incompleteness? Is canonical going to make this version work properly any time soon? Almost every computer available today is 64 bit, and multicore! I'm surprised that Canonical hasn't got this working right yet. I definitely need a reliable system, but I'm not able to get it here it seems. Why?

5) Self-explanatory question, but how would I know if both or only one processor were being used by the OS if I'm able to boot and run?

6) I wanted to use Ubuntu! So much so that I bought my laptop specifically for that intent. Am I 'barking up the wrong tree'? Please save me time if so and let me know I'm not going to get anywhere any time soon!

7) Is this why the download link for 64 bit Linux says not to use it for daily activities? Could it be that the install went bad somehow, or is it going to be sluggish using 64 bit no matter what?

8) The 4 drum sounds when the loggin window shows up is followed by a frozen screen and I have to reboot. Could this have to do with a firmware issue as mentioned in question 2?

9) Will the latest batch of Intel dual-core processors have problems too, perhaps because they are too new, or should I go get one of those machines? Is it better to buy something a couple of years old in order to run Ubuntu successfully?

Thank you for your attention. Any help appreciated.

Tim Nugent

---

### Post by gordintoronto on 2010-08-04
1. I would be amazed if Ubuntu would not work with your CPU. Problems are much more likely related to the video controller.

2. Unlikely.

3. Not yet. (Last summer I installed 64-bit Ubuntu on "the latest and greatest" AMD desktop, and it works very nicely.)

4. No one understands why Canonical has the disclaimer on 64-bit.

5. Yes

6. No

7. That's the heart of the issue. It shouldn't be sluggish.

8. There's an Ubuntu "HCL" web site (hardware compatibility list) but it's terribly outdated.

Also, Mint and Lubuntu should run very nicely, especially Lubuntu.

Have you ever Googled: Dell 15R Ubuntu

Did you do a Wubi install?

---

### Post by timnugent on 2010-08-04
Thank you Gordontoronto. I have not tried Wubi, this time or ever. I'm open to it, though. I installed Ubuntu over the old Windows 7 OS. Doesn't Wubi require a Windows install to work? Should I reinstall Windows and try that?

I noticed that during the 3 times I tried to install 32bit Ubuntu, there were slightly different outcomes each time. The first time wouldn't boot at all, the second time gave the four drum sounds at the login and almost let me click on my user account name, and the third time didn't let me get that far.

I'm going to try a few more of these installs along with an older distro or two, and other distros besides Ubuntu (still have my heart set on Lucid, though).

Again, shall I try a Windows reinstall and then a Wubi install? I'll look up Wubi and see how to do it.

Thanks again,

Tim Nugent

---

### Post by Ayjaytee on 2010-08-05
I am also having problems installing Ubuntu on a Dell. It's an Inspiron about 4 years old. I had Ubuntu 9.04 and it worked fine. But when I updated to 10.04 it won't boot. It boots from a CD and from a USB. I tried booting from the USB and then reinstalling but it won't boot from the new installation. All I get is 

error: out of disk
grub rescue


Any ideas? 
Ayjaytee

---

### Post by gordintoronto on 2010-08-05
Sorry about mentioning Wubi, I do NOT suggest using Wubi.

However, it might be worthwhile re-installing Windows, then confirm that your hardware works properly. About 5% of brand new systems do not! If you try to take the computer back, they will expect it to have the original OS.

Ayjaytee: please start your own thread.

---

### Post by timnugent on 2010-08-12
Terrific news! I did try Wubi, but with limited success. Then I tried a whole bunch of other Linux Distros, including Slackware, Scientific Linux, Knoppix, OpenSuSE.. might have even tried Fedora. Nearly all of those distros didn't install properly or at all. I also tried Ubuntu as configured by Dell for older laptops they sold, and I forget what the problem was, but I found it unsatisfactory.

Finally, I decided to give Lucid a try before returning the laptop and getting an Intel one. I installed the AMD 64 version and it still had the choppiness. However, I installed all the updates for the system, and lo! It worked like a charm!

I've been using it happily ever since!

Thank you for your time and attention--Maybe this will help or encourage someone else! Your encouragement was the only thing that kept me from bringing the system back prematurely.

Thanks again,

Tim Nugent

---

