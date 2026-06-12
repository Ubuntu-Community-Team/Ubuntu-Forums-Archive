---
title: "Mac-style Dvorak-Qwerty keyboard"
date: 2008-04-29
forum: Desktop Environments
---

### Post by BryceCovert on 2008-04-29
I've been a dvorak typist for about two years now, and while I love my keyboard layout, I have never been able to adjust to how frustrating one-handed tasks like Ctrl-C and Ctrl-V have become. In trying to resolve this problem, I have found a number of posts, but no one seems to have figured out how to emulate apple's dvorak-qwerty layout. Through some resources online, specifically [http://forums.gentoo.org/viewtopic-p-5077984.html#5077984](http://forums.gentoo.org/viewtopic-p-5077984.html#5077984). After tweaking crzysdrs's work, it seems like I have a fully functioning dvorak-qwerty keyboard layout.

Here is the howto to implement the dvorak-qwerty keyboard layout for linux.

Add this to /usr/share/X11/xkb/types/basic
```

default xkb_types "basic" {
...
 type "CONTROL_Q" {
        modifiers = Shift+Lock+Control;
        map[None] = Level1;
        map[Shift] = Level2;
        map[Lock] = Level2;
        map[Control] = Level3;
        level_name[Level1] = "Base";
        level_name[Level2] = "Caps";
        level_name[Level3] = "Control";
	preserve[Control] = Control;
    }; 
...
};

```

Then add this to /usr/share/X11/xkb/symbols/us
```
partial alphanumeric_keys
xkb_symbols "dvorakqwerty" {

    name[Group1]= "U.S. English - Dvorak/Qwerty";

    // Alphanumeric section

    key <TLDE> { [       grave, asciitilde ]  };

    key <AE01> { [          1,  exclam   ] };
    key <AE02> { [          2,  at     ] };
    key <AE03> { [          3,  numbersign ] };
    key <AE04> { [          4,  dollar  ] };
    key <AE05> { [          5,  percent  ] };
    key <AE06> { [          6,  asciicircum  ]  };
    key <AE07> { [          7,  ampersand ] };
    key <AE08> { [          8,  asterisk ] };
    key <AE09> { [          9,  parenleft ] };
    key <AE10> { [          0,  parenright ] };
    key <AE11> { [ bracketleft, braceleft ] };
    key <AE12> { [ bracketright, braceright ]   };

    key <AD01> {
        type = "CONTROL_Q",
        symbols[Group1] = [  apostrophe, quotedbl, q ]
    };
    key <AD02> {
        type = "CONTROL_Q",
    symbols[Group1] = [ comma,  less,  w ]
    };
    key <AD03> {
        type = "CONTROL_Q",
        symbols[Group1] = [      period, greater,e ]
    };
    key <AD04> {
        type = "CONTROL_Q",
        symbols[Group1] = [         p, P,  r ]
    };
    key <AD05> {
        type = "CONTROL_Q",
        symbols[Group1] = [         y, Y, t ]
    };
    key <AD06> {
        type = "CONTROL_Q",
        symbols[Group1] = [         f, F, y ]
    };
    key <AD07> {
        type = "CONTROL_Q",
        symbols[Group1] = [         g, G, u ]
    };
    key <AD08> {
        type = "CONTROL_Q",
        symbols[Group1] = [         c, C, j ]
    };
    key <AD09> {
        type = "CONTROL_Q",
        symbols[Group1] = [         r, R, o ]
    };
    key <AD10> {
        type = "CONTROL_Q",
        symbols[Group1] = [         l, L, p ]
    };
    key <AD11> { [      slash,  question ] };
    key <AD12> { [      equal,  plus    ] };

    key <AC01> {
    type = "CONTROL_Q",
    symbols[Group1] = [     a,  A,  a  ]
    };
    key <AC02> {
    type = "CONTROL_Q",
    symbols[Group1] = [     o,  O,  s  ]
    };
    key <AC03> {
        type = "CONTROL_Q",
        symbols[Group1] = [         e, E, d ]
    };
    key <AC04> {
        type = "CONTROL_Q",
        symbols[Group1] = [         u, U, f ]
    };
    key <AC05> {
        type = "CONTROL_Q",
        symbols[Group1] = [         i, I, g ]
    };
    key <AC06> {
        type = "CONTROL_Q",
        symbols[Group1] = [         d, D, h ]
    };
    key <AC07> {
        type = "CONTROL_Q",
        symbols[Group1] = [         h, H, j ]
    };
    key <AC08> {
        type = "CONTROL_Q",
        symbols[Group1] = [         t, T, k ]
    };
    key <AC09> {
        type = "CONTROL_Q",
        symbols[Group1] = [         n, N, l ]
    };
    key <AC10> { [          s,  S      ] };
    key <AC11> { [      minus,  underscore ] };

    key <AB01> {
        type = "CONTROL_Q",
        symbols[Group1] = [   semicolon, colon, z ]
    };
    key <AB02> {
        type = "CONTROL_Q",
        symbols[Group1] = [         q, Q, x ]
    };
    key <AB03> {
        type = "CONTROL_Q",
        symbols[Group1] = [         j, J, c ]
    };
    key <AB04> {
        type = "CONTROL_Q",
        symbols[Group1] = [         k, K, v ]
    };
    key <AB05> {
        type = "CONTROL_Q",
        symbols[Group1] = [         x, X, b ]
    };
    key <AB06> {
        type = "CONTROL_Q",
        symbols[Group1] = [         b, B, n ]
    };
    key <AB07> {
        type = "CONTROL_Q",
        symbols[Group1] = [         m, M, m ]
    };
    key <AB08> { [          w,  W      ] };
    key <AB09> { [          v,  V      ] };
    key <AB10> { [          z,  Z      ] };
}; 

```

Finally, change /etc/X11/xorg.conf to change your keyboard variant to our new custom variant.
```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbVariant" "dvorakqwerty"
EndSection

```

Ctrl-Alt-Backspace, and gnome will ask you which settings you would like to use. Choose X's settings, and you can now press Ctrl-C, Ctrl-V, and the like in qwerty, while still typing using the dvorak layout for everything else.

Bryce

---

### Post by BryceCovert on 2008-04-29
Actually, I think I misplaced this thread. Could a moderator move it to the tutorials forum?

Bryce

---

### Post by steelmole on 2008-05-01
I've applied this as best I can (it was something I spent ages looking for) and now when I use pidgin as an IRC client it thinks letters like o and i are shortcuts even when they are the only key pressed.  This is rather annoying, any ideas on what to do?

---

### Post by BryceCovert on 2008-05-07
Yes, I've been having similar issues with gnome-terminal. I haven't figured it out yet, but I think that sometimes shift is interpreted as Control. I haven't figured out why yet. I'm still looking into it.

Good luck,
Bryce

---

### Post by eldir on 2009-04-21
Thanks a lot for this tip! I've used it to great effect. Only modification was that I overwrote the Dvorak layout in the symbols/us file instead, since the system didn't recognize the new layout despite the change to xorg.conf. Shortcuts have worked beautifully since then, though I encountered the Pidgin bug and the Gnome console bug as others have. The way I got around that in Pidgin was to erase the key bindings that were giving me trouble. As for the console, I don't use it nearly as much as my browser or word processor, so I don't worry about it.

An easy way to change the key bindings in Pidgin is to go to terminal, type gconf-editor, go to desktop -> gnome -> interface, and activate can_change_accels. Then in a Pidgin message window, hover the mouse pointer over the menu item with the troublesome key binding (such as conversation -> new message (Ctrl+M)), and press backspace to erase the key binding or enter a new key combination to set a new key binding. In my case I erased four key bindings that were making conversation impossible: New Message (Ctrl+M), Find (Ctrl+F), Wipe (Ctrl+L), and Get Info (Ctrl+O). Afterwards you can disable can_change_accels or leave it on.

---

### Post by john.m on 2009-11-11
Just joined this Forum and not very used to Ubuntu. 

A Dvorak keyboard with Qwerty control keys - excellent. This is just what I am looking for. Unfortunately it doesn't work with Karmic and a UK keyboard. I can't find an xorg.conf file. I have looked for the file that contains the defaults but no success so far. I have tried to get it to work using a US keyboard but can't get that to work either. The Gnome dropdowns offering keyboard layouts don't seem to recognise the additions I have made to either the us or uk symbols files.  Grateful for any advice.

J

---

### Post by Malaz on 2010-02-06
> **john.m said:**
> I can't find an xorg.conf file.

A bit late, but:

I'm pretty sure there's no longer a xorg.conf file by default.  You can just make one with that stuff in it, IIRC.

I switched to Dvorak a few weeks ago, and am having issues with the shortcuts.  Hopefully this will work.

---

### Post by Kenton Varda on 2010-02-09
As others here have noted, while BryceCovert's keyboard layout is technically correct, many Gnome and KDE apps become buggy when the layout is loaded.  Note that every X app is expected to interpret the keyboard layout on its own.  I believe that Gnome and KDE each choose to forgo Xlib's built-in keymap interpretation code and instead use their own, and neither implementation was tested with a layout like DQ.  Ironically, the result is that simple Xlib apps work fine with the layout, but Gnome and KDE apps do not.

I've come up with an alternative solution to this problem, involving a program that grabs modified keys and actively remaps them.  I've put the code here:

[http://dvorak-qwerty.googlecode.com](http://dvorak-qwerty.googlecode.com)

Of course, ideally someone would fix the bugs in Gnome and KDE, but alas I do not have time.  :/  In the meantime, my hack seems to get the job done.

---

