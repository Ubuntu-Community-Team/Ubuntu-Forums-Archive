---
title: "Firefox is hosed. How do I fix it?"
date: 2006-07-14
forum: Desktop Environments
---

### Post by zergberg on 2006-07-14
First off, greetings from Lynx. It's surprisingly usable... Moreso than when my video card went haywire and I had to use IE with 640X480 resolution and 256 colors for a week.

Anyway, I was lazy, and tried to sync my Windows Firefox with this one using the FEBE extension. This had several adverse effects:
- Not working whatsoever
- Putting a bunch of unremovable extensions in my Extensions dialogue, none of which did anything. (Particularly, they refused to uninstall.)
- Not allowing any other extensions to install. (They'd show up, but no matter how many times I restarted they never got past the "foo will be installed when Firefox is restarted.")
- Not allowing Profile Manager to start up, for some reason.
- Not fixing any of the above problems when I told Synaptic to Complete Remove and then Install the Firefox package.

This was rather annoying, but I eventually got the extension crap to go away by deleting some stuff in ~/.mozilla, at which point all the above problems were fixed. However...
I performed the arduous task of manually installing all my old extensions, only to discover that I couldn't edit their preferences or uninstall them, much like the extensions that FEBE had created. Not only that, Profile Manager has failed yet again. And these new extensions, like some drug-resistant form of TB, can't be destroyed by my old methods, or by uninstalling/reinstalling Firefox.

Furthermore, ubuntuforums now looks odd (no images) and refuses to let me log in.

This is, as you may imagine, quite a problem. I'd like it to go away, as Lynx, while usable, isn't what I'd like to use for a browser. (Pictures? What?)
So, any ideas on how to get rid of my zombie/tubercolosis extensions, fix Firefox in general, and allow me to install extensions properly again?
Thanks.

---

### Post by philippe_carlo on 2006-07-14
Try to remove (or better, move for backup) the .mozilla directory in your home directory. Firefox should reinitialize all settings.

---

### Post by Malac on 2006-07-14
Have you tried ```
firefox -safe-mode
``` in a terminal.
You need to have no other instances of firefox running.
You should then be able to uninstall stuff.

Hope this helps.

---

### Post by zergberg on 2006-07-14
Deleting .mozilla : No effect.
-safe-mode : No effect, I assume it's in the same boat as -profilemanager.

---

### Post by abelthorne on 2006-07-14
> **zergberg said:**
> Anyway, I was lazy, and tried to sync my Windows Firefox with this one using the FEBE extension. This had several adverse effects:

If it can help when you've sorted your main problem out : when I switched from Windows to Ubuntu, I just backuped my Firefox profile directory, copied it to my Linux partition and created a new profile pointing to it. All my preferences, bookmarks & extensions were kept and fully usable.

---

### Post by ChrisDerson on 2006-07-14
If I were in your position, I'd uninstall firefox with dpkg/synaptic, then trawl for everything left of the filesystem that mentions firefox (using locate) and rename/delete it (including ~/.mozilla/), then re-install firefox.
You could also try Opera (no, I'm not a big fan, but it's prettier that Lynx ;) ).

---

### Post by Malac on 2006-07-14
[COLOR=Black]Okay the only other thing I can think of is to delete the .mozilla directory *after* uninstalling firefox (if you are using ubuntu one use synaptic to mark it for Complete Removal).
then re-install.
[B]AND / OR
[/B]Create a whole new user
login as that user open firefox set it all up as you want then copy that users .mozilla directory to your home directory.
login as your original user.
run [/COLOR]```
sudo chown -Rv yourusername ~/.mozilla
```[COLOR=Black] replacing[/COLOR] [COLOR=DarkGreen]yourusername.
[COLOR=Black]There are also two plugins folders which you may want to clearout incase there is still some residual file there.
/usr/lib/mozilla/plugins
/usr/lib/mozilla-fiefox/plugins[/COLOR]
[/COLOR]

---

### Post by Malac on 2006-07-14
Oh yeah, if you upgraded to Dapper then you may have two main firefox directories, I have three at the moment :), you may be using one of these inadvertently.

---

