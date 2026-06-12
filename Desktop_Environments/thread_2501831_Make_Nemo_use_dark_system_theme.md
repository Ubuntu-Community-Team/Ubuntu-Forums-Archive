---
title: "Make Nemo use dark system theme"
date: 2024-10-22
forum: Desktop Environments
---

### Post by davetheoldcoder on 2024-10-22
Ubuntu 24.04.1
Gnome 46.0

I've installed the Nemo 6.0.2 file manager because I prefer it to Nautilus. (It's part of the Cinnamon desktop environment, but I didn't install Cinnamon.)

I installed Nemo using synaptic (package name: nemo).

Is there a way to get Nemo to use the system dark theme?

I've searched for an answer, but haven't found a good one.

---

### Post by 1fallen on 2024-10-22
I'm Guessing here, but will this work?
```
gsettings set org.gnome.desktop.interface color-scheme 'prefer-dark'
```
If not you might have to 
Navigate to your home directory:
   ```
cd ~
```
  Create a new file called settings.ini inside of the GTK 4 directory:
   ```
nano ~/.config/gtk-4.0/settings.ini
```
  Enter the following fields into the configuration file:
  ```
[Settings]
gtk-application-prefer-dark-theme=1
```
  Write the changes to disk by pressing control + x, then press y, then enter.

I hope that still works, I haven't used Gnome for over 10 years now I might have a little rust setting in....LOL

---

### Post by davetheoldcoder on 2024-10-22
> **1fallen2 said:**
> ```
gsettings set org.gnome.desktop.interface color-scheme 'prefer-dark'
```

That is already set.

> $ gsettings get org.gnome.desktop.interface color-scheme
'prefer-dark'

The dark theme works correctly in general, including in Nautilus.

It's only Nemo that doesn't use the theme.

Before I try the second method (settngs.ini), these warning messages from Nemo seem relevant:

> ** (nemo:68461): WARNING **: 14:12:46.458: Current gtk theme is not known to have nemo support (HighContrast) - checking...

** (nemo:68461): WARNING **: 14:12:46.483: The theme appears to have no nemo support.  Adding some...

Maybe I need to find a dark theme that Nemo supports. Any ideas on how to do that?

---

### Post by 1fallen on 2024-10-22
Well dang @davetheoldcoder it works on my end.
Again no Gnome here.

Are these shown when trying my 2nd suggestions?
```
** (nemo:68461): WARNING **: 14:12:46.458: Current gtk theme is not known to have nemo support (HighContrast) - checking...

** (nemo:68461): WARNING **: 14:12:46.483: The theme appears to have no nemo support.  Adding some...
```

```
 apt policy nemo
nemo:
  Installed: 6.0.2-2
  Candidate: 6.0.2-2
  Version table:
 *** 6.0.2-2 500
        500 http://us.archive.ubuntu.com/ubuntu plucky/universe amd64 Packages
        100 /var/lib/dpkg/status

```
I'm on XFCE

---

### Post by davetheoldcoder on 2024-10-22
I tried adding that settings.ini file, but it had no effect. And the warning messages still appear.

I tried logging out and in to reset the desktop, but that didn't help.

---

### Post by 1fallen on 2024-10-22
Can or will you try this, To circumvent this, add the selected theme into your ~/.profile or ~/.bash_profile:

```
export GTK_THEME=<MyFavoriteTheme>
```
Yes include the real theme name and leave off "<>"
and restart your session (log out/in)

BTW is Nemo a snap?

---

### Post by davetheoldcoder on 2024-10-22
I installed Nemo using synaptic (package name: nemo).

**Nemo is now using the dark theme!**

I'm not sure if it was your last suggestion, or if one of the earlier ones kicked in. I'll try to figure that out later.

Thanks for your help.

---

### Post by 1fallen on 2024-10-22
Well it was the last one "export" and to test that theory you can remove>>" ~/.config/gtk-4.0/settings.ini"
I'll bet it still works after.

---

