---
title: "Change Theme and now no title bar, mouse cursors displays X"
date: 2014-01-30
forum: Desktop Environments
---

### Post by kdesrosiers-2 on 2014-01-30
Hi,

In a fresh install of Xubuntu (12.04) after changing the theme and logging off (with the save desktop option), when I log back in. I have no more title bar, my mouse cursors displays an X. Worse... I don't have access to the window manager to re-modify the theme to see if it will solve my problem.

Is there a way with the terminal to solve this ?

This is my second time (first time I've re-install Xubuntu) :(. What's up with the theme ??? Is there a better tools to modify theme ?

Thanks

---

### Post by Toz on 2014-01-30
Hello and welcome to the forums.

Try clearing your sessions cache before you login.

From the login screen:
1. Go to the fist virtual console (Ctrl+Alt+F1)
2. Login to the text session.
3. Enter these commands:
```
cd .cache
rm -rf sessions
```
4. Go back to the GUI console (Ctrl+Alt+F7)
5. Log in.

Does it help? What theme were you selecting that caused this?

---

### Post by kdesrosiers-2 on 2014-01-30
Wow thanks, it works ! I dont remember what theme it was. Now that I have a solution I'll make some test playing with the theme and apperance and post the result.

---

### Post by kdesrosiers-2 on 2014-01-30
I played with theme and appearance several times with a logout, login each time... can't reproduce the problem.

If I have it back again, I'll repost here. Thanks for solving my problem.

---

### Post by Toz on 2014-01-30
It may have just been a random corruption of the sessions cache. I recall it being more of an issue on 12.04 (Xfce 4.8) than on later versions.

---

### Post by kdesrosiers-2 on 2014-02-04
Haha... I got the problem again.... this time I only changed the font from droid to arial. I did the change in the appearance and in the window manager.

---

