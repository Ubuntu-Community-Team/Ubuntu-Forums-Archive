---
title: "[SOLVED] Can't shift+alt+tab in Gutsy"
date: 2007-10-18
forum: Desktop Effects &amp; Customization
---

### Post by yang on 2007-10-18
I can't shift+alt+tab in 7.10. I installed and looked in compizconfig-settings-manager, and under the Application Switcher's Actions tab, I found that "Prev window" was unset. However, I could not set it to be Shift+Alt+Tab, though I could set it to other keys and key combos.

I also tried setting "Prev window" to Alt+Tab, which was already taken by "Next window", and it similarly wouldn't let me set it. This leads me to believe something else is occupying Shift+Alt+Tab. I don't know what, though - there are too many plug-ins to check!

---

### Post by yang on 2007-10-18
Turns out the settings manager has a nifty search feature that lets you search by value (type in lower-case "tab").

I'm still not sure what was causing the problem, but I also tried typing in "<shift><alt>tab" rather than "shift+alt+tab".

It would be nice if shift+alt+tab were working from the get-go, though.

---

### Post by DasCrushinator on 2007-10-19
> **yang said:**
> Turns out the settings manager has a nifty search feature that lets you search by value (type in lower-case "tab").

I'm still not sure what was causing the problem, but I also tried typing in "<shift><alt>tab" rather than "shift+alt+tab".

It would be nice if shift+alt+tab were working from the get-go, though.

Thank you,this fixed my problem.

---

### Post by victor.zamanian on 2007-10-20
DasCrushinator: How did that solve your problem? I'm having the same problem, but upon searching for even just "tab" in the advanced search of compizconfig settings manager, I find no conflicting keyboard shortcut bindings (yes, I enabled 'Settings value').

I'm going to keep searching to see if I can find something, and if so I'll post it here since this was my first hit on Google.

---

### Post by DasCrushinator on 2007-10-20
> **victor.zamanian said:**
> DasCrushinator: How did that solve your problem? I'm having the same problem, but upon searching for even just "tab" in the advanced search of compizconfig settings manager, I find no conflicting keyboard shortcut bindings (yes, I enabled 'Settings value').

I'm going to keep searching to see if I can find something, and if so I'll post it here since this was my first hit on Google.

Let me see if I can recall my steps:

1) Go to the plugin you want to change the bindings for
2) Go to the 'Actions' tab
3) Double click on the name of the specific action you want to alter
4) Type <Alt>Tab (or something similar) in the 'Key' field

That should do it.

Not sure why it is we have to alter it this way.  A bug maybe?  Either way, that has worked perfectly fine for me.

Goold luck :)

---

### Post by notthatway on 2007-12-01
I'm still having trouble with this one. I followed the steps that DasCrushinator posted and type in my desired key combination <Alt><Shift>tab (and also tried <Alt><Shift><Tab> and variations on caps). When I click OK on the edit dialog, the Key setting still says Disabled.

Now, I assume that this might be caused by another plug-in using <alt><shift><tab> as one of it's action's key bindings. As discussed earlier in this thread, I ran a search to find all actions that use the tab key. There were a bunch, but none seemed to be using <alt><shift><tab>.

I'm running Gutsy, ATI Radeon 9200se with the ati driver. Things are working great, but I'd love to get this little detail fixed :)

Anyone seeing this problem? Any ideas?

---

### Post by victor.zamanian on 2007-12-07
> **DasCrushinator said:**
> Let me see if I can recall my steps:

1) Go to the plugin you want to change the bindings for
2) Go to the 'Actions' tab
3) Double click on the name of the specific action you want to alter
4) Type <Alt>Tab (or something similar) in the 'Key' field

That should do it.

Not sure why it is we have to alter it this way.  A bug maybe?  Either way, that has worked perfectly fine for me.

Goold luck :)

Hah! I didn't know you could double-click on the name of the action to _type_ in the value. I thought one was forced to single-click the key field and _press_ the key combination. Right, well, thank you, that helped a lot. :- )

Now, if only the special effects in Ubuntu 7.10 wouldn't be so buggy then all would be well. I'm talking about the nasty bug (that at least I have) where if I enable effects, switch user to any other user, then try logging back into my own (or any other account with effects enabled that is already logged in), I get a black screen (or white, depending on... something). I can sometimes type in my password and actually blindly get into my account but sometimes that doesn't work and the whole system freezes up just because I can't break through this bug in the special-effects interface. This thing with the password obviously also depends on... something. If you know what I mean. ;P (For those of you who don't, it means I have absolutely no clue why this happens.)

Note, I'm not trying to find an answer to this problem, I'm just rambling. I'm fine with refraining from the special effects, 'cause I'd rather my graphics card shut up than see the wobbly windows etc, though they are kind of nice.

Anyway, peace, and enjoy your free software!

---

### Post by mkoyle on 2008-01-23
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/150702](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/150702)

I found that this is fixed if I run gconf-editor and change

```
/apps/metacity/global_keybindings/switch_windows_backward
```

to  "<Alt><Shift>Tab"

As far as I can guess, compiz is modifying that key binding for some reason....  It is filed as a bug, so hopefully it will be fixed soon.

--Matthew

---

