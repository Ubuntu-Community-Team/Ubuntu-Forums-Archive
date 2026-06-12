---
title: "Remove the &quot;Preferences&quot; drop-down in favor of Gnome Control Center?"
date: 2005-12-20
forum: Desktop Environments
---

### Post by MetalMusicAddict on 2005-12-20
I like using Gnome Control Center. Kinda like MS Control panel but more like the OSX one. So Im wondering, whats involved, how hard would it be to make "Preferences" launch gnome-control-center instead of the drop-down menu? Maybe even rename it to Gnome Control Center or maybe just Control Center?

---

### Post by MetalMusicAddict on 2005-12-22
This falls under the "System" menu. Can it be edited?

---

### Post by hyperair on 2007-04-23
In Ubuntu Feisty Fawn 7.04 there is supposedly an option in the Alacarte Menu Editor (a.k.a "Main Menu"). Supposedly, if you go to system->preferences and check the checkbox for "Control Center" it will exchange your Preferences and Administration menus with a menu item for "Control Center". But it doesn't work for me. >.< Could someone help?

---

### Post by gapplewagen on 2007-04-25
Same here.  Enabling control center just puts that option under preferences.  I thought there was talk of using control center by default.  What happened to that?

---

### Post by phidia on 2007-04-25
It's a good question. In the beta all I had was the control center now that I've updated to final it's not there but when I searched synaptic for control center it says it's installed.

---

### Post by gapplewagen on 2007-04-26
I had control center only in Herd 4 but Herd 5 switched me back to having Preferences and Settings and final is the same.

---

### Post by scot524 on 2007-04-26
Yep, same here and it looks like changing the system menu in Gnome is pretty involved! I can't seem to find anything in the forums that will you easily make Gnome Control Centre the default.

---

### Post by mlind on 2007-04-26
Here's how:

as root user, edit **/etc/xdg/menus/settings.menu** and make <Layout> section look like this
```

<Layout>
    <Menuname>Preferences</Menuname>
    <Menuname>Administration</Menuname>
**    <Filename>gnomecc.desktop</Filename>**
</Layout>

```

then, right click ubuntu logo on top left corner (alacarte) -> Edit Menus -> System -> tick Control Center checkbox.


/edit
To make changes locally only (**safer&better**)
edit file ~/.config/menus/settings.menu (create file if it doesn't exist)

And make it look like this:
```

<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Desktop</Name>
	<MergeFile type="parent">/etc/xdg/menus/settings.menu</MergeFile>
	[B]<Include>
		<Filename>gnomecc.desktop</Filename>
	</Include>
	<Layout>
		<Filename>gnomecc.desktop</Filename>
	</Layout>[/B]
</Menu>

```

---

### Post by gapplewagen on 2007-04-26
Many thanks mlind.  I'll try this later on.  Nice to see you added the local only way too.  Do you know what happened to making this the default?

---

### Post by mlind on 2007-04-27
> **gapplewagen said:**
> Many thanks mlind.  I'll try this later on.  Nice to see you added the local only way too.  Do you know what happened to making this the default?

I guess it was dropped in favor of old System menu layout because it wasn't ready as replacement. Not sure why the entry was removed from the menu though, it used to be just hidden until Feisty final was released.

---

