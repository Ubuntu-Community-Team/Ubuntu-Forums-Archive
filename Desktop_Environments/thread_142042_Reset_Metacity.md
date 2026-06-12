---
title: "Reset Metacity?"
date: 2006-03-09
forum: Desktop Environments
---

### Post by nalmeth on 2006-03-09
After logging out, and saving my session, I can't log back in to one particular user account. The splashscreen stops at "loading Metacity". Gnome in my other accounts is fine. I'm not sure what I did to screw that up, but is there a way to reset config for metacity?

edit: or to revert to an old saved state for gnome?

Thanks

---

### Post by lamego on 2006-03-09
You can remove the metacity configuration for that user with:
```
rm -rf /home/user/.metacity
```

---

### Post by nalmeth on 2006-03-10
I did this, but am not sure if it made a difference.. 
The splashscreen stopped at "metacity window manager" again, but I keep pushing buttons, until I prompted rhythmbox to open (keyboard shortcut). Then I prompted nautilus to open, and it brought up the desktop and nautilus, but no panels. I just kept opening things, and eventually the panels appeared, and everything was there..
I don't get what is going on and causing the long delay. It is only in this user account that this happens.
Can I reset the gnome session some how (without damage of course) or is there a better course of action?

---

### Post by aysiu on 2006-03-10
How about this? ```
mv ~/.gconf/apps/metacity ~/.gconf/apps/metacity_backup
```

---

### Post by nalmeth on 2006-03-10
```
mv ~/.gconf/apps/metacity ~/.gconf/apps/metacity_backup
```
thanks asiyu this restored an older metacity setting, but didn't speed up the loading of gnome. I think I can be assured that metacity isn't causing this problem now. 
When splashscreen stops loading, it will disappear when I click on it. I think it is just a matter of taking a long time to load everything after I open nautilus, because last time I just left it, came back and everything had loaded.

What could cause such a delay in gnome? I don't get any error output from any misbehaving app, so I don't know where to start.

Has anyone seen this?

This all stemmed from one session aparently, which I saved while logging out. If I could revert to an old saved state for gnome, or even go back to default, this might solve this. Anyone know how I might do this?

---

### Post by aysiu on 2006-03-10
This may be a rather convoluted way to do it, but you could try this:

1. Back up your important config files (for me, that would be ~/.mozilla and ~/.thunderbird).

2. Create a new user with sudo privileges (or, if you have an existing extra user, temporarily give that user sudo privileges).

3. Log in as that other user and delete the original user (nalmeth). If you're asked whether you want to delete that user's /home folder, too, say "yes."

4. Create the original user (nalmeth) again with the appropriate (probably sudo) privileges. Copy the important config files back there.

5. Log in as the new original user.

---

### Post by Carambouille on 2006-03-22
I am having exactly the same problem as Nalmeth.

Has someone an alternate solution to propose ?
I don't feel comfortable to delete an user account and to safely restore all set-ups as kindly suggested by Aysiu.


EDIT : problem FIXED
I went through the menu System/preferences/Sessions and I deleted the session (named default) in the list of the Session Name.
Now I login in 1 second versus 5 minutes previuously.

---

### Post by nalmeth on 2006-03-27
>  EDIT : problem FIXED
I went through the menu System/preferences/Sessions and I deleted the session (named default) in the list of the Session Name.
Now I login in 1 second versus 5 minutes previuously.
This worked for me too.
What would cause this kind of thing to happen in the first place? It's happened to at least two people.
Anyone know?

---

### Post by W. Irving on 2006-04-11
[QUOTE=nalmeth]This worked for me too.
What would cause this kind of thing to happen in the first place? It's happened to at least two people.
Anyone know?[/QUOTE]

Three. Metacity wouldn't start (or it took forever to get going, I'm an impatient bugger) after I'd done Ctrl+Alt+Backspace in a previous session. I could log in in failsafe though. Deleting the default session did the trick.
For future reference.

---

### Post by groggyboy on 2006-04-16
so this makes four.
and i know of more - just search the forums for a bit.

think it's a bug?

---

