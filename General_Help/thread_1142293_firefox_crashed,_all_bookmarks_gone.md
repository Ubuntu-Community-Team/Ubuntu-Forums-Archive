---
title: "firefox crashed, all bookmarks gone"
date: 2009-04-29
forum: General Help
---

### Post by redruby on 2009-04-29
firefox has crashed 2 days after moving to 9.04. All my bookmarks have been erased. very odd. its as if firefox is only half working, the address bar doesn't seem to work. I was using google earth at the time. Any thoughts? Please. And yes 9.04 seems slower and more cumbersome, boots quick though!

---

### Post by lovinglinux on 2009-04-29
Looks like a corrupted profile. Create a new profile and check if it works.

---

### Post by mihai.ile on 2009-04-29
if you look in ~/.mozilla/firefox you have there your user profile (one of the folders) and inside there should be a folder with bookmarks backup or something like that.
In firefox open the bookmark manager and select import and point to one of the backups. note that importing like this erases the ones you have now, do a backup of the one that currently have if important.

---

### Post by sahabcse on 2009-04-29
Fire fox backup and restore follow below url

[http://sahabm.blogspot.com/2009/02/mozilla-bookmark-backup-and-restore.html](http://sahabm.blogspot.com/2009/02/mozilla-bookmark-backup-and-restore.html)

---

### Post by redruby on 2009-04-29
I have found out that I can get firefox working again if I start it from root. That must have happened whilst I was using Googleearth which I also need to start from root. I dont really understand.....
Can I change that so that I can start those application as User?

---

### Post by sahabcse on 2009-04-29
Hi

This may be help

[http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/](http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/)

---

### Post by lovinglinux on 2009-04-29
Starting Google Earth or Firefox as root is a bad idea. Don't do it. Make a backup copy of the contents of ~/.mozilla, then delete it and start Firefox.

---

### Post by mihai.ile on 2009-04-30
I also suggest not to use applications (especially Firefox) in root, as possible vulnerabilities could be better exploited.
as the other user said just backup ~/.mozilla, delete it and start firefox.

---

### Post by nucleuskore on 2009-04-30
And after you do the above use an addon like foxmarks to backup your bookmarks

---

### Post by redruby on 2009-05-01
Seems to be resolved, instead of trying to start Firefox in any other way, In Terminal I simply used "sudo firefox" (as user) and all was back to normal.

---

### Post by lovinglinux on 2009-05-01
See **Solution** [*[COLOR="Red"]**FOT001**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT001).

---

### Post by mihai.ile on 2009-05-01
If you run sudo before any command (as a user) you become root, super admin so this even if seems an easy solution it will come with many drawbacks.

---

