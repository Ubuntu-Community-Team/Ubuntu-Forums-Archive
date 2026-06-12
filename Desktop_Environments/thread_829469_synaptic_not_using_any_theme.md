---
title: "synaptic not using any theme"
date: 2008-06-14
forum: Desktop Environments
---

### Post by of_darkness on 2008-06-14
I cant change the look of synaptic, i have tried symlinking my user setting to my root as described as working in a closed hardy heron dev  tread, but it is not working, nethier is starting systemsetting as root and chenge to qt or any other gnome theme that i have..

only if i run  gnome-settings-daemon does it work, but as gnome-settings-daemon is a huge  mem consuming deamon it is not a valid alternative.. 100k of mem is a bit to mouch for only synaptic..

i have the gtk-qt-engine installed.

---

### Post by p_quarles on 2008-06-14
Not being a Gnome or Synaptic user myself, I can't easily test this, but I believe this should work. Create a new launcher, and use the following as the command:
```
gksu -k synaptic
```
The "-k" option for gksu preserves the $PATH and $HOME variables from the current user, so it should retain the various GUI settings you want.

---

### Post by urukrama on 2008-06-15
You can set a Gtk theme, icons, and font in the /root/.gtkrc-2.0 file (create one if you don't have one). Add the following to that file:
> 
	style "Sans"
	{
	font_name = "Sans 10"
	}
	widget_class "*" style "Sans" 

	gtk-font-name = "Sans 10"

        gtk-theme-name="Human"
	gtk-icon-theme-name = "Human"

Replace 'Sans' and 'Human' with whatever font, Gkt theme and icon set you want to use.

All your applications launched as root (sudo/gksudo) will follow these theme settings. The changes won't be made on the fly, though: if you have any applications running as root you'll have to restart those to make them follow these theme settings.

The fonts, icons and Gtk theme you want to use have to be installed systemwide (in /usr/share/), not in your home directory.

**p_quarles**: I tried that in Openbox, but it didn't work.

---

### Post by euclidean on 2008-06-15
This was noticed by other people as well:
[http://ubuntuforums.org/showthread.php?t=637729](http://ubuntuforums.org/showthread.php?t=637729)

However, I don't think symlinking in the root dir is recommended.


The simple fix for root applications not using the proper theme seems to be here:
[http://ubuntuforums.org/showthread.php?t=811752](http://ubuntuforums.org/showthread.php?t=811752)

I quote (credit to onlineapps):

1. Install gtk-chtheme (sudo apt-get install gtk-chtheme
2. Run gtk-chtheme as root (sudo gtk-chtheme
3. Select Qt, Apply, and hit OK
4. You may have to reboot for changes to occur
5. Open Synaptic as root

---

### Post by of_darkness on 2008-06-15
ohh hay it workt:) i just copyed my user .gtkrc-2.0 too /root/gtkrc-2.0

```
sudo cp -v $HOME/.gtkrc-2.0 /root/gtkrc-2.0
```

---

### Post by nvivo on 2008-06-29
I guess you meant:
```

sudo cp -v $HOME/.gtkrc-2.0 /root/.gtkrc-2.0
```

---

### Post by meho_r on 2009-06-01
To revive an old thread. As noted above, copying .gtkrc-2.0 to /root solved problem with style for Synaptic in KDE4, but is there any way to retain icons too? For unified look, I downloaded Oxygen icon pack for Gnome and applied it, but every time I log in KDE4, icons in Nautilus are reverted to Gnome default set. Any ideas?

---

### Post by surajitray on 2009-12-18
>  sudo cp -v $HOME/.gtkrc-2.0 /root/.gtkrc-2.0 

worked for me ... thanx

---

