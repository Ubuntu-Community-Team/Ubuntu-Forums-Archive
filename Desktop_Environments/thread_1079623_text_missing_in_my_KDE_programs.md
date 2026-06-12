---
title: "text missing in my KDE programs"
date: 2009-02-24
forum: Desktop Environments
---

### Post by Anxious Nut on 2009-02-24
I've installed Kalarm, kdenlive, and PDFeditor and as you know all of these are KDE programs, I'm running these applications on ubuntu 8.10 (Gnome). My problem is Text is missing everywhere in every KDE based program, even the text in menus... please help!!

---

### Post by Anxious Nut on 2009-02-25
... :(

---

### Post by wikwanderlust on 2009-03-29
I'm having the same problem, if anyone can help...

---

### Post by sheshdd on 2009-03-29
me too,KVirc and some other messengers don't display anything in the menus or system messages.

---

### Post by sheshdd on 2009-03-30
BUMP!

add Kmess to my list,same problem,i can't see what's in the menus

---

### Post by Anxious Nut on 2009-04-02
so everybody is suffering from the same problem .... !! 

Mine was solved somehow! I didn't do anything but it returned to it's original looking (readable) menus!! 

BTW i still want to know the answer

thanks

---

### Post by sheshdd on 2009-04-02
i still have the problem :\

---

### Post by canadiandude007 on 2009-04-03
I am trying to play around with the Fonts under Appearance to see if that improves the situation.  I know that disabling Effects clears the problem, but see that as a workaround.

---

### Post by Anxious Nut on 2009-04-03
Thanks canadiandude007, I think you've just solved the problem!!

Apparently our ubuntu 8.10 has some problems with the Visual Effects thingie and text, so if you have that problem try going to Visual effects (by pressing rightclick on desktop=>change Desktop background=>Visual Effects) and select no effects. 

I just tried it and realized that when i choose normal or advanced the text disappears but once i click on no effect the text returns, I hope it works with you.

I know Having no effects look ugly, but at least we can use it again!! 

... Thanx everybody for your help,.... a mystery have been solved, but another mystery just rose "why is this happening!?"

---

### Post by canadiandude007 on 2009-04-03
I'm using NVidia driver 96.43.09 by the way.  You might be using the same.

---

### Post by canadiandude007 on 2009-04-03
I think I found the answer:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/295991](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/295991)

So hopefully there will be an update soon in the repositories.

---

### Post by canadiandude007 on 2009-04-03
Yes I can confirm that a definite workaround is below.  This enables one to still use visual Effects, but allow the correct drawing of the menu text for KDE programs.

```

sudo gedit /etc/X11/xorg.conf

# Under the device section add:
Option "RenderAccel" "False"

# Save the xorg.conf file and exist


```

Then logout as the user and re-logon (to get the new Xorg configuration).

You should then see Effects still working, but KDE programs contain the menu text.

Again, still waiting for a bug fix for this to be included in the repositories.

---

### Post by Anxious Nut on 2009-04-03
LOL, yup it's the same one!!

---

### Post by sheshdd on 2009-04-07
i tried changing fonts and fonts appearances and still got the problem.

EDIT
i did
sudo gedit /etc/X11/xorg.conf

# Under the device section add:
Option "RenderAccel" "False"

# Save the xorg.conf file and exist

and it worked,thank you so much

---

