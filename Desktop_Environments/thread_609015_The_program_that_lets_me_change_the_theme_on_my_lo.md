---
title: "The program that lets me change the theme on my login screen has DISAPPEARED!"
date: 2007-11-10
forum: Desktop Environments
---

### Post by Les_Caesars on 2007-11-10
...from my menu, anyway.

A while ago, I switched from kubuntu to ubuntu. And Just now I switched back. However, I'm STILL logging in from that awkward blue kubuntu scheme. How do I go back to the good 'ol orange ubuntu theme?

I'm using an updated install of Gutsy Gibbon RC (NOT the final release, originally), and "Login screen" does not seem to have been added to the Admin menu.

I've also tried running #gdmsetup itself, but I get this error:

```
GDM is not running.

You might be using a different display manager, such as KDM (KDE Display Manager), CDE login (dtlogin), or xdm. If you wish to use this feature, then your system will need to be configured to use GDM instead.
```


In case if it's important: I originally ran Ubuntu 7.10 RC (NOT the final release), switched to KDE, configured compiz-fusion to work in KDE (because compiz-fusion doesn't work with kubuntu by default), and eventually stopped using KDE session and went back to gnome.

---

### Post by Happy_Man on 2007-11-10
First: ```
sudo dpkg-reconfigure kdm
``` Choose gdm there, and then press ctrl-alt-backspace. gdmsetup will work now.

---

### Post by Les_Caesars on 2007-11-10
Ah! That command, with a little bit of fidgiting makes it work now. Thank you very much



Important note for anyone else who might have the same problem:

The above command did not work immediately..

Here's what I did to get it to work:

switch to init1 (Control Alt F1)

[Log in as myself]

```
 sudo dpkg-reconfigure kdm

```
[hit ENTER, selected GDM, and hit ENTER]

```
sudo dpkg-reconfigure gdm
```

[hit ENTER, selected GDM, and hit ENTER] 
I got an error when I entered the last command.

switch to init7, or was it init9? I just switched until I found a graphical screen (Control Alt [any f-key] )

Restart X (Control Alt Backspace)

Click the session button (paper-icon) and select "console login"

switch to init1 (Control Alt F1)

```
sudo gdm
```

---

