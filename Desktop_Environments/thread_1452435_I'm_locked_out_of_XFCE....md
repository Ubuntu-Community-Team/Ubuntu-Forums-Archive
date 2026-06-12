---
title: "I'm locked out of XFCE..."
date: 2010-04-11
forum: Desktop Environments
---

### Post by SantaFe on 2010-04-11
Don't know quite how this happened, well yes I do.  I was logged into my XFCE session, and decided to try to change the window decoration at the top of each window, was tired of the default & wanted to see different ones.

So anyway I went into Window-Manager and clicked on the first one shown.  Didn't like that one so I clicked on two more.  The fourth one I clicked on suddenly made my Ubuntu 10.04 LTS Beta 2 system reboot.  Not only that, after I entered my login info,  it reboots right after the splash screen (the one with the spinning cog & the mouse running inside it) finishes.  PooP, back to the Dell boot up screen then the Login screen.  Lucky for me GNOME was still an option so I chose that, and ran Synaptic to see if perhaps removing XFWM and the Xubuntu packages & reinstalling them would work.

Sadly it still dies after the XFCE splash screen, but now it goes right to the login screen.:(

Should I just go back into Synaptic & remove everything connected to XFCE & then repick them?  Or is there some text file that has the window manager themes listed & hopefully a backup of the original one in case the one I picked was one I added instead of a system supplied one?:confused::D

---

### Post by Simian Man on 2010-04-11
This has happened to me when creating my own Xfwm themes.  It's possible to segfault the window manager with a badly done theme.  I'm kind of shocked that Xubuntu came with such a bug however.

There is a text file somewhere under ~/.config that stores your current xfwm theme.  I am away from my Linux machine now, but I will post the location tomorrow if nobody has by that time.

---

### Post by MooPi on 2010-04-11
Found the .config file. ```
~/.config/xfce4/xconf/xfce-perchannel.xml/xsettings.xml
``` Login to recovery mode and edit this xml.

---

### Post by Simian Man on 2010-04-12
Actually the file MooPi gave contains the information for your Gtk+ theme, not your xfwm window manager theme.  Edit the following file instead:

```
~/.config/xfce4/xfconf/xfce-perchannel-xml/xfwm4.xml
```

And find this line:
```
 <property name="theme" type="string" value="Simian"/>
```

Where value is equal to the window theme you chose which broke everything.  Change it to some safe theme which you have installed.  I don't know which themes Xubuntu comes with as I'm using Fedora, but you can do:
```
ls -l /usr/share/themes/* | grep -B 3 xfwm
```

Which will list all of the themes you have installed which come with an xfwm theme.  You can try "Xfce", "Sassandra", or "Redmond" which will probably be there.

---

### Post by SantaFe on 2010-04-12
Hmmmm.... used root terminal & tried this:
```

root@santafe-desktop:~# 
root@santafe-desktop:~# cd ~/.config/
root@santafe-desktop:~/.config# ls
enchant  qtcurve  Trolltech.conf
root@santafe-desktop:~/.config# 


```
Can't seem to find /XFCE4/ anywhere.  Somethings messed up.  May just reinstall the Xubuntu 10.04 Beta2 cd I burned & try again. 

Thanks for the ideas though. :)

---

### Post by Simian Man on 2010-04-12
You shouldn't do that as root.  When root cd's into "~" it will go into roots home directort (/root) which is not where **your** user settings are stored.  Do those commands as your non-priveleged user and you should find it.

---

### Post by SantaFe on 2010-04-12
> **Simian Man said:**
> You shouldn't do that as root.  When root cd's into "~" it will go into roots home directort (/root) which is not where **your** user settings are stored.  Do those commands as your non-priveleged user and you should find it.

Okay, thanks.  But the point is kinda moot.  While I was in GNOME I was looking in /usr/bin/ & found xfce4-settings-manager, which I right clicked on & picked Execute. Up popped the XFCE Settings window which had the Window Manager icon.  Needless to say I was ecstatic. :lolflag:   Picked one I KNEW worked and am back up.  Why didn't I think of this in the first place? ;)  So I guess this one can be called Solved.

---

### Post by Simian Man on 2010-04-12
> **SantaFe said:**
> Okay, thanks.  But the point is kinda moot.  While I was in GNOME I was looking in /usr/bin/ & found xfce4-settings-manager, which I right clicked on & picked Execute. Up popped the XFCE Settings window which had the Window Manager icon.  Needless to say I was ecstatic. :lolflag:   Picked one I KNEW worked and am back up.  Why didn't I think of this in the first place? ;)  So I guess this one can be called Solved.

Ha ha, that is an easier solution isn't it?

---

