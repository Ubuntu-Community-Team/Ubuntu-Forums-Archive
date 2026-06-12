---
title: "auto-maximumizing of program windows"
date: 2009-05-26
forum: Desktop Environments
---

### Post by linesma on 2009-05-26
I am running 9.04 NBR on my Asus Eeepc 900HA, and I absolutely love it.  I ended up switching to the standard-look desktop (gnome) because I prefer it to the normal NBR interface.  I stay with the NBR version, because it is optimized for the hardware on the netbook.  

There is one setting that I have not been able to figure out how to change.  When I open a program, it opens in what appears to be a full screen window.  When I try to resize it smaller, it will not let me.  How can I go about changing this behavior?  It is a minor, but for me an annoying, problem.

Thanks,

linesma

---

### Post by ugm6hr on 2009-05-26
Do you want to turn off the auto maximize function?  If so, just remove maximus:

```
sudo apt-get remove maximus
```

You should be able to resize windows once launched without removing maximus: just unmaximize and then resize as normal.

If you want some applications to launch maximized, and others in a normal window, you need to manually select the applications not to maximize from gconf-editor (be careful - this can mess up your Gnome desktop if you change the wrong setting):
```
sudo apt-get install gconf-editor
```
Open Applications -> Other -> Configuration Editor
Select apps -> maximus
Right-click "exclude_class" -> Edit Key
Click Add
Type in the application executable name of the programs you want to be launched in a normal size: e.g. totem, gnome-terminal, nautilus etc
I think the undecorate option is what removes the window borders when maximized, meaning you can't resize some windows.  However, I have never tried changing it to false.

---

### Post by linesma on 2009-05-26
> **ugm6hr said:**
> Do you want to turn off the auto maximize function?  If so, just remove maximus:

```
sudo apt-get remove maximus
```

You should be able to resize windows once launched without removing maximus: just unmaximize and then resize as normal.

If you want some applications to launch maximized, and others in a normal window, you need to manually select the applications not to maximize from gconf-editor (be careful - this can mess up your Gnome desktop if you change the wrong setting):
```
sudo apt-get install gconf-editor
```
Open Applications -> Other -> Configuration Editor
Select apps -> maximus
Right-click "exclude_class" -> Edit Key
Click Add
Type in the application executable name of the programs you want to be launched in a normal size: e.g. totem, gnome-terminal, nautilus etc
I think the undecorate option is what removes the window borders when maximized, meaning you can't resize some windows.  However, I have never tried changing it to false.

If I remove Maximus, will that prevent me from switching back over to the NBR interface?  I use that interface for guest accounts.  It is easier for non-Linux users to use.

Thanks,

linesma

---

### Post by MuddBuddha on 2009-05-26
No, it won't.  I run the Netbook interface without Maximus.  You can also remove it from the start-up applications so uninstall is not necessary.

Go to Preferences>Startup Programs and uncheck the Mamximus block.

That's the easiest way.

---

### Post by linesma on 2009-05-26
Thank you both for your replies to my question.  I uninstalled Maximus and now everything works as it should.  I will have to add this to my list of things to remember.

linesma

---

### Post by MuddBuddha on 2009-05-26
Glad it worked out for you.

I didn't care much for Maximus myself.  I'm sure there are those who like it, but I just didn't see the point.

---

