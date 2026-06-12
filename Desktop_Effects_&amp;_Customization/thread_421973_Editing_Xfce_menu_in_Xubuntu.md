---
title: "Editing Xfce menu in Xubuntu"
date: 2007-04-24
forum: Desktop Effects &amp; Customization
---

### Post by kikuhi on 2007-04-24
Hi there,
        I recently installed Kubuntu on Xubuntu, and now the Xubuntu menu is messed up. :(  Xfce menu editor is not intuitive. I checked the forum, but the answer is not very clear. Is there a better way to edit menu in Xubuntu?

Thanks,
KiKuHi

---

### Post by drakos on 2007-04-27
Yeah, I'm having a similar problem trying to customize the menu. The way Xfce has the menu editor set-up you can't edit the preset list of apps. You can however open menu.xml (in the hidden folder $/.config/xfce4/desktop) as a text file and edit it manually. At the point I'm at, it looks like this:

```
<?xml version="1.0" encoding="UTF-8"?>
<xfdesktop-menu>
	<menu name="Settings" icon="gnome-settings">
		<app name="Settings Manager" cmd="xfce-setting-show" icon="gnome-settings" snotify="true"/>
	</menu>
	<separator/>
	<include type="system" style="simple" unique="true" legacy="true" visible="yes"/>
	<menu name="Accessories" icon="applications-accessories"/>
	<menu name="Games" icon="gnome-joystick"/>
	<menu name="Graphics" icon="applications-graphics"/>
	<menu name="Network" icon="applications-internet">
		<app name="Firefox" cmd="firefox" icon="/usr/share/pixmaps/firefox.png"/>
		<app name="Gaim" cmd="gaim" icon="/usr/share/pixmaps/gaim.png"/>
		<app name="Thunderbird" cmd="mozilla-thunderbird" icon="/usr/share/pixmaps/mozilla-thunderbird.png"/>
	</menu>
	<menu name="Multimedia" icon="gnome-multimedia">
               <app name="VLC Media Player" cmd="wxvlc" icon="/usr/share/pixmaps/vlc.png"/>
               <app name="Banshee Music Player" cmd="banshee --play-enqueued --enqueue" icon="/usr/share/pixmaps/banshee.xpm"/>
	       <app name="Orage" cmd="orage" icon="/usr/share/pixmaps/gnome-gnumeric.png"/>
	</menu>
	<menu name="Office" icon="applications-office">
            <app name="AbiWord" cmd="abiword" icon="/usr/share/pixmaps/abiword.png"/>
            <app name="Gnumeric" cmd="gnumeric" icon="/usr/share/pixmaps/gnome-gnumeric.png"/>
       	</menu>
        <menu name="System" icon="applications-system"/>
	<separator/>
	<app name="About Xfce" cmd="xfce4-about" visible="no"/>
	<builtin name="Quit" cmd="quit" icon="gnome-logout"/>
</xfdesktop-menu>
```

It's time consuming but you can find a list of most of the launchers found in your Apps menu in /usr/share/applications. Then it's just a matter of finding the right icon for each program. I find it slightly less annoying than trying to create launchers using the Menu Editor. Hope that helps a little.

---

### Post by Copter on 2007-07-19
Hi!

```

copter@xidgex:~/.config/xfce4/desktop$ cat menu.xml 
<?xml version="1.0" encoding="UTF-8"?>
<xfdesktop-menu>
        <menu name="Ustawienia" icon="gnome-settings">
                <app name="Ustawienia" cmd="xfce-setting-show" icon="gnome-settings" snotify="true"/>
        </menu>
        <separator/>
        <include type="system" style="simple" unique="true" legacy="true"/>
        <separator/>
        <app name="O Xfce" cmd="xfce4-about"/>
        <builtin name="Wyjd&#378;" cmd="quit" icon="gnome-logout"/>
</xfdesktop-menu>

```and my Xfce menu is still full of entries that I dont want there.

copter :]

---

### Post by clarezoe on 2008-05-04
it a very old thread, but I'll still reply, because i came here for help but not very help solutions.

Coper, I know that the entries are from this line, 
> <include type="system" style="simple" unique="true" legacy="true"/>
but I haven't found where to find the system menu, I found the menus are from these directories > 
/usr/share/applications
/usr/share/gnome/apps
/etc/X11/applnk/ #I don't have this directory
~/.local/share/applications
it's a kind of messy, really don't know how to arrange it.:KS

---

