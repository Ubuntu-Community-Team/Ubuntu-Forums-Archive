---
title: "Key binding ?"
date: 2009-05-22
forum: Desktop Environments
---

### Post by Kiro42 on 2009-05-22
Hi

I'm looking for a way to bind a key to another key, to be able, for exemple, to press "A" in order to press "P" :)

Thanks in advance !

---

### Post by Minsky on 2009-05-22
I think what you mean is that you want "P" to be displayed when you press "A". You need to find the keycode for "A", so open a terminal window and type **xev**. A small window will pop up with a black square outline inside it, which you can ignore, and a list of PropertyNotify event codes will be displayed in the terminal window.

Press the "a" key, and two blocks of code will be displayed - one for the keypress down and one for the keyrelease up. On the third line down of both blocks, you will find the keycode for the key that you've just pressed, in our case "38". Make a note of the number and close the terminal window.

Go to **Applications > Accessories > Text Editor** and type:

**keycode 38 = p P p P**

Make sure that there's a space between each character in the "p" key sequence, the sequence represents - key pressed, Shift+key, Mode key+key and Shift+Mode key+key. Go to the **File** menu in the text editor and select **Save As**. Save the file as **.Xmodmap** in your home folder, don't miss out the period\full stop at the beginning of the filename.

The .Xmodmap file should be loaded whenever you login but if not then go to **System > Preferences > Sessions** and click on the **Add** button. In the small window that appears type **Xmodmap** in the "Name " field, and type **~/.Xmodmap** in the "Command" field, and click on **Add** then **Close**. And that should do the trick.

---

