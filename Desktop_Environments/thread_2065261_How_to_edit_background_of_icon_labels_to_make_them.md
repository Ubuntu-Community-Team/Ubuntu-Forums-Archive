---
title: "How to edit background of icon labels to make them clear?"
date: 2012-10-01
forum: Desktop Environments
---

### Post by Longstreet on 2012-10-01
Hello all. Recently switched to xubuntu from Mint. I'm trying to edit the background of the icon labels. I'd like white lettering on clear background.

I've tried a couple of different methods of editing gtkrc files in the theme I'm using without success. I'm most likely doing something wrong, but can't figure out what.

Is there an easier way to do this? Or can someone point me to a REALLY SIMPLE step by step for edit the theme files?

Thanks.

---

### Post by vasa1 on 2012-10-01
See if this helps: [http://askubuntu.com/a/194635/25656](http://askubuntu.com/a/194635/25656)

---

### Post by Longstreet on 2012-10-01
I hadn't seen that particular page, but it's similar to what I've done before. Still, I tried the instructions there, and no joy. Looks just the same as before.

AAaargh. I'm not a Linux gunslinger, but I'm not a complete noob either. This is making me feel stupid.

Thank you nonetheless.

---

### Post by JKyleOKC on 2012-10-01
Here's the code that I am using in the hidden ~/.gtkrc-2.0 file to achieve exactly the result you are looking for:```
style "xfdesktop-icon-view" {
XfdesktopIconView::label-alpha = 0

fg[NORMAL] = "#ffffff"
fg[SELECTED] = "#ffffff"
fg[ACTIVE] = "#ffffff"
}


widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"

```Leaving out the "base" settings is what makes the background disappear, although it does come back when I select or activate one of the icons.

You need to logout and log back in for it to take effect.

---

### Post by SantaFe on 2012-10-01
```
# DO NOT EDIT! This file will be overwritten by LXAppearance.
# Any customization should be done in ~/.gtkrc-2.0.mine instead.

style "xfdesktop-icon-view" {

XfdesktopIconView::label-alpha = 0
XfdesktopIconView::selected-label-alpha = 0
font_name="Verdana"

base[NORMAL] = "#ffffff"
base[SELECTED] = "#ffffff"
base[ACTIVE] = "#fefefe"

fg[NORMAL] = "#ffffff"
fg[SELECTED] = "#73B2D0"
fg[ACTIVE] = "#97CDFD"
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"
```

This is mine.  You got clear backgrounds, White unselected Text, Darker blue Selected Text, and lighter blue active text.

From what I've read, it's the value settings in both XfdesktopIconView lines that controls the Transparency.  255 solid box, 0 clear box, anything in between a combination of both. ;)

And don't mind the comment line, I've also got LXDE on this computer as well.

---

### Post by Longstreet on 2012-10-01
Both of those sound like the direction I'm wanting to go with this. Still doing something wrong.

Here's what I'm doing:

**1. Open Thunar from the terminal as su.**

I'm using the Bluebird theme, so I

**2. Navigate down to what I think is the right folder, like so:**

File system>usr>share>themes>Bluebird>gtk-2.0

**3. Click on File, Create Document**, 

and name it .gtkrc-2.0

**4. Right click on and open that doc with Leafpad**

and copy/paste this code from JKyleOKC's post:

```
style "xfdesktop-icon-view" {
XfdesktopIconView::label-alpha = 0

fg[NORMAL] = "#ffffff"
fg[SELECTED] = "#ffffff"
fg[ACTIVE] = "#ffffff"
}


widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"

```
**5. Save file and exit Thunar**

**6. Log out, and back in**

**7. Curse at my computer, then go to the fridge for a cold beer.**


What am I missing?

---

### Post by Toz on 2012-10-01
> 2. Navigate down to what I think is the right folder, like so:

File system>usr>share>themes>Bluebird>gtk-2.0


Actually, the correct location of the file is your home directory, not the theme file directory (~/.gtkrc-2.0) - no sudo required. 

Or if you want to set it system-wide for everyone, the the correct location is /etc/gtk-2.0 in a file called gtkrc - sudo required.

And, instead of logging out and back in again, you can also change the appearance theme away and back to read the file.

---

### Post by Longstreet on 2012-10-01
> **Toz said:**
> Actually, the correct location of the file is your home directory, not the theme file directory (~/.gtkrc-2.0) - no sudo required.

And there it is. I knew I was doing something simple wrong.

Thank you all for your advice and patience.

---

### Post by JKyleOKC on 2012-10-01
After following the links higher in this thread, I added two more lines to my .gtkrc-2.0 file:```
XfdesktopIconView::selected-label-alpha = 0
XfdesktopIconView::active-label-alpha = 0
```
These did away with the background appearing when I selected or activated an icon.

Now I'm wondering where to find documentation of all the properties that might go into this file...

---

### Post by SantaFe on 2012-10-02
I found this link: [http://git.xfce.org/xfce/xfdesktop/tree/README]("http://git.xfce.org/xfce/xfdesktop/tree/README") where I found out how to do this.  Has some other options for XfdesktopIconView:: I'll have to check out. ;)

---

### Post by JKyleOKC on 2012-10-02
Thanks! I've bookmarked that page; it offers several ideas to follow up.

---

### Post by Toz on 2012-10-02
There are also these links:

- [http://wiki.xfce.org/tips#gtkrc_files]("http://wiki.xfce.org/tips#gtkrc_files")
- [http://git.xfce.org/xfce/xfce4-panel/tree/docs/README.gtkrc-2.0]("http://git.xfce.org/xfce/xfce4-panel/tree/docs/README.gtkrc-2.0")

---

### Post by Longstreet on 2012-10-02
> **JKyleOKC said:**
> Thanks! I've bookmarked that page; it offers several ideas to follow up.

Yep. Bookmarked. That info might be helpful.

btw JKyle, I live just a few hours south of you, on the right (ahem, south :)) side of the Red River. We're practically neighbors.

---

### Post by SantaFe on 2012-10-02
> **JKyleOKC said:**
> Thanks! I've bookmarked that page; it offers several ideas to follow up.
Glad it could be usefull! :popcorn:

---

