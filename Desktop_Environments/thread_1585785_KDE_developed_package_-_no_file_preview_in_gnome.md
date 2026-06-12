---
title: "KDE developed package - no file preview in gnome"
date: 2010-10-01
forum: Desktop Environments
---

### Post by Sciezyna on 2010-10-01
Recently I installed , on gnome, an application developed under KDE with ImageMagick (Magick++). This is one of a kind application (crosstitch) so I have no choice.

It appears that installed on Gnome the app. have some problems. When opening graphic files (eg. .jpg) the app.does not display icons and/or  previews (in the file manager) even though the design is there. All I get are some kind of generic icon and generic preview instead.

I have ither apps (Gwenview) installed an all is working

Would anyone be familiar with porting KDE apps with ImageMagick into Gnome? Where and what to look for?

I compiled / installed the app. There were numerous libraries to be installed but it went well. Is the a general procedure to be looked at?

I am in contact with the developer, however, it would be nice to be able to understand and maybe learn something for future or even help a bit.

Thanks

---

### Post by SeijiSensei on 2010-10-01
1)  Did you install kubuntu-desktop or are you trying just to install the applications you think you need?  If the latter, you may not have all the libraries required to run a KDE application.  Install kubuntu-desktop and try again.

2)  Of course, you could just run [Kubuntu]("http://www.kubuntu.org/").

3)  If you're committed to GNOME, you could run VirtualBox and set up a virtual machine running Kubuntu in it.

---

### Post by Sciezyna on 2010-10-04
Thanks for reply,

> **SeijiSensei said:**
> 1) Did you install kubuntu-desktop or are you trying just to install the applications **you think you need**? If the latter, you may not have all the libraries required to run a KDE application. Install kubuntu-desktop and try again.

The number of post next to my ID should suggest that I am very new to Linux..., however, I do like your sense of humour when you suggest that I may not be sure what I need - I do know what I need KXStitch app. :)
> 
2) Of course, you could just run Kubuntu.

3) If you're committed to GNOME, you could run VirtualBox and set up a virtual machine running Kubuntu in it.

These suggestion got me, of course, in trouble. I installed the kubuntu-desktop - yes silly of me. The install behaved worse than, one other OS. It took over my Gnome desktop. It installed maybe 30-50 applications (I thought - and I still think I did not need) and they appear now both in my Gnome session and KDE.

The problem of not displaying preview in File dialogue in KXStitch is still there - so now I have old problem and the new one Gnome polluted by KDE.

'sudo apt-get remove kubuntu-desktop' did a lot of questioning me and fiddling with files but nothing apparently changed - all the not needed apps are appearing in menus (or maybe in did I not know what I need?).

So my q. now is: is the any, reasonably easy way to undo the kde influence on Gnome or does it mean reinstalling the OS?

Is there a log. file I can examine so I know what was installed and when and get rid of the pollutants manually?

Am I asking for too much?

Thanks

---

### Post by glitch323 on 2010-10-05
I don't know about uninstalling kubuntu-desktop, but I do know there is a way to hide KDE apps from Gnome within KDE.  Unfortunately, I don't think that's gonna help you much unless you keep KDE for that one application.

Oh, maybe if you need only kde for one application, you could install the kde-base or kde-minimal package so that you don't have a million other applications.  Just a though, hope it helps.

---

### Post by Sciezyna on 2010-10-05
Thanks  glitch323,

It is just one of those little annoyances with computers and it seems I have to accept it. I can get rid of some of the apps that I don't need (or hide them) but I will just let the KDE exist there...

What did happen though and that is not pleasant is that I lost Gnome login screen and somehow the KDE login screen will not let me change the kb and desktop language before login...

Oh well...

Thank you again

JS

---

### Post by glitch323 on 2010-10-06
I found this really old thread, but it may help: [http://ubuntuforums.org/showthread.php?t=95275](http://ubuntuforums.org/showthread.php?t=95275)

The command that I think may be useful is: 
$ sudo dpkg-reconfigure gdm
I hope that helps, I also like the Gnome login screen and splash screen.
I had trouble loading Ubuntu 10.04 on an older laptop, so I did some research and found the following commands that allowed me to download a plymouth theme that works for the laptop:

$ sudo apt-get install plymouth-theme*
$ sudo update-alternatives --config default.plymouth
$ sudo update-initramfs -u

I use this method to change the splash screen just in case it's changed over to the kubuntu one.

---

### Post by Sciezyna on 2010-10-07
@glitch323,

It just worked :) very nicely, thank you, I have my old Gnome splash.

What I noticed on this forum (and I guess any other Linux forum) - and maybe You, experienced users are not aware of - is that new Linux users trust your knowledge (I least I do) blindly. We come here with problems and we are given one or set of commands to be typed in terminal as 'su', and in most cases we have (I don't) no idea what such a command will do; we type them and problems are solved. That is nice.

Thanks
J

---

### Post by glitch323 on 2010-10-07
I'm glad you got everything working! :)  I know how you feel with some of these commands.  Most of the time, people have good intentions and try to help.  If you haven't already, check out this thread: [http://ubuntuforums.org/announcement.php?f=385](http://ubuntuforums.org/announcement.php?f=385) for warnings on dangerous commands.

---

