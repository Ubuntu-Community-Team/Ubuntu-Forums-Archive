---
title: "Desktop Theme"
date: 2012-01-10
forum: Desktop Environments
---

### Post by makitso on 2012-01-10
I must say that I am very partial to the Lubuntu theme in version 11.04.  I like the blue with white lettering on the panel and desktop theme.  IMO, the 11.10 theme is less vibrant so I would like to identify the files to move from 11.04 to 11.10 to fix this.

What files should I find and replace?

---

### Post by Frogs Hair on 2012-01-10
You should be able to identify the currently installed themes from the synaptic package manager . You also need to know the name of the 11.04 theme and this could be found in appearance or theme settings . If the 11.04 theme is compatible with 11.10 you should be able install it .

---

### Post by Dennis N on 2012-01-10
> **makitso said:**
> I must say that I am very partial to the Lubuntu theme in version 11.04.  I like the blue with white lettering on the panel and desktop theme.  IMO, the 11.10 theme is less vibrant so I would like to identify the files to move from 11.04 to 11.10 to fix this.

What files should I find and replace?

In Lubuntu 11.04, the background image for the panel is:

/usr/share/lxpanel/images/lubuntu-background.png

Just use that instead of the 11.10 image. (set through Panel Settings > Appearance).

The wallpaper is at:

/usr/share/lubuntu/wallpapers/lubuntu-default-wallpaper.png

Good luck.

---

### Post by makitso on 2012-01-10
Thanks!

---

### Post by makitso on 2012-01-12
Panel and background work great.  But, when I open a window or folder or application the top of the window is the old light gray with black text.  How do I change this to the blue with white text?
Said another way, the 11.04 Openbox Lubuntu-default, where might this be?

---

### Post by Dennis N on 2012-01-12
> **makitso said:**
> Panel and background work great.  But, when I open a window or folder or application the top of the window is the old light gray with black text.  How do I change this to the blue with white text?
Said another way, the 11.04 Openbox Lubuntu-default, where might this be?

Recommended:

The simplest way would be to change the window border to have a blue background with white text is to use Clearlooks border:

Preferences > Customized Look and Feel > Window Border

Select Clearlooks

Press the Apply button.

Close and you are done.

----------------------------

Harder Option:

If you want the exact same theme/border as in Lubuntu 11.04: 

The **folder** containing the default theme components in Lubuntu 11.04 and 11.10 is:

/usr/share/themes/Lubuntu-default

I would definitely back up the 11.10 Lubuntu-default folder before making any changes, in case something goes wrong and you want to restore it. Proceed at your own risk.

Ideas:

You should be able to copy the old theme folder into /usr/share/themes/ directory of 11.10. I would change to another theme and window border **before** doing that, then reselect.

If you want to change only the window border, you might be able to  replace only the Openbox-3 folder which defines the window border theme. It's inside the Lubuntu-default folder. 

Note: The newer Lubuntu theme contains a GTK-3 theme version the old one doesn't have.

Except for using Clearlooks border, these are suggestions with unknown final results, so be sure to back up the theme folder before proceeding.

---

### Post by makitso on 2012-01-14
Yes, I am using clearlooks now.  It is very close but personally, I don't like the boxes around the window controls.  Thanks for the second option.:P

As a side note, there have been many posts about the stunning beauty of the lubuntu 11.04 theme.  IMO, it was jaw dropping in its simplicity and elegance.  I requested on the 12.04 wish list that this theme be made available.

Update:  I copied the folders in  /usr/share/themes/Lubuntu-default from my 11.04 installation to 12.04 and it works perfect!

Now, 12.04 looks as stunning.  

Thanks for  your help.

---

