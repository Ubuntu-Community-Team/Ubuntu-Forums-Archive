---
title: "Can't Install New Mouse Themes"
date: 2005-07-01
forum: Desktop Environments
---

### Post by palsyboy on 2005-07-01
If I want to install, for example, the [Hematite theme](http://kde-look.org/content/show.php?content=19594) from kde-look.org, the instructions given are:
___________________________
Open the Control Centre
Open Peripherals -> Mouse
Click the Cusor Theme tab
Click Install New Theme...
Select the cursor theme archive
Restart KDE
Have fun!
___________________________

For one, I don't know what the "cursor theme archive" is, but clicking on the tar itself or on the folder extracted from the tar gets me the following messages, respectively:

"The file 19594-haematite-1.0.tar.gz does not appear to be a valid cursor theme archive."

and

"The file 19594-haematite-1.0.tar.gz does not appear to be a valid cursor theme archive."

The same happens for any other themes I've tried to install.  What am I doing wrong?  :?

---

### Post by dresnu on 2005-07-01
Try this one: Extract the theme. Create the directory /usr/share/icons/kubuntu. Move index.theme(from the extracted theme) to that directory and create another directory /usr/share/icons/kubuntu/cursors. Inside that last dir move all the cursors(or just move the cursors dir from the extracted theme to /usr/share/icons/kubuntu). Restart the X server, and that should do the trick ;-). Tell me if it worked!

---

### Post by odrop on 2005-07-02
Some mouse themes require you to unpack them and run the install scripts, like the Crystalcursors mouse themes.

Try unpacking the mouse theme package in some directory and see if it includes any special install instructions.

For instance, with Crystalcursors, you have to unpackage it, then do make and make install.

And the "Cursor theme archive" is the file you downloaded, 19594-haematite-1.0.tar.gz in your case.

---

### Post by palsyboy on 2005-07-02
**dresnu**: It works in its own hack-ey way with simple themes such as Hematite (which, in practice, I didn't end up liking :( ), but more complex ones such as Crystalcursors don't have analogous cursors.  Thanks for your input, though. :)

**odrop**: I've tried referring to the tar itself, and it isn't recognized as a valid theme.  As for the make command, I've had the following happen:
```

# make -C /opt/pictures/desktop_modifications/mouse_themes/Crystalcursors/blue_src/         
make: Entering directory `/opt/pictures/desktop_modifications/mouse_themes/Crystalcursors/blue_src'
xcursorgen base_arrow_down.conf ../blue_cursors/base_arrow_down
make: *** [../blue_cursors/base_arrow_down] Error 1
make: Leaving directory `/opt/pictures/desktop_modifications/mouse_themes/Crystalcursors/blue_src'
# make install -C /opt/pictures/desktop_modifications/mouse_themes/Crystalcursors/blue_src/
make: Entering directory `/opt/pictures/desktop_modifications/mouse_themes/Crystalcursors/blue_src'
xcursorgen base_arrow_down.conf ../blue_cursors/base_arrow_down
make: *** [../blue_cursors/base_arrow_down] Error 1
make: Leaving directory `/opt/pictures/desktop_modifications/mouse_themes/Crystalcursors/blue_src'

```
After that, nothing happens.  I don't get an option to use the mouse theme.  :?  I also tried restarting KDE, but that didn't do anything.

Perhaps I'm misunderstanding the "make" command?

Thanks for the help. :)

---

### Post by vladuz976 on 2005-07-31
apt-get install gcursor
maybe

---

### Post by palsyboy on 2005-08-05
Thanks for the suggestion.  I tried it, but gcursor didn't know what to do with the mouse themes, either. :(

---

### Post by vladuz976 on 2005-08-05
what mouse themes?
i got the crystal theme from gnome-look.org and all i did was untar and  and read the instructions, 
i think you just do "make" "make install" and "make clean" "make uninstall" to get rid or it. 
after install gcursor will show themes in its menu.

---

### Post by palsyboy on 2005-08-11
I'm trying to install [Haematite](http://kde-look.org/content/show.php?content=19594) and [Grounation](http://kde-look.org/content/show.php?content=14484).  I don't see what file upon which I'm supposed to run make.  :-?

Thanks again for trying to help me out.

---

### Post by Zhukov on 2005-09-02
Just sudo apt-get install gcursor

Now you have an app in system preferences allowing you to manage you themes.

---

### Post by mort1 on 2005-09-03
Try this, it works for me.. Download the file and extract the file, then compress the folder inside the main folder to tar.gz ..and install it like normal..

---

### Post by alcatraz678 on 2007-10-26
My cursor stays the same. Even after restarting my computer.
But I managed to install the theme to the KDE Manager.

---

