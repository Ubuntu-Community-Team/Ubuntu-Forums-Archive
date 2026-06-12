---
title: "Changing Nautilus Keyboard Shortcuts"
date: 2007-09-28
forum: Desktop Environments
---

### Post by 23meg on 2007-09-28
There's no obvious way to change the keyboard shortcuts used by Nautilus. Is there a non-obvious one?

If not, I'd like Shift + Alt + A to act as Shift + Alt + UpArrow; it's late, my head is aching so I'm unable to RTFM, and I need to get this working ASAP so I'd love some help from someone experienced with xmodmap.

---

### Post by lisati on 2007-09-28
System->preferences->Keyboard shortcuts???????

---

### Post by 23meg on 2007-09-28
No; Nautilus keybindings aren't there. I need to change the parent folder key in spatial Nautilus.

---

### Post by Wolki on 2007-09-28
> **23meg said:**
> No; Nautilus keybindings aren't there. I need to change the parent folder key in spatial Nautilus.

Feisty and lower, go System -> Preferences -> Menus and Toolbars.
Gutsy, go System -> Preferences -> Appearance -> Interface.

Enable "Editable Keyboard shortcuts" (or similar, I'm not usre about the wording in the english version, it should be the second checkbutton)

The hover the mouse over the menu entry in the application (in your case, Nautilus -> File -> Open Parent Folder) and press the shortcut you want it to have.

Afterwards it may be a good idea to uncheck the setting (edited shortcuts should persist) to prevent changing shortcuts by accident, this is of course not necessary though.

Keyboard shortcuts in many (most? all? not sure) GNOME applications can be changed this way.

And spatial nautilus rocks 8)

---

### Post by 23meg on 2007-09-28
I've completely forgotten about this well thought out feature; thanks. 

There's a problem though: when I assign a new shortcut key combination, the old one still stays effective (that's not really a problem), but while the original shortcut closes the existing window before opening a new one, the new one doesn't. Any ideas?

Spatial Nautilus really rocks. I've been meaning to get the hang of it and stick to it for a long time; if I can overcome the few small obstacles it puts in front of people used to browser mode, I'll do it this time.

---

### Post by Wolki on 2007-09-28
> **23meg said:**
> There's a problem though: when I assign a new shortcut key combination, the old one still stay effective (that's not really a problem), but while the original shortcut closes the existing window before opening a new one, the new one doesn't. Any ideas?

Hm, you're right, parent+close-behind doesn't have a menu entry and as such can't have a custom shortcut, and just adding the shift won't trigger the shortcut anymore. I guess the shift is hardcoded for the arrow keys :-/ I recommend filing a bug, what you want to do sounds reasonable enough.

Just in case you didn't know, middle-click will also work.

(and a less-known bonus feature: close-behind will also work on files, just middle-click/alt-shift-down on them and the nautilus window closes when the application opens)

> Spatial Nautilus really rocks. I've been meaning to get the hang of it and stick to it for a long time; if I can overcome the few small obstacles it puts in front of people used to browser mode, I'll do it this time.

It requires some getting used to and some setup (mostly placing folders so that they fit together well, and removing unneeded complexity in the structure) but afterwards it's simple, powerful and quite efficient. I'm running it since warty.

---

### Post by 23meg on 2007-09-29
> **Wolki]Hm, you're right, parent+close-behind doesn't have a menu entry and as such can't have a custom shortcut, and just adding the shift won't trigger the shortcut anymore. I guess the shift is hardcoded for the arrow keys :-/ I recommend filing a bug, what you want to do sounds reasonable enough.[/QUOTE]

Right said:**
> Just in case you didn't know, middle-click will also work.

Middle click works for opening a subfolder and closing the existing folder (when no_ubuntu_spatial is set); is there a way to go to the parent folder of the folder you're viewing by middle clicking somewhere?


> **Wolki](and a less-known bonus feature: close-behind will also work on files, just middle-click/alt-shift-down on them and the nautilus window closes when the application opens)[/QUOTE]

Right said:**
> 
It requires some getting used to and some setup (mostly placing folders so that they fit together well, and removing unneeded complexity in the structure) but afterwards it's simple, powerful and quite efficient. 

And the nice thing is that you don't need to completely give up on browser mode. When you need a browser mode window temporarily, you can launch one with "nautilus --browser" (having a launcher for that command makes it easy), or right click the combo box in the lower left corner of a spatial window and click "Browse Folder".

[QUOTE=Wolki]I'm running it since warty.[/QUOTE]

It was default in Warty, wasn't it?

---

### Post by Wolki on 2007-09-29
> **23meg said:**
> Right; when things are left as default, Shift + Alt + Up does close the existing window and opens the parent, but when I explicitly set Shift + Alt + Up as a custom shortcut, it just opens the parent.

That's to be expected, since the shortcut is just for opening the parent, not for open parent+closebehind. With the default shortcut, you can get the closebehind by adding shift, but it doesn't seem work with a custom shortcut :-/

> Middle click works for opening a subfolder and closing the existing folder (when no_ubuntu_spatial is set); is there a way to go to the parent folder of the folder you're viewing by middle clicking somewhere?


Sure: Click on the button in the lower left corner, and a list with all parent folders will pop up. Middle-click a folder and that folder will open with close-behind. :)

> And the nice thing is that you don't need to completely give up on browser mode. When you need a browser mode window temporarily, you can launch one with "nautilus --spatial" (having a launcher for that command makes it easy), or right click the combo box in the lower left corner of a spatial window and click "Browse Folder".


Huh, you learn something new every day... I knew you could get the browser by right-clicking a folder, but didn't think of doing it in that combo box. Nifty. (I do think you mean nautilus --browser though :) And standard gnome has a launcher for that, Ubuntu's hiding it since moving to browser since it wouldn't make sense - places menu does the same)

