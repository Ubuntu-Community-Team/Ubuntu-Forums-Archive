---
title: "How to add pictures to usr/share/backgrounds?"
date: 2012-07-25
forum: Desktop Environments
---

### Post by orange2k on 2012-07-25
I want Ubuntu to see the pictures I add to that folder. I added some pictures to the folder, but they do not appear in the "change background image" dialog box, just the standard Ubuntu do...

What do I need to do to make them appear there?

And I know I can make any picture from anywhere to appear as my background, but then they are not on my login screen because my home folder is encrypted, if I expressed myself corectly...

---

### Post by vasa1 on 2012-07-25
> **orange2k said:**
> I want Ubuntu to see the pictures I add to that folder. I added some pictures to the folder, but they do not appear in the "change background image" dialog box, just the standard Ubuntu do...

What do I need to do to make them appear there?
...

Just copy them there using **sudo cp**.

---

### Post by orange2k on 2012-07-25
> **vasa1 said:**
> Just copy them there using **sudo cp**.

Yes, I managed to copy them there, but they are not visible in the dialog. Only the standard Ubuntu backgrounds appear there.
I want the pictures that I added there to appear in the dialog.
Try to copy some pictures there and see what happens...

---

### Post by hakermania on 2012-07-25
> **vasa1 said:**
> Just copy them there using **sudo cp**.

or give ALT+F2 type in, gksudo nautilus and hit enter. Then, manually copy your pictures to /usr/share/backgrounds using the file browser window that opened. Be careful though because you have super user privileges with this window and it lets you edit any part of your system!

So, when you're done, close the window.

---

### Post by orange2k on 2012-07-25
> **hakermania said:**
> or give ALT+F2 type in, gksudo nautilus and hit enter. Then, manually copy your pictures to /usr/share/backgrounds using the file browser window that opened. Be careful though because you have super user privileges with this window and it lets you edit any part of your system!

So, when you're done, close the window.

I did that, but the pictures that I added do not appear in the "change desktop background" dialog box...

---

### Post by howefield on 2012-07-25
You may need to edit the following file..

```
/usr/share/gnome-background-properties/precise-wallpapers.xml
```

Best to make a back up of the file first though :)

---

### Post by vasa1 on 2012-07-25
> **orange2k said:**
> Yes, I managed to copy them there, but they are not visible in the dialog. Only the standard Ubuntu backgrounds appear there.
I want the pictures that I added there to appear in the dialog.
Try to copy some pictures there and see what happens...

I did just that two days ago and they do appear as options.

---

### Post by orange2k on 2012-07-25
> **howefield said:**
> You may need to edit the following file..

```
/usr/share/gnome-background-properties/precise-wallpapers.xml
```

Best to make a back up of the file first though :)

Thats it! Thank you!

I didn't know it would be so complicated, though...:mad:

---

