---
title: "Save folder options in Nautilus?"
date: 2014-08-11
forum: Desktop Environments
---

### Post by axelsword on 2014-08-11
Hi!

Is there a way to save folder view settings of search in Nautilus file manager?

Effective file management is essential to me. For windows there's a very handy Total Commander file manager application that allows for quick navigation between partitions. It's important since I use various external storage.

I've noticed that it's really cumbersome to quickly find the files I need in default file manager. When I click the search icon in Ubuntu 12.04 LTS, I get the search results in the same window (and tab) I started from. Then I go to Edit->Visible columns, enable "Location" to see path to file and I can sort results by location. But I have to redo this setting for every search.

So, is there an effective way to have search behave in a user specified way? I don't know how to access and make changes to source code of Ubuntu. Being able to repeat a search with a simple call would be helpful as well like it's done with "reuse last filter" in GIMP.

Additional information: ok, sometimes I just want to open all png images that sit in separate folders sorted by event and start a slideshow with Image viewer 3.4.2. Apart from a long console command listing individual files, I don't know any way to specify a file collection. There should be short-cuts to collections of files instead of just individual files or folders or apps.

Thanks!

---

### Post by CantankRus on 2014-08-12
Try out [COLOR=#333333][FONT=monospace]Double Commander.
[/FONT][/COLOR]> [COLOR=#333333][FONT=monospace]Double Commander is a cross platform open source file manager with two panels side by side. 
It is inspired by Total Commander and features some new ideas.[/FONT][/COLOR] 
[https://launchpad.net/~alexx2000/+archive/ubuntu/doublecmd](https://launchpad.net/~alexx2000/+archive/ubuntu/doublecmd)

---

### Post by axelsword on 2014-08-14
Please help with installation!

I added PPA to repository list, but instructions end there. I tried this command and got:

**sudo apt-get install doublecmd**
[COLOR=#696969]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package doublecmd is a virtual package provided by:
  doublecmd-qt 0.5.10-0+svn5514~precise
  doublecmd-gtk 0.5.10-0+svn5514~precise
You should explicitly select one to install.

E: Package 'doublecmd' has no installation candidate[/COLOR]

I know so little about linux. I mainly use ubuntu software center. Exception was Skype, but it had clearer instructions. I have 64 bit system.
Cheers!

*Edit* [SOLVED]
Nevermind. I found this resource [http://ubuntuforums.org/showthread.php?t=2238971&p=13095361#post13095361](http://ubuntuforums.org/showthread.php?t=2238971&p=13095361#post13095361)
it explained the rest. Now to figure out what graphics environment this Ubuntu uses...
Searching for answers here [http://askubuntu.com/questions/249150/what-is-kde-gtk-gtk-qt-and-or-gnome](http://askubuntu.com/questions/249150/what-is-kde-gtk-gtk-qt-and-or-gnome)

---

