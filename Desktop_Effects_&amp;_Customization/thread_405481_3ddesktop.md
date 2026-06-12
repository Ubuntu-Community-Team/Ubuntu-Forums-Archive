---
title: "3ddesktop"
date: 2007-04-09
forum: Desktop Effects &amp; Customization
---

### Post by JB LARSON on 2007-04-09
HIYA

IM DYING TO SEE THIS CUBE THAT IS ALL THE HUBUB
I HAVE INSTALLED WITH SYNAPTIC 
IT BUT CANT FIQURE OUT HOW TO TURN IT ON

JEFF  THE ONE WEEK OLD NOOB:confused:

---

### Post by picpak on 2007-04-09
Hit Alt+F2; a run box should pop up. In it, type

```
3ddesk
```

and the cube should show up.

---

### Post by JB LARSON on 2007-04-09
Hiya  Picpak

No Joy On That Fix 
I Tried Run In Terminal
It Said
Xlib:    Extension "glx"  Missing On Display  ":0.0".

---

### Post by JB LARSON on 2007-04-09
Hiya Picpak

No Joy On That Fix 
I Tried Run In Terminal
It Said
Xlib: Extension "glx" Missing On Display ":0.0".

---

### Post by Masterj15 on 2007-04-10
Then it is your xorg.config or your Xfree86. (I don't know which you you have) Go into your xorg.config with nano-w in the terminal (Of course your going to have to find your xorg or youXfree86 on you computer. I think it is /etc/X11/xorg.config. So it should be 
sudo nano -w /etc/X11/xorg.config then look in your zorg and keep going download untill you see your modules extention. (where all these words Load is their. Check if you have the dri, glx, and glcore loaded if not type them in like this.

Load      glx
#Load      glcore
#Load      dri

It does not have to be in that order and they don't have to be near each other. glcore and dri do have to have the word #Load on theirs don't ask me why I just go it to work. glx does not need the # neither do the other ones that were their before this conversation.(LOL)
Hope this works for you.:)

---

