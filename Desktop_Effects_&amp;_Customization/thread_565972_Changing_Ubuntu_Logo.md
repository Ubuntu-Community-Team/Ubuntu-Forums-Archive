---
title: "Changing Ubuntu Logo"
date: 2007-10-02
forum: Desktop Effects &amp; Customization
---

### Post by evolushun on 2007-10-02
I am trying to change the logo in the lefthand corner of my Ubuntu and I cannot get permission to overwrite this file:

/usr/share/icons/hicolor/48x48/apps/distributor-logo.png

How do I achieve this?  I am trying to add the OSX Apple.

---

### Post by bimmerd00d on 2007-10-02
use sudo for permissions

---

### Post by evolushun on 2007-10-03
I do not know how to use sudo for permissions.  I have been a Linux user for about 4 days now.  Care to elaborate?

---

### Post by fdrake on 2007-10-03
if your using gimp to edit the file just type thin on the terminal:

sudo gimp "/usr/share/icons/hicolor/48x48/apps/distributor-logo.png"

and you'll be able to same the changes.

---

### Post by evolushun on 2007-10-03
> **fdrake said:**
> if your using gimp to edit the file just type thin on the terminal:

sudo gimp "/usr/share/icons/hicolor/48x48/apps/distributor-logo.png"

and you'll be able to same the changes.

OK...first of all, I have no idea how to use Gimp as, well, graphics aren't my thing.  I wish they were, but I don't have the creative capacity to create my own designs, therefore I use other peoples creativity.  With that being said, I have opened the image (of the Ubuntu logo), opened the Apple logo, deleted the Ubuntu logo and placed the Apple logo in it's place.  I then tried to save the image, it asked if I wanted to overwrite in which I chose yes and it told me I needed to export before I could save.  I clicked OK, let it do it's thing to a default folder that I have no idea where it is and I still have the Ubuntu logo in the top left hand corner.  

What did I do wrong and where do I go from here?

---

### Post by fdrake on 2007-10-03
> **evolushun said:**
> OK...first of all, I have no idea how to use Gimp as, well, graphics aren't my thing.  I wish they were, but I don't have the creative capacity to create my own designs, therefore I use other peoples creativity.  With that being said, I have opened the image (of the Ubuntu logo), opened the Apple logo, deleted the Ubuntu logo and placed the Apple logo in it's place.  I then tried to save the image, it asked if I wanted to overwrite in which I chose yes and it told me I needed to export before I could save.  I clicked OK, let it do it's thing to a default folder that I have no idea where it is and I still have the Ubuntu logo in the top left hand corner.  

What did I do wrong and where do I go from here?
strange it should work if u replaced the ubuntu logo with another image using the same name and format. by the way i am a little bit confused witch logo are trying to edit? can u post a screen shoot of it?

---

### Post by evolushun on 2007-10-03
The image that is circled...

[IMG]http://i97.photobucket.com/albums/l229/evolande/Screenshot-1.png[/IMG]

---

### Post by Fred_E _krugar on 2007-10-03
> **evolushun said:**
>   I clicked OK, let it do it's thing to a default folder that I have no idea where it is and I still have the Ubuntu logo in the top left hand corner.  

What did I do wrong and where do I go from here?




    I am sorry for laughing at this but that Sounds Exactly Like me lol:):):)

---

### Post by fdrake on 2007-10-03
i am pretty sure that the icon path u posted before doesn't belong to thee menu-bar

hope this help.

[http://ubuntuforums.org/showthread.php?p=2841579](http://ubuntuforums.org/showthread.php?p=2841579)

---

