---
title: "Change &quot;Ubuntu&quot; logo on startup to another image"
date: 2010-05-25
forum: Desktop Environments
---

### Post by pzkfw on 2010-05-25
I've been using Debian for a few years. I know ubuntu has something like this where it has a graphical loading bar instead of listing what drivers/things are being loaded.  I'm working with my father who complains about his laptop problems which relate to almost every single thing that Linux provides (complaints of bad battery life, viruses from porn, paying $500 for MS office, computer runs &quot;slow&quot;, only uses it for e-mail, etc) and he won't use Linux because there's no shiny interface and there isn't a commercial for it on television. He even goes so far as to tell me not to tell people about linux because he still thinks it's hard to use even after using gnome. I figured I should show him up by completely fooling him into thinking he's still on Windows.  I made GNOME look exactly like Vista with GNOmenu, using a custom metacity skin, and making a custom panel background image.  The only thing I can't replicate is the startup process where it just says &quot;Microsoft Corporation&quot; and a loading bar.  If I use ubuntu, can I change that image? Or is there some kind of bash script that I can do to load an image? Even a static image would work fine, he might buy it.  Thanks for any help or suggestions.

---

### Post by iMattcotv on 2010-05-25
You need "Startup Manager"

Google it or visit:
[http://web.telia.com/~u88005282/sum/installation.html](http://web.telia.com/~u88005282/sum/installation.html)

This allows the GRUB and Bootscreen content to be changed.

---

### Post by hok00age on 2010-05-25
> **iMattcotv said:**
> You need "Startup Manager"

Google it or visit:
[http://web.telia.com/~u88005282/sum/installation.html](http://web.telia.com/~u88005282/sum/installation.html)

This allows the GRUB and Bootscreen content to be changed.

What version of Ubuntu you're using?

---

### Post by hok00age on 2010-05-25
> **pzkfw said:**
> I've been using Debian for a few years. I know ubuntu has something like this where it has a graphical loading bar instead of listing what drivers/things are being loaded.  I'm working with my father who complains about his laptop problems which relate to almost every single thing that Linux provides (complaints of bad battery life, viruses from porn, paying $500 for MS office, computer runs &quot;slow&quot;, only uses it for e-mail, etc) and he won't use Linux because there's no shiny interface and there isn't a commercial for it on television. He even goes so far as to tell me not to tell people about linux because he still thinks it's hard to use even after using gnome. I figured I should show him up by completely fooling him into thinking he's still on Windows.  I made GNOME look exactly like Vista with GNOmenu, using a custom metacity skin, and making a custom panel background image.  The only thing I can't replicate is the startup process where it just says &quot;Microsoft Corporation&quot; and a loading bar.  If I use ubuntu, can I change that image? Or is there some kind of bash script that I can do to load an image? Even a static image would work fine, he might buy it.  Thanks for any help or suggestions.

What version of Ubuntu you're using?

---

### Post by Barafu Albino Cheetah on 2010-05-25
I advice you to look carefully at Emerald windows decorator. It will allow you to simulate Aero transparancies. There is also a ready theme for it with vista-like settings. 
About boot logo - you will need to create a new plymouth theme. Never tried, but they say it is an easy thing to create one with static image.

---

### Post by pzkfw on 2010-05-25
> **hok00age said:**
> What version of Ubuntu you're using?

I'm using Debian Lenny 5.04 but if SUM is a .deb package or just a make/make install thing then there shouldn't be a problem.

---

### Post by iMattcotv on 2010-05-26
Im running 10.04 LTS.

I personally havent tried it, but I know it works for the latest version of ubuntu.

---

### Post by hok00age on 2010-05-28
> **iMattcotv said:**
> Im running 10.04 LTS.

I personally havent tried it, but I know it works for the latest version of ubuntu.

If you're using default Lucid plymouth theme, you can change the Ubuntu logo by editing image in:
```
/lib/plymouth/themes/ubuntu-logo
```

And if you want black background like M$ Windows, edit "ubuntu-logo.script" located in the mentioned folder above:
```
sudo gedit ubuntu-logo.script
```

Find these lines:
```
# Previous background colour
# #300a24 --> 0.19, 0.04, 0.14
# New background colour
# #2c001e --> 0.16, 0.00, 0.12
#
Window.SetBackgroundTopColor (0.16, 0.00, 0.12);     # Nice colour on top of the screen fading to
Window.SetBackgroundBottomColor (0.16, 0.00, 0.12);  # an equally nice colour on the bottom
```

Change the color value to 0.00, it should look like this:
```
# Previous background colour
# #300a24 --> 0.19, 0.04, 0.14
# New background colour
# #2c001e --> 0.16, 0.00, 0.12
#
Window.SetBackgroundTopColor (0.00, 0.00, 0.00);     # Nice colour on top of the screen fading to
Window.SetBackgroundBottomColor (0.00, 0.00, 0.00);  # an equally nice colour on the bottom
```

Hope it works :)

---

