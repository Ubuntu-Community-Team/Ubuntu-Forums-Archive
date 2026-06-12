---
title: "Setting a picture between login and desktop"
date: 2005-04-18
forum: Desktop Environments
---

### Post by AlP on 2005-04-18
Hi everyone,

I am currently putting a costum theme onto my Gnome. My current problem is, that I use an identical picture as background in the graphical gdm-login and as background of the desktop. After loging in the gdm-background disappears, the color choosen as the background-color of the standard-greeter gets shown, and then the bg-picture of the desktop is loaded. 

My question is, if there is any way to keep gnome/gdm form showing that color and instead "keep" my default background?

Chao,
   AlP

---

### Post by kassetra on 2005-04-19
[QUOTE=AlP]Hi everyone,

I am currently putting a costum theme onto my Gnome. My current problem is, that I use an identical picture as background in the graphical gdm-login and as background of the desktop. After loging in the gdm-background disappears, the color choosen as the background-color of the standard-greeter gets shown, and then the bg-picture of the desktop is loaded. 

My question is, if there is any way to keep gnome/gdm form showing that color and instead "keep" my default background?

Chao,
   AlP[/QUOTE]

I don't believe so.  I know you can change the color, but I don't think you can prevent your GDM image from disappearing... you might be able to get away with using the same image for your splash screen though... and then it would go GDM image ->Color (briefly)->Splash image->Background image.

---

### Post by shu on 2005-04-19
In /etc/gdm/ you'll find Init and PreSession directories. They contain 'Default' script, which is being read gdm. 

Want you probably want to do is to alter the following lines in PreSession/Default file:

```

XSETROOT=`gdmwhich xsetroot`
if [ "x$XSETROOT" != "x" ] ; then
        # Try to snarf the BackgroundColor from the config file
        BACKCOLOR=`grep '^BackgroundColor' /etc/gdm/gdm.conf | sed 's/^.*=\(.*\)$/\1/'`
        if [ "x$BACKCOLOR" = "x" ]; then
                BACKCOLOR="#76848F"
        fi
        "$XSETROOT" -cursor_name left_ptr -solid "$BACKCOLOR"
fi

```

I think you can safely comment out that whole part and instead put a simple line like this:

```

xsetroot -cursor_name left_ptr -bitmap _your_gdm_backgrund_

```

---

### Post by AlP on 2005-04-22
Thanks, your posting put me onto the right way.

I changed the PreSession/Default, but I did not use xsetroot, but xsetbg, because xsetroot can only process xbms which support only two colors, while xsetbg is capable of handling jpegs.

So thank you, now all that disturbs my gnome-startup are two white "flashes" which actually don't disturb.

---

