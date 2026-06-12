---
title: "Openbox installation and setup on ubuntu 15.04"
date: 2015-05-21
forum: Desktop Environments
---

### Post by trezo on 2015-05-21
Please i need step by step guidelines on how to setup openbox on ubuntu 15.04.I have seen trying since two days ago without any success.I could actually install it with apt-get but setting up menu(debian)has been hell.I'm new to linux please help.This is my first distro.

---

### Post by vasa1 on 2015-05-21
If you're new to Linux and this is your first distro, I'd suggest there's no need to install Openbox. Just use the default system.

I've been using Openbox myself for a couple of years and tried the debian menu for a while but I found it was too complicated for me. So now all I use is rc.xml and menu.xml.

In any case, you need to describe your exact problem in more detail.

---

### Post by oldos2er on 2015-05-21
Moved to Desktop Environments.

---

### Post by trezo on 2015-05-21
> **vasa1 said:**
> If you're new to Linux and this is your first distro, I'd suggest there's no need to install Openbox. Just use the default system.

I've been using Openbox myself for a couple of years and tried the debian menu for a while but I found it was too complicated for me. So now all I use is rc.xml and menu.xml.

In any case, you need to describe your exact problem in more detail.


[http://www.maketecheasier.com/configure-andcustomize-openbox/](http://www.maketecheasier.com/configure-andcustomize-openbox/)

I was following the set up procedures from the above link.I successfully installed openbox with "sudo apt-get install openbox obconf  ". Then when i tried to run the second line in the below code, it tells me no such file or directory.
sudo apt-get install menu
cp /var/lib/openbox/debian-menu.xml ~/.config/openbox/debian-menu.xml
cp /etc/xdg/openbox/menu.xml ~/.config/openbox/menu.xml
cp /etc/xdg/openbox/rc.xml ~/.config/openbox/rc.xml
openbox --reconfigure

I thought i couldn't do without debian menu,if i could then, how can i setup rc.xml and menu.xml? I wanted the openbox because i hear it is fast.This ubuntu 15.04 seems to be slow.Is Lubuntu faster?

---

### Post by v3.xx on 2015-05-21
If I understand right, you have Unity installed and find it slow.

I would suggest trying yet another window manager just because its super easy to install and lightweight.
Not as lightweight as Lubuntu, but better than Unity.  Its called 'Flashback' and used Metacity as a WM.
You may find it light enough. To install:
```
sudo apt-get install gnome-panel
```
Reboot and at the login screen, click on the icon and choose Flashback (metacity).  See what you think of it.

And to answer your question, yes, Lubuntu is fast.

---

### Post by trezo on 2015-05-22
Ok thanks;It makes sense.Do you know how i can make my screen dark color like in openbox?If i can also set up conky i should be good.Thanks

---

### Post by buzzingrobot on 2015-05-22
Read that MakeTechEasier piece carefully.  It says it is for both Debian and Ubuntu, and they are not identical. The files you were trying to copy are located in a different directory in Ubuntu, as the article explains.

Openbox displays a dark gray background by default.  If you want to use another background or wallpaper, you need to use an external program to do that. A program called "nitrogen" is popular; there are others. It is typically made an entry in the Openbox autostart script.

If you are using Unity and you think your machine is unusually slow, you should start another thread, and include informaton about your hardware.

The Lubuntu version of Ubuntu runs a desktop environment called LXDE, which is a combination of Openbox (as its window manager) and a coordinated collection of other programs. (in its default configuration, it is quite a bit different from a default Openbox setup.)  Lubuntu has a reputation for requiring less memory. Applications, of course, take more or less the same amount of memory no matter where they run.

---

### Post by Melodie on 2015-07-27
Hi,

To get a root desktop (no background no layer) and you want it to be black, add this to your file ~/.config/openbox/autostart:
```
hsetroot -solid '#000000'
```

You need to have one of these programs installed for it to work: hsetroot, esetroot, or xsetroot. I think only hsetroot can be found in the repos. This is from the file /usr/lib/<i686|or|x86_64>/openbox-autostart:
```

# Set a background color
BG=""
if which hsetroot >/dev/null 2>/dev/null; then
  BG=hsetroot
elif which esetroot >/dev/null 2>/dev/null; then
  BG=esetroot
elif which xsetroot >/dev/null 2>/dev/null; then
  BG=xsetroot
fi

```

If you want a full fledged ready to go Openbox in Ubuntu, you can try Bento Openbox, from here: [http://linuxvillage.org/](http://linuxvillage.org/)

There is a 15.04 ready (rc2, well shouldn't have many issues) for the next Vivid, stay tuned. There might be a version even smaller and lighter next, which might become the rule for versions in between the LTS. Here is [the description]("http://linuxvillage.org/en/2015/05/bento-openbox-vivid-rc1-and-rc2/").

I have posted [here]("http://ubuntuforums.org/showthread.php?t=2286820") about it, if you have questions, please ask.

---

