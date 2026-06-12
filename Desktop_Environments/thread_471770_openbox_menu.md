---
title: "openbox menu"
date: 2007-06-12
forum: Desktop Environments
---

### Post by whytheam on 2007-06-12
I just installed openbox and when I right click and I go to applications it gives me Xterm, Mozilla, Gaim, and Quark. How do I add all my other applications to the menu?

---

### Post by ingvildr on 2007-06-12
There is a GUI tool called obmenu, here is a nice guide to setting it up
[http://doc.gwos.org/index.php/Openbox_GnomeStraight#Use_obmenu]("http://doc.gwos.org/index.php/Openbox_GnomeStraight#Use_obmenu")

---

### Post by whytheam on 2007-06-12
I have never been able to install .tar.ANYTHING in to my computer. When I put in the code this is what I get:

obmenu-1.0/icons/mnu48.png
obmenu-1.0/icons/mnu16.png
obmenu-1.0/pipes/obm-xdg
obmenu-1.0/pipes/obm-moz
obmenu-1.0/pipes/obm-nav
obmenu-1.0/pipes/obm-dir
obmenu-1.0/COPYING
obmenu-1.0/obxml.py
obmenu-1.0/obmenu
obmenu-1.0/pipes-help
obmenu-1.0/minisetup.py
obmenu-1.0/obmenu.glade
obmenu-1.0/README
obmenu-1.0/.obmenu_temp
obmenu-1.0/obxml-help
obmenu-1.0/setup.py
tar: cd: Not found in archive
tar: sudo: Not found in archive
tar: python: Not found in archive
tar: setup.py: Not found in archive
tar: install: Not found in archive
tar: Error exit delayed from previous errors

I tried changing cd obmenu-1.0 to cd setup.py because that is what the official website says to use. What am I doing wrong?

---

### Post by moore.bryan on 2007-06-12
[I]let me see if i understand.  you download obmenu ([http://prdownloads.sourceforge.net/obmenu/obmenu-1.0.tar.gz?download](http://prdownloads.sourceforge.net/obmenu/obmenu-1.0.tar.gz?download)) and when you try to untar it you get the crap above?
```
tar -xvzf  obmenu-1.0.tar.gz
```
[/I]

---

### Post by urukrama on 2007-06-12
It shouldn't be that difficult. I have heard there are problems with obmenu (or was it obconf?) in Feisty, but can't confirm that as I use Dapper.

What you should normally do to get obmenu installed is this:

First make sure you have the necessary dependencies installed 

> Dependecies
Python 2.3 or better, pygtk and pyglade.

Search through Synaptic to find them, and install them if you do'nt have them. You might need the development versions of these (pygtk-dev etc) as well.

**Download the archive** from the [website]("http://prdownloads.sourceforge.net/obmenu/obmenu-1.0.tar.gz?download") to your home folder (/home/USERNAME/)

**Extract the archive.** You can do this graphically, by right clicking in Thunar or Nautilus and select "Extract here" or by using an archive manager. Alternatively you can use the command line (terminal) by typing```
tar -xvvzf obmenu-1.0.tar.gz
```

**Install obmenu**: Open a terminal (or just use the one you have already open) and type
```
cd obmenu*
```

to move into the obmenu-1.0 folder you have automatically created by extracting the tar archive. Alternatively, if you use Thunar, you could just right click the folder and select "Open Terminal Here", which would do the same thing as the cd ("change directory") command.

To install obmenu, then type the following command:
```
sudo python setup.py install
```
You'll have to give your password, and then all should go fine. If you were unable to install the package and some errors come up, post them here, and perhaps someone can offer some help.

Good luck!

Installing applications in Ubuntu (or Linux) is not *that* hard as it seems at first. First look in the repositories (Synaptic); if it is not there download the file from the projects webpage, un-tar it (as explained above) and read the installations instructions that come with it, or that are given on the project's website (most have either one or both). Also have a look at [How to instally anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing.html")

Once you get used to it, it is fairly straightforward. But the first packages you want to install can be very tough -- I know, because I've been there. :-)

btw: tar is not an installer or executable. It is an archive format, much like .zip in Windows. Unpack it, and you'll find the installer in there.

---

### Post by whytheam on 2007-06-12
> **urukrama said:**
> It shouldn't be that difficult. I have heard there are problems with obmenu (or was it obconf?) in Feisty, but can't confirm that as I use Dapper.

What you should normally do to get obmenu installed is this:

First make sure you have the necessary dependencies installed 



Search through Synaptic to find them, and install them if you do'nt have them. You might need the development versions of these (pygtk-dev etc) as well.

**Download the archive** from the [website]("http://prdownloads.sourceforge.net/obmenu/obmenu-1.0.tar.gz?download") to your home folder (/home/USERNAME/)

**Extract the archive.** You can do this graphically, by right clicking in Thunar or Nautilus and select "Extract here" or by using an archive manager. Alternatively you can use the command line (terminal) by typing```
tar -xvvzf obmenu-1.0.tar.gz
```

**Install obmenu**: Open a terminal (or just use the one you have already open) and type
```
cd obmenu*
```

to move into the obmenu-1.0 folder you have automatically created by extracting the tar archive. Alternatively, if you use Thunar, you could just right click the folder and select "Open Terminal Here", which would do the same thing as the cd ("change directory") command.

To install obmenu, then type the following command:
```
sudo python setup.py install
```
You'll have to give your password, and then all should go fine. If you were unable to install the package and some errors come up, post them here, and perhaps someone can offer some help.

Good luck!

I do that and then in the terminal when I type obmenu it gives me this:
/home/whytheam/.config/openbox/menu.xml" not found

---

### Post by llamakc on 2007-06-12
So copy the default menu.xml from /etc/xdg/openbox to ~/.config/openbox/

---

### Post by whytheam on 2007-06-12
It  works, thanks.

---

