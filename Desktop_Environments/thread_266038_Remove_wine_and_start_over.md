---
title: "Remove wine and start over"
date: 2006-09-26
forum: Desktop Environments
---

### Post by IusedTObeSOMEONEelse on 2006-09-26
I followed a how-to thread on installing wine and I believe it's messed up. So I would like  to remove it the simplest way and I have done the synaptic thing but I want all removed and no trace of it left, Then I can start over agin

---

### Post by CatKiller on 2006-09-27
If you've already removed Wine through Synaptic, then delete your ~/.wine folder. That's where configuration settings and the pretend C: drive are kept.

---

### Post by IusedTObeSOMEONEelse on 2006-09-27
How would I do that please. I don't want to mess up a good thing here. Edgy is running pretty smooth for me and I don't wanna blow it apart yet

---

### Post by Lord Illidan on 2006-09-27
Simple.

rm -R ~/.wine

---

### Post by IusedTObeSOMEONEelse on 2006-09-27
~$ rm -R ~/.wine
rm: remove write-protected regular empty file `/home/------/.wine/drive_c/windows/system32/sfp/MSCREATE.DIR'?    am I supposed to do something else now?

---

### Post by Predius on 2006-09-27
> **MustangSallydd said:**
> ~$ rm -R ~/.wine
rm: remove write-protected regular empty file `/home/------/.wine/drive_c/windows/system32/sfp/MSCREATE.DIR'?    am I supposed to do something else now?
rm -fr or sudo rm -r

---

### Post by IusedTObeSOMEONEelse on 2006-09-27
~$ rm -R ~/.wine
rm: remove write-protected regular empty file `/home/--------/.wine/drive_c/windows/system32/sfp/MSCREATE.DIR'? rm -fr or sudo rm -r
rm: remove write-protected regular empty file `/home/-------/.wine/drive_c/windows/system32/sfp/ie/MSCREATE.DIR'?    I get the same thing over again!

---

### Post by echo $USER on 2006-09-27
> **MustangSallydd said:**
> ~$ rm -R ~/.wine
rm: remove write-protected regular empty file `/home/--------/.wine/drive_c/windows/system32/sfp/MSCREATE.DIR'? rm -fr or sudo rm -r
rm: remove write-protected regular empty file `/home/-------/.wine/drive_c/windows/system32/sfp/ie/MSCREATE.DIR'?    I get the same thing over again!

You need to use sudo

> sudo rm -rf ~/.wine

---

### Post by IusedTObeSOMEONEelse on 2006-09-27
:~$ sudo rm ~/.wine

Password:
rm: cannot remove `/home/-----/.wine': Is a directory

---

### Post by Lord Illidan on 2006-09-27
Did you by any chance make Wine mount your  actual windows drive?

---

### Post by IusedTObeSOMEONEelse on 2006-09-27
I'm not sure. Is there a way to find out? Thanks for your reply.

---

### Post by echo $USER on 2006-09-27
> **MustangSallydd said:**
> :~$ sudo rm ~/.wine

Password:
rm: cannot remove `/home/-----/.wine': Is a directory

You forgot to use the -rf command along with it.  -r is for recursive(deletes directories, -f is to force the action.  Once again, use this command...

> sudo rm -rf ~/.wine

Just copy that and paste into terminal, press enter... it will work.

---

### Post by IusedTObeSOMEONEelse on 2006-09-27
Did that. Nothing came but back to my user name. Hope that's all that was supposed to happen. Thanks

---

### Post by tuxcantfly on 2006-09-27
yep, that's all.

---

### Post by chajuram on 2006-09-27
if you prefer using nautilus then open it go to /home/<username>/
do Ctrl-h locate .wine and delete it.

---

### Post by IusedTObeSOMEONEelse on 2006-09-27
Forgive my ignorance, but how do I open nautilus?

---

### Post by CatKiller on 2006-09-28
> **MustangSallydd said:**
> Forgive my ignorance, but how do I open nautilus?

Nautilus is the name of the File Manager/Windows Explorer style file browser. If you're looking at icons of files, then you're in Nautilus.

---

### Post by Jeremy23 on 2006-09-28
> **MustangSallydd said:**
> :~$ sudo rm ~/.wine

Password:
rm: cannot remove `/home/-----/.wine': Is a directory

You probably left the -R out.
```
~$ sudo rm -Rf ~/.wine
```
should work.

---

### Post by vseehua on 2006-09-28
> **MustangSallydd said:**
> :~$ sudo rm ~/.wine

Password:
rm: cannot remove `/home/-----/.wine': Is a directory

when you are using sudo, the home directory refers to the superuser root at /root.

use this command instead:

```
sudo rmdir -rf /home/<username>/.wine
```<username> refers to your log in name...

hope that helps...cheers~

---

### Post by IusedTObeSOMEONEelse on 2006-09-28
: No such file or directory
:~$ sudo rmdir -rf /home/-----/.wine
Password:
rmdir: invalid option -- r
Try `rmdir --help' for more information.
~$ sudo rmdir -f /home/-----/.wine
rmdir: invalid option -- f
Try `rmdir --help' for more information.~$ ~$ sudo rm -Rf ~/.wine
bash: ~$: command not found

---

### Post by IusedTObeSOMEONEelse on 2006-09-28
This may sound silly, but my ?? regarding"How do I get to Nautilus} was not answered.

---

### Post by CatKiller on 2006-09-28
Yes it was. Go to Places -> Home Folder. The window that opens is a Nautilus window. If you don't believe me, type ```
nautilus
``` into a terminal. Same thing.

---

### Post by IusedTObeSOMEONEelse on 2006-09-28
Thanks CatKiller, I believe I'm all set now and it's gone. Now I want to try and put wine in with out any screw-ups. I followed a winetools how-to last week and that is what started this whole mess. Any one with insight is welcome to help me out.

---

