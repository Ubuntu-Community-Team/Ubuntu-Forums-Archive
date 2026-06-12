---
title: "Binding caps-lock to a range of commands shortcut-keys keyboard-layout"
date: 2019-07-20
forum: Desktop Environments
---

### Post by bjohas on 2019-07-20
I never use caps lock, so I'd like to use it as an addition custom modifier key. What modifier keys are there? Super, meta, hyper?

Could I turn the caps lock key into say "hyper" and then assign commands to hyper-a, hyper-b etc? How would I do that?

I'm thinking mainly of commands like beginning of line, end of line etc. Where would those commands (that are currently found to other legal so I can assign them?

(Also asked here: [https://askubuntu.com/questions/1159620/binding-caps-lock-to-a-range-of-commands](https://askubuntu.com/questions/1159620/binding-caps-lock-to-a-range-of-commands) )

---

### Post by Holger_Gehrke on 2019-07-20
'man xmodmap' should tell you what you want to know about remapping keys (and mouse buttons).

Holger

---

### Post by bjohas on 2019-07-21
Hi Holger,

thank you very much! I've looked into xmodmap with some success.

I'm a bit confused about some of the modifiers though. For example, [https://wiki.archlinux.org/index.php/Xmodmap](https://wiki.archlinux.org/index.php/Xmodmap) says

```
[FONT=sans-serif]Each *keysym* column in the table corresponds to a particular combination of modifier keys:[/FONT]

[LIST=1]
[*]Key
[*]Shift+Key
[*]Mode_switch+Key
[*]Mode_switch+Shift+Key
[*]ISO_Level3_Shift+Key
[*]ISO_Level3_Shift+Shift+Key
[/LIST]

```

But: the xmodmap has up to 10 entries for each key. So what do those correspond to? 

Further, how does 
```

$ xmodmap -pmxmodmap:  up to 4 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Meta_L (0xcd)
mod2        Num_Lock (0x94)
mod3      
mod4        Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  ISO_Level3_Shift (0x6c),  Mode_switch (0x85),  Mode_switch (0xcb)
```

then correspond to the above? I read this list as "the function 'shift' is fulfilled by the phyiscals keys Shift_L and Shift_R" etc.  I'm on a laptop without num_lock, and isn't it also strange that mod3 is not assigned? Or is it that somehow only mod1/4/5 aer used in the above list?

And then it would make sense to have 
```

[LIST=1]
[*]
Key
[*]Shift+Key
[*]mod1+Key
[*]mod1+Shift+Key
[*]mod2+Key
[*]mod2+Shift+Key
[/LIST]

```

Is that correct?

---

### Post by bjohas on 2019-12-08
I've added a lot of notes about xmodmap / xev / setxkbmap here: [https://github.com/bjohas/Ubuntu-keyboard-map-like-OS-X](https://github.com/bjohas/Ubuntu-keyboard-map-like-OS-X)

---

### Post by TheFu on 2019-12-08
> **bjohas said:**
>  
I'm thinking mainly of commands like beginning of line, end of line etc. Where would those commands (that are currently found to other legal so I can assign them?
 

Each program can have different key-chords for those things.  
If you are talking about an editor, each will be different.
If you are talking about a shell, most have ways to alter between well-known setups - either vi or emacs key bindings.  There are books on each shell program which get into those key chords.

[https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) is one summary.

xmodmap is one way.  xdotool connected with xmodmap is helpful too. Both should work on an X11 setup.  Additionally, each Window Manager + DEs can handle these things differently.  Some have GUI programs to setup/modify shortcuts.  Others use text file configurations.

---

### Post by amirdarkevil on 2019-12-09
I had the same problem
Thanks[.]("https://film4irani.ir")

---

