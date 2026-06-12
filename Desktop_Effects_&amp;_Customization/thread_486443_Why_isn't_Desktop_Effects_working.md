---
title: "Why isn't Desktop Effects working?"
date: 2007-06-28
forum: Desktop Effects &amp; Customization
---

### Post by Arenlor on 2007-06-28
I know I've got work to do, but I'm not sure A: what to install B: what to uninstall C: if I should do anything with modules or not, I've already been through pain getting my wireless to work but now it does (bcm43xx model of course).

Here's the error I get when I try to start desktop effects through System > Preferences > Desktop Effects; Enable Desktop Effects:
```
Desktop effects could not be be enabled
```
Which as you can tell is not helpful at all, I know there are ATI issues, so here's my card in the xorg.conf
```
Section "Device"
	Identifier	"ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
EndSection
```
Thanks ahead of time for anyone who helps me.

---

### Post by Mr Greencastle on 2007-06-28
I have the same card as you do, and I had to install Xgl,

Instead of desktop-effects, try Beryl. Or, if your willing, try Compiz Fusion (don't have a link though).

Heres the tutorial I used (follow it step by step and it should work)


[http://ubuntuforums.org/showthread.php?t=399643](http://ubuntuforums.org/showthread.php?t=399643)

Hope this helps!

Mr Green

---

### Post by Arenlor on 2007-06-28
I followed it exactly but I think I'm missing something, like literal missing something, when I use beryl-manager it fills my terminal with the same line over and over, ctrl+c does nothing to stop it, only quitting beryl manager in my tray thing.
```
** (beryl-manager:8709): CRITICAL **: can't execute beryl-xgl: Success
```
I'm half considering screenshotting that for thisisbroken. So what do you think I'm missing or maybe that I have that I shouldn't?

---

### Post by spoilerhead on 2007-06-28
theres no beryl-xgl in the official ubuntu package
get the beryl svn builds from trevino or get compiz fusion

see [http://forums.opencompositing.org/](http://forums.opencompositing.org/) for links to packages of CF and installation help

---

### Post by Arenlor on 2007-06-28
Tried the svn thing and got this error
```
Failed to fetch http://download.tuxfamily.org/3v1deb/dists/feisty/Release  Unable to find expected entry  beryl-svn/binary-i386/Packages in Meta-index file (malformed Release file?)
```

---

### Post by Mr Greencastle on 2007-06-28
You will need to add the security key first

Code:
sudo wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -

Then type in:
sudo gedit /etc/apt/sources.list

It will open a file....

Add this to the very bottom:
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

Then save and exit.

You will need to update so:
sudo apt-get update

To install beryl:
sudo apt-get install beryl beryl-manager beryl-core beryl-plugins beryl-settings

After it is done type:
beryl-manager

You may need to change the window manager, do this by right-clicking the beryl icon and selecting Beryl from the 'Select Window Manager' menu.

Then you're all set! Oh and don't forget to add this to your startup, 
to do this click system > preferences > sessions

Click on 'New' and type in 'Beryl' (without quotes) for the name and for the command 'beryl-manager' (again without quotes)

Good Luck!


Mr Green

---

### Post by Arenlor on 2007-06-29
Thanks, that worked.

---

### Post by Mr Greencastle on 2007-06-29
You're very welcome!

---

