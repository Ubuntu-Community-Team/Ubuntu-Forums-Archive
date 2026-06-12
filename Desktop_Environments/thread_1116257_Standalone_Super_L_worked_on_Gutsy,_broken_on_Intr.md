---
title: "Standalone Super_L worked on Gutsy, broken on Intrepid"
date: 2009-04-04
forum: Desktop Environments
---

### Post by bziman on 2009-04-04
The topic of super keys has been discussed at painful length, usually with someone wanting to use Super as a modifier like Shift or Alt.  That's NOT what I'm trying to do.  In Gutsy (and for many, many years -- since Warty), I had Super_L launch the default browser, Ctrl-Super_L launch the default terminal, and Alt-Super_L launch the default mail client.  These were configured using the Preferences / Keyboard Shortcuts dialog.  Worked fine.

In a clean installation of Intrepid, I am able to use the Keyboard Shortcuts to create the same configuration.  I know the keyboard is configured properly, because when I go to set the key, Super_L appears exactly like I expect it to.

However! Only Ctrl-Super_L works (launches a terminal).  The plain Super_L and the Alt-Super_L shortcuts do not work.  I have tried binding them to other actions, which does not work, and I have tried binding other keys to these actions, which do work.

I've read that compiz can interfere with it because it expects the Super key to be a modifier (which is the most bizarre thing I've ever heard!) -- but I have compiz disabled.  I did install the compiz configuration manager, to make sure that there weren't any compiz shortcuts that use the Super key as a modifier, as some forums imply that could cause the behaviour to break.  I didn't see any such shortcuts.  And anyway, why would it cause a problem with Alt-Super_L but not Ctrl-Super_L?

This leads me to believe that some part of the system (metacity, x.org, whatever) is eating my Super_L.

Has anyone else experienced this?  Has anyone else got a fix for this?  I'm afraid that "sucking it up" (common advice) and learning to use an additional key for my most frequent three tasks is out of the question.  It worked correctly for years, and now does not, so there's got to be something that changed, and that can be fixed.

Thanks,
Brian

---

### Post by bziman on 2009-04-04
I found a workaround.  It's horrible.  But at least it works.  Using gconf-editor (actually, using grep!), I discovered that the key binding for running a terminal is in a different section than launching a browser or e-mail client.  The terminal is configured under /apps/metacity/global_keybindings, while the others are under /apps/gnome_settings_daemon/keybindings.  For whatever reason, keyboard shortcuts configured under gnome_settings_daemon do not respond properly to Super_L, while those configured under metacity do.

So, the workaround is to first delete your properly configured mappings in the "Keyboard Shortcuts" dialog that use Super_L.  Then, go launch gconf-editor, and navigate to /apps/metacity/keybinding_commands.  There are twelve empty, numbered commands (though I think you can add others, and give them names, if you wanted to).  Configure these with the command lines of the actions you want to take, then flip over to /apps/metacity/global_keybindings and specify your keyboard shortcuts for the keys that correspond to your commands -- so I set up:

```
/apps/metacity/keybinding_commands/command_1 = '/bin/launch-firefox.sh'
/apps/metacity/keybinding_commands/command_2 = '/bin/launch-mail-client.sh'
```

and

```
/apps/metacity/global_keybindings/run_command_1 = 'Super_L'
/apps/metacity/global_keybindings/run_command_2 = '<Alt>Super_L'
```

Now I can use it as I did before.  However, it still begs the question why it would work when under one key, but not under the other key.  And of course it should work using the Keyboard Shortcuts dialog, without using the gconf-editor!!

---

### Post by nostra16 on 2009-05-10
This solution does not work on 9.04 anymore.

Custom keyboard shortcuts in Gnome-Do do not accept Super_L as standalone shortcut. "Menu Key" does. Any workaround this time?

I managed to add 'Super_L' as a shortkey in gconf /apps/gnome-do/preferences/Do/CorePreferences/SummonKeybinding but has no effect. Setting the value to '<Super>' or 'Super' doesn't do any better.

Why, oh why?

---

### Post by bziman on 2009-05-10
It's unfortunate that my workaround no longer works.  Intrepid was so broken, that I rolled back to Gutsy, in the hopes that Intrepid would become less broken after a few months of release.  I guess it's moving in the opposite direction.

---

### Post by twizler on 2009-11-10
matthodge --> 
Re: Can't press Super L + other key
Here is the solution :

1) Goto System > Preferences > Keyboard
2) Goto "Layout Options" tab.
3) Expand "Alt/Win Behavior".
4) Put the dot on "Super is mapped to the Win-keys (default)".
5) Press close.
6) Goto System > Preferences > Keyboard Shortcuts.
7) Map your WinKey + Whatever combos.

It should come up as "Mod4+ KEY"

---

