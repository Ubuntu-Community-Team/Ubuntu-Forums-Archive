---
title: "window selector applet hot key"
date: 2009-05-28
forum: Desktop Environments
---

### Post by jworr on 2009-05-28
Does anyone know of a way to activate the window selector applet with a keyboard combo?

---

### Post by longman on 2009-11-13
I am also looking for this. Is there any way to invoke window selector menu without waving the mouse?

Is there an alternative maybe? (There is similar functionality in compiz scale addons, but i can't use compiz on my machine).

---

### Post by kasdan on 2010-01-07
I would love to have this feature.  I've been searching for how to bind a keyboard shortcut to this applet and but haven't been able to figure it out.  Anybody?  Thanks.

---

### Post by hariks0 on 2010-01-07
Alt+Shift+Up Arrow

I don't know it is what you need, but hope you find it useful. Also for Keyboard bindings, follow the link at my signature.
:)

---

### Post by kasdan on 2010-01-07
Thanks for the quick reply, hariks0, but that doesn't seem to do it - in fact, nothing happens when I try that.  I like the idea of using the windows key, since it's just wasted space right now.  I'm trying to get the maximum real estate from my 5 year old 12.1" laptop and have the Window Selector applet on a hidden left panel.  I can switch workspaces with ctrl-alt-arrow, and switch windows with alt-tab, but would like to be able easily access all my open windows on all my workspaces with one key combo - without enabling desktop effects (old laptop).  Hence the reason for searching for a keyboard shortcut to open the Window Selector applet...

---

### Post by okmijn22 on 2010-01-14
I am searching for the same problem.

---

### Post by explicitly ambiguous on 2010-04-23
I found a hack that gives a shortcut key but it isn't pretty -- please devs add an option to call this handy app with the keyboard!

My workaround is to record a macro and set it as a hotkey as follows:

[LIST=1]
[*]Install xmacro.
```
sudo aptitude install xmacro
```

[*]Record and save macro.
```
xmacrorec2 > ~/.WindowSelectorMacro
```

 [LIST=2]
 [*]Select an escape key to end recording before starting to record the macro.
 [*]Mouse over the Window Selector Applet.
 [*]Press escape key to end recording.
 [/LIST]

[*]Check you have recorded correctly with
```
cat ~/.WindowSelectorMacro | xmacroplay -d 100ms $DISPLAY
```
(it took me a couple of iterations to get it working when the mouse starts at a random position on the screen...) The -d option is the delay (10ms by default) -- I needed around 100ms to get the command to work after the next step.

[*]Make a one line script with the above command in e.g.
```
echo "cat ~/.WindowSelectorMacro | xmacroplay -d 100ms $DISPLAY" > ~/.WindowSelectorCommand.bash
```

[*]Make script excutable with
```
chmod +x .WindowSelectorCommand.bash
```

[*]Associate the command 
```
bash .WindowSelectorCommand.bash
```
to a shortcut.  See [http://www.captain.at/howto-gnome-custom-hotkey-keyboard-shortcut.php]("http://www.captain.at/howto-gnome-custom-hotkey-keyboard-shortcut.php") or [http://www.codejacked.com/create-custom-keyboard-shortcuts-in-linux/]("http://www.codejacked.com/create-custom-keyboard-shortcuts-in-linux/") (they both have the same instructions).
[*]...?
[*]Profit.
[/LIST]

---

### Post by gnu.en.carlos on 2011-03-02
I-ve found a solution for keyboard navigation,

You have to 'move between panels and desktop' to the panel where is the 'Window Selector Applet' and then press F10.

In my system by default..
'Ctrl+Alt+Tab ' move between panels and desktop using popup window'
'Ctrl+Alt+Esc'  'move between panels and desktop immediatly'
Then press F10, like used on gnome-terminal to menu access.

Saludos

---

