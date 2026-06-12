---
title: "Hard Disk is full and is prohibiting boot."
date: 2009-03-19
forum: General Help
---

### Post by neon100 on 2009-03-19
Here is a stupid mistake that i did. I scheduled a long list of downloads to desktop without realizing that the root disk space was about to end. 

Sometime in the night.. the HD became full and all downloads stopped. I woke up in morning and turned my computer off. But now when i turned it on .. its not booting into ubuntu. Its says something about "Cannot write the server X" 

Kindly suggest a solution while considering following:

- I can boot into Windows XP
- I dont have any live/installation CD.
- Don't have a fast internet connection to download files great than few MBs.
- Cannot boot into recovery mode either.

:popcorn:

---

### Post by neon100 on 2009-03-19
By the way, why doesn;t ubuntu has any mechanism like windows to prohibit such incident?

---

### Post by neon100 on 2009-03-19
tell me some procedure to delete some files from my ubuntu desktop so that i can boot again.

---

### Post by drs305 on 2009-03-19
there are windows apps that let you access ext3 file systems.  You can read about them here and then should be able to access your ubuntu partition and delete some of the files you downloaded.

[http://www.howtoforge.com/access-linux-partitions-from-windows]("http://www.howtoforge.com/access-linux-partitions-from-windows")

---

### Post by bruno9779 on 2009-03-19
How about using live cd?

---

### Post by PmDematagoda on 2009-03-19
Even if you cannot start the X-Server, you still must be able to use the computer through the CLI. Try this, once Ubuntu has booted up, press Ctrl+Alt+F1 to move to a tty. Then login with the credentials you would normally use. After that it is a pretty simple matter of going through the stuff in your hard drive and deleting the stuff you want and to free a little space(about 500 Mb should be sufficient).

The commands you maybe interested in:-
```
cd - to change directory
ls - to list the contents in a directory.
mv - to move a file/directory to another location.
rm - to delete a file or directory.
sudo reboot - to reboot the computer once you are done.
```
if you face any problem with a command you can get help using:-
```
man *command*
```

---

### Post by neon100 on 2009-03-19
> **drs305 said:**
> there are windows apps that let you access ext3 file systems.  You can read about them here and then should be able to access your ubuntu partition and delete some of the files you downloaded.

[http://www.howtoforge.com/access-linux-partitions-from-windows]("http://www.howtoforge.com/access-linux-partitions-from-windows")

My file system is ReiserFS. But I found some windows applications for this file system too. Thanks for the suggestion. But is it secure to the file system's health to access it from windows. Because my brother once mentioned that accessing linux partition from windows MAY corrupt some data there.

> **bruno9779 said:**
> How about using live cd?
I don't have it bro.

---

### Post by drs305 on 2009-03-19
I don't use ReiserFS but I am not aware of problems with the file system after accessing it from windows. Just make sure you only delete non-system files.

---

### Post by lykwydchykyn on 2009-03-19
> **neon100 said:**
> By the way, why doesn;t ubuntu has any mechanism like windows to prohibit such incident?

Traditionally this kind of thing was mitigated by partitioning the system so that the partition essential for boot was not going to fill up.

But even when the disk has become full I've never seen it unable to boot.  Usually normal users just can't log in, and you have to go to recovery mode to boot.

Can you not download a liveCD image on Windows and create a new one?  Or live USB?  Just curious, it would make things a lot simpler.

---

### Post by neon100 on 2009-03-19
> **PmDematagoda said:**
> Even if you cannot start the X-Server, you still must be able to use the computer through the CLI. Try this, once Ubuntu has booted up, press Ctrl+Alt+F1 to move to a tty. Then login with the credentials you would normally use. After that it is a pretty simple matter of going through the stuff in your hard drive and deleting the stuff you want and to free a little space(about 500 Mb should be sufficient).

The commands you maybe interested in:-
```
cd - to change directory
ls - to list the contents in a directory.
mv - to move a file/directory to another location.
rm - to delete a file or directory.
sudo reboot - to reboot the computer once you are done.
```
if you face any problem with a command you can get help using:-
```
man *command*
```


thats great but when i type command for help like "copy --help" it gives a long list and all that text is too big for screen. So it only lists the last 23 lines and i cannot see the lines above. 

In windows i used to write /p after the command to make a pagewise. How can i do that here?

---

### Post by drs305 on 2009-03-19
> **neon100 said:**
> thats great but when i type command for help like "copy --help" it gives a long list and all that text is too big for screen. So it only lists the last 23 lines and i cannot see the lines above. 

In windows i used to write /p after the command to make a pagewise. How can i do that here?

Add this to the cat command " | less "

There is also a "more" option. You can read about them by typing
```
man less
man more
```

---

### Post by PmDematagoda on 2009-03-19
If you use the manpages using the man command I told you about, you could just go through the help like a book using the up and down keys. You close a man using the "Q" key.

And may I ask what you are doing with copy? I haven't heard of copy as a command on a normal Ubuntu install.

---

### Post by neon100 on 2009-03-19
RM command worked. Thank you all. You people are great. 

If i had a million dollars, i would have donated it all to such a wonderful community here.

---

