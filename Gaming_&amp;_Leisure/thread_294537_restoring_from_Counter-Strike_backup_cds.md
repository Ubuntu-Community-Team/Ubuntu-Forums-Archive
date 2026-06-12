---
title: "restoring from Counter-Strike backup cds"
date: 2006-11-06
forum: Gaming &amp; Leisure
---

### Post by anonymous_user on 2006-11-06
I tried running steambackup.exe under wine, but then i get an error message saying: 

Could not execute the external program
C:/program files/steam\steam.exe

What should I do?

---

### Post by dbd on 2006-11-06
you could just backup the gcf files yourself from c:\program files\steam\steamapps\

If you are backing up to DVD or another harddrive then that will be easy, but if you want to back up to CDs then some of these files will be too big to fit on a single CD, so you'll have to split them between cds. I've never done this myself, but it looks like you can do it with tar, see here for more info:
[http://www.gnu.org/software/tar/manual/tar.html#Multi_002dVolume-Archives](http://www.gnu.org/software/tar/manual/tar.html#Multi_002dVolume-Archives)
If that pages makes no sense to you then just say and I'll translate into non-techie speak :)

---

### Post by anonymous_user on 2006-11-07
so that means i cant use my existing backup?

ill just download counter-strike then.

---

### Post by dbd on 2006-11-08
Not sure, what format are the backups in? Are they just gcf files on the cd?

---

### Post by anonymous_user on 2006-11-08
i used the backup (wizard) from Steam. its an executable and the backup files have their own extension (dont remember atm).

---

### Post by dbd on 2006-11-10
hmmm, if you havn't already guessed, I don't really know much about steambackup! So I'm not sure what to suggest.

Do you have access to a windows install? Because if you do then you could restore your backups there, and then you'd have the gcf files you need, so you can just copy them over to your linux install. 

(Or if you want to have both a linux install and a windows install then in the linux install just have symbolic links to the windows gcfs).

---

