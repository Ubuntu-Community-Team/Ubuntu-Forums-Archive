---
title: "xfce4 wdm/gdm confusion at boot"
date: 2006-07-05
forum: Desktop Environments
---

### Post by takayuki on 2006-07-05
Hi,

just installed xfce4 and love it.  i did a server install, then 

```
sudo apt-get install wdm x-window-system-core xfce4 mozilla-firefox synaptic
```

in the terminal for a base system.  see [here]("http://https://help.ubuntu.com/community/Installation/LowMemorySystems") for low mem installs.

after installing nvidia drivers, i needed to restart wdm.  but i ignorantly restarted gdm via: sudo /etc/init.d/gdm restart

now i'm getting funky errors at startup, like: "can't find human theme..."  etc.

how can i undo this?

thanks,

takayuki

---

### Post by adwait on 2006-07-05
Press Ctrl+Alt+F1, login and use
```
sudo dpkg-reconfigure wdm
```

I think that will set wdm as your default wm

---

### Post by aysiu on 2006-07-05
You can also do ```
sudo /etc/init.d/gdm stop
```

---

### Post by takayuki on 2006-07-05
adwait and aysiu,

thanks for your replies.

well, i actually *don't* have wdm installed, i am running gdm.  :oops: 

i tried 

```
sudo dpkg-reconfigure gdm
```

but still have funkiness at boot.  it acts like it wants to boot into the brown, ubuntu gnome interface, then the log in screen has "..." in the user name, so i click cancel, then enter my user and pass and it jumps to xfce.

also had some xserver funkiness: "server is already active for display..."  I fixed that by removing /tmp/.X0-lock

any thoughts?  it's got to be a config file somewhere, but where?

thanks again for any suggestions.

takayuki

---

### Post by aysiu on 2006-07-05
Check /etc/gdm/gdm.conf

Mine has this section in it: ```
# These two keys are for the themed greeter (gdmgreeter).  Circles is the
# standard shipped theme.  If you want GDM to select a random theme from a
# list then provide a list that is delimited by /: to the GraphicalThemes
# key and set GraphicalThemeRand to true.  Otherwise use GraphicalTheme
# and specify just one theme.
**GraphicalTheme=Human**
#GraphicalThemes=circles/:happygnome
GraphicalThemeDir=/usr/share/gdm/themes/
GraphicalThemeRand=false
``` Or try this ```
sudo aptitude update
sudo aptitude install gksu
gksudo gdmsetup
``` and change the theme graphically.

---

### Post by takayuki on 2006-07-05
aysiu,

thanks.  i'll tweak the gdm conf file as you suggested.

question: what's the difference b/t installing wdm or gdm with xfce4?  does it matter?

in the low memory systems page it specifies:

```
sudo apt-get install wdm x-window-system-core xfce4 mozilla-firefox synaptic
```

thanks again,

takayuki

---

### Post by aysiu on 2006-07-05
I've never used *wdm*, but I'd imagine it takes up slightly less hard drive space. Since even my low-end computer has 20 GB of hard drive space, I never found a need to try it.

---

### Post by takayuki on 2006-07-05
Success!

I tweaked the /etc/gdm/gdm.conf-custom file per aysiu's advice.

I specified the correct gui:

```
[gui]
GtkRC=/usr/share/themes/Default/gtk-2.0-key/gtkrc
```

and i'm back to normal at login.  still wondering if it was the nvidia driver install that caused the funkiness...

thanks aysiu and adwait for your support.

takayuki

---

