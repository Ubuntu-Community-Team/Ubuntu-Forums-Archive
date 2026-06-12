---
title: "Menus in KompoZer trashed"
date: 2014-06-15
forum: Desktop Environments
---

### Post by Tom_ZeCat on 2014-06-15
The best WYSIWYG HTML editor for Linux is supposed to be KompoZer.  I installed it maybe about a month or two ago and it was working great at first.  However, somehow its menus have gotten trashed.  At first when I'll pull a menu down, it will be grey, though readable and somewhat distorted.  As I move the mouse pointer down it, it turns black and items are difficult or impossible to read.  In some cases the menu pulls down black from the start.  I'm including some screen shots in my post.  

In Synaptic Package Manager, I did a complete uninstall.  At that point it was no longer in the package manager.  I then attempted a re-install from the command line following the instructions on this page:
[https://help.ubuntu.com/community/InstallKompozer](https://help.ubuntu.com/community/InstallKompozer)

That was not successful.  In the terminal, it got to one of the download commands and it timed out.  I looked in Kubuntu's interface and found it not installed.  I then installed it from the command line with the following instructions: 
[http://linuxg.net/how-to-install-kompozer-on-ubuntu-13-04-12-10-12-04/](http://linuxg.net/how-to-install-kompozer-on-ubuntu-13-04-12-10-12-04/)

That worked as far as getting it running again.  However, it did not solve the problem of the trashed menus.  I tried disabling wobbly windows, but that did no good.  
If anyone has any idea what's going on, I would be grateful for any help.  

Here are the screen shots: 

[[img]http://s20.postimg.org/iluqhe225/Kompozer_Prob.png[/img]](http://postimage.org/)
[free photo hosting](http://postimage.org/)

[[img]http://s20.postimg.org/cwehx2vvx/Kompozer_Prob2.png[/img]](http://postimage.org/)
[picture upload](http://postimage.org/)

[[img]http://s20.postimg.org/pmiqa63u5/Kompozer_Prob3.png[/img]](http://postimage.org/)
[upload pic](http://postimage.org/)

[[img]http://s20.postimg.org/ylde0xy3x/Kompozer_Prob4.png[/img]](http://postimage.org/)
[screenshot software](http://postimage.org/app.php)

---

### Post by gpb2 on 2015-03-16
I had the same problem on Kubuntu. It seems to be caused by the GTK Theme. You probably have KDE as desktop manager.
Go to System Configuration > Common Appearance and Behavior > Application Appearance > GTK > GTK2 Theme
Change the theme from Oxygen to anything else (in my case Raleigh).
Now Kompozer works.
I found that on a Bluegriffon help forum (same type of bug, same solution).
I hope this will still be of use.

---

