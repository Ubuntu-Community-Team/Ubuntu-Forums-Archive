---
title: "Empty and unresponsive desktop"
date: 2013-12-06
forum: Desktop Environments
---

### Post by tombaugh on 2013-12-06
Hi all,

When I started my Xubuntu 13.10 laptop this morning all I got after logging in was an empty desktop. The panel is not there and neither is the mouse pointer so there is nothing I can do. The only unusual thing I did was to connect my TV to watch a movie last night. Any thoughts?

Thanks!

---

### Post by mörgæs on 2013-12-06
Can you boot into recovery mode?

---

### Post by tombaugh on 2013-12-06
Yes, I ran fsck and "repair broken packages" but that didn't help. However, I found that the message "system program problem detected" flashes briefly on the screen (had to make a video to be able to read it), which apparently is often caused by video driver issues. I'll look into that now.

Thanks

---

### Post by Toz on 2013-12-06
Possibly a corrupt sessions cache. Try clearing it (Settings Manager -> Session and Startup -> Session -> Clear saved sessions) and logging out and back again (do not check the "Save sessions" option in the logout dialog).

If that doesn't work, you may need to clear it manually.
1. Before you login, go to the first console (Ctrl+Alt+F1)
2. Log in to the text console
3. Run:
```
cd $HOME/.cache
rm -rf sessions
```
4. Go back to the gui console (Ctrl+Alt+F7)
5. Login

---

### Post by tombaugh on 2013-12-06
Sorry, I wasn't very clear, I am able to choose recovery mode get to the menu with dpkg, fsck, etc. but resuming boot from there gives the same result. I now chose root shell and cleared the sessions but no luck...

---

### Post by Toz on 2013-12-06
> **tombaugh said:**
>  I now chose root shell and cleared the sessions but no luck...
You need to clear the sessions for your user account, not the root account (it wasn't clear which saved sessions you deleted). Either startup normally and try again (before you login) or from the root shell, delete your user's session cache.

---

### Post by tombaugh on 2013-12-06
I did clear the sessions for my user, not for root. Also, I don't seem to be able to use keyboard shortcuts, although my macbook keyboard and sticky keys (broke my wrist yesterday) may complicate things.

Thanks again

---

### Post by Toz on 2013-12-06
There is a log file in your home directory (.xsession-errors and .xsession-errors.old (for the previous login)). Have a look through there to see if there are any clues as to what is causing the hangups.

---

### Post by tombaugh on 2013-12-06
No clues, to me at least:

> openConnection: connect: No such file or directorycannot connect to brltty at :0
Script for cjkv started at run_im.
Script for default started at run_im.

---

