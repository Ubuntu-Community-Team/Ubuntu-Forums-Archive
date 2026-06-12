---
title: "adding cut/copy/paste icons to nautilus toolbar"
date: 2005-05-13
forum: Desktop Environments
---

### Post by 23meg on 2005-05-13
i wonder if it would be possible in some way to add cut, copy and paste icons to the nautilus toolbar. for repeated file copying/moving, the context menus are a bit clumsy, and former mac os/windows users would be able to get back to their habit of using toolbar icons. this probably would only be possible by modifying source code, right?

i've made a mock image to illustrate this, see the attachment.

---

### Post by ow50 on 2005-05-13
$ sudo gedit /usr/share/nautilus/ui/nautilus-navigation-window-ui.xml

Have the toolbar section look like:
```
<toolbar name="Toolbar">
	<toolitem name="Back" action="Back"/>
	<toolitem name="Forward" action="Forward"/>

	<toolitem name="Up" action="Up"/>
	<toolitem name="Stop" action="Stop"/>
	<toolitem name="Reload" action="Reload"/>
	<separator/>
	<toolitem name="Home" action="Home"/>
	<toolitem name="Computer" action="Go to Computer"/>
	<separator/>
	<toolitem name="Cut" action="Cut"/>
	<toolitem name="Copy" action="Copy"/>
	<toolitem name="Paste" action="Paste"/>

	<placeholder name="Extra Buttons Placeholder">
		<placeholder name="Extension Actions"/>
	</placeholder>
</toolbar>
```

---

### Post by Alexander Kirillov on 2005-05-13
[QUOTE=23meg]i wonder if it would be possible in some way to add cut, copy and paste icons to the nautilus toolbar. for repeated file copying/moving, the context menus are a bit clumsy, and former mac os/windows users would be able to get back to their habit of using toolbar icons. this probably would only be possible by modifying source code, right?

i've made a mock image to illustrate this, see the attachment.[/QUOTE]
 As you know, it is also possible to use Ctrl-C/Ctrl-V shortcuts for copying files. Faster than both context menus and icons. Of course, it does not quite eliminate the need for icons...

---

### Post by yanik on 2005-05-13
Is there a place I could get all the possible buttons I can add this way?

thks

---

### Post by ow50 on 2005-05-13
[QUOTE=yanik]Is there a place I could get all the possible buttons I can add this way?[/QUOTE]
Just look at the other xml files in /usr/share/nautilus/ui/. You can try to put any menuitems to the toolbar as well. Note that all menuitems might not have icons or tooltips defined, which will make them unsuitable for toolbar.

---

### Post by 23meg on 2005-05-13
excellent!  thanks a lot. i'll now experiment with menu items.

---

### Post by 23meg on 2005-05-14
i noticed that after doing this the back button on the toolbar shrinked to about half the size of the forward one. any way to remedy this?

---

### Post by MaX on 2005-05-15
[QUOTE=23meg]i noticed that after doing this the back button on the toolbar shrinked to about half the size of the forward one. any way to remedy this?[/QUOTE]
 Why do you want to do this?
Just change to allways in browser mode in gconf-editor.
Then you have you'r toolbar.

---

### Post by 23meg on 2005-05-15
[QUOTE=MaX]Why do you want to do this?
Just change to allways in browser mode in gconf-editor.
Then you have you'r toolbar.[/QUOTE]

well, i already have my toolbar, and i'm already working in "always open in browser windows" mode.

another question: is it possible to remove text labels from the icons, and just have graphics?

---

