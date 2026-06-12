---
title: "Firefox and Acorbat"
date: 2006-07-25
forum: Desktop Environments
---

### Post by punkybouy on 2006-07-25
On several occasions I have visited websites which have a link to a multipage acrobat document.  Firefox opens the document but there are no controls to advance to the next page.  Any ideas.  I don't have the same problem in Windows going to the same site and document.  Thanks in advance for your help. Hopefully as usual the forum will have an answer.

---

### Post by john_spiral on 2006-07-25
easy way to install Acrobat is with the Automatix - GUI install script

[http://www.ubuntuforums.org/forumdisplay.php?f=77](http://www.ubuntuforums.org/forumdisplay.php?f=77)

---

### Post by punkybouy on 2006-07-27
I have Acrobat installed.  I believe there is even a Mozilla snapin there as well.

---

### Post by mannheim on 2006-07-27
> **punkybouy said:**
> On several occasions I have visited websites which have a link to a multipage acrobat document.  Firefox opens the document but there are no controls to advance to the next page.  Any ideas.  I don't have the same problem in Windows going to the same site and document.  Thanks in advance for your help. Hopefully as usual the forum will have an answer.

So, when Firefox opens the document, do you have the acrobat (pdf) document visible inside a Firefox window? If so, do you have a toolbar or status bar at the top of the document? At the bottom of the document? Or both?

In my setup, the navigation buttons for page-forward etc are in the toolbar/status bar at the bottom of the document.

If you don't have navigation buttons anywhere, right-click on the top acrobat toolbar (just above the acrobat document), and select "Navigation". That should give you the navigation buttons. If they are in a separate free-floating window, right-click the same toolbar again and select "Dock all Toolbars" (or something like that).

If you don't even have a toobar visible, just hit F8.

---

### Post by punkybouy on 2006-07-31
I have an Ubuntu laptop running the same Ubuntu version (6.06) Both desktop and laptop have Acrobat installed plus the Acrobat plugin for Firefox.  The laptop will open a popup window with the pdf in it using Aarobat and includes navigation controls.  The desktop also opens a popup window but it seems to be using some default viewer and not Acrobat.  How do I get the OS to use Acrobat as its default for pdf's?  Thanks in advance.  As usual the forum is very responsive.

---

### Post by punkybouy on 2006-07-31
I should also point out the the laptop is a fresh install while the desktop was an upgrade from Breezy.

---

### Post by mannheim on 2006-07-31
> **punkybouy said:**
>   How do I get the OS to use Acrobat as its default for pdf's? 

To get the OS (or actually gnome) to open pdf's using Acrobat, right-click on a pdf document, and select "Properties". Then select the "Open With" tab. You should be able to select "Acrobat Reader" there as the default, from a list of options with radio-buttons.

I'm not sure that Firefox will respect the gnome settings. To configure Firefox, you open Firefox and select "Edit --> Preferences --> Downloads --> View & Edit Actions ... "

---

