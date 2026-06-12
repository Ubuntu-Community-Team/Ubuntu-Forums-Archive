---
title: "Theme strange, plain background, keyboard remapped."
date: 2008-07-19
forum: Desktop Environments
---

### Post by notyetroot on 2008-07-19
Not long ago I installed the Enlightenment WM. After deciding to uninstall it and change back to GNOME, the theme changed. Now instead of the brown human theme, I have a blue bar at the top of the windows (changing themes does make a difference, but the blue bars stay), and the background is stuck at plain brown, although Ubuntu thinks otherwise. Also, my keyboard appeared to have remapped itself, which is annoying.

On top of that, I cannot log on if I don't use the fglrx drivers.

I have Compiz installed if that makes a difference. All the effects still work.

Any advice?

---

### Post by pauper on 2008-07-20
Are you referring to Gnome themes, such as Clearlooks, Crux, Human?
In Theme tab press Customize, then choose Colors. At "Selected items" field
click on colored button and pick another color.
An alternative way: instead of Colors open Controls tab and choose any other
theme you like.

If nothing of that seems to work try reinstalling ubuntu-artwork,
ubuntu-desktop, human-theme packages.

Regarding drivers, maybe try VESA instead of fglrx.
Note: Back up your current xorg.conf

```
sudo cp /etc/X11/xorg.conf{,.bak}
```

Then create new xorg.conf
```
sudo dpkg-reconfigure xserver-xorg
```

[Edit:] Run these commands anyway just to check your keyboard layout.

---

### Post by notyetroot on 2008-07-20
No, the themes are set to the default brown in the colour tab, they just show up as blue. Ubuntu-desktop, ubuntu-artwork etc, seemed to have uninstalled themselves, probably because of Enlightenment, but reinstalling them made no difference. 

Instead of the shutdown button in the corner, I have a fire exit sign, in case that helps. Could it be bulletproofx? I don't have any warning messages.

Reconfiguring the X server helped with the keyboard. 

Another possibly related problem: When starting Firefox I have to set the Google Toolbar options over again (Enable or disable pagerank). Related?

I found this in the syslog:
Jul 20 11:03:58 localhost kernel: [   78.478360] glxinfo[6561]: segfault at 00000200 eip b7f1ebad esp bff49760 error 4
Jul 20 11:03:58 localhost kernel: [   78.493357] glxinfo[6567]: segfault at 00000200 eip b7fbbbad esp bff8d540 error 4
Jul 20 11:03:58 localhost kernel: [   78.538426] glxinfo[6573]: segfault at 00000200 eip b7f3dbad esp bfafd0b0 error 4
Jul 20 11:03:58 localhost kernel: [   78.577019] glxinfo[6590]: segfault at 00000200 eip b7fb3bad esp bfe3c3f0 error 4

Is that related? Any help appreciated.

---

### Post by pauper on 2008-07-20
I guess there are some Enlightenment config files left behind. When you
uninstall it did you use "apt-get remove --purge package" in CLI or "Mark for
Complete Removal" in Synaptic?

What is your current window manager? Did you have the same logout button in
Enlightenment?
Try this: Switch to TTY (Ctrl+Alt+F2), log in.

```
sudo apt-get remove --purge ubuntu-artwork ubuntu-desktop human-theme
```
```
sudo apt-get remove --purge enlightenment enlightenment-data
```

Note: Plus all enlightenment-theme-* packages, if any.

```
sudo apt-get install ubuntu-artwork ubuntu-desktop human-theme
```

Switch back to X session--Ctrl+Alt+F7.

I doubt that Google Toolbar has any correlation to desktop environment. I'm not
familiar with page rank feature--can't help you here.

---

### Post by notyetroot on 2008-07-21
No difference, except that now I have to reinstall wicd :)
Unless there happens to be a difference between apt-get purge (what I used)
and apt-get remove --purge.

Is the updating initramfs part a vital part of the installlation? Since I removed a newer kernel without uninstalling the packages, so it generates an initramfs for a nonexistant (newer) kernel.

I'll try again after compiling a new kernel...

Edit: Window manager is Compiz (default), so I don't think that would be it. Is it worth trying Metacity just to be sure?

---

### Post by pauper on 2008-07-21
```
cat $HOME/.gconf/desktop/gnome/interface/%gconf.xml
cat $HOME/.gconf/desktop/gnome/background/%gconf.xml
cat $HOME/.gconf/desktop/gnome/applications/window_manager/%gconf.xml
```

Are you running compiz with emerald? Try changing emerald theme. The thing is
that when you running compiz _some_ changes, like title bar color, done to
metacity theme won't be seen unless you turn off the former one.

---

### Post by notyetroot on 2008-07-21
I don't use Emerald, and Synaptic agrees.

Command 1:
<?xml version="1.0"?>
<gconf>
        <entry name="can_change_accels" mtime="1215018919" type="bool" value="false">
        </entry>
        <entry name="icon_theme" mtime="1216466472" type="string">
                <stringvalue>Human</stringvalue>
        </entry>
        <entry name="gtk_theme" mtime="1216466472" type="string">
                <stringvalue>Human-Clearlooks</stringvalue>
        </entry>
</gconf>

Command 2:
<?xml version="1.0"?>
<gconf>
        <entry name="primary_color" mtime="1216549920" type="string">
                <stringvalue>#8f8f539b1c1c</stringvalue>
        </entry>
        <entry name="secondary_color" mtime="1216549920" type="string">
                <stringvalue>#8f8f4a4a1c1c</stringvalue>
        </entry>
        <entry name="color_shading_type" mtime="1216549920" type="string">
                <stringvalue>solid</stringvalue>
        </entry>
        <entry name="picture_options" mtime="1216549920" type="string">
                <stringvalue>zoom</stringvalue>
        </entry>
        <entry name="picture_filename" mtime="1216549920" type="string">
                <stringvalue>/usr/share/backgrounds/warty-final-ubuntu.png</stringvalue>
        </entry>
</gconf>

Command 3:
<?xml version="1.0"?>
<gconf>
        <entry name="current" mtime="1216658899" type="string">
                <stringvalue>/usr/bin/compiz</stringvalue>
        </entry>
        <entry name="default" mtime="1215014735" type="string">
                <stringvalue>/usr/bin/compiz</stringvalue>
        </entry>
</gconf>

---

### Post by pauper on 2008-07-21
Disable Compiz and then try changing colors in metacity.

By the way mine gnome/interface/%gconf.xml has "gtk_color_scheme" entry.
See attachment.

---

### Post by notyetroot on 2008-07-22
Disabling Compiz makes no difference. Using your gconf.xml made no difference (original definately had no gtk_color_scheme entry, and yes, I have backed it up). 

Note: Some themes work correctly, but many including the "human" set of themes do not. For example, the "high contrast inverse" themes display as advertised.

Edit: Some windows do not display correctly. For example, sometimes there are no close, minimize, maximize buttons,
and the console never has the drop down menus.

---

### Post by pauper on 2008-07-22
> (original definately had no gtk_color_scheme entry, and yes, I have backed it up).

You right about that. I run default human theme--no "gtk_color_scheme" value.
But the theme I'm using is quite customized, so that explains this value
appearance.

---

### Post by notyetroot on 2008-07-22
Maybe some other (custom) themes work? If all else fails, Intrepid Ibex is only around the corner anyway.

Edit: Using Emerald to hide some of the differences.

---

