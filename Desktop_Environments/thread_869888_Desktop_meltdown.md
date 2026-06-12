---
title: "Desktop meltdown"
date: 2008-07-25
forum: Desktop Environments
---

### Post by claschxtreme on 2008-07-25
I need some serious help here, the troubles began when i upgraded to hardy heron but it had been getting better, in some respects and worse in others .. until today when i experienced a total break down of gnome.
First my trash icon disappeared from the desktop about a moth ago, then some desklets started to act funny on login, sometimes popping up all over, picture colors and videos have turned very dark.
After today's update all my desktop icons are gone, compiz won't work (i can still access settings but it just has no effect), on login both upper and lower bars are empty : after ctrl-alt-backspace the bars are populated again but are sometimes irresponsive.

Where to begin?

gconf-editor shows a lot of empty settings

I won't try a new install since there are things that still work pretty good on this machine that i haven't got working so well on others.

---

### Post by andrewc6l on 2008-07-25
You might want to try creating a new user and logging in as that instead of your existing user. If that works, you've got a few choices:

1. (hardest) Compare the hidden files for each user and copy over the working settings to your original user
2. (simpler) Copy the original user's files to the new user's ~/ and chown them to be owned by the new user.
3. (slightly harder) Copy the original user's files to somewhere else, then blow away the original user and recreate it with the same userid / groupid. Then copy the files back.

---

