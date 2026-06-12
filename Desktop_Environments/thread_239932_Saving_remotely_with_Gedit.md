---
title: "Saving remotely with Gedit"
date: 2006-08-20
forum: Desktop Environments
---

### Post by leetcharmer on 2006-08-20
I've been trying to update my website's html code remotely via gedit and for some reason, it won't let me save to the server unless I close out of that tab.  Does anyone know how to save while it's still open so I can continue to edit as I go -- with convenience?  Thanks!

---

### Post by zami on 2006-08-20
I'd **love** to know this also.

Are you able to really remotely save after closing the tab, or are you having to close the entire gedit program?  I have to shut down the entire gedit program... wich is kind of a pain because I'm usually editing more then one file at a time (ex: an .html and .css file being worked on simultainiously).

Here's to hoping for a solution!  

-zami

---

### Post by sapo on 2006-08-20
Enjoy ;)

[http://ubuntuforums.org/showthread.php?t=238058&highlight=filezilla+linux](http://ubuntuforums.org/showthread.php?t=238058&highlight=filezilla+linux)

---

### Post by zami on 2006-08-20
Thanks for the pointer!  I'll give that a whirl!

-zami

---

### Post by DC@DR on 2006-08-20
I didnt experience the same problem. Did you mean that when you're editing your files directly in your website host's FTP server, then close gedit, the files wouldn't be updated back to the server?. I have tried something similar and it worked just fine for me. View/Edit the file, when close the editor, it asks for reupload back to the server...Everything goes as expected..

---

### Post by zami on 2006-08-20
> **DC@DR said:**
> I didnt experience the same problem. Did you mean that when you're editing your files directly in your website host's FTP server, then close gedit, the files wouldn't be updated back to the server?. I have tried something similar and it worked just fine for me. View/Edit the file, when close the editor, it asks for reupload back to the server...Everything goes as expected..


I think the OP is asking for a way to edit and remotely save **without** closing the file at all.  So he can edit, save, edit, save, edit, save, and so on, without having to re-open the file between every change made.

I'm pretty much wondering the same.  In my case I'm working on a .css file and it's easiest to edit and save, and veiw the results right there on the page the .css file is affecting.  

(But hell, in my case I'd be very happy to just close the file... I have to close down the entire gedit program before gFTP will ask if I want to upload the changed file.  Wich is a pain since I'm usually working on more then one file at a time, and don't want to close them ALL down just to have gFTP offer to upload one of them.)

-zami

---

### Post by zami on 2006-08-20
> **sapo said:**
> Enjoy ;)

[http://ubuntuforums.org/showthread.php?t=238058&highlight=filezilla+linux](http://ubuntuforums.org/showthread.php?t=238058&highlight=filezilla+linux)

Darn darn!

Filezilla doesn't currently have a remote edit ability, at all!  Or if it does I haven't found it.

Still, tis just in it's infancy on Linux.  I'll keep an eye on it.  Thanks again for the headsup!

-zami

---

### Post by scxtt on 2006-08-20
what DE are you using?

i can SSH (connect to server) and edit a file in gedit, then save it w/o closing ... {Gnome}

i can fish (from konqueror) and edit a file in kate, then save it w/o closing ... {KDE}

if you're just using FTP, it will never work the way you want ... you're not really editing the file 'over the network' in-as-much-as you're downloading a temporary copy, editing it, then uploading it ...

---

### Post by zami on 2006-08-20
> **scxtt said:**
> what DE are you using?

i can SSH (connect to server) and edit a file in gedit, then save it w/o closing ... {Gnome}

i can fish (from konqueror) and edit a file in kate, then save it w/o closing ... {KDE}

if you're just using FTP, it will never work the way you want ... you're not really editing the file 'over the network' in-as-much-as you're downloading a temporary copy, editing it, then uploading it ...

I'm sorry, I said "Filezilla doesn't currently have a remote edit ability, at all! Or if it does I haven't found it."... bad verbage on my part.  What I mean is, I can't just quickly download&open a remote file for editing, through Filezilla  (at least not yet!).  With filezilla you have to do the slowpokey, save to local directory, and open and edit from there, then re-upload from that directory.  (So Windows Filezilla is stupid fast, gFTP takes a few more steps, and Linux Filezilla takes even more steps.)

What is this SSH you speak of that allows you to edit in gedit, then save without closing?

::is very intrigued::

-zami

---

### Post by scxtt on 2006-08-20
my comment wasn't directed @ the FileZilla aspect - tho what you describe is the 'problem'/'issue' i was talking about - ftp isn't meant to work that way ...

SSH is a secure shell, allows you to connect to a remote host and issue commands as if you were sitting right in front of it (if you have an account on the box) ...

in Gnome you can 'connect to server' and have ssh essentially 'forward' files to your GUI gedit where you can edit / save them w/o closing and reuploading ...

in KDE you can use fish via konqueror (type **fish://<username>@<hostname>** into the location bar) to open a file in kate, edit and save ...

and you shouldn't need to install anything in either DE for this to work ... you have ssh outbound access by default for both and fish is built-in to KDE ...

---

### Post by zami on 2006-08-20
Well darn!  That sounded very promising.  But after wrestling with it and failing miserably(Places>Connect to Server fill in info and get a never ending request for password), I wrote to my hosting company.

Sadly they "do not support SSH for security reasons". 

Ah well.  It was worth a try and it might be just what the OP was looking for, if his host allows it.

Despite FTP not being intended to work like the OP and I are trying to make it work... well it fake-worked that way wonderfully with Windows Filezilla & FileEditor, and it ALLMOST works that way with gFTP & gedit.  

I do understand I'm not realy editing files right there on the remote server, and that my FTP program it's saving the files to a temporary local directory.  But it's so quick quick quick!  I just want to make the save & upload quick quick quick as well!

So, no SSH for me.  In the meanwhile I'll work slowpokey and keep my eyes on how Filezilla for linux comes along.

-zami

---

### Post by fubarbundy on 2006-10-28
From [http://bamboomoon.org/gnome/use_gedit_to_edit_files_across_ftp](http://bamboomoon.org/gnome/use_gedit_to_edit_files_across_ftp) you can enable this curiously (stupidly I would say) disabled feature by adding ftp to the list of writable VFS schemes through gconf-editor under apps > gedit-2 > preferences > editor > save

---

