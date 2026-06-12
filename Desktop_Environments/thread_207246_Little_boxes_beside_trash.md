---
title: "Little boxes beside trash"
date: 2006-07-01
forum: Desktop Environments
---

### Post by Miki01 on 2006-07-01
Hello, I'm Miki and I'm new to Ubuntu. I just built my first PC and installed Ubuntu last night.

I accidentally removed those little boxes beside the trash bin, the on with the last 3 being gray and the 1st one before the three gray ones being a brown color. How do I go about bringing them back on to the taskbar/panel? Your help is greatly appreciated.

---

### Post by aysiu on 2006-07-01
Right-click on the panel.
Add to Panel.
Workspace Switcher.

---

### Post by Miki01 on 2006-07-01
Ah, many thanks. 

I also have another question, instead of making a new thread, I thought I'd post it here.

My question is about installing Adobe Flash Player on Ubuntu.

The instructions were:


1. Click the "Download Now" button. A dialog box will appear asking you where to save the Installer.

2. Save the Installer to your desktop and wait for the file to download completely.

3. Unpackage the file. A directory called install_flash_player_7_linux will be created.

4. Navigate to this directory and from the command line type ./flashplayer-installer to run the installer (Note: this can only be run from the command line). The installer will instruct you to shut down your browser(s).

5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

In step (4), it tells me to navicate to that directory. What does that mean? Am I supposed to goto the Desktop and open the folder? Or am I supposed to type something in the command terminal? Sorry, I am new to using Ubuntu.

Can someone guide me step-by step?

---

### Post by aysiu on 2006-07-01
Yeah.

1. Delete whatever you downloaded.
2. [Enable extra repositories](http://www.psychocats.net/ubuntu/sources)
3. Paste this command in the terminal: ```
sudo aptitude update && sudo aptitude install acroread acroread-plugins mozilla-acroread
``` Now it's installed, and you didn't even have to find whatever directory you wanted to install it in.

---

### Post by Miki01 on 2006-07-01
Okay thanks, but when I type in the first command in the terminal from the "Enabling Extra Repositories" site you linked to, I keep getting this error. (see attachment)

---

### Post by aysiu on 2006-07-01
Those are two separate commands: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
``` is one command. After you paste that command in, hit **Enter** before pasting this command in: ```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Miki01 on 2006-07-01
okay. I've got it installed, so I closed all my Firefox windows and returned to the site where the Adobe Flash plugin appeared. It seems like it wasn't installed. When I restarted firefox though, it was doing something like checking extentions or something... When I go back to the website I was at, the flash plugin doesn't show proof that it was installed... see the screencap

---

### Post by aysiu on 2006-07-01
Oops! Sorry. I saw the word *Adobe* and assumed you were looking for Adobe Acrobat Reader.

Now I realize you were looking for the Flash player! Sorry. For Flash, do this: ```
sudo aptitude update
sudo aptitude install flashplugin-nonfree
```

---

### Post by Miki01 on 2006-07-01
ah, that's okay, everyone makes mistakes now and then. I will now do just that

---

### Post by Miki01 on 2006-07-01
I did just that and ended up with this, something about 

"Could not find package whose name or description name matched "
flashplugin-nonfree"

---

### Post by aysiu on 2006-07-01
That's weird. With extra repositories, it should be in there.
Can you try this, then? ```
wget -c http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.63.3ubuntu3_i386.deb
sudo dpkg -i flashplugin-nonfree_7.0.63.3ubuntu3_i386.deb
``` By the way, you can highlight terminal text and copy and paste it into posts--it's probably faster than taking screenshots and uploading them.

---

### Post by Miki01 on 2006-07-01
I get an error saying:

> dpkg: error processing flashplugin-nonfree_7.0.63.3ubuntu3_i386.deb (--install): package architecture (i386) does not match system (amd64)


I guess I need one for my AMD system... hmm

---

### Post by aysiu on 2006-07-01
Oh! Yeah... I didn't realize you had an AMD64. That makes things a little more complicated, unfortunately, for a lot of things.

From [the Help Docs](https://help.ubuntu.com/community/RestrictedFormats#head-f375cba46014e861cd5ec7643bd7c4ef05acff2b) >     *

      Flash for AMD64 and PPC
          o

            At present, there is no non-free flash implementation available for 64-bit processors (or Mac) because the manufacturer does not support them. However, there are two free implementations in the works. One is gnash and the other is swfdec. [WWW] Gnash, whilst still under development, aims to be a proper free, open source replacement for all the platforms. There is a repository hosting AMD64 Gnash packages at [WWW] [http://ubuntu.moshen.de/](http://ubuntu.moshen.de/)

            If you are determined, install a i386 Ubuntu in a DebootstrapChroot and launch your browser with flash plugin from there.

---

### Post by Miki01 on 2006-07-01
Ah, alright, hmm... Well... I guess I could surf around for a while and look for answers upon that myself. Thanks for all the help!

What about that Playing DVDs, MP3s, and any other mpeg-type files. What would I need to do to get around that?

---

### Post by aysiu on 2006-07-01
This page may help you:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

