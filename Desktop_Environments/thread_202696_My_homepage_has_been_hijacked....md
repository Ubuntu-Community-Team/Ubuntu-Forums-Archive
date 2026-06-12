---
title: "My homepage has been hijacked..."
date: 2006-06-23
forum: Desktop Environments
---

### Post by threethirty on 2006-06-23
... in linux no less. [http://www.arizona.edu/](http://www.arizona.edu/) has decided that it wants to be homepage reguardless of what I say. I've tried reinstalling FireFox, but no good. I'm not going to reinstall Ubuntu, its not that bothersome, but it is a little annoying.

any ideas:-k

---

### Post by aysiu on 2006-06-23
Yes. I have an idea. If you use a launcher to launch Firefox, and it has ```
firefox %u
``` try changing it to ```
firefox
``` Or if it doesn't have the %u, add it.

Or if you use a keyboard shortcut to launch it, go to System > Preferences > Preferred Applications and if the command is ```
firefox %s
``` change it to ```
firefox
``` or if it has no %s, add it.

In other words, switch whatever you've got to the other thing. To change the Firefox command, you may have to select **custom** instead of **Firefox**.

---

### Post by threethirty on 2006-06-23
thanks that did the trick.

---

### Post by subtler on 2006-06-24
I had the same problem when I use the gdesklet launcher. I got rid of it with this hint you gave.. thank you. 

arizona is the DEVIL!!

---

### Post by astoltz on 2006-06-24
[QUOTE=subtler]I had the same problem when I use the gdesklet launcher. I got rid of it with this hint you gave.. thank you. 

arizona is the DEVIL!![/QUOTE]Arizona's got nothing to do with it.  Firefox is just doing a Google "I'm feeling lucky" search on "%u" when it gets started with that command line.  Try putting only %u in the address bar and press return: same result.  Same thing if you put %u in Google's search and press the I'm feeling lucky button.

---

### Post by richbarna on 2006-06-26
I had that when I was using a Firefox icon on a Gdesklets taskbar.

I right clicked on the icon and chose edit starter/advanced and then removed all the languages accept English-AU, and then it didn't do it anymore.

---

### Post by ssergeje on 2006-08-17
I experienced the same problem, maybe someone could submit a bug. I don't know where and how :oops: 
My FF launched OK from thee Gnome menu, but did [http://ubuntuforums.org/showthread.php?p=1389262#post1389262]("this") from the gDesklets starter, removing %u helped.

---

