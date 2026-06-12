---
title: "Getting Started with running latest development release on VM"
date: 2012-07-11
forum: Development CD/DVD Image Testing
---

### Post by epikvision on 2012-07-11
I synced with Quantal image on TestDrive. I was very excited to run the development release until I realized how slow QEMU was!  It takes 15 minutes every time for Ubuntu 12.10 to get to the screen, Try or Install Ubuntu. 

I don't want to install Quantal from scratch into my computer. Thus, I've been seeking ways to install Quantal safely and efficiently.  One solution I found was to use virtualbox in accordance with QEMU, but the question is how? 

How can I link TestDrive and QEMU together so that I could try Quantal? A prospective developer should run the latest release... Thanks.

---

### Post by sanderj on 2012-07-11
Installing VirtualBox with any Ubuntu version is a matter of minutes. No QEMU needed.

So:
Install & Start VirtualBox
Create a new Virtual Machine, boot it, point it to the download quantal image

---

### Post by epikvision on 2012-07-11
Alright, thanks!

---

### Post by epikvision on 2012-07-11
Ok, I started running Ubuntu Quantal in VM, and I see this.

> This kernel requires an x86-64 CPU, but oonly detected an i686 CPU.  Unable to boot - please use a kernel appropriate for your CPU. 

How do I fix this?

---

### Post by sanderj on 2012-07-11
> **epikvision said:**
> Ok, I started running Ubuntu Quantal in VM, and I see this.



How do I fix this?

Well, as the error message suggests: download the 32-bit version of Quantal.

(You downloaded the 64-bit version of Quantal, and your OS and/or your CPU is only 32-bit).

---

### Post by epikvision on 2012-07-11
Well! I never knew that I was running x32 Ubuntu all along!  My computer has x64 processor.

---

### Post by sanderj on 2012-07-11
> **epikvision said:**
> Well! I never knew that I was running x32 Ubuntu all along!  My computer has x64 processor.


"uname -a" will tell you.

And: ubuntu.com still offers the 32-bit Ubuntu version as the default version. So, if you just click, you will get the 32-bit version.
Reason: the 32-bit version will run on any x86-CPU, and thanks to the PAE-kernel, even 32-bit versions can use all the memory (also more than 4GB). In other words: the 32-bit version always works.

---

### Post by epikvision on 2012-07-11
Ok, I encountered a new challenge.  As I was trying to install quantal by running it, I was hoping to be directed to the "Try or Install Ubuntu" window. Instead, an error message pops up saying 
> Installation failed. Installation encountered a serious error. You will be redirected to the desktop session...

Then I get redirected to the desktop session.  I press on "Install Ubuntu 12.10" only to get another error message, that Ubuntu 12.10 experienced an internal error with executable path, do-release-upgrade. 

Is this a bug?  if so, how can I report it? 

Is it necessary for the prospective developer to have the development release installed, because I'm trying to my utmost to install it in virtualbox?

---

### Post by michaelbenson on 2012-09-10
I had a hard time finding this post. I'm glad i'm here finally. Thanks

---

