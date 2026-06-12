---
title: "Ubuntu on (old)work stations"
date: 2006-05-03
forum: Desktop Environments
---

### Post by Quentusrex on 2006-05-03
I am trying to setup 8 work stations for a child center. I would like to put ubuntu on the machines but I seem to have a problem after the install. Here are the hardware specs:

Pentium 3 667
256 MB Ram
20 Gig HD
16MB Graphics Cards

This is the same for all the machines.

After installing Ubuntu I am left with a black screen with a solid horizontal cursor on the upper left of the screen. It seems that it will not display the GUI. I have only tried to install on one of the machines so I don't know if it was a bad install, or a particular bad piece of hardware. 

Thanks for any and all help/advice.

---

### Post by aysiu on 2006-05-04
A horizontal... cursor?
So is it a black screen with white text that looks like a login?
Or do you mean a mouse cursor? How is the cursor... horizontal exactly?

Did you encounter any errors during the installation, or did the rest of it seem to go okay?

---

### Post by Quentusrex on 2006-05-04
The underline like blicky CLI based cursor. Like you find in some old text based systems, rather then the vertical text cursor I see here in the forum reply box. I don't remember seeing any errors at all.

---

### Post by deadgobby on 2006-05-04
[http://ubuntuforums.org/showthread.php?t=42873](http://ubuntuforums.org/showthread.php?t=42873)
[http://linus.yhspatriot.net/cs/docs/ubuntu_howto/UbuntuLite](http://linus.yhspatriot.net/cs/docs/ubuntu_howto/UbuntuLite)
I hope this of good aid to you
Gobby

---

### Post by aysiu on 2006-05-04
Just a black screen with a cursor, or do you see a login? If it's the latter, you may have done a *server* install. If it's the former, something went wrong (yes, it's a bad install).

If you see a login, log in as the account you created during installation, and then type ```
sudo apt-get update
sudo apt-get install ubuntu-deskop
sudo /etc/init.d/gdm start
``` The password is your user password.

---

### Post by Quentusrex on 2006-05-04
I reinstalled and followed this guide:
[http://www.ubuntuforums.org/showthread.php?t=75971](http://www.ubuntuforums.org/showthread.php?t=75971)

The graphics card I have is:
Nvidia TNT M64 16MB PCI Video Card

Now I am getting a blue screen error that X won't work. It says:

(WW) VESA: No matching device for instance (Bus ID PCI:1:&:0) found
(EE)VESA(0): Cannot read V_BIOS
(EE) Screen(s) found, but none have a usable configuration

---

### Post by Michael Steinberg on 2006-05-04
Why are you trying to use xfce? There's nothing WRONG with xfce, it's a fine and fast desktop environment, but if you're just starting out with Linux you're asking for trouble the more tweaking you do on the install.

One point I'd make is that a P3 even at 667 mHz isn't incredibly slow for Ubuntu. I've loaded Breezy on 450 mHz P3s and it runs fine with Gnome. Why not try a straight-from-the-beginning install without any special options--just let the installer make choices for you? You'll end up with fewer pitfalls. Learn to use the system a bit; load a 686 kernel instead of the default 386. Get comfortable. If you find the Gnome desktop too slow on your machines you can load xfce from the repositories or try Xubuntu. In a month Dapper will be out, and it's reported to be much faster anyway.

Good luck!

---

### Post by Quentusrex on 2006-05-04
Steinberg, I'm not going to take that personally. Did it say that I just started out with linux? Did it even say that I was just starting out with Ubuntu?

On with the problem at hand.

I had problems with the first straight install for ubuntu on one of these machines. I'm trying different things, and I'll try the livecd's to see if there is a change.

---

### Post by Quentusrex on 2006-05-04
I just took out the pci graphics card and used the onboard graphics and Ubuntu installed and seems to work fine. For some reason Ubuntu did not seem to work well out of the box with that particular card.

---

### Post by missmoondog on 2006-05-06
which nvidia drivers are you using? legacy or glx?

i had a heck of a time getting the old nvidia drivers working correctly on one machine of mine.

have since found that using automatix works pretty good and is very easy.
[http://ubuntuforums.org/forumdisplay.php?f=77](http://ubuntuforums.org/forumdisplay.php?f=77)

---

