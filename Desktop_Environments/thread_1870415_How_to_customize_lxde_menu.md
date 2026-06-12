---
title: "How to customize lxde menu?"
date: 2011-10-27
forum: Desktop Environments
---

### Post by tanoloco on 2011-10-27
Hello,

I would like to know how could I **add a custom category **in lxde menu.
I already know how to add or modify applications changing .desktop entries under /usr/share/applications.

What I would like to do is to add a complete new category on the menu and choose its position, for example "My Staff" after "Office" or "My Apps" before "Accessories" and then populating it by changing .desktop entries under /usr/share/applications.

I tried to undesrtand something changing things under /etc/xdg/menus but I came to no point.

I also discovered a useful tool to edit menu called lxmed
[http://lxmed.sourceforge.net/]("http://lxmed.sourceforge.net/")
and using it I discovered I had hidden categories on my menu,
for example there's a category called "Other" which is not shown on my menu.

So: how can I (also) make visible hidden categories? Or viceversa how can I hide visible categories?

Last thing: is it possible to add sub-categories?
I mean category: Internet > subcategory: Browsers > applications: Chrome, Firefox, Opera

and so on.

Thanks for any help! :)

---

### Post by gsmanners on 2011-10-27
It's probably easier to just change the menu in leafpad. You can add a menu to the layout by inserting something into the layout like:

```
<Menuname>Faves</Menuname>
```

Then define the menu like this:

```
<Menu>
    <Name>Faves</Name>
    <AppDir>dir</AppDir>
    <Include>
	<All></All>
    </Include>
</Menu>
```

Then, any .desktop file you copy into the "dir" subfolder (of the folder where you store this .menu file) will appear in your submenu.

---

### Post by tanoloco on 2011-10-27
Thanks for your tip.

Yes: that's was my idea too, but I haven't understood which is the menu file to change.

Could you point me to the right file?
Thanks

---

### Post by gsmanners on 2011-10-27
If there isn't already a file in ~/.config/menus you should create that folder and copy one of the menus from /etc/xdg/menus into it first. Then edit the copy.

---

### Post by tanoloco on 2011-10-28
Ok, many thanks for having pointed me to the right direction.

I' ve found a working way to solve it, [COLOR="Red"]**it's a little bit tricky, so not so easy**[/COLOR], but it works.

First of all I noticed [COLOR="red"]it requires to have installed **alacarte**[/COLOR], I don't know what change this does but that's it.
_**[COLOR="RoyalBlue"]Maybe someone could explain me that, it would be great to know.[/COLOR]**_

So, for future reference, here's my *howto* to have a new main category with its sub-category on the menu:

**1.**
As said install alacarte
```
sudo apt-get install alacarte
```

**2.**
create a new file **lxde-applications.menu** under **~/.config/menus**
```
touch ~/.config/menus/lxde-applications.menu
```

edit it and add the follow:
```
leafpad ~/.config/menus/lxde-applications.menu
```
[HTML]<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>

<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/lxde-applications.menu</MergeFile>
	<Directory>lxde-menu-applications.directory</Directory>
	<!-- Read standard .directory and .desktop file locations -->
	<DefaultAppDirs/>
	<DefaultDirectoryDirs/>
	<!-- Read in overrides and child menus from applications-merged/ -->
	<DefaultMergeDirs/>
</Menu>[/HTML]

**3**
create a new file **scripts.menu** under **~/.config/menus/applications-merged/**
```
touch ~/.config/menus/applications-merged/scripts.menu
```

edit it and add the follow:
```
leafpad ~/.config/menus/scripts.menu
```
[HTML]<!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN"
"http://www.freedesktop.org/standards/menu-spec/menu-1.0.dtd">

<Menu>
	<Name>Applications</Name>
	<Menu>
		<Name>MY Scripts</Name>
		<Directory>scripts.directory</Directory>
		<Include>
			<Filename>scripts-app1.desktop</Filename>
		</Include>
		<Menu>
			<Name>Scripts Folder</Name>
			<Directory>scripts-folder.directory</Directory>
			<Include>
				<Filename>scripts-app2.desktop</Filename>
			</Include>
		</Menu>
	</Menu>
</Menu>[/HTML]

**4**
create a new file **scripts.directory** under **~/.local/share/desktop-directories/**
```
touch ~/.local/share/desktop-directories/scripts.directory
```

edit it and add the follow:
```
leafpad ~/.local/share/desktop-directories/scripts.directory
```
[HTML][Desktop Entry]
Encoding=UTF-8
Icon=utilities-terminal
Type=Directory
Name=Scripts[/HTML]

**5**
create a new png icon under
**~/.local/share/icons/**
and call it **scripts-app1.png**

**6**
create a new file **scripts-app1.desktop** under **~/.local/share/applications/**
```
touch ~/.local/share/applications/scripts-app1.desktop
```

edit it and add the follow:
```
leafpad ~/.local/share/applications/scripts-app1.desktop
```
[HTML][Desktop Entry]
Type=Application
Name=Scripts First Application
Comment=Here your comment
Exec=lxterminal %u
Icon=scripts-app1
Categories=PackageManager;GTK;[/HTML]

**7**
create a new file **scripts-folder.directory** under **~/.local/share/desktop-directories/scripts-folder.directory**
```
touch ~/.local/share/desktop-directories/scripts-folder.directory
```

edit it and add the follow:
```
leafpad ~/.local/share/desktop-directories/scripts-folder.directory
```
[HTML][Desktop Entry]
Type=Directory
Name=Scripts Folder
Icon=folder[/HTML]

**8**
create a new png icon under
**~/.local/share/icons/**
and call it **scripts-app2.png**

**9**
create a new file **scripts-app2.desktop** under **~/.local/share/applications/**
```
touch ~/.local/share/applications/scripts-app2.desktop
```

edit it and add the follow:
```
leafpad ~/.local/share/applications/scripts-app2.desktop
```
[HTML][Desktop Entry]
Type=Application
Name=Scripts Second Application
Comment=Here your comment
Exec=lxterminal %u
Icon=scripts-app2
Categories=PackageManager;GTK;[/HTML]


Then you have to refresh you lxpanel by loggin out and in again or by killing it and restarting it.
```
killall lxpanel
lxpanel
```

To complete you can use alacarte to hide/show your categories/sub-categories/elements

I still haven't worked on this to know how it does it,
maybe in the future I will investigate on it or [COLOR="Blue"]_maybe someone can help me in that_[/COLOR].

For now this works for me!
Hope this may help.

Cheers

---

### Post by gsmanners on 2011-10-28
That looks like a lot of trouble just to avoid understanding how the Layout or Include tags work. But if it works, it works. Good job. :D

---

### Post by tanoloco on 2011-10-28
I know: I will try to find a easier way.
I'll follow in testing :)

Thanks for your help

---

