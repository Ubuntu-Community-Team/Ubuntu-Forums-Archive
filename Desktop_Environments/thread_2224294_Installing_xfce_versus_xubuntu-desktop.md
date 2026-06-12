---
title: "Installing xfce versus xubuntu-desktop"
date: 2014-05-15
forum: Desktop Environments
---

### Post by jmeeter on 2014-05-15
A few questions. First, what's the difference between installing [FONT=Courier New]xfce[/FONT] vs [FONT=Courier New]xubuntu-desktop[/FONT]? I mean I know Xubuntu is Ubuntu with xfce but what exactly is the difference between installing the aforementioned? Is one better than the other?

Next, does installing multiple desktop environments slow down your computer? I have a netbook with 4GB of RAM.

And last, how do you set the default desktop environment?

Thanks!

---

### Post by papibe on 2014-05-15
Hi jmeeter.

xfce4 is just the desktop environment (and some extras needed to support it).

xubuntu-desktop is the whole enchilada, including the applications that Xubuntu uses. For instance biword, gthumb, etc.

Another way to see it is that xubuntu-desktop includes xfce4, and much more.

Does that help?
Regards.

---

### Post by jmeeter on 2014-05-15
Yes that helps, thank you. Can installing multiple desktop environments (just one or two) slow down your system?

---

### Post by PJs Ronin on 2014-05-15
I have recently done what you are alluding to, that is I overlaid xfce4 on to a standard 14.04/Unity environment using:```
sudo apt-get install xfce4 --no-install-recommends xfce4-goodies
``` and have not noticed any negative performance impact.  In fact, when my frustration with Canonical's convergence rises and unity starts doing things I don't like, I switch to xfce4 for a soothing couple of hours.   Should have done it years ago.

---

### Post by Frogs Hair on 2014-05-15
Running two file manages can take some getting used to because where nautilus handles the desktop in Ubuntu Thunar in XFCE does not. When using XFCE I used Thunar and the XFCE native applications as much as possible . With more than one desktop you will see some application duplication such as file manager , image viewer ,terminal and so on.

---

### Post by papibe on 2014-05-15
> **jmeeter said:**
> Can installing multiple desktop environments (just one or two) slow down your system?
No, but yes.

It is the application-library mismatch that would produce an slow down feeeling. 

Xfce uses GTK+v2, Unity, and current Gnome, mainly use GTK+v3. When you get into your Xfce desktop, the v2 libraries are loaded in memory, so when an application is launch, they load fast. If you launch an Gnome application, like Nautilus, the loading of the v3 libraries would produce the impresssion of slow start. Also as a side effect you would be using more RAM.

Xfce, Unity and Gnome share some libraries (less than it used to be), so it is not the worst case. If you do this with Gnome and KDE the effect would be more evident.

Regards.

---

### Post by amanchesterman on 2014-05-16
As Papibe said above, I noticed a slight slow down when I installed different desktop environments, and confusing extra folders and desktop apps. As an alternative approach I now have a laptop with three different distros installed *in separate partitions*, but all sharing the same partition for my data files. I've had no problems with it, and it allows me to tweak and even change one distro setup without inadvertently messing up the others. The only downside is that if I want to switch from one distro to another I have to reboot, so that's a little slower than just logging out and logging back in.

---

### Post by pretty_whistle on 2014-05-16
You can switch to another desktop environment at the login screen.  I use xfce desktop and once I switched to that from unity I never had to switch again.  And this runs faster than unity imo.

---

