---
title: "[SOLVED] compiz ati driver problems"
date: 2008-02-21
forum: Desktop Effects &amp; Customization
---

### Post by steve_d on 2008-02-21
I've recently installed the new ATI driver, using [this guide.]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

Originally I couldn't get desktop effects to work at all, then i tracked it down this being partially to blame

```

steve@workstation:~$ compiz
.: 3: Can't open /etc/xdg/compiz/compiz-manager.ubuntu

```

so I put a # in compiz-manager to stop that line from being loaded because the file doesn't exist.

```

#Updated whitelist and source Ubuntu settings

# . /etc/xdg/compiz/compiz-manager.ubuntu

# Driver whitelist
WHITELIST="nvidia intel ati radeon i810 fglrx"

```

So now I get three options for desktop effects, IE: i don't have the 'custom' option.

If i goto restricted drivers under system->admin, it tells me "Your hardware does not need any restricted drivers"

Someone correct me if I'm wrong, but I should have my ATI driver listed in there. Which I never have.

Some additional info:
```

steve@workstation:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2400 PRO
OpenGL version string: 2.1.7281 Release

```

```

steve@workstation:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:94c3 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (8192): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

and when i goto change the desktop effects, this is listed in my terminal window as if the compiz command is still running:

```

A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"
A handler is already registered for the path starting with path[0] = "org"

```

So I'm lost as to how to get custom desktop effects, and I'm really confused with all the info I've put together, and why compiz-manager.ubuntu doesn't exist, but is referenced to in /etc/xdg/compiz/compiz-manager

Any help is greatly appreciated.

If it matters at all, I tried to install these drivers the ati way using the ./<filename> which didn't work very well, and I then followed the guide I listed word for word to get to where I am now.

Thanks
-Steve

---

### Post by lswest on 2008-02-21
well, about not having the custom option, you need to install compizconfig-settings-manager (i think that's the name of the package, not 100% sure)  which will add "advanced desktop effects" to the system-->preferences menu, and give you the custom option in the visual effects tab.  As to the restricted driver manager...i'm not sure

2 possibilities:  the manager doesn't recognize it as installed since you installed it elsewhere, or you installed it and it was removed from the list since it's a newer version than what was in the manager.  Also, the error about missing xgl is probably causing problems with the driver (i don't use the ATI drivers, so i'm not sure what package has those files, but someone else probably does)

---

### Post by steve_d on 2008-02-21
Wow... I totally don't remember installing that compizconfig-settings-manager seperately before, but I could be mistaken. Thanks, all those options are available now.

As far as the other issues go, I've got a smoothly rotating cube now, so I don't think its really a problem... I'm sure it will surface again though...

thanks again

---

### Post by lswest on 2008-02-21
no problem, glad you've got your eye-candy back now^^ don't forget to mark the thread as [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") so others know it's been solved^^

---

