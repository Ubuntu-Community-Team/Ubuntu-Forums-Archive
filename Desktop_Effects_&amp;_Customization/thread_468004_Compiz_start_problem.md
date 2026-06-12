---
title: "Compiz start problem"
date: 2007-06-08
forum: Desktop Effects &amp; Customization
---

### Post by Bluecircle on 2007-06-08
I'm trying to get compiz running on my 915gm graphics card. I know it will run because it worked perfectly when I had version 0.3.6, now I have 0.5.0, and I get this error:

```

brian@brian-laptop:~$ compiz --replace
compiz: GLX_EXT_texture_from_pixmap is not supported by direct rendering context, trying indirect rendering context instead
compiz: GLX_EXT_texture_from_pixmap is missing
compiz: Failed to manage screen: 0
compiz: No manageable screens found on display :0.0

```

Direct rendering is enabled

```

brian@brian-laptop:~$ glxinfo | grep directdirect rendering: Yes

```

All the titlebars disappear and I have to run metacity to fix it. Any ideas?

---

### Post by dannyboy79 on 2007-06-08
you need to remove the "dri" module from being loaded within your xorg.conf. Give that a try. So there may be a line like this within your xorg.conf file:

    Load           "dri"

It'll be towards the top of the file within this area 

Section "Module"

either delete it or put a # in the begining of it so it doesnt get loaded. I know this sounds weird but just try it, I have read that you can't use both the XGL and DRI. Also, if you have the thing about DRI at the bottom, something about 0666, then make sure that entire section is commented as well (meaning, put # at the begining of each line)

I can't tell you all this because I use Feisty's Desktop Effects (compiz) and I DON'T have anything about DRI anywhere in my xorg.conf. Good luck

---

### Post by Bluecircle on 2007-06-08
Oddly enough, my load files section is empty:

```

Section "Files"
EndSection

```

also I don't have the 0666 thing. I used to, but now it's not there, and when I reconfigure X it doesn't give me the option to.


Hmmm...

---

### Post by dannyboy79 on 2007-06-08
i didn't think I said anything about Section "Files"????

---

### Post by Bluecircle on 2007-06-08
It's where the modules are loaded. There are none at all.

---

### Post by dannyboy79 on 2007-06-08
and didn't you ever create a backup of you xorg.conf file? This is always a good idea when you get a file configured exactly how you want it and it's working great as your signature says. If you don' t have a backup of it, than I would suggest googling around or search this forum, fot other users with the same card as you. I use nvidia so I can't tell ya what to do. 

If when you ran
sudo dpkg-reconfigure xserver-xorg
than when you get to the load modules section, just hit the space bar on the ones that want to be loaded.
good luck

---

