---
title: "Xserver fix broke my Xserver"
date: 2006-08-25
forum: Desktop Environments
---

### Post by Vinze on 2006-08-25
Hey, I read about the Xserver update that would crash your X before I updated, so I took some measures. I installed an Xserver package created by a member. It worked, but of course it wasn't official. Then I saw [this](http://www.ubuntu.com/FixForUpgradeIssue) so I followed it's instructions, though instead of downloading it on the command line I did it from packages.ubuntu.com because the internet dropped too. As the member package was a higher version I first had to uninstall that and a load of other package. Then I installed the official xserver-xorg-core and now I have no graphical interface again. What to do?

---

### Post by _profox on 2006-08-25
It could help if you know what exactly you uninstalled by uninstalling the "member package"

Check the file **/var/log/dpkg.log**
like this:

**cat /var/log/dpkg.log|grep "2006-08-25" > ~/dpkglog**

This command will put all changes in the packages on 2006-08-25 in the file "dpkglog" in your home folder.

You can put this on line if you do the following:

```
cd ~
sudo apt-get install perl libwww-mechanize-perl libgetopt-mixed-perl
wget http://www.novell.com/coolsolutions/tools/downloads/paste2pastebin.pl
./pastebin2pastebin.pl ~/dpkglog
rm ~/dpkglog
```

This will download the needed perl libraries and execute a perl script to upload a piece of the dpkg log. You will get a URL. Paste that URL here.

---

### Post by Vinze on 2006-08-25
> **_profox said:**
> It could help if you know what exactly you uninstalled by uninstalling the "member package"

Check the file **/var/log/dpkg.log**
like this:

**cat /var/log/dpkg.log|grep "2006-08-25" > ~/dpkglog**

This command will put all changes in the packages on 2006-08-25 in the file "dpkglog" in your home folder.

You can put this on line if you do the following:

```
cd ~
sudo apt-get install perl libwww-mechanize-perl libgetopt-mixed-perl
wget http://www.novell.com/coolsolutions/tools/downloads/paste2pastebin.pl
./pastebin2pastebin.pl ~/dpkglog
rm ~/dpkglog
```

This will download the needed perl libraries and execute a perl script to upload a piece of the dpkg log. You will get a URL. Paste that URL here.

I'll do this and just post it on pastebin.com as I don't have internet access too, only when I'm using the LiveCD.

---

### Post by _profox on 2006-08-25
Oh? okay..

Then you don't have to do those 5 lines to install the perl libraries and the pastebin script.

**cat /var/log/dpkg.log|grep "2006-08-25" > ~/dpkglog**
That will be enough. dpkglog will be located in your homefolder

Afterwards, you can remove it -- after the pastebin:
**rm ~/dpkglog**

---

### Post by Vinze on 2006-08-25
OK, I added it in the attachment, I really hope it helps.

---

### Post by Vinze on 2006-08-26
OK, I downloaded all (64!) packages that I removed manually via packages.ubuntu.com, I'm going to install them now (which is going to be a bit fast: sudo dpkg -i /media/usbdisk/packages/xserver/*.deb, few...)

---

