---
title: "Nice Screen Saver, Forgot How I Did It."
date: 2014-08-14
forum: Desktop Environments
---

### Post by parl8256 on 2014-08-14
Some time ago, when I was first using 12.04, I installed a screen saver which shows a small peaceful green valley with green hills on the sides. There is blue sky and there are some clouds. The nice part is that the wallpaper image changes during the day to sort of match the time of day. At night there is a dark sky and at sunrise and sunset, there is twilight, etc.. I remember that I had to so something unusual, but I no longer remember what it was.

That computer is now fated to be discarded, as it doesn't work for more than 15 to 30 minutes at a shot. I'd like to recover the screen saver and install it on another machine.

Does anyone have some suggestions as to where I could look for this screen saver, either in my computer or on the net?

Thanks,

Ross Parlette

---

### Post by yancek on 2014-08-14
/usr/share/backgrounds is the default location for wallpaper/background images.  I don't know if what you are looking for would be there.

---

### Post by parl8256 on 2014-08-14
The unique quality of this set of images is that they portray this same valley at different times of the day and night and they are displayed at the appropriate times of the (local) day.

If I could capture one of the images and do a google search on it, that might lead me to it. But I'm not sure how to do that.

---

### Post by amanchesterman on 2014-08-15
Umm ... is [this](http://www.omgubuntu.co.uk/2011/04/this-neat-wallpaper-for-ubuntu-changes-with-the-time-of-day) what you had in mind?

---

### Post by Rob Sayer on 2014-08-16
> **yancek said:**
> /usr/share/backgrounds is the default location for wallpaper/background images.  I don't know if what you are looking for would be there.

Did you try looking there?  It's the standard location for Unity and I think the other DEs too.

You may have to open your file manager with gksudo to be able to access it, or boot with the live iso and mount that drive.

---

### Post by CantankRus on 2014-08-16
Is it a desktop background or a screensaver?

If it's a desktop background and it's in use this should show the location
```
gsettings get org.gnome.desktop.background picture-uri
```

May even be gconf on 12.04
```
gconftool-2 --get /desktop/gnome/background/picture_filename
```

---

### Post by parl8256 on 2014-08-17
YES, AMANCHESTERMAN! This is it. I'll see if it still works on 14.04, which it should.

---

### Post by parl8256 on 2014-08-17
Thanks to all of you for your helpful replies. I'm gradually increasing my knowledge and you're helping.

---

