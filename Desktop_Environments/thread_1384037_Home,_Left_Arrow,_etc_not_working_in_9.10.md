---
title: "Home, Left Arrow, etc not working in 9.10"
date: 2010-01-17
forum: Desktop Environments
---

### Post by HyperHacker on 2010-01-17
I just upgraded Xubuntu from 9.04. I copied everything to an external hard disk, did a clean install, and then restored /home from the backup. I notice now that some of the keys on my keyboard have strange mappings:
Left Arrow -> Right Alt
Down Arrow -> Right Super
Page Up -> Slash (numpad divide)
Page Down -> ???
End -> Left Super

The reverse is not true (i.e. actually pressing Right Alt still works as Alt). I'm not certain whether these keys worked before restoring /home, but I suspect I would have noticed. The keys work normally in TTY (but not terminal windows).


Also there has been a problem with Num Lock for some time now on two machines. When the system is started up, when logging in, or when switching to/from TTY, the Num Lock state may be changed. Particularly frustrating is sometimes it's turned off, but the LED is on.

---

### Post by XubuRoxMySox on 2010-01-18
> **HyperHacker said:**
> I just upgraded Xubuntu from 9.04. I copied everything to an external hard disk, did a clean install, and then restored /home from the backup. 

This sentence doesn't quite make sense to me, but if it means exactly what it appears to say, then you apparently copied settings (including keybindings) that worked in Jaunty and imposed them on a "fresh" install of Karmic.

What most folks do on a truly fresh install is to *preserve* the /home _partition_ (not their /home _directory_), rather than *restore* a /home directory from a previous version. If I'm not being too literal in my reading of your post, I think it may explain what happened.

When I do a fresh installation, during the Partitioning process I choose "manual partitioning" and designate my partitions as follows:

10 to 15 gigs as "**/**" (for the OS),

a **swap** are that is equal to twice the amount of RAM, and

the rest of the drive as "**/home**".


Then UNCHECK the li'l box that says "format this partition" on the "/home" partition. This *preserves* the *partition* (rather than restoring a directory). I still lose programs, but when I re-install them from Synaptic, I still have all my e-mail folders and settings and address book; all my browser favorites and plugins, all my documents, photos, music, etc.

If I *restore* a /home *directory* _after_ a new installation, it imposes old settings upon new software that may be incompatible. Another fresh install is pro'lly the easiest and quickest way to fix it.

Back up important stuff, but don't restore the entire /home _directory_. Rather, just restore your docs and pix and music, etc from external media. If you set up your new installation with manual partitions as described above, you needn't lose e-mail folders and favorites and settings thereafter. With every subsequent new install, simply *preserve* your /home *partition*.

If I interpreted your post too literally, I apologize. But maybe it'll help someone anyway. :)

-Robin

---

### Post by HyperHacker on 2010-01-18
I don't think I can do that since I use full-disk encryption. If there is a way to do a fresh install inside the encrypted container partition without wiping it out, I'd like to know.

Something ended up breaking somehow anyway (no idea what that was about) and I had to reinstall again anyway <.< so I excluded certain important-seeming directories from the restore, and that seems to have prevented the issue from re-occurring. (Except the Num Lock issue that's been around forever. I guess that'll never be fixed.)

---

