---
title: "[SOLVED] Control+Alt+Del no shutdown/reboot option anymore?"
date: 2008-12-22
forum: General Help
---

### Post by joehte on 2008-12-22
Hi,

with Ubuntu Intrepid the behaviour of Control+Alt+Del changed. It used to be very easy to shutdown the computer from keyboard by Control+Alt+Del and pressing s for shutdown.

Now with Intrepid it just gives the choises:
- Log Out
- Switch User

Is there anyway to configure this dialog so that I could shutdown easily? IMO the current behavior is quite braindead. I'd imagine the common desktop user much more often needs to shutdown his computer than log out or switch users. At least that's the case for me.

I am also a developer, so if this is not possible I am willing to put some work into reintroducing this functionality. I just don't know where to look for. Is this a Gnome behavior or where should I look into?

---

### Post by SlidingHorn on 2008-12-22
1. Right-Click your "Quit" icon in your panel and click Properties
2. There should be a dialog for a command, if so change it to:
```
gnome-session-save --kill
```

I use XFCE, so I only have a dropdown menu...if you have that, select "Quit"

---

### Post by PocketDog on 2008-12-22
In system > administration > login window > local tab: tick 'show actions menu'.

---

### Post by joehte on 2008-12-22
Thanks, but there don't seem to be any Quit panel. Nor could I find one by using "Add to Panel". I'm shutting down now, as Control+Alt+Del don't work, by using the "Switch users or Shut Down" panel item (it's the User Switcher panel, I think). But that panel has no Properties to change.

Now that I looked at it, in "System" there are two menu items:

 - Log Out <user>...
 - Shut Down...

It seems Control+Alt+Del launches the above Log Out option. I'd just need it to instead launch the Shut Down option instead and I'd be ok with that. But I haven't found where I could change that keybinding.

---

### Post by joehte on 2008-12-22
> **PocketDog said:**
> In system > administration > login window > local tab: tick 'show actions menu'.

This seems to have only effect in the login window, not when I'm already logged in and using Gnome. I do have that ticked already.

---

### Post by mageus on 2008-12-25
The correct command is:
```
gnome-session-save --shutdown-dialog
```

Looks like we need to map this command to ctrl-alt-del.  Anyone know how to do that to override the logout dialog?

For now I'm just going to map a script of this to ctrl-alt-s or something.

---

### Post by mageus on 2008-12-25
A search points to this thread:

[http://ubuntuforums.org/showthread.php?t=952657]("http://ubuntuforums.org/showthread.php?t=952657")

It shows you where to remap the keybindings.

---

### Post by joehte on 2008-12-27
Thanks mageus, I was going for the alternate shortcut syntax also, but the solution you posted works too. I think I'll maybe continue to use control+alt+shift+del for shutdown to make transferring to future Ubuntu installs as painless as possible.

Hint to Compiz users:

the keybindings are in the CompizConfig Settings Manager. If you have any focus prevention level set, then you should add to Focus Prevention Windows following rule:

```
(any) & !(class=Gnome-session)
```

This makes sure that when you hit your shotcut, the shutdown/logout dialog will come on top and not arrive behind the window you're working on.

---

