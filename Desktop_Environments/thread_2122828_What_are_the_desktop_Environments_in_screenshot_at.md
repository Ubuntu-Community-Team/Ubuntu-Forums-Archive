---
title: "What are the desktop Environments in screenshot attached"
date: 2013-03-06
forum: Desktop Environments
---

### Post by c2tarun on 2013-03-06
Hi friends,

In this screenshot:

[ATTACH=CONFIG]239841[/ATTACH]   Sorry I don't know why is it rotated :P

I can figure out all options, but what is GNOME Classic(No Effects)-second option, and how is it different with Ubuntu 2D?

---

### Post by ibjsb4 on 2013-03-06
If you want to see the difference in gnome-classic, just install it to your current desktop and try it.

```
sudo apt-get install gnome-session-fallback
```

Or do you have it installed?  Is that a pic of your login?

---

### Post by c2tarun on 2013-03-06
> **ibjsb4 said:**
> If you want to see the difference in gnome-classic, just install it to your current desktop and try it.

```
sudo apt-get install gnome-session-fallback
```

Or do you have it installed?  Is that a pic of your login?

Yeah that is the pic of my Login :) I was not able to find the difference between Gnome Classic (No Effects) and Ubuntu, i.e. Unity 3D. But there must be some difference right, otherwise why two different options?

---

### Post by ibjsb4 on 2013-03-06
Yes, theres a big difference.

[https://www.google.com/search?q=gnome+classic&hl=en&client=ubuntu&hs=Fgx&channel=fs&tbm=isch&tbo=u&source=univ&sa=X&ei=5mo3UeSLN4a7qgHvv4GgAQ&ved=0CEcQsAQ&biw=1024&bih=604](https://www.google.com/search?q=gnome+classic&hl=en&client=ubuntu&hs=Fgx&channel=fs&tbm=isch&tbo=u&source=univ&sa=X&ei=5mo3UeSLN4a7qgHvv4GgAQ&ved=0CEcQsAQ&biw=1024&bih=604)

[https://www.google.com/search?q=unity+ubuntu&hl=en&client=ubuntu&hs=SMI&channel=fs&tbm=isch&tbo=u&source=univ&sa=X&ei=GWs3UbifKc6_qQGt2oHQDQ&ved=0CEgQsAQ&biw=1024&bih=604](https://www.google.com/search?q=unity+ubuntu&hl=en&client=ubuntu&hs=SMI&channel=fs&tbm=isch&tbo=u&source=univ&sa=X&ei=GWs3UbifKc6_qQGt2oHQDQ&ved=0CEgQsAQ&biw=1024&bih=604)

---

### Post by c2tarun on 2013-03-06
> **ibjsb4 said:**
> Yes, theres a big difference.

[https://www.google.com/search?q=gnome+classic&hl=en&client=ubuntu&hs=Fgx&channel=fs&tbm=isch&tbo=u&source=univ&sa=X&ei=5mo3UeSLN4a7qgHvv4GgAQ&ved=0CEcQsAQ&biw=1024&bih=604](https://www.google.com/search?q=gnome+classic&hl=en&client=ubuntu&hs=Fgx&channel=fs&tbm=isch&tbo=u&source=univ&sa=X&ei=5mo3UeSLN4a7qgHvv4GgAQ&ved=0CEcQsAQ&biw=1024&bih=604)

[https://www.google.com/search?q=unity+ubuntu&hl=en&client=ubuntu&hs=SMI&channel=fs&tbm=isch&tbo=u&source=univ&sa=X&ei=GWs3UbifKc6_qQGt2oHQDQ&ved=0CEgQsAQ&biw=1024&bih=604](https://www.google.com/search?q=unity+ubuntu&hl=en&client=ubuntu&hs=SMI&channel=fs&tbm=isch&tbo=u&source=univ&sa=X&ei=GWs3UbifKc6_qQGt2oHQDQ&ved=0CEgQsAQ&biw=1024&bih=604)

No no... you got me wrong. There is obviously difference between Unity and Gnome classic. Ok, let me rephrase my question.

From that menu in screen shot, what is difference between GNOME Classic, GNOME Classic (No effects) and Ubuntu.

Try GNOME Classic (No Effects) once it looks just like Unity, with all the feature animations.

---

### Post by schragge on 2013-03-06
If you are curious what entry on the screenshot executes which command, try
```

egrep -i '^(name|exec)=' /usr/share/xsessions/*.desktop

```

---

### Post by c2tarun on 2013-03-06
> **schragge said:**
> If you are curious what entry on the screenshot executes which command, try
```

egrep -i '^(name|exec)=' /usr/share/xsessions/*.desktop

```

I was looking for some operation difference.

---

### Post by vasa1 on 2013-03-06
> **c2tarun said:**
> I was looking for some operation difference.
So basically you want to know how the different DE's differ from each other? Since you seem to have them all installed, you can see for yourself. Wouldn't that be the best solution?

---

### Post by stinkeye on 2013-03-06
Basic differences are...
**Ubuntu** uses the window manger **compiz** with the **unity plugin**(unity3d)
**GNOME Classic** uses the window manger **compiz** with the unity plugin disabled and a gnome3 compatible version of **gnome-panel**
**GNOME Classic (No effects)** uses the window manger **metacity** and a gnome3 compatible version of **gnome-panel**

**Unity2d** has a similar look and feel to  unity3d, but was written to use a slightly tweaked version of **Metacity** to run on gfx cards
that don't meet the OpenGL requirements of compiz.

---

### Post by grahammechanical on 2013-03-06
May I try to guess what you are asking about?

The Ubuntu option gives you the Unity user interface. It runs on graphic adapters that are capable of 3D effects. If a machine does not have a graphic adapter that can run Unity (3D) then it would get Ubuntu 2D = Unity 2D without special effects. This is true for Ubuntu 12.04 but from Ubuntu 12.10 onwards Ubuntu (Unity) 2D is no longer available. Another method of giving a Unity 3D experience is used for lower specified graphic adapters.

Some people did not like the look of Unity. They use Gnome Classic which is how Ubuntu used to look up to about 2 years ago. Machines that had graphic adapters that could not display 3D (special) effects would run Gnome Classic (without effects).

Openbox is a window manager that can be used on machines they do not a powerful graphic adapters and CPUs. Xfce is a desktop environment that can be run on machines that do not have powerful graphic adapters and CPUs. 

Ubuntu by default uses the Gnome Desktop Environment with the Unity user interface.

---

### Post by ibjsb4 on 2013-03-06
Stinkeye has it.  They use different window managers.  You get basic eye candy with classic-no effects (metacity window manager) and classic-w/compiz you can have max eye candy (even the cube).

[https://www.google.com/search?client=ubuntu&channel=fs&q=gnome+cube&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=gnome+cube&ie=utf-8&oe=utf-8)

---

### Post by c2tarun on 2013-03-06
> **stinkeye said:**
> Basic differences are...
**Ubuntu** uses the window manger **compiz** with the **unity plugin**(unity3d)
**GNOME Classic** uses the window manger **compiz** with the unity plugin disabled and a gnome3 compatible version of **gnome-panel**
**GNOME Classic (No effects)** uses the window manger **metacity** and a gnome3 compatible version of **gnome-panel**

**Unity2d** has a similar look and feel to  unity3d, but was written to use a slightly tweaked version of **Metacity** to run on gfx cards
that don't meet the OpenGL requirements of compiz.

This answers my question :) Thanks, I'll mark this thread as solved.

---

