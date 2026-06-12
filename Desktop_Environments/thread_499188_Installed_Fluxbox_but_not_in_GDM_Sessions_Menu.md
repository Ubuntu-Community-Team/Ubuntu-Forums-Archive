---
title: "Installed Fluxbox but not in GDM Sessions Menu"
date: 2007-07-12
forum: Desktop Environments
---

### Post by sml on 2007-07-12
I installed Fluxbox with the usual method.
That is;
sudo apt-get fluxbox

But it does not apprear in my gdm sessions menu.

Any ideas?

---

### Post by Jagot on 2007-07-12
Are you sure you did that, or did you

```
sudo apt-get update && sudo apt-get **install **fluxbox
```

---

### Post by RedSquirrel on 2007-07-12
What Jagot suggested should work fine.

After that, run 

```
sudo update-menus
```

so that you will have a menu when you login to Fluxbox. ;)

---

### Post by sml on 2007-07-12
Opps .. typo .. I did do the apt-get install fluxbox.

I tried the update-menus .. but still fluxboxm is not an option on the gdm. After a week of struggling, I tried xfce .... with install xubutu-desktop. xfce then appeared on the menu options.

But still no luck on fluxbox :(

---

### Post by RedSquirrel on 2007-07-12
I have never had this problem.

Are you sure it installed correctly?

What is the output of:

```
dpkg -l fluxbox
```and

```
ls -l /usr/share/xsessions/
```

EDIT: By the way, the *update-menus* command has nothing to do with gdm; it's used to build your Fluxbox menu.

---

### Post by sml on 2007-07-12
sml@sml:~$ dpkg -l fluxbox
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  fluxbox        1.0~rc3-1      Highly configurable and low resource X11 Win


AND ...

sml@sml:~$ ls -l /usr/share/xsessions/
total 8
-rw-r--r-- 1 root root 2948 2007-06-27 01:08 gnome.desktop
-rw-r--r-- 1 root root 1048 2007-05-04 19:49 xfce4.desktop

---

### Post by Rui Pais on 2007-07-12
try a:
```
sudo aptitude reinstall fluxbox
```

if that fails you can manual create a fluxbox.desktop on the folder RedSquirrel mentioned

---

### Post by RedSquirrel on 2007-07-12
Well, that explains the lack of a Fluxbox entry in gdm. You have no "desktop" file in /usr/share/xsessions for Fluxbox.

Are you trying out Gutsy Gibbon? I just checked on [http://packages.ubuntu.com/gutsy/x11/](http://packages.ubuntu.com/gutsy/x11/) and they say the gutsy repositories have 1.0~rc3-1 which is the version you have installed. I guess they haven't included a desktop file for Fluxbox in gutsy yet... :(

Verify the location of the startfluxbox script with this command:

```
which startfluxbox
```

Create the file fluxbox.desktop (in your home directory is fine) and put this in it:

```
[Desktop Entry]
Name=Fluxbox
Comment=Highly configurable and low resource X11 Window manager
Exec=[COLOR=Red]/usr/bin/startfluxbox[/COLOR]
Terminal=False
TryExec=[COLOR=Red]/usr/bin/startfluxbox[/COLOR]
Type=Application

```

Make sure the lines I have highlighted in red match the output of 'which startfluxbox'.

Then you just have to copy the file to /usr/share/xsessions:

```
sudo cp fluxbox.desktop /usr/share/xsessions
```

That should give you an entry for Fluxbox in gdm.

---

### Post by RedSquirrel on 2007-07-12
> **Rui Pais said:**
> try a:
```
sudo aptitude reinstall fluxbox
```

I think he used apt-get to install it. Is it wise to mix apt-get and aptitude? I would think he should remove it with apt-get and then perhaps try aptitude. In any case, I think the Fluxbox package in gutsy is just missing the desktop file...

---

### Post by sml on 2007-07-12
Many thanks guys.

I just used RedSquirrel method above and I was up and running in 30 secs :)

---

### Post by Rui Pais on 2007-07-12
> **RedSquirrel said:**
> I think he used apt-get to install it. Is it wise to mix apt-get and aptitude? I would think he should remove it with apt-get and then perhaps try aptitude. In any case, I think the Fluxbox package in gutsy is just missing the desktop file...

No, no problem in mix (underneath the table they use dpkg and the same deb packages).

But it wouldn't work cause, as you well checked it was not a failure of install but a development version. 
Reinstall would just leave him without the desktop file.  :)

---

