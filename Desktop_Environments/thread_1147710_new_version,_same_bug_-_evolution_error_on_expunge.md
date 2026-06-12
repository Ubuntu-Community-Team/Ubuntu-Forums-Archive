---
title: "new version, same bug - evolution error on expunge on Ubuntu 9.04 - Jaunty"
date: 2009-05-03
forum: Desktop Environments
---

### Post by costamatrix on 2009-05-03
Hi folks... i have this old bug on my evolution...

i cant expunge any folders (like the junk folder)...when i try, i get the error:

[IMG]http://www.piadasonline.com.br/_images/Screenshot-Evolution%20Error-1.png[/IMG]

"Error storing '~/.evolution/mail.....' 
Summary and folder mismatch, even after a sync.


Any help people?

---

### Post by jeroenvrp on 2009-05-03
This has nothing to do with a new version, because it's properly related to files in your home folder.

Close Evolution. Check if that file in the .evolution folder is not set to read only or is owned by another user. If that is the case, please correct it, and restart Evolution.

If that is not the case, try to delete the files; *Sent.cmeta*, *Sent.ibex.index* and *Sent.ibex.index.data*. [COLOR="Red"]Don't delete the file *Sent*[/COLOR], because that is your mailbox. Restart Evolution and click on the Sent folder. It should regenerate your index. Properly you have to mark them all as read again.

Good luck.

---

### Post by hictio on 2009-05-03
Is that using an IMAP account? I have been using Evolution as the default email client since Hardy, and I haven't see that error before.

---

### Post by jeroenvrp on 2009-05-03
@hictio: I don't think so. It's a file located under *local* and at the end it reads *mbox*.

---

### Post by costamatrix on 2009-05-03
hi folks...

answering...i use pop for gmail...

i check the .evolution directory... all files and directorys belongs to my user...so its ok...

i check the internet and several users have reported this same problem on older versions of evolution/ubuntu....

i have a little bit of fear to try this solution of delete some files....

why i have to do this? it is a bg of evolution right?

and another thing...the problem occured when i tried to expurge several folders: trash, junk....

---

### Post by nab on 2009-06-27
Hi,

I have the same problem with drafts.

I shutdown evolution /home/nab/.evolution/mail/local and deleted in /home/nab/.evolution/mail/local all files Drafts*.*.

After restarting evolution the old titles were still shown in evolution and expurge still doesn't work.

Any suggestions?

TIA,
Niko

---

### Post by nab on 2009-07-04
well, I forgot about this tread so I wrote the solution in my own. 

Here is the link:
[http://ubuntuforums.org/showthread.php?t=1204369]("http://ubuntuforums.org/showthread.php?t=1204369")

Sorry about that.

---

### Post by Ian Sinclair on 2010-11-24
Got this problem on Ubuntu 10.04. Ultimate solution - change to Thunderbird!:P

---

### Post by claracc on 2010-11-24
You can keep evolution and solve the problem in this way:

Close evolution, go to Places, personal folder, select see hiden files, then go to .evolution/mail/local, there, delete file folders.db, restart evolution and the problem has to be fixed.

---

