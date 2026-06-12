---
title: "Firefox in Linux crashes when I load this page?"
date: 2009-03-27
forum: General Help
---

### Post by swraman on 2009-03-27
Hi,

THis page loads fine in FF for windows.  But if I try to load it in Ubuntu (fully updated) the flash player starts to load its content (it shows a progress bar), but then as soon as it is loaded FF just closes abruptly.

[http://blog.indecisionforever.com/2009/02/10/the-daily-show-bill-oreilly-exposes-the-scum-bag-paparazzi-at-the-oreilly-factor/](http://blog.indecisionforever.com/2009/02/10/the-daily-show-bill-oreilly-exposes-the-scum-bag-paparazzi-at-the-oreilly-factor/)

Again, it works fine in Windows.

Anyone else have the same problem?

---

### Post by Locutus_of_Borg on 2009-03-27
works fine for me, including video

---

### Post by sekinto on 2009-03-27
I do not have this problem. Are you using a 32-bit or 64-bit Firefox/Flash?

---

### Post by Chemical Imbalance on 2009-03-27
> **Locutus_of_Borg said:**
> works fine for me, including video

same here.  I'm on 64-bit jaunty with the latest flash.

---

### Post by Yashiro on 2009-03-27
Flash crashes the browser on me. 
8.04/64/Latest 64bit Flash/Ati Fglrx driver.
Only 64bit flash is installed, no other crud is left over. 

Happens on alot of flash movies, but not the more popular ones.
It also occurs on a fresh Jaunty install with the same setup but using the Open source video driver.
The same videos fail in Opera too.

Which means it's probably the Flash plugin code or an Audio related issue.
Basic debugging doesn't highlight anything in particular.

---

### Post by lovinglinux on 2009-03-28
> **swraman said:**
> Anyone else have the same problem?

[http://www.google.com/search?hl=en-US&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=lkR&q=flash+firefox+crash+site%3Aubuntuforums.org](http://www.google.com/search?hl=en-US&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=lkR&q=flash+firefox+crash+site%3Aubuntuforums.org)

---

### Post by swraman on 2009-03-28
It isn't flash, other flash video player and apps work fine.

Now everything in firefox seems to be acting up - my back and forward buttons dont work, downloads don't ownload (after I tell it to save the file, it just dosn't save).  Firefox also randomly closes, and when it opens it doesn't have an of the file/edit etc...lots of little problems.

I think its time to reinstal.. ff.

---

### Post by Chemical Imbalance on 2009-03-28
Check your update-manager for the 3.0.8 update to firefox and see if that solves your problems.

---

### Post by swraman on 2009-03-28
OK, new developements....

Reinstalling FF did nothing.

I can run firefox as an admin (sudo firefox) and it runs fine.

So im guessing it is a problem with my user's FF files.

I deleted the contents of /home/user/.mozilla and now i have even more problems.  FF Doesn't start at all, it just brings up a thing that says "Starting Mozilla Firefox" then it closes.

I tried deleting the entire /home/user/.mozilla folder, but it won't delete.  If I try "cd /home/user/.mozilla" and it says permission denied.

I don't know what to do, I cant acess the folder anymore, and FF won't start (unless I run as an admin).

Any advice?

Thanks

---

### Post by Chemical Imbalance on 2009-03-28
You just need to change the permissions of the folder:

sudo chmod -R u=rwx /folder/path/here

---

### Post by swraman on 2009-03-28
ran the chmod command, no errors.  I was able to get rid of the .mozilla folder.

But Firefox still has the same problem.  It doesn't open.

Again, it has to be something to do with my user data, because I can run FF as an admin.

if I run "firefox" nothing happens.
If I click on the FF icon (it says the command is "firefox %u" ???) it says "Starting Firefox Web Browser" in the tray briefly, then disappears.

Advice?

Thanks

---

### Post by swraman on 2009-03-28
Problem solved.

If anyone else needs to know:
From what I gather, it started when, somehow, FF process did not end properly.  So every time I try to start FF, it would give an error saying that the FF process is still running and I had to end it first.

Not knowing how to, I ran "sudo firefox".  This changed the owner of my .mozilla folder to "root".

I eventually ran "killall firefox" so FF would start, but FF would now not run b/c it couldnt write to the .mozilla folder.

Now after I changed the owner of the .mozilla folder, FF worked by my bookmarks didnt load and a lot of other random things didnt work (eg. the Google search bar didnt work).  I also couldn't create a shorrtcut for FF on my desktop.

I finally found out that these were all related; I was out of HD space :lolflag:.

If anyone else is as dumb as me to have both of these problems at the same time, I hope I can save you some time by you reading this.

:lolflag:

---

### Post by Yashiro on 2009-03-29
This has nothing to do with your original problem though. Unless you installed the flash plugin manually to your root filesystem with the wrong permissions.

---

### Post by swraman on 2009-03-29
Im guessing the flash problem was because I did not have sufficient hard drive space.  It works now.

Thanks :)

---

