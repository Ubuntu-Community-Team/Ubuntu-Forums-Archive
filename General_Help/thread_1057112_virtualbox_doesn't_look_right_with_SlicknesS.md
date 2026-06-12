---
title: "virtualbox doesn't look right with SlicknesS"
date: 2009-02-01
forum: General Help
---

### Post by Dark Aspect on 2009-02-01
Hello

The latest version of virtualbox whites out a large part of the text when using the [SlicknesS theme]("http://www.gnome-look.org/content/show.php/SlicknesS?content=71993"). My other applications don't do that with SlicknesS, any idea why this is happening?

Human-Clearlooks:

[IMG]http://img87.imageshack.us/img87/1831/screenshotsunxvmvirtualfy1.png[/IMG]

SlicknesS

[IMG]http://img134.imageshack.us/img134/4686/screenshotsunxvmvirtualkc0.png[/IMG]

Thanks for any ideas.

---

### Post by hajbal92 on 2009-02-01
Hello I am looking for some VirtualBox help...
I made my slot for a WinXP. The install goes well, but when I try to install my NVidia Driver it says wrong hardware configuration... I know that this is the right driver.. I am using NVidia 8600GTS it works well in ubuntu and in non-Virtualised Windows...

p.s sorry for my englishD: :popcorn::-({|=

---

### Post by Dark Aspect on 2009-02-01
> **hajbal92 said:**
> Hello I am looking for some VirtualBox help...
I made my slot for a WinXP. The install goes well, but when I try to install my NVidia Driver it says wrong hardware configuration... I know that this is the right driver.. I am using NVidia 8600GTS it works well in ubuntu and in non-Virtualised Windows...

p.s sorry for my englishD: :popcorn::-({|=

You.......could have created another thread you know. The reason your Nvidia driver is not working is virtualbox doesn't support 3D drivers, install guest additions and your get "some" 3D.

Don't expect much in terms of gaming, however it is possible for really old games to run very slow.

---

### Post by hajbal92 on 2009-02-01
> **Dark Aspect said:**
> You.......could have created another thread you know. The reason your Nvidia driver is not working is virtualbox doesn't support 3D drivers, install guest additions and your get "some" 3D.

Don't expect much in terms of gaming, however it is possible for really old games to run very slow.

Thanks man... I dont need it for gaming but for some project testing...

---

### Post by Dark Aspect on 2009-02-01
> **hajbal92 said:**
> Thanks man... I dont need it for gaming but for some project testing...

Great, Thats wonderful

*Any idea about the GTK+ theme problem??????*

---

### Post by Tibuda on 2009-02-01
I don't think it is a Gtk+ theme problem, but a QGtkStyle problem, because VirtualBox is written in Qt. Try to use another Qt theme than QGtkStyle.

---

### Post by Dark Aspect on 2009-02-01
> **danielrmt said:**
> I don't think it is a Gtk+ theme problem, but a QGtkStyle problem, because VirtualBox is written in Qt. Try to use another Qt theme than QGtkStyle.

How do I do that, qtconfig has no affect.

---

### Post by sidny4 on 2009-02-12
edit your gtkrc file (should be either ~/.themes/SlicknesS/gtk-2.0/gtkrc or /usr/share/themes/SlicknesS/gtk-2.0/gtkrc)

You will need to change:

bg[SELECTED]    = "#ffffff" 

to 

bg[SELECTED]    = "#808080"

It should be line 70 or in that vicinity. It worked for me and I hope it works for you.

---

### Post by Dark Aspect on 2009-02-15
> **sidny4 said:**
> edit your gtkrc file (should be either ~/.themes/SlicknesS/gtk-2.0/gtkrc or /usr/share/themes/SlicknesS/gtk-2.0/gtkrc)

You will need to change:

bg[SELECTED]    = "#ffffff" 

to 

bg[SELECTED]    = "#808080"

It should be line 70 or in that vicinity. It worked for me and I hope it works for you.

Thank you, this works great. Its on line 71 and line 65.

---

### Post by andydread on 2009-05-10
I had a similar problem in Jaunty.  The menus in Virtualbox with the SlickneSS theme were too light to read because the menu bg was a light color and so was the text.   I edited the /usr/share/themes/Slickness/gtk-2.0/gtkrc and line 1256 changed to read 

From:
```
 
bg[NORMAL] = "#d9d9d9"

```

To:
```

bg[NORMAL] = "#000000"

```

---

### Post by JedMeister on 2010-08-05
Sorry to necropost but i have just run into a similar issue and would like to clarify andydread's fix (the one that worked for me) in case others find themselves in my situation and come across this thread (as I did) which contains the answer but I initially missed a vital point.

The problem is slightly different to the OP but I'm assuming the same as andydread (post above). Rather than the writing being washed out in the main window (OP problem), the menus are (ie light coloured background with light coloured text). In SlickneSS, gtk menus have black background but VBox doesn't abide (Qt rather than GTK). 

andydread's fix works but its the second instance of bg[NORMAL] you need to change. On my system (Ubuntu 10.04) there are 3 instances of bg[NORMAL] - lines 67, 1256 & 1316. The first instance has a different value (#CCCCCC) - leave that (I initially changed this one and it didn't work and I wondered why - Doh!) The other 2 have the value andydread states (#d7d7d7). I only needed to change the middle one (line 1256) to #000000.

Thanks andydread, works like a charm now!

---

