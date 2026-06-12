---
title: "Backspace key broken in terminal"
date: 2009-04-29
forum: General Help
---

### Post by _firebug on 2009-04-29
Suddenly my backspace key does not work in the terminal. I was looking at a log and bumped the scrollback up to 10000, for a few minutes and then turned it back down,  ever since then the backspace key is messed up. :mad:  When I press it it flashes the terminal screen almost like a visual bell, and it makes the menu for the terminal disappear. Pressing it again makes the menu reappear. Very frustrating. Where are the settings for keybindings? I find a bunch of google remnants saying go to "Applications->System Tools->Configuration Manager" or somesuch thing but that's not in 8.10...

my $HOME/.gconf/apps/metacity/keybinding_commands/%gconf.xml  contains:

```

<?xml version="1.0"?>
<gconf>
        <entry name="command_window_screenshot" mtime="1237584394" type="string">
                <stringvalue>gnome-screenshot --window</stringvalue>
        </entry>
        <entry name="command_screenshot" mtime="1237584394" type="string">
                <stringvalue>gnome-screenshot</stringvalue>
        </entry>
</gconf>
```The compatability menu for terminal is set to default so backspace apparently maps to ASCII DEL and Del maps to "Escape Sequence"

Anyone know what's going on?

---

### Post by _firebug on 2009-04-29
Update: If I hit shift-backspace that seems to make a regular backspace

What gives?

---

