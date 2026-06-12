---
title: "How do I completely remove/uninstall Berly?"
date: 2007-01-23
forum: Desktop Environments
---

### Post by Solidcell on 2007-01-23
It froze and now won't work as ift did before the freeze, so I want to remove every trace of it so I can do a fresh install.  A simple "apt-get remove Berly" then a "install Beryl" just puts it back to where it was before, same problem.

Thanks.

---

### Post by Stemp on 2007-01-23
after the apt-get remove did you start your computer ? is it working fine under metacity ?
glxinfo is ok ? direct rendering: Yes ?
What version of beryl are you using ? etc...

---

### Post by Solidcell on 2007-01-23
I'm not sure of the version, but I just installed it yesterday from the guide at: [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

Metacity works fine still, and everything acts fine as it did before Beryl.  Beryl's just messed up now.  I can open both the menus for Themes and Settings fine.  Themes just doesn't load up any themes when I click on one and Settings lets me swtich tabs and open drop down menus, but once I start scrolling within the main screen, it starts to leave artifacts and everything starts to look jumbled.

---

### Post by Solidcell on 2007-01-23
Actually, the menu only freezes when I'm in Desktop > Rotate Cube > General.  I can use the sliders and check boxes from every other menu (even the drop down menu right above the 'General' one still under Rotate Cube).  This blows.

All I really need is a way to get rid of all Beryl's presence on my computer so I can reinstall it and go back to how it worked when I first loaded it.

---

### Post by Stemp on 2007-01-24
> All I really need is a way to get rid of all Beryl's presence on my computer so I can reinstall it and go back to how it worked when I first loaded it.

```
sudo aptitude purge beryl
sudo aptitude purge emerald
```

---

### Post by Solidcell on 2007-01-24
I used your commands and also did:

```
emerald --replace
```

Then I went back to the wiki and followed it again, and one thing I noticed as I was going through it again, was that my xorg.conf file had some lines missing from the part I added during the last install.  Here it is as I'm supposed to add it (and as it was when it worked I assume):

```

# Enable 32-bit ARGB GLX Visuals
    Option "AddARGBGLXVisuals" "True"

# If you are using an older version of compiz that
# does not support rendering into the Composite
# Overlay Window, you will need to disable clipping
# of GLX rendering to the X Root window with this
# option, or you will get a blank screen after
# starting compiz:
    Option "DisableGLXRootClipping" "True"

```

but it had three lines being (with 2 being the options):

```

# Enable 32-bit ARGB GLX Visuals
 
# does not support rendering into the Composite
# Overlay Window, you will need to disable clipping
# of GLX rendering to the X Root window with this
# option, or you will get a blank screen after
# starting compiz:
 
```

I compared it with a backup I had and those were the only changes.

I fixed that and then continued installing and when I finished, I still have the same problems. :mad:

---

### Post by proxima estacion on 2007-01-25
Did you fix it yet? If not

do a :
rm -r ~/.beryl

it'll delete your beryl settings folder and reset the settings to default the next time u launch beryl

---

### Post by onlybui on 2007-01-26
Hi I'm having the same issue, but I tried that command rm -r ~/.berly and It didn't get restarted....

---

### Post by Solidcell on 2007-01-26
Nope, didn't do it for me either.

---

### Post by proxima estacion on 2007-01-26
hmmm If the stuff mentioned here doesnt work that exhausts my (limited) knowledge I'm afraid. Its not a great solution but my only other suggestion would be to point you towards this forum. Its specifically for installing/trouble shooting beryl. As always the people in there are pretty friendly. Its not a great answer but if it helps what the heck.

I hope its of some use:-p

[http://forum.beryl-project.org/viewforum.php?f=36](http://forum.beryl-project.org/viewforum.php?f=36)

---

### Post by onlybui on 2007-01-28
Hi I followed all these instructions here [http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia](http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia)[http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia]("http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia") not to sure what fixed it but I was playing  around with the settings and I toggled the Select Window manager and it seemed to worked again...

---

