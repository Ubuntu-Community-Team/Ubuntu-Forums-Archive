---
title: "No scripts menu in nautilus?"
date: 2008-11-27
forum: Desktop Environments
---

### Post by ErroneousBosch on 2008-11-27
Hello all!

Very frustrating problem, and I cant seem to find a solution anywhere. I did a fresh install of Intrepid AMD64 and moved my old (Hardy i686) home directory to a new partition. Setup the new partition as home and everything seems to work fine (a few permission issues I had to sort out, but that was expected) but for the life of me, I cannot get Nautilus to show scripts! I have a few in ~/.gnome2/nautilus-scripts, and they worked under hardy, but no matter what I do I cannot get the scripts menu to even come up, either on right click or on the file menu! I of course have restarted the machine, restarted X and reinstalled nautilus (once using reinstall, once using purge then install) but no effect. All the scripts are marked executable and owned by me. This problem has persisted for the month or so I have had Intrepid. Any advice?

---

### Post by NewDisciple on 2008-11-28
**Check synaptic, see if nautilus action is installed.  I think this is needed for the scripts menu.  You may also need to reinstall your scripts.**

---

### Post by ErroneousBosch on 2008-11-28
It was present, reinstalled it, no luck. Anyone else?

---

### Post by Ivo Moelans on 2008-11-28
Baffling. I'm going out on a limb here, but have you tried recreating the directory? I mean, get rid of (move or delete it) *~/gnome2/**nautilus-scripts*** and recreate it manually. Then try it out with one script.

---

### Post by ErroneousBosch on 2008-11-29
Nope, no luck. Renamed the nautilus scripts folder in a terminal window, then created a new one, copied a script back and started nautilus, but no luck
Additional-  nautilus-script-manager does not find any scripts. It seems like nautilus is not looking in the correct directory for scripts maybe? could this have anything to do with my having my home directory on a different partition? gnome doesn't seem to have any trouble otherwise

---

### Post by Ivo Moelans on 2008-11-29
Oh well. Still guessing, but have you tried launching the script(s) manually, open the nautilus-scripts directory and click on the scripts? If they don't work, maybe the directory is not in your path although I can't think how that could have happened.
Good luck.

---

### Post by ErroneousBosch on 2008-11-29
should the nautilus-scripts folder be in the path?

---

### Post by Ivo Moelans on 2008-11-29
Not to sure about this, but you could try adding it to ~/.profile

```
PATH=$PATH: $HOME/.gnome2/nautilus-scripts
export PATH
```

Then logout & login I suppose.

Like I said, I'm only guessing, but *something* is preventing those scripts being executed, even recognized by nautilus.
By the way: *do* they work when clicked upon manually?

---

### Post by ErroneousBosch on 2008-11-29
Nautilus does not appear to be recognizing shell scripts in general... very strange.

Odd... Nautilus is trying to open shell scripts in Wine of all things. I uninstall ed wine and now it opens them with Archive manager, even though under preferences, I have told it to run them

---

### Post by ErroneousBosch on 2008-11-29
OK
I think the issue might be the mimetype association
Can someone do me a favor and post the contents of their ~/.local/share/applications/mimeapps.list

---

### Post by ErroneousBosch on 2008-11-29
nevermind.. doesn't seem to be fixing it

---

### Post by Ivo Moelans on 2008-11-29
Here you go

---

### Post by ErroneousBosch on 2008-11-29
More and more I am starting to think this is some kind of permissions messup. My systems seems to have permissions issues, for instance, firefox cannot save then open items from /tmp/ ( for instance, when I downloaded your gz file, I told it to open it directly and it errored out.)

Very frustrating

---

### Post by Ivo Moelans on 2008-11-29
I am all out of ideas, but maybe it is time to think of a clean install. In case you have never done this before, this *[link]("http://hehe2.net/linuxhowto/howto-fresh-ubuntu-install-without-losing-your-current-settings/")* gives good advice to make it as fast and painless as possible.

Anyway, good luck and sorry I couldn't be of more help.

---

### Post by ErroneousBosch on 2008-12-03
Hmm
did a reinstall and wiped out almost all my hidden directories (didn't care about the settings in them)

I copied over my nautilus-scripts folder and no love ](*,)

Ivo, if you are still watching this thread, could I prevail upon you to let me know the permissions you have set on your nautilus scripts folder and the scripts within it? It's the only thing I can think of left

---

### Post by Ivo Moelans on 2008-12-03
In attachment my nautilus-scripts folder and settings.

Maybe you could try replacing your nautilus-scripts folder with mine. On my system these scripts work and show up in the context menu.

Good luck!

---

### Post by ErroneousBosch on 2008-12-03
Ivo, thanks. I will try replacing when I get home. In your screenshot you understandably removed your username, but is the owner your username and the group your username group(1000) as well?

---

### Post by ErroneousBosch on 2008-12-03
Ivo, thanks. I will try replacing when I get home. In your screenshot you understandably removed your username, but is the owner your username and the group your username group(1000) as well?

---

### Post by Ivo Moelans on 2008-12-03
Yes, they are.
Let me know how it goes and good luck.

---

### Post by ErroneousBosch on 2008-12-05
Still nothing. Oh well
Thanks for all your help Ivo

---

### Post by ErroneousBosch on 2008-12-05
the weird part is that Nautilus won't even run them if I just double click on them... it opens them in gedit, even though I have told it in preferences to run executable text files.

---

### Post by ErroneousBosch on 2008-12-05
Well, one last reinstall and wiping the ~/.nautilus folder...and it works! thx for all your  help ivo

---

### Post by Ivo Moelans on 2008-12-05
Congratulations!
Sorry I couldn't be of more actual help, but anway, we both learned something I suppose.

---

