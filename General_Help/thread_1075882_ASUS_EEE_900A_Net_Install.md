---
title: "ASUS EEE 900A Net Install"
date: 2009-02-20
forum: General Help
---

### Post by NintendoTogepi on 2009-02-20
So I decided on the net install of Ubuntu. 

I used unetbootin and have it on a USB, and so now I need to get a wired internet connection right?

What are all of the vital things I should download? (in terms of actual programs I don't plan on installing much more than Firefox, but I know that there's a lot of other small stuff that pretty much needs to be installed)

x? xorg? xvesa?

And then once I get it working, I need to go to that one website and download the array kernel to get the wireless to work, right?

---

### Post by NintendoTogepi on 2009-02-20
bump

---

### Post by kerry_s on 2009-02-20
[http://www.eeebuntu.org/](http://www.eeebuntu.org/)
or
[http://www.ubuntu-eee.com/wiki/index.php5?title=Main_Page](http://www.ubuntu-eee.com/wiki/index.php5?title=Main_Page)
or
[http://wiki.eeeuser.com/ubuntu:eeexubuntu:home](http://wiki.eeeuser.com/ubuntu:eeexubuntu:home)

---

### Post by NintendoTogepi on 2009-02-20
> **kerry_s said:**
> [http://www.eeebuntu.org/](http://www.eeebuntu.org/)
or
[http://www.ubuntu-eee.com/wiki/index.php5?title=Main_Page](http://www.ubuntu-eee.com/wiki/index.php5?title=Main_Page)
or
[http://wiki.eeeuser.com/ubuntu:eeexubuntu:home](http://wiki.eeeuser.com/ubuntu:eeexubuntu:home)

That doesn't really answer my questions. Oh well.

---

### Post by kerry_s on 2009-02-20
> **NintendoTogepi said:**
> That doesn't really answer my questions. Oh well.

all right, i think you should just use the base install version:
[http://www.eeebuntu.org/index.php?page=base](http://www.eeebuntu.org/index.php?page=base)
but if you want to go the full do it yourself route.

> I used unetbootin and have it on a USB, and so now I need to get a wired internet connection right?

yes, if you did the net install you'll be at command line and will need to get what you want. so once you plug it in:
(i'm going to demo xfce4 for a lighter install)

[B]sudo apt-get install xorg gdm xfce4 synaptic firefox
sudo reboot
[/B]

that is enough to get you to the gui and you can use synaptic to install what ever else you want.

> And then once I get it working, I need to go to that one website and download the array kernel to get the wireless to work, right?

yes

---

### Post by kyphi on 2009-02-20
If you follow my little walkthrough, you will not need to download anything else.

Installing ubuntu-eee-8.04.1 on an eeepc

On your computer (not the eeepc):

Download “ubuntu-eee-8.04.1.iso” (606.7 MB) from [http://www.ubuntu-eee.com/](http://www.ubuntu-eee.com/)
as well as “unetbootin-eeeubuntu-linux-276” (3.4 MB).

Then get three essential files required for making unetbootin fully functional:

sudo apt-get install mtools syslinux p7zip-full

Insert your empty USB device (empty is important).

In a terminal type:  “mount | grep /media/disk” to find the name of the mounted drive (mine said “sdc1”).

Make “unetbootin-eeeubuntu-linux-276” executable, either via the command line interpreter (chmod +x unetbootin-eeeubuntu-linux-276) or by a right click on the file, going to Properties, Permissions and placing a tick into the “make executable” box.

Now double click on unetbootin-eeeubuntu-linux-276 and in the dropdown screen insert the value for your USB device and select Disc Image ISO and type in “ubuntu-eee-8.04.1.iso”.  Click OK.

The installation files will now be written to your USB device.

When finished, unmount the USB device and remove it.

On the eeepc:

Insert the USB device (I used the second slot on the right after reading that some operators had experienced difficulties with the left side slot).  The first slot was in use for a mini-mouse (no relation to mickey).

Boot your eeepc repeatedly pressing “Esc” until the option appears as to which device to boot from.  Select your USB device and after pressing OK, installation will commence.  

There will be a long pause after about 7 files have been unzipped – be patient, installation will continue.

---

### Post by NintendoTogepi on 2009-02-22
> **kerry_s said:**
> all right, i think you should just use the base install version:
[http://www.eeebuntu.org/index.php?page=base](http://www.eeebuntu.org/index.php?page=base)
but if you want to go the full do it yourself route.



yes, if you did the net install you'll be at command line and will need to get what you want. so once you plug it in:
(i'm going to demo xfce4 for a lighter install)

[B]sudo apt-get install xorg gdm xfce4 synaptic firefox
sudo reboot
[/B]

that is enough to get you to the gui and you can use synaptic to install what ever else you want.



yes


Ok I will try out Eeebuntu first, if I do not like it I will do as you said ;)

---

### Post by NintendoTogepi on 2009-02-22
Thanks everyone, eeebuntu base install is gret :D

---

