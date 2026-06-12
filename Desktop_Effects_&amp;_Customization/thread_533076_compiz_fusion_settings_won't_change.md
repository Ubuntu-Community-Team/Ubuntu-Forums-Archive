---
title: "compiz fusion settings won't change"
date: 2007-08-23
forum: Desktop Effects &amp; Customization
---

### Post by JonD25 on 2007-08-23
I used the directions from this thread

[http://ubuntuforums.org/showthread.php?t=508769](http://ubuntuforums.org/showthread.php?t=508769)

to get Fusion up and running. However, now when I go to change a setting, enable or disable a plugin, nothing changes. If I close the config manager and open it again, all my changes are back to default. How do I fix this? I used to use Treveno's repository, but I could no longer connect to that to get any updates, so I decided to uninstall and try this version. But now this won't work!

---

### Post by hogweed on 2007-08-23
You are not alone in this, and it looks like we'll just have to be patient until it gets fixed. Take a look here:

[http://ubuntuforums.org/showthread.php?t=531055&highlight=compiz+settings]("http://ubuntuforums.org/showthread.php?t=531055&highlight=compiz+settings")

and here:

[http://smspillaz.wordpress.com/2007/08/19/compiz-fusion-community-news-edition-12-for-august-19-2007-radical-changes/]("http://smspillaz.wordpress.com/2007/08/19/compiz-fusion-community-news-edition-12-for-august-19-2007-radical-changes/")

-- hogweed

---

### Post by Inxsible on 2007-08-23
Trevino's repos have been rectified now. At least they work for me. But you have to first do a complete un-install and even remove the config files from your /home folder and then re-install

---

### Post by hogweed on 2007-08-23
> **Inxsible said:**
> Trevino's repos have been rectified now. At least they work for me. But you have to first do a complete un-install and even remove the config files from your /home folder and then re-install

Nope, it ain't happening for me. I got rid of the compiz-related files in .compizconfig and .config and .gconf -- is there something that I am missing? Maybe this is not fixed for KDE yet?

--hogweed

---

### Post by Dracojk on 2007-08-23
I've just gotten it installed from Trevino's repo and it's still got the settings bug.  Is it possible to manually change the settings via the files?  If so how would I do that?  I'm still learning Linux, so a link to where I could find that information or something would be great.

---

### Post by Inxsible on 2007-08-24
> **hogweed said:**
> Nope, it ain't happening for me. I got rid of the compiz-related files in .compizconfig and .config and .gconf -- is there something that I am missing? Maybe this is not fixed for KDE yet?

--hogweed

if you use KDE, then you should probably be looking at the config files under .kconfig ...as in /home/.kconfig/apps/compiz of /home/.kconfig/compiz  -- something like that, i dont have kde, so i cant say for sure.

---

### Post by hogweed on 2007-08-24
> **Inxsible said:**
> if you use KDE, then you should probably be looking at the config files under .kconfig ...as in /home/.kconfig/apps/compiz of /home/.kconfig/compiz  -- something like that, i dont have kde, so i cant say for sure.

Thanks, Inxsible. You'd think that after all these years I'd know that I would have to put a "K" in front of whatever I was looking for!

So: 

1. complete removal of everything from Trevino's repos;
2. delete all personal compiz related config files in the home directory (found in: /.compizconfig and  /.gconf and /.kde/share/config/compizrc;
3. reinstall list of everything removed from Trevino's repos;
4. reboot (just kidding);
5. fireup compiz.

It looks like changes to the default settings hold now, and are snuggled away in **both** ~/.config/compiz/compizconfig/config [odd but true] **and** ~/.kde/share/config/compizrc

I will now hunt around to see how to get a session to start automagically with compiz enabled...

-- hogweed

---

