---
title: "Customizing navigation keys for text"
date: 2009-06-10
forum: Desktop Environments
---

### Post by dansmith on 2009-06-10
I don't like the default navigation keys for text editing (keys taking me to the previous word, next word, start of line, etc.)  How do I customize them?

System->Preferences->Keyboard Shortcuts doesn't seem to have anything relevant, nor could I find anything in gconf-editor.

---

### Post by dansmith on 2009-06-24
Any suggestions?

My specific concern is that I hate having to track down the "Home" and "End" keys way up in the corner of my screen just to navigate -- at that point, I'm almost better off using the mouse.  I much prefer the shortcuts provided by Mac OS X: Command-Left for start of line, Command-Right for end of line.

---

### Post by dansmith on 2009-06-26
Looks like either nobody cares, the people that do care have just decided to deal with it, or the solution is obvious and I'm just missing it.

In any case, I've successfully made this work, and it seems to do very nicely.  My  solution is to manually introduce a GTK key binding theme.

1) Put the following in a new file named /usr/share/themes/Mac/gtk-2.0-key/gtkrc (directories will need to be created):

```
# Mac-like text editing keybindings

binding "gtk-mac-text-entry"
{
  bind "<ctrl>Left" { "move-cursor" (display-line-ends, -1, 0) }
  bind "<shift><ctrl>Left" { "move-cursor" (display-line-ends, -1, 1) }
  bind "<ctrl>Right" { "move-cursor" (display-line-ends, 1, 0) }
  bind "<shift><ctrl>Right" { "move-cursor" (display-line-ends, 1, 1) }

  bind "<ctrl>Up" { "move-cursor" (buffer-ends, -1, 0) }
  bind "<shift><ctrl>Up" { "move-cursor" (buffer-ends, -1, 1) }
  bind "<ctrl>Down" { "move-cursor" (buffer-ends, 1, 0) }
  bind "<shift><ctrl>Down" { "move-cursor" (buffer-ends, 1, 1) }

  bind "<alt>Left" { "move-cursor" (words, -1, 0) }
  bind "<shift><alt>Left" { "move-cursor" (words, -1, 1) }
  bind "<alt>Right" { "move-cursor" (words, 1, 0) }
  bind "<shift><alt>Right" { "move-cursor" (words, 1, 1) }
}

class "GtkEntry" binding "gtk-mac-text-entry"
class "GtkTextView" binding "gtk-mac-text-entry"
```2) Run gconf-editor (don't remember if I had to install this or if it was already available) and set the value of /desktop/gnome/interface/gtk_key_theme to "Mac" (the default setting is "Default").

3) Run gedit, etc to verify the behavior: ctrl-left should jump to the start of line, ctrl-right to the end; ctrl-up and ctrl-down jump to the start and end of the document; alt-left and alt-right jump one word at a time; and shift combined with any of these selects while jumping.

Note that certain applications (I think Firefox will have this issue) override the GTK key bindings, and so certain key combinations won't have the desired effect.

I had a very hard time finding good documentation about this, but here are some relevant links if anyone is interested.  I had a particularly hard time figuring out that "Left" (not "left", "leftarrow", "arrow-left", etc.) is the appropriate term for the left arrow key.

GTK resource files: [http://www.gtk.org/api/2.6/gtk/gtk-Resource-Files.html](http://www.gtk.org/api/2.6/gtk/gtk-Resource-Files.html)
GTK signals: [http://www.gtk.org/api/2.6/gobject/gobject-Signals.html](http://www.gtk.org/api/2.6/gobject/gobject-Signals.html)
"move-cursor" signal: [http://library.gnome.org/devel/gtk/2.6/GtkTextView.html#GtkTextView-move-cursor](http://library.gnome.org/devel/gtk/2.6/GtkTextView.html#GtkTextView-move-cursor)
GTK bindings (some useful text only appears in this older version of the document): [http://library.gnome.org/devel/gtk/2.15/gtk-Bindings.html](http://library.gnome.org/devel/gtk/2.15/gtk-Bindings.html)

Also look at the file /usr/share/themes/Emacs/gtk-2.0-key/gtkrc for a more comprehensive example of a key bindings theme (which can be used by setting the gconf value to "Emacs").

---

### Post by mozillalives on 2009-08-31
Thank you, I thought I was going to go mad without this.

---

### Post by kruvalig on 2010-03-16
How to select text by word? For example i press Ctrl + Shift + left left - and selet 2 word on the left from cursor, and cursor move by two word on the left.

---

### Post by alainpannetier on 2010-04-30
Dear all,

Eclipse under gtk and windows exhibit different behaviours because of this weird gtk concept of a "one word forward" move...

So I came up with the following kludge to try to mimic windows behaviour for which "move one word forward" actually means "move to the *beginning* of the next word" (resp. "one word backward" means "beginning of the previous word").

It's really a kludge because it does not work under all circumstances (e.g. beg of line and beg of buffer)... It steps 2 words forward and one backwards (playing on the fact that you need to "come from behind" to find the beginning of a word).
Here it is anyway, FWIW, if someone comes up with a better solution, please let me know (email).

binding "gtk-win-text-entry"
{
  bind "<ctrl>Left" { "move-cursor" (words, -1, 0) }
  bind "<shift><ctrl>Left" { "move-cursor" (words, -1, 1) }
  bind "<ctrl>Right" { "move-cursor" (words, 2, 0) "move-cursor" (words, -1, 0) }
  bind "<shift><ctrl>Right" { "move-cursor" (words, 2, 1) "move-cursor" (words, -1, 1) }

}

class "GtkEntry" binding "gtk-win-text-entry"
class "GtkTextView" binding "gtk-win-text-entry"

---

### Post by fredrikc on 2010-07-12
I found that for me this works better:
bind "<Control>Right" { "move-cursor" (words, 1, 0) "move-cursor" (logical-positions, 1, 0) }
bind "<Control><Shift>Right" { "move-cursor" (words, 1, 1) "move-cursor" (logical-positions, 1, 1) }

It's still a kludge but for me it works better in most cases (as is does not break at last word.).

---

