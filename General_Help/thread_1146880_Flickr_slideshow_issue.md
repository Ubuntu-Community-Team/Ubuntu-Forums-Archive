---
title: "Flickr slideshow issue"
date: 2009-05-03
forum: General Help
---

### Post by lucifuge on 2009-05-03
[SIZE=3]I can see Flickr pictures individually no problem. However, the slide-show option just shows a black screen, ie no worky. This is with Ubuntu 9.04, anyone else noticed this?  Maybe a plug-in is required?[/SIZE]

---

### Post by trpnblies7 on 2009-05-03
Have you made sure you have flash player installed? And if you do, try uninstalling and reinstalling it first to see if that works.

---

### Post by lucifuge on 2009-05-03
> **trpnblies7 said:**
> Have you made sure you have flash player installed? And if you do, try uninstalling and reinstalling it first to see if that works.


when you say flash, do you mean Shockwave flash or Firefox flash or other?  is there a difference?

---

### Post by diham on 2009-08-18
I am also having the same issue. I tried with both firefox and Opera but can see only a blank screen and also installed adobe flash player 10 manually.:confused:

---

### Post by diham on 2009-08-18
:popcorn:

yes now it worked for me.

What I did...

removed other flash plugins through commandline

sudo apt-get remove gnash*
sudo apt-get remove swfdec*

Now uninstalled the AdobePlugin through 'Add/Remove'

and also did
sudo apt-get remove flashplugin-nonfree


NOW , reinstalled flashplugin.

sudo apt-get installe flashplugin-nonfree

closed the mozilla browser and open again!!

Everything working perfectly!!!!!!\\:D/

---

