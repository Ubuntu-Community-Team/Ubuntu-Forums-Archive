---
title: "wine &amp; VM"
date: 2008-12-25
forum: General Help
---

### Post by hirohitosan on 2008-12-25
Hi there.
For many reasons I have to use some Windows products like Word 2007, CorelDraw, etc.
I also have a MacOS computer and in Apple world there is a Virtual Machine called "Parallels Desktop" where you can install WinXP (or others OS) and run all WIN applications in a Mac windows.

There is something similar in Ubuntu?

Wine is something similar with "Parallels Desktop" in Mac?

thanks

---

### Post by SPr on 2008-12-25
Wine can be used to run some Windows executables but not all.
Crossover Office (based on Wine, I believe) can run MS Office on Linux.
There is a version of CoralDraw for Linux (but it's not free).

VirtualBox and VMPlayer sound more like Parallel Desktop. VBox might be in the repos but VMPlayer isn't but Google will find their site for you.

---

### Post by AnRa on 2008-12-25
[VirtualBox](http://www.virtualbox.org/)

---

### Post by hirohitosan on 2008-12-26
> **SPr said:**
> VBox might be in the repos
I installed VBox but there are some things that don't work. For example the arrow keys doesn't work PgUp $ PgDn keys doesn't work.
Has someone experience in using VBox?

---

### Post by happyhamster on 2008-12-26
Have you installed the guest-additions? (Boot the VM into windows and choose Device--> Install Guest Additions. It should mount VboxGuestAdditions.iso for you and start the installer. Afterwards, you'll probably have to reboot the virtual machine to be able to see the effect.)

Good luck.

---

### Post by albinootje on 2008-12-26
> **hirohitosan said:**
> I installed VBox but there are some things that don't work. For example the arrow keys doesn't work PgUp $ PgDn keys doesn't work.
Has someone experience in using VBox?

Which Ubuntu release are you using ?
I started having similar annoying problems with the arrow keys and page-up/down when using Ubuntu Intrepid connecting to a FreeNX-server :(

Here's a bug-report and a lot of comments :
[https://bugs.launchpad.net/ubuntu/intrepid/+source/xorg-server/+bug/255008](https://bugs.launchpad.net/ubuntu/intrepid/+source/xorg-server/+bug/255008)

Here's more bugs with arrow keys with synergy :
[https://bugs.launchpad.net/ubuntu/+source/synergy/+bug/281546](https://bugs.launchpad.net/ubuntu/+source/synergy/+bug/281546)

---

### Post by hirohitosan on 2008-12-26
> **happyhamster said:**
> Have you installed the guest-additions? (Boot the VM into windows and choose Device--> Install Guest Additions. It should mount VboxGuestAdditions.iso for you and start the installer. Afterwards, you'll probably have to reboot the virtual machine to be able to see the effect.)
No I haven't installed guest-additions.
How to "Boot the VM into windows"? I don't have Win on my computer I just installed through VBox.
I installed Virtual Box OSE and VBoxGtk both from repositories. It's strange, when I start WinXP with "Virtual Box OSE" I cannot capture mouse, when I start with VBoxGtk I can capture the mouse but some keys doesn't work

How can I install guest-addition from Linux?

---

### Post by albinootje on 2008-12-26
> **hirohitosan said:**
>  How can I install guest-addition from Linux?

I think for XP you would do :

- start the XP guest
- wait till it's started
- inside VirtualBox mount the Guest Additions cdrom (Under Devices ?)
- then it probably will autorun
- say yes to the "trust software from" during the install
- restart the VM after installation
- after booting the VM again, set the proper resolution if needed

---

### Post by hirohitosan on 2008-12-26
> **albinootje said:**
> I think for XP you would do :

- start the XP guest
- wait till it's started
- inside VirtualBox mount the Guest Additions cdrom (Under Devices ?)
- then it probably will autorun
- say yes to the "trust software from" during the install
- restart the VM after installation
- after booting the VM again, set the proper resolution if needed

I downloaded Guest Additions and start the installation but after a while it cannot recognize the Graphic Adapter, but I have a IBM T40 laptop on which I used for years WinXP. The two choices that I have is to STOP installation or Continue anyway?

I don't know if it's dangerous to chose "Continue Anyway"

any advices?

---

### Post by albinootje on 2008-12-26
> **hirohitosan said:**
> I downloaded Guest Additions and start the installation but after a while it cannot recognize the Graphic Adapter, but I have a IBM T40 laptop on which I used for years WinXP. The two choices that I have is to STOP installation or Continue anyway?

I don't know if it's dangerous to chose "Continue Anyway"

any advices?

You should continue the installation of Guest Additions in order to have it installed properly.

And VirtualBox will use a virtual video-card, and a virtual network-card, don't worry about that.

---

