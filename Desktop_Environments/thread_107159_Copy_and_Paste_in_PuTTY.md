---
title: "Copy and Paste in PuTTY????"
date: 2005-12-22
forum: Desktop Environments
---

### Post by jakev383 on 2005-12-22
I installed putty from the respositories. I log into 12 machines daily, and putty makes it a lot easier for me to have all the connections in one spot.
Anyway, may sound like a dumb question, but how do I copy data on the screen in putty and paste it somewhere else (like into gedit?) I've tried Ctrl-C, highlighting (both left and right mouse buttons) and nothings worked yet. In putty on my Win machine, all I do is highlight the text, and I can paste it into Win apps.
Any help/suggestions is appreciated!

---

### Post by Sheco on 2005-12-22
I havent used putty on linux, what are its advantages over the standard ssh?


(have you tried middle mouse clicking? (or clicking both left and right mouse buttons at the same time?))

---

### Post by jakev383 on 2005-12-22
[QUOTE=Sheco]I havent used putty on linux, what are its advantages over the standard ssh?

(have you tried middle mouse clicking? (or clicking both left and right mouse buttons at the same time?))[/QUOTE]

Tried both buttons at the same time, and that copies and pastes within that putty window, but I can't paste to gedit or anything.
No real advantages. I sometimes just SSH in from the command line, but putty has the "bookmark" page where I can list all of my servers at the same time.

---

### Post by matid on 2005-12-22
[QUOTE=Sheco]I havent used putty on linux, what are its advantages over the standard ssh?[/QUOTE]
Probably the only advantage is that you can save sessions you use frequently along with all settings, etc.

---

### Post by Sheco on 2005-12-22
I use ~/.ssh/config

---

### Post by jakev383 on 2005-12-22
[QUOTE=Sheco]I use ~/.ssh/config[/QUOTE]

Thanks for the suggestion, but it didn't allow me to copy and paste out of putty, either ;)

---

### Post by gebasz on 2005-12-25
[QUOTE=jakev383]Thanks for the suggestion, but it didn't allow me to copy and paste out of putty, either ;)[/QUOTE]
Hi, 

I have never used Putty under Linux, but in the Windows version:
- you can select and take some content from the terminal window to the clipboard by holding down the left SHIFT key and the left mouse button
-  you can paste some content into the terminal window: by holding down the right SHIFT and click with the right mouse button to the actual position of the cursor.
I don't know if it makes you happy; but merry XMAS. :)
Cheers

---

### Post by B-Art on 2007-10-16
Linux users: In Gnome, you can paste text without previously copying it to the clipboard. 
How does this work? 
First, highlight a chunk of text in any application, then open a new application and middle-click the mouse. The highlighted text will automatically get pasted into the active application -- bypassing the clipboard altogether! In fact, this method will not disturb the existing contents of the clipboard in any way.
This method works fine for Putty on Linux.

---

### Post by billyyu on 2007-12-02
Can we just re-edit the configuration of putty's? Use the middle mouse button to paste is more inconvenient than to use the right mouse button. How can I reconfigure the properties?

---

### Post by private_meta on 2008-02-18
Actually, I'd rather like to know too how to paste, but without use of the middle mouse button. the windows putty has "shift insert", but that doesn't work either

---

### Post by frankos44 on 2008-02-18
I might be missing the point but why not just open a terminal and type:

ssh loginname@domain 

or

loginname@ipaddress

To paste simply right-click in the terminal and select paste.

I never use putty on Linux.

---

### Post by yingeric on 2008-05-13
Jak,
I just tried PuTTY on linux and found if you use right buttom to select message on the PuTTY window and then open any editor to past it by clicking mouse middle key.  In my case, I selected the texts in the PuTTY by clicking Right buttom and then opened VI clicked 'i' for inserting text status and then clicked my middle button which is the scroll key. Hope you knew the trick already.


Eric

---

