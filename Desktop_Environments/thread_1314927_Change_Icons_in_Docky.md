---
title: "Change Icons in Docky?"
date: 2009-11-04
forum: Desktop Environments
---

### Post by javyn999 on 2009-11-04
Hey everyone.  Rather strange question here.  I installed the GRPN calculator from the repositories (I love RPN!).  Anyway, I drug the GRPN icon to Docky before I thought to set an icon for GRPN in the main menu.  

So my GRPN icon in Docky is a white X.  I set the icon for it in the main menu as a more appropriate calculator icon, but when I drag it back to Docky to reset it, the white X icon is still there.  

Any ideas?

---

### Post by milky2313 on 2009-11-26
You need to make an application launcher for GRPN with the appropriate icon in the /usr/share/applications folder.  

I did this to fix icons in docky for some programs that I have installed manually and it worked fine.

The only problem I am having now is that when I open some of my applications from docky, a new icon with a white ? shows up rather than showing the blue dot under the appropriate icon that is already there. For some reason, it is not associating the open window with the appropriate icon. 

I'm not sure that makes sense, but here's a picture to show you what I mean. You see I have a screenlets icon in docky but when I open screenlets, a new ? icon shows up...

---

### Post by duanedesign on 2009-12-19
In Docky i am trying to change my folder icons from plain blue folders to unique folder icons to differentiate Downloads, Pictures, Documents.

I created the entries in Docky originally with the old plain blue folders. I then changed the icons on those folders. The Docky icons remained the plain blue icons i had originally. Deleting the icons in Docky and dragging over the folder with the new icon does not work.

I haven't been able to locate a config file that seems to hold this info...


I tried placing the new icons in /usr/share/applications, but had no success.

[IMG]http://farm3.static.flickr.com/2629/4197642529_2653f2f0fb_m.jpg[/IMG]

---

### Post by DBO on 2009-12-20
You can change folder icon colors just by scrolling on them. Designed to help with this situation.

---

### Post by Bobbyrne01 on 2010-09-04
> **milky2313 said:**
> You need to make an application launcher for GRPN with the appropriate icon in the /usr/share/applications folder.  

I did this to fix icons in docky for some programs that I have installed manually and it worked fine.

The only problem I am having now is that when I open some of my applications from docky, a new icon with a white ? shows up rather than showing the blue dot under the appropriate icon that is already there. For some reason, it is not associating the open window with the appropriate icon. 

I'm not sure that makes sense, but here's a picture to show you what I mean. You see I have a screenlets icon in docky but when I open screenlets, a new ? icon shows up...

yea this worked fine for me too :)

---

