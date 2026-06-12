---
title: "Natty: Appearance-&gt;Fonts won't show Tahoma"
date: 2011-07-14
forum: Desktop Environments
---

### Post by kkruecke on 2011-07-14
After going to **Appearance->Fonts**, in Natty, I changed the "Window title font" from Tahoma to "Arial Black". Now I can't change it back because Tahoma isn't listed in the "Pick a Font" dialog.  

I don't know how I originally got Tahoma. I think it did that several versions of Ubuntu ago. How do I get it to show up in the "Pick a Font" dialog? I do have ttf-mscorefonts-installer installed. Doing

```
# dpkg -L ttf-mscorefonts-installer
```

shows that they are in this directory:

```

/usr/share/fonts/truetype/msttcorefonts

```

But Tahoma is not in there? Very strange.

---

### Post by koleoptero on 2011-07-15
Tahoma isn't included in the fonts the msttcorefonts-installer pack installs. You'll have to find it from some other source and install it by copying it either to /usr/share/fonts/ or to ~/.fonts

Obviously in your case it somehow got removed at some point when the package was updated although it does seem strange.

---

### Post by kkruecke on 2011-07-15
Thanks for your reply. Evidently, they can be copied from my window partions, from c:/Windows/Fonts. But do I need to worry about ant-aliasing? This [article]("http://www.stchman.com/ms_fonts.html") (which is a bit old) says: 
> 
Get the XML scripts

Now that the fonts are installed we will **need to use the XML scripts to turn off the anti-aliasing**.  Download the scripts here.  These scripts also have quite a few aliases so that the Microsoft core fonts are used mostly.

Unpack the scripts to your /etc/fonts folder by doing the following in a terminal:

sudo tar -xvjpf fontconfig.tbz -C /etc/fonts/

---

### Post by koleoptero on 2011-07-16
Sorry for the late reply...

You don't need to no. At least my copy of tahoma doesn't look ugly or anything. A bit different than in windows perhaps, but that's better.

---

### Post by kkruecke on 2011-07-16
Thanks for the reply!

---

