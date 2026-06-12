---
title: "Real Desktop in KDE 4?"
date: 2008-12-27
forum: Desktop Environments
---

### Post by mfox on 2008-12-27
The one feature I'm really unhappy with in KDE 4 is its implementation of the Desktop as a window on the display, rather than as the whole display that you see in KDE 3, Gnome, MacOS X, etc.  I much prefer the standard implementation of the Desktop, and this window approach is keeping me from adopting KDE 4.  It there any way to change this to a standard implementation?

---

### Post by jlacroix on 2008-12-27
Install KDE 4.2 Beta 2. Although it's not finished, it has an option to do this. It comes out in January.

Having a folder view on the desktop instead of traditional icons is actually really sweet anyway, once you get used to it.

---

### Post by MickS on 2008-12-27
> **jlacroix said:**
> Install KDE 4.2 Beta 2. Although it's not finished, it has an option to do this. It comes out in January.

Having a folder view on the desktop instead of traditional icons is actually really sweet anyway, once you get used to it.

+1
I didn't like it at first but now I have got used to it I much prefer it, keeps the actual desktop nice and tidy.

Mick

---

### Post by Linux Lurker on 2008-12-29
> **jlacroix said:**
> Install KDE 4.2 Beta 2. Although it's not finished, it has an option to do this. It comes out in January.

Having a folder view on the desktop instead of traditional icons is actually really sweet anyway, once you get used to it.

Me three...
Didn't quite understand the concept at first, but decided to give it a go.  It really is a decent alternative the the traditional desktop.

Depending on your needs, you can place as many "Folder View" widgets on your plasma workspace (traditional desktop area) as you like.  For example, an accountant can keep the folder with current working spreadsheets visible. Of course, they are all resizeable too.

Try it... you may get to like it, as it seems many of us have.

---

### Post by gjoellee on 2008-12-29
You can just remove the gadget and drag icons to your desktop...

---

### Post by jlacroix on 2008-12-29
> **gjoellee said:**
> You can just remove the gadget and drag icons to your desktop...

That method creates Plasmoids from the icons, it doesn't show things like folders unless you're using 4.2.

---

### Post by Dr.Suave on 2008-12-29
> **jlacroix said:**
> That method creates Plasmoids from the icons, it doesn't show things like folders unless you're using 4.2.
Maybe I've misunderstood here, but in my experience when you drag a folder to the desktop you're given the option to have it as either an icon or a folder view.

And with regards to the original poster, I can happily say that you can use a real desktop - and do some pretty cool things with it (I can't resist showing everyone a picture of my cat at this point).

---

### Post by jlacroix on 2008-12-29
> **Dr.Suave said:**
> Maybe I've misunderstood here, but in my experience when you drag a folder to the desktop you're given the option to have it as either an icon or a folder view.

And with regards to the original poster, I can happily say that you can use a real desktop - and do some pretty cool things with it (I can't resist showing everyone a picture of my cat at this point).

You are using desktop icons, but not in the traditional sense that the original poster was referring to.

When you add a desktop icon to KDE 4.x below 4.2, it makes KDE create plasmoid launchers. The difference is that the launchers are not desktop files that are in your deskop folder. For evidence of this, open your desktop folder in your home directory, and you'll see that the desktop icons that you created aren't there. They may be, but it's still not the same.

Another experiment, go to your home folder and then your desktop folder. Create several folders. Notice that after creating them, they do not appear on your desktop itself.

Now please keep in mind, KDE 4.0 had desktop icons in the traditional sense, 4.1 did not.

The desktop icons you have may be traditional ones, I could be wrong, but it won't show the contents of your Desktop folder if you create folders and/or files. Save an open office file or folders and they won't be there, unless you are using 4.0 and not 4.1.

By the way, that's a very impressive looking desktop configuration. Good job!!!!!!!!

---

### Post by Dr.Suave on 2008-12-29
> **jlacroix said:**
> You are using desktop icons, but not in the traditional sense that the original poster was referring to.

When you add a desktop icon to KDE 4.x below 4.2, it makes KDE create plasmoid launchers. The difference is that the launchers are not desktop files that are in your deskop folder. For evidence of this, open your desktop folder in your home directory, and you'll see that the desktop icons that you created aren't there. They may be, but it's still not the same.

Another experiment, go to your home folder and then your desktop folder. Create several folders. Notice that after creating them, they do not appear on your desktop itself.

Excellent refutation. I hadn't noticed that, and there is definitely a real difference. Very excited about 4.2!

---

### Post by mfox on 2008-12-30
Thanks, jlacroix, you understood what I was trying to get at with my question.  Aside from the space not being the Desktop folders, plasmoids are not folders either, at least in the way I think about folders.  With all that space around them, I find them intrusive.  Perhaps with KDE 4.2 I'll be able to look at KDE in a new light, or at least an old Desktop.  

Meanwhile, what exactly is this thing KDE 4.1 has on the screen.  Is it another folder just not called a Desktop?  Where, if anywhere in hierarchical space, does one find folders or any kind of icons put on this desktop that's not a Desktop?  :confused:

---

### Post by jlacroix on 2008-12-30
> **mfox said:**
> Thanks, jlacroix, you understood what I was trying to get at with my question.  Aside from the space not being the Desktop folders, plasmoids are not folders either, at least in the way I think about folders.  With all that space around them, I find them intrusive.  Perhaps with KDE 4.2 I'll be able to look at KDE in a new light, or at least an old Desktop.  

Meanwhile, what exactly is this thing KDE 4.1 has on the screen.  Is it another folder just not called a Desktop?  Where, if anywhere in hierarchical space, does one find folders or any kind of icons put on this desktop that's not a Desktop?  :confused:

Are you referring to the Folder View plasmoid that's on the desktop by default?

---

### Post by mfox on 2009-01-01
I guess I wasn't very clear with my question.  No, I didn't mean the folder view plasmoid, but rather the "Desktop" itself.

---

### Post by SuperSonic4 on 2009-01-01
In KDE4.2 beta you can have the desktop icons actually on the desktop, a la KDE 3.5 or windows XP if you right click the desktop -> Appearance settings -> Select Folder View from the topmost box

If you want to try kde 4.2 beta in kubuntu add the following to /etc/apt/sources list and update (sudo apt-get update)

```
deb http://ppa.launchpad.net/kubuntu-experimental/ubuntu intrepid main
deb-src http://ppa.launchpad.net/kubuntu-experimental/ubuntu intrepid main
```
```
sudo apt-get update && sudo apt-get upgrade
```

---

