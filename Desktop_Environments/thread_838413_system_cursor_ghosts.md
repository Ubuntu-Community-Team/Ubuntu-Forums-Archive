---
title: "system cursor ghosts"
date: 2008-06-23
forum: Desktop Environments
---

### Post by rfrapp on 2008-06-23
I have Hardy installed on a Omnibook XE2, and pretty much all is well.  However, during login, and in some apps (so far Adobe Reader 8, from the medibuntu repository), rather than then installed theme, which works fine, I get the system theme.  That would be ok,  except that all of the pointers, cursors, etc. have two ghost images, plus the actual pointer.

Once logged in, or not in Adobe Reader, the installed theme takes over, but while in the app or during login it is somewhat annoying to see the "ghosts" (more so, of course, in the app than during login).

Any ideas of how to fix this, or where to look?  Yes, I am a n00b to Linux, but not otherwise ;-)

rfr

---

### Post by rfrapp on 2008-06-24
Found my own answer, I think.  I first tried to redetect the video card, which gave me more choices, but did not seem to solve the problem.  But, in playing with it, I managed to configure x in a way that made it display a blank screen ;-)

When I went to reboot in repair mode, and then chose to fix x, it worked fine.  While it fixed the incorrect resolution it must have also fixed the default system cursors.

rfr

---

### Post by rfrapp on 2008-06-24
Not so fast, as it turns out.  Sometimes, but not always, if I log out and back in, the system cursors will look fine.  However, if I then try to log out or shut down, the system crashes more often than not.  If I restart the x server first, the "ghosted" system cursors come back, and then I can log off or shut down fine.

Obviously something to do with the x server startup, but I have no idea what to look for yet.

rfr

---

