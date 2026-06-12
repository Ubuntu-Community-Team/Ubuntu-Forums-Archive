---
title: "wrong icons in AWN"
date: 2007-11-14
forum: Desktop Effects &amp; Customization
---

### Post by BDNiner on 2007-11-14
Ever since i upgraded to gutsy the icons in my AWN bar are not the system theme icons. I have to manually add icons to replace the ones i have. This would not be a problem since i use icons from a couple different icons themes. But i am unable to change the trash can icon. Has anyone else run into this issue?

---

### Post by Aquaman420 on 2007-11-14
I also have this problem.  There is a fix which involves putting symbiotic links in a folder.  I saw the thread on launchpad. Here's the link:  [https://answers.launchpad.net/awn/+question/11180]("https://answers.launchpad.net/awn/+question/11180")

---

### Post by BDNiner on 2007-11-14
I thought the instructions would work but they didn't. Does it matter that my icons are *.svg and not *.png? i created symbolic links to both *.png and *.svg and neither worked.

on another note, how do i delete symbolic links? can i delete them like regular files?

---

### Post by Aquaman420 on 2007-11-14
I apologize that it didn't work.  As far as my knowledge goes, you can delete them regularly.  If not you can *sudo nautilus* and navigate to the folder you put them in and delete them that way, just remember that you would be in the file browser as root.

---

### Post by ericesque on 2007-11-14
Niner, have you made sure to update your sources.list to the gusty repos and updated AWN from those repos?  Just a hunch, but that might help.

---

### Post by Aquaman420 on 2007-11-14
BdNiner,   I just tried to change the icon and I was successful.  After you put the links in you have to go to AWN's preferences and remove the trash applet then replace the trash applet. I used a PNG image.  Not to sure about the SVG.  Just open up your icon in the gimp and do a SAVE AS and down near the bottom you can pick the png extension.   Let me know if you are successful.  Best of luck.

---

### Post by ericesque on 2007-11-14
AWN accepts svg icons.  It shouldn't be any different for this link thing you're working with.

---

### Post by BDNiner on 2007-11-14
> **ericesque said:**
> Niner, have you made sure to update your sources.list to the gusty repos and updated AWN from those repos?  Just a hunch, but that might help.

Yeah i installed AWN using the Gutsy repos. I just decided to use an icon theme that has the correct trash icons. I will try and save the files as png now and see if it help. Yeah the other svg icons work fine, just the trash is broken.

Nope it still didn't work after removing the icon and then placing it back. I have also uninstalled awn and then reinstalled it to no avail.

---

### Post by Aquaman420 on 2007-11-14
I would like to help you as others have helped me so with that being said please do not take offense to my next tips they are not meant to make you feel dumb and are meant purely to help you incase something was overlooked.  Now with the actual symbiotic links:
ln -s user-trash-empty.png gnome-stock-trash.png

ln -s user-trash-full.png gnome-stock-trash-full.png

It would seem that the latter part of the link is calling for PNG images only, so maybe try converting the SVG's into PNG's if you haven't already,then saving them to the folder, closing that folder, then removing the trash applet then replacing it in AWN's preferences.  Also double check the first part of the link and make sure that is has the icons correct name.  I renamed my icons to *trash-empty.png* and *trash-full.png* just to simplify things for my self.  So my links looked like this

ln -s trash-empty.png gnome-stock-trash.png

ln -s trash-full.png gnome-stock-trash-full.png

This is what I did step by step.  Don't give up.  Once you do this you can look in tha folder the icons are in and see if there is a duplicate icon in there with a curved arrow on it.   Indicating the link is there for the icon.  Best of luck

---

### Post by BDNiner on 2007-11-20
After converting the svg files to png files it works fine. but when i empty the trash can another trash can (wrong icon) appears in the notification area and then disappears. i guess because the trash folder is a kind of regular folder. what is the name of the icons that briefly appears in the notification area? so i can change it also.

---

### Post by Aquaman420 on 2007-11-22
I am sorry BDNiner I do not know that one.  I use a top gnome panel as my notification area and when i click on the trash nothing shows up in the notification area.  Although at first it looks as if something will.  The area darkens slightly, then like that it's gone.  bump.

---

