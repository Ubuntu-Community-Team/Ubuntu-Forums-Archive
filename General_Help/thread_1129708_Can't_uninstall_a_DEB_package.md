---
title: "Can't uninstall a DEB package"
date: 2009-04-19
forum: General Help
---

### Post by Flexico on 2009-04-19
I installed a .deb package and it messed up my sound driver somehow, but now I can't uninstall it because it doesn't show up in the installed applications list! Help!

---

### Post by balaknair on 2009-04-19
Did you try Synaptic(System menu> Administration> Synaptic Package Manager)?

Search for the package name there. In most cases, it should show up there.
Or use the command line
***sudo apt-get purge package_name***

---

### Post by Flexico on 2009-04-19
**Thanks!** I found that, but it says "this package is not the program, it just downloads it."

I uninstalled the installer package, but some of the files from the program are still there, and my sound still doesn't work. :( I'm going to try robooting to see if that helps.

---

### Post by balaknair on 2009-04-19
If you could post a link to the deb file, I can try and find the packages the installer links to. You can then use Synaptic to uninstall those packages.

---

### Post by Flexico on 2009-04-19
Here it is:

[http://www.getdeb.net/download/3124/0](http://www.getdeb.net/download/3124/0)

---

### Post by balaknair on 2009-04-19
try searching for secondlife in Synaptic

---

### Post by Flexico on 2009-04-19
I did, and nothing. The only thing I see left is the icon in the applications menu (now it's just a gray box) and my sound still doesn't work!

---

### Post by balaknair on 2009-04-19
If you used Synaptic to uninstall the application it would probably have been uninstalled now. If you're in doubt, in Synaptic, use the 'Fix Broken Packages' option(Edit> Fix broken Packages). This will usually take care of any residual cruft left behind by bad installs.

I remember installing SecondLife with a deb from getdeb.net(64 bit version). But I uninstalled it via Synaptic, and I don't recall having any issues with the uninstallation process.

As for the audio problem, that may no longer have anything to do with SecondLife being un/installed. If you post some info about that here, we may be able to fix the audio issue.
For example post the output of the following commands(copy paste the following commands one by one into a terminal- Applications> Accessories> Terminal)
[B][I]lspci -v
aplay -l[/I][/B]

Rather than messing up the drivers, Secondlife might have just altered the audio settings a bit. Right click on the volume icon in the upper panel, and ensure that all channels are unmuted. In System menu> Preferences> Sound make sure that all options are set to 'Autodetect' and test them to see if changing those settings gets your audio to work.

---

### Post by oldos2er on 2009-04-19
Try running
```
sudo dpkg -r secondlife-install_1.20.15-0~getdeb1_i386.deb 
```
in a terminal.

---

### Post by Flexico on 2009-04-19
Oh I feel stupid, it was just the PCM volume turned all the way down. XD Thanks for the info on the synaptic package manager, that was helpful. :)

Also, last night I got the .tar.bz2 version of SecondLife from the official site running great.

---

### Post by balaknair on 2009-04-19
Glad to hear that.

All the best.

---

### Post by Flexico on 2009-04-19
While we're talking about second life, where are screenshots saved? I took a couple and selected "save to disk", but it won't let me specify where to save the images and I did a search of the hard drive and I can't find them. =\

---

### Post by balaknair on 2009-04-19
I used Second Life for a pretty short while(just trying it out), and uninstalled it around 3-4 months back, so my memory about most of it is a bit hazy. So I'm not sure about this.

Try looking in the home folder, which is where logically it ought to be saved(and in Ubuntu normally the only area you have write perssions to). It might be in a hidden folder for Secondlife config files- Open your home folder and hit Ctrl+H to view hidden files, look for the secondlife folder(it ought to be named something like .secondlife), and look inside this folder/subfolders.

---

### Post by Flexico on 2009-04-20
I found several system folders for SL, but no screenshot image files. *shrugs* Maybe I should look it up on their website.

---

### Post by balaknair on 2009-04-20
:D
Wish you luck with that. Sorry I wasn't able to help you more but second life just wasn't my scene(I have enough trouble managing my first life) so my knowledge there is limited.

Have fun

---

### Post by Flexico on 2009-04-20
Ha ha ha, I don't have any intention to make a "second life", I just use it to design 3D versions of my cartoon characters. =P Gives a fun little world for them to run around in.

---

