---
title: "A few problems..."
date: 2005-11-22
forum: Desktop Environments
---

### Post by tmmuk on 2005-11-22
Hi,
I recently did a fresh install of Breezy (after i screwed the X-server trying to upgrade from hoary - I eventually formatted the hdd and started again) and I have a few problems:

1. The k-menu no longer seems to update itself. It used to, but now it doesnt. After I edit it and save it doesnt make a difference. I have tried update-menus, but that doesnt seem to have fixed it. 

2. Whenever I type a command into the command box (Alt+F2) that doesnt exist ( or is not recognised), it opens firefox and goes to the url: [http://thecommandijusttyped.domain.com/](http://thecommandijusttyped.domain.com/) - a site for registering domain names. for example, if i typed asdf in the command box, it goes to [http://asdf.domain.com/](http://asdf.domain.com/)
This seems almost like adware or something, but I dont see why I should have it.

3. I cant seem to play any media files in kaffine or kaboodle. I have the w32 and other codecs installed, but i only seem able to play stuff in mplayer.

4. I can't seem to send files in kopete, it just fails

Also, does anyone know of a program that can encode videos into MPEG-4 format for the Sony PSP?

And if someone could help me get LMMS working (or suggest a similar prog) that would be good

thanks

---

### Post by daller on 2005-11-22
About the kaffeine thing:

Did you install kaffeine-xine, and choose it as the default engine?

---

### Post by tmmuk on 2005-11-22
ok, i do have that package installed, and after a kde restart (with ctrl+alt+bkspc) kaboodle / kaffeine are now working fine.
Thanks

Any help on the other problems?

---

### Post by GeneralZod on 2005-11-22
[QUOTE=tmmuk]
1. The k-menu no longer seems to update itself. It used to, but now it doesnt. After I edit it and save it doesnt make a difference. I have tried update-menus, but that doesnt seem to have fixed it. 
[/QUOTE]

Try running kmenuedit from the command-line and making and saving some changes, and see if it reports any errors, especially stuff relating to DCOP.

[QUOTE=tmmuk]
2. Whenever I type a command into the command box (Alt+F2) that doesnt exist ( or is not recognised), it opens firefox and goes to the url: [http://thecommandijusttyped.domain.com/](http://thecommandijusttyped.domain.com/) - a site for registering domain names. for example, if i typed asdf in the command box, it goes to [http://asdf.domain.com/](http://asdf.domain.com/)
This seems almost like adware or something, but I dont see why I should have it.
[/QUOTE]

I've no idea why this happens; it doesn't happen for me :/ 

If you just want to launch apps, you might want to check out "katapult".

Can't help with the other questions, I'm afraid :/

---

### Post by tmmuk on 2005-11-23
after kmenuedit then deleting an item i didnt want, then saving, i got:

```

  X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x26003fd

```

---

### Post by kkass on 2005-11-29
I am having the same exact problem!  I am also receiving the same error code described in the post above.  Has there been any resolution to this?

Thanks

**Edit:**
I should have kept reading.  This issue is resolved in the following thread.
[http://www.ubuntuforums.org/showthread.php?p=531087#post531087]("http://www.ubuntuforums.org/showthread.php?p=531087#post531087")

---

