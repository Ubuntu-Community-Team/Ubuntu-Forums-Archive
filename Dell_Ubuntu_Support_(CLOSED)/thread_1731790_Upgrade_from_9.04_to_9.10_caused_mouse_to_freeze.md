---
title: "Upgrade from 9.04 to 9.10 caused mouse to freeze"
date: 2011-04-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RSASKA on 2011-04-17
As I type on another computer, my Ubuntu 9.04 is being reinstalled on Dell 1545 Inspiron after I attempted to upgrade from 9.04 to 9.10

I went to application manager, hit the upgrade button to upgrade to 9.10

1. When machine rebooted, it bought me to terminal. I typed in startx, which bought me to GUI
2. Mouse pointer was frozen in GUI
3. Rebooted machine
4. Booted into GUI, mouse was frozen

I had no choice but to re-install original 9.04

Please tell me how to upgrade to 9.10 without error

---

### Post by mrcollinz on 2011-04-17
That's an interesting issue, you upgraded threw the update manager?. Seems to be some kind of driver related issue are you using a wireless mouse that requires a usb drive to be plugged in or just a standard mouse?.

If I could make a suggestion, why not upgrade to maverick?, as far as I know support for 9.10 is no longer available so there won't be any further updates. If this isn't plausible for you try doing the following.

Download the alternate cd version

[http://releases.ubuntu.com/karmic/ubuntu-9.10-alternate-i386.iso](http://releases.ubuntu.com/karmic/ubuntu-9.10-alternate-i386.iso) (intel based)

[http://releases.ubuntu.com/karmic/ubuntu-9.10-alternate-amd64.iso](http://releases.ubuntu.com/karmic/ubuntu-9.10-alternate-amd64.iso) (amd based)

Mount it preferably to a cd and upgrade that way, or you can choose to upgrade manually from inside the environment by running the following commands in the terminal.

  	 	 	 	 	 	  sudo mkdir -p /media/cdrom (press enter)


   	 	 	 	 	 	  sudo mount -o loop ~/Desktop/ubuntu-9.10-alternate-i386.iso /media/cdrom (be sure to change this to whatever version you are using and change the file location from "Desktop" to wherever you saved the file.


From there you should be prompted to upgrade,

---

### Post by RSASKA on 2011-04-17
Will try this out

---

### Post by mrcollinz on 2011-04-17
Good luck!

---

### Post by mörgæs on 2011-04-18
I would strongly recommend a clean install of 10.04.2 or 10.10 rather than upgrades.

The ISO's are for 32 and 64 bit. Whether the processor is Intel or AMD has no significance.

Here is an overview of the support plan:
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

---

### Post by RSASKA on 2011-04-22
I will try these out, thank you for your responses.

---

