---
title: "Reset Firefox settings"
date: 2009-04-28
forum: General Help
---

### Post by eyescovered on 2009-04-28
hey all. in ubuntu 9.04, how can you uninstall all the extensions and restore all defaults so it's like you just installed it?

---

### Post by Jim Danner on 2009-04-28
Close Firefox, hit ALT+F2, type *firefox -P* and choose to create a new profile.

---

### Post by Brandon Williams on 2009-04-28
Creating a new profile should work, but you will have to set up the new profile to be the default so that you don't have to select a profile every time you start firefox.

Alternatively, you can close firefox, open a terminal and 'rm -Rf .mozilla/firefox/*.default', and then start firefox up again.

---

### Post by eyescovered on 2009-04-28
> **Brandon Williams said:**
> Creating a new profile should work, but you will have to set up the new profile to be the default so that you don't have to select a profile every time you start firefox.

Alternatively, you can close firefox, open a terminal and 'rm -Rf .mozilla/firefox/*.default', and then start firefox up again.

how do you make it the default profile?

---

### Post by codeseer on 2009-04-28
> **eyescovered said:**
> how do you make it the default profile?

If you're ditching the old profile, just use the profile manager until you can transfer your bookmarks and such, then delete the old profile. By default, Firefox will start with the profile you last used.

---

### Post by eyescovered on 2009-04-28
> **codeseer said:**
> If you're ditching the old profile, just use the profile manager until you can transfer your bookmarks and such, then delete the old profile. By default, Firefox will start with the profile you last used.
yep, totally ditching! thanks much!

---

### Post by Jim Danner on 2009-05-21
> **Brandon Williams said:**
> Creating a new profile should work, but you will have to set up the new profile to be the default so that you don't have to select a profile every time you start firefox.For the record (in case other people find this thread), the setting as default happens automatically. So *firefox -P* is probably the fastest procedure (though the other one works too -- you just lose the old profile so make sure there's *nothing* in there you might want to keep).

---

