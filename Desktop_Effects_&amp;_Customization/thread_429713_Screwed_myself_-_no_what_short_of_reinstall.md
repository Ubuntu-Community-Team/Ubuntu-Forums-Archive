---
title: "Screwed myself - no what short of reinstall??"
date: 2007-05-01
forum: Desktop Effects &amp; Customization
---

### Post by becatlibra on 2007-05-01
Just switched to Feisty on the 20th of April

I SCREWED myself by installing beryl.  It seemed okay yesterday, but now nothing works.  I changed a setting I shouldn't have (set it to XGL instead of auto because it was slow and didn't work half the time) and now Beryl won't load and know loads but appears to not be using any kind of window manage (meaning none of the windows have handles of any kind) - I purge beryl hoping to eliminate the changes I made and reinstalled it all.  GNOME will only work in SAFE MODE.

I asked on my LUG an didn't really get an answer from anyone of beryl so I thought I'd try it.  I didn't think it would be irreversible.

Help - I don't want to have to reinstall - I have a dualboot system and have many things installed on linux that I don't want to have to reconfigure again.  

PLEASE

---

### Post by rolf-c on 2007-05-01
Well, it seems like if it worked before the change to XGL, it may work again if we get off the XGL.  Have you tried that?

---

### Post by becatlibra on 2007-05-01
One would think that yes.  However I can't get to the beryl-settings manager AT ALL.  I am sure there is a text config file somewhere I can change but I am not sure where to.  

Fluxbox was always so much simplier.  I was taken over by the beauty of beryl and wanting to show it to my windows friends . . . 

ANYWAY.  Yeah - I can't change it back because I can't get to it and I don't know what .conf file (or whatever) to modify.  Really, at this point, I would be happy to go back to a working gnome desktop.  Beryl would be nice though and it worked fine last night - It started acting funny today though so I tried to tweak it and it all fell apart.  I kept running into problems where the windows were empty (the terminal app window, for instance, had no shell cursor and no menu bar unless i used windowshade and then when I unshaded it, the contents would appear - but never update while I was viewing it.)

I want to start over without having to reinstall ubuntu.

So I need to uninstall beryl completely and get rid of all settings files.  Then step by step rebuild.  The problem is, as I said, it appears that (when I pick Gnome from the GDM instead of berly) that there is NO Window Manager.  There are no title bars to any of the windows.  Unless I go to gnome "safe-mode"  -- Is there a way to copy these "safe mode" settings back to my own settings?

HELP HELP :D

---

### Post by rolf-c on 2007-05-01
You can wipe out beryl from the command line with:

```
sudo apt-get remove --purge beryl*
```

That will remove everything Beryl from your system, including config files.

Then restart gdm:

```
sudo /etc/init.d/gdm restart
```

At the login, hit F10 and choose your session, then login as normal.

You should have a running system and from here can go any direction you wish.

As always, you mileage may vary so proceed with caution!

---

### Post by becatlibra on 2007-05-01
Okay - well I did that myself earlier and it didn't purge everything (which I thought odd)

I went through and cleaned it up (I thought) however I am still having problems.  I have 2 users on my PC.  One works fine (it was a test user I created long ago.)  The other, ME, when I login I get the panel but no desktop background and right clicking does NOTHING on the desktop.  If I go into failsafe mode it seems fine.  I thought, once in failsafe, I could save my session and everything would be fine again but no.  So the ME user has no desktop, no context menu on the desktop and no titlebars for any windows - like the window manager is not loading.

I suppose I could create a new user and copy everything over but it seems I SHOULD be able to just copy whatever is loading when i select 'failsafe' but I don't know what that is or where it is.  I come from a dos and blackbox/fluxbox world and the gnome vfs and it's menus, etc have always seemed slightly esoteric to me.

Any suggestions on what file I use (whatever is happening when I pick failsafe) - how to 'reset' the user to defaults.  I have very customized menus and don't want to lose all the entries I put in (icon selections, etc)

Further advice?

---

### Post by YoG%*@ on 2007-05-01
hell-o!

maybe this is of help for you: [http://ubuntuforums.org/showthread.php?t=354228&highlight=reinstall+beryl+howto]("http://ubuntuforums.org/showthread.php?t=354228&highlight=reinstall+beryl+howto")
helped me with beryl trouble...

---

### Post by becatlibra on 2007-05-04
Like I said, even without beryl installed (or reinstalled) nothing worked - 

I will close out this thread now for future seekers of wisdom.  What I did to make it all work again (just gnome, forget beryl) was this.

I deleted my .gconf and .gconfd folders and then found something - I believe it was ~/.config/sessions or ~/.local/sessions

Either way it was called sessions and I deleted it - I guess I had set some things up screwy as far as the startup was concerned so that the window manager would never really load.

Pretty specific problem so I doubt anyone else will EVER have to deal with it again.

Maybe but probably not

Regards

Benjamin

---

### Post by N/A on 2007-05-04
:lolflag: 
 
it happed to mee to.... damn beryl  !
i stil try to find a fix to get window decorations back so i can have my panels back

When i try to get Window Manager Settings it says: These settings cannot work with your current window manager (unknown)

well i fixed it by deleting all files in the  /home/<my username>

---

### Post by becatlibra on 2007-05-07
Yeah - the actual file I got rid of was in the .metacity folder - the file was named sessions.

---

