---
title: "&lt;period&gt; opens help window in nautilus"
date: 2010-05-25
forum: Desktop Environments
---

### Post by laoshi on 2010-05-25
I have met with a rather annoying problem in nautilus:
every time i press . (period) the help-window opens - consequently I am not able to quick-find hidden files in nautilus, nor create new files with file extensions in the GUI.
I am running 10.04, metacity, awn - and have searched this annoying setting in nautilus settings, awn settings, keyboard bindings, but without success. Have also searched 'keybindings' in gconf but found no solution.
So any suggestions would be welcomed.

---

### Post by ..::| Dave89 |::.. on 2010-05-25
Try this; Go to the Preferences submenu in the System menu, and click on Keyboard Shortcuts. Go to the Desktop category, and the first listed option is Launch Help Browser.  Click on the Shortcut column entry to the right, hit backspace, close the Keyboard Shortcuts windows and your problem should be solved

---

### Post by laoshi on 2010-05-25
No success, sorry. I had already tried assigning a keyboard combination to launch the help window - and as you suggested I now deactivated it. Logged out and in - and same result.
I have also tried resetting keyboard preferences, and tested its workings. <period> behaves as expected in test and in programmes. But in nautilus the key is dead, and still launches the help window.
So it is something nautilus specific - but what?

---

### Post by laoshi on 2010-05-25
This is getting weird!
As mentioned above: in nautilus, and only nautilus, the <.> key is dead. But <shift>+<.> is alive and outputs <:> as expected.

---

### Post by laoshi on 2010-05-30
There has been some progress, but I am still not there.

In g-conf-tool I located **apps > gnome_settings_daemon > keybindings** and found the key '*help <control><period>*'
After changing this to '*help <control>y*' and logging out and in again the following happens:

When I use quick-search in a nautilus window, hitting <period> does not open the search box, but yelp, as before. 
But if I first hit another character, then the search box opens, and I can enter <period> as expected and it now outputs a <period>, so now I can search for hidden files.

But when I create a file on the Desktop and try to give it an extension, the <period> key on the keyboard is still dead, and hitting it opens yelp as before.

Of course I can create and rename files using the terminal, but it still it is a little annoying not being able to fix this.

I have searched for keybindings in metacity, gnome, nautilus, compiz, but found nothing unusual. So can anyone suggest where to find this strange binding?

---

