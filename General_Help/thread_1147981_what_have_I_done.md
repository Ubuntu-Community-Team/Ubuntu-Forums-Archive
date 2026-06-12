---
title: "what have I done?"
date: 2009-05-03
forum: General Help
---

### Post by Zom-b on 2009-05-03
I don't even know what exactly has happened, but, I was trying to get AWN to work and finally had it up and running, I was going to get rid of one of my panels, ended up deleted both of them, so I started searching for how to fix that.
I found a post elsewhere on the forum about how to reset both panels back to default using

gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

I tried that several times without it working so I tried restarting to see if it would help, only it made things worse, when I try to use my last session or the regular gnome session it logs in loads the back ground and then stops nothing happens. I tried using the failsafe and it logged in and works fine, I am just wondering how I have managed this? and if I just keep using this session if I'll be fine or if there is a way to fix the normal session.

---

### Post by pytheas22 on 2009-05-03
A quick and dirty fix would be to run these two commands:
```

mv /home/USERNAME/.gnome /home/USERNAME/.gnome-OLD
mv /home/USERNAME/.gnome2 /home/USERNAME/.gnome2-OLD
```

where 'USERNAME' is the name of the account you're trying to fix.  Then log out and back in.  This will delete all of your Gnome settings (including wallpapers, window border theme, etc.) and fall back to the defaults.  Depending on how much work you've put into customizing your desktop, this may or may not be a good solution for you.

If the above isn't acceptable for you, let me know and we can try to fix just the panels.  I vaguely remember being in the same situation once, and having to change some value in gconf to get the panel back.

---

### Post by JK3mp on 2009-05-03
Possibly  alt+f2 then in run: insert gnome-panel ?

---

### Post by Zom-b on 2009-05-03
> **pytheas22 said:**
> A quick and dirty fix would be to run these two commands:
```

mv /home/USERNAME/.gnome /home/USERNAME/.gnome-OLD
mv /home/USERNAME/.gnome2 /home/USERNAME/.gnome2-OLD
```

where 'USERNAME' is the name of the account you're trying to fix.  Then log out and back in.  This will delete all of your Gnome settings (including wallpapers, window border theme, etc.) and fall back to the defaults.  Depending on how much work you've put into customizing your desktop, this may or may not be a good solution for you.

If the above isn't acceptable for you, let me know and we can try to fix just the panels.  I vaguely remember being in the same situation once, and having to change some value in gconf to get the panel back.

hehe, as of yet, I am still learning, so I am usually doing something a bit too advanced for me and mess something up, I have been bound a determined not to have to do another reinstall XP I haven't really don't too much tweaking on the way it looks, so if this works that'll be fine for me


time to see if it works. -crosses fingers-

oh yeah, just to clarify, even though it might sounds stupid, this just deletes the settings an doesn't get rid of anything right?

---

### Post by pytheas22 on 2009-05-03
> 
oh yeah, just to clarify, even though it might sounds stupid, this just deletes the settings an doesn't get rid of anything right?

Yes, it just sets you back to the default Gnome settings; no files are deleted.

---