I find I rarely use it, but I tend to use a terminal for messing in messy system directories anyway and for my own folders I'm more happy with spatial. I use it when for some reason I need a folder opened twice, like drag&dropping many things into different subdirectories in a very large folder - it's convenient to have one window showing the folders and another one the files you want to move.

> It was default in Warty, wasn't it?

Yeah, standard spatial in Warty, Ubuntu spatial in Hoary, browser mode since then. I used Ubuntu spatial for a long time, but it had several bugs and inconsistencies, so I moved back. Also, if I ever wanted to switch distros, i'd have to unlearn that anyway, I think no other distro uses that patch.

Ubuntu spatial was forced in and made the default very late in the release cycle, I can remember arguing to delay that change one release to fix the bugs and make it work better... makes me feel old ^^;;

I think spatial's problem was that it was advertised as a "we make it simple for the ordinary user", which, combined with people not being used to it, strengthened the "GNOME thinks we're stupid!" bias. While it's certainly simple for basic use, it requires a certain amount of control in heavy use and in exchange gives you great customizability of your environment... a power user feature, but many didn't give it a real chance because they thought it was for the "stupids".

---

### Post by Wolki on 2007-09-29
Sorry for the double-post...

OK, I found a way to redirect another keybinding to alt-shift-up. It's a bit ugly though.

You'll need to install xbindkeys and xvkbd, and for easier configuration xbindkeys-config

Start xbindkeys-config and create a new binding. You can use the get key button, then just hit the combination you want.

Then, use the following as the action:

```
/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Shift_L]\[Up]"
```

Apply, Save & Exit.

Then try it, the new keybinding should work now.

Some problems, though:
- You'll need to have xbindkeys running, so add it to your session startup
- The key combination will be available in all applications, so be careful to choose one not in use in other applications (not sure which one takes precedence though)
- It doesn't seem to work for the scroll lock key

---

### Post by zerwas on 2007-09-30
Thank you very much for this Wolki. i was also fiddling around with xbindkeys last night.

It's not the best solution though, but a usable :-).

Another idea that i came up with was to use a gtkrc file for defining the keybinding: [Blog entry]("http://www.gnome.org/~federico/news-2005-09.html#15")

I also noticed that Shift + Backspace does the same thing like Shift + Alt + Up

---

### Post by bernardobraga on 2007-10-26
hey guys. This is the closest I got to what I want, I intend to make a keyboard shortcut to "nautilus-open-terminal"... Right now, what I can do is Alt+f -> t . That opens the File tab and then I go to t for terminal. Nautilus wouldn't let me do a keybinding in that "editable shortcuts" (I was so hopeful :(  )
What I managed to do was go into nautilus-open-terminal source code and find this function:

```
static NautilusMenuItem *
open_terminal_menu_item_new (TerminalFileInfo  terminal_file_info,
			     GdkScreen        *screen,
			     gboolean          is_file_item)
{
	NautilusMenuItem *ret;
	const char *name;
	const char *tooltip;

	switch (terminal_file_info) {
		case FILE_INFO_LOCAL:
		case FILE_INFO_SFTP:
			name = _("Open In _Terminal");
			if (is_file_item) {
				tooltip = _("Open the currently selected folder in a terminal");
			} else {
				tooltip = _("Open the currently open folder in a terminal");
			}
			break;

		case FILE_INFO_DESKTOP:
			name = _("Open _Terminal");
			tooltip = _("Open a terminal");
			break;

		case FILE_INFO_OTHER:
		default:
			g_assert_not_reached ();
	}

	ret = nautilus_menu_item_new ("NautilusOpenTerminal::open_terminal",
				      name, tooltip, "gnome-terminal");
	g_object_set_data (G_OBJECT (ret),
			   "NautilusOpenTerminal::screen",
			   screen);

	return ret;
}]
```

Everything indicates that the "_" printed in "Open _Terminal" indicates where the shortcut should be (this case, T).

I'm also inclined to belive that I could create a keyboard shortcut to that aplication using bonobo event source, because I found this on nautilus-internals.pdf:
> 
6.3 Context menu item
If you want to integrate an application with the file manager you can install a context menu
component for a particular file type. This will add a menu item in the context menu for files
in the icon and list views that lets you launch your application on the file(s). The name of the
menu item can be translated.
This works by installing a component in bonobo-activation that has a boolean attribute called
nautilus:context_menu_handler set, and optionally a
nautilus:can_handle_multiple_files attribute. When the other normal
attributes of the component (bonobo:supported_mime_types,
bonobo:supported_uri_schemes, etc) matches the files selected when the context
menu is showed, all the attributes starting with nautilusverb: are read and put into the
context menu.
The attributes can look like this: (the attributes with underscores will be translated by
intltool): <oaf_attribute name="nautilusverb:DoExtract"
type="string" _value="Extract To..."/>
When the context menu item is selected the component will be activated, and the
Bonobo::Listener::event() method will be called with a sequence of the selected
URIs as arguments.
Examples of how to implement context menu plugins are available in file-roller, nautilus-cd-
burner and fontilus.


so I googled bonobo-event and found [http://library.gnome.org/devel/libbonobo/unstable/libbonobo-bonobo-event-source.html](http://library.gnome.org/devel/libbonobo/unstable/libbonobo-bonobo-event-source.html)

problem is, it's not as simple as I thought it would be.. I'll take studying their code (and they usually don't document so much, or I'm not looking in the right places)

I'll try to look into that myself, but maybe if someone here has experience with that, can help me out :-\" 
](*,)  <--what I'm feeling trying to solve this
Cheers

---

