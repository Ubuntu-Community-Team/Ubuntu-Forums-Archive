---
title: "Geany - input/output error"
date: 2009-04-10
forum: General Help
---

### Post by haaglin on 2009-04-10
Hi. 

I'm using geany to edit text files over ftp. This has worked fine until i started editing files on a webserver on the same network. I can open files, but not save.The wierd thing is that i get this error only on files on my server in the same network, and _only_ with geany. 

Some info:

The server is running ubuntu with ISPConfig. When i started having this problem it was running 7.04. I then upgraded to 7.10 and 8.04.

My computer is running intrepid.

I have edited my /etc/hosts to make domains work to my webserver.

I'm using nautilus with gvf

geany is version 0.16 (same problem with 0.14 and 0.17svn)

The error i get is "Error saving file (Input/output error)."



Anyone got a solution?

---

### Post by haaglin on 2009-04-15
Bump

---

### Post by huroliu on 2009-05-19
I get this error too with Geany 0.17 on Jaunty when I try to save the file in .gvfs folder.
Geany has powerful editing capabilities, but I have to edit remote files often and native remote file support is highly needed.
By the way Bluefish (unstable v1.3.4 has even a synchronize files option too), Gedit and Anjuta can edit remote files without problems.
Does anyone know a workaround for this error?

---

### Post by guywithcable on 2009-05-19
Can you run Geany from the terminal, then try to save, and see if it gives any more details?

---

### Post by huroliu on 2009-05-20
[FONT=DejaVu Sans, sans-serif][SIZE=2]Thanks for advice![/SIZE][/FONT]
 [FONT=DejaVu Sans, sans-serif][SIZE=2]Running geany -v form the terminal results (when trying to save):[/SIZE][/FONT]
 [FONT=DejaVu Sans, sans-serif][SIZE=2](geany:8815): Gtk-WARNING **: Operation not supported by backend[/SIZE][/FONT]
 [FONT=DejaVu Sans, sans-serif][SIZE=2]Save as with another file name works, the problem occurs only when trying to overwrite a file after modifying its content but replaces the document with empty content.[/SIZE][/FONT]

---

### Post by guywithcable on 2009-05-20
Odd. You should try using SFTP (SSH) instead of FTP. I use SFTP to edit files on my website's server, and I haven't had this error with Geany. Plus, SFTP is more secure than FTP :)

To set it up, just install SSH from Synaptic, then you can configure it in /etc/ssh/

---

### Post by morganpatrick on 2009-07-23
I just made a change to the homepage of a client's home page, simple phone number change whatever, tried to save, it, got this error, and the ******* file on the server is now completely empty, I didn't delete the code. It just gave me an import/outport error and emptied the file. I am completely screwed unless ubuntu puts up a backup somewhere.

---

### Post by haaglin on 2009-07-23
I dont think geany keeps an backup, but if you didn't close geany, you can open the file with gedit, paste the content and save.

---

### Post by guywithcable on 2009-07-26
> **morganpatrick said:**
> I just made a change to the homepage of a client's home page, simple phone number change whatever, tried to save, it, got this error, and the ******* file on the server is now completely empty, I didn't delete the code. It just gave me an import/outport error and emptied the file. I am completely screwed unless ubuntu puts up a backup somewhere.

Hope you backup. I was in your situation too many times, so I set up BackupPC. It's great, though I'd recommend something simpler, like sbackup, unless you like spending an entire day getting a backup server setup.

---

### Post by rootrhift on 2010-03-13
Yeah, I also have problems with remote file operations in Geany.  I've experienced that exact situation several times.

It's gotten to the point that I'm afraid to touch any remote file with Geany.  Which is a shame, because I like it so much...if only they would put code folding in gEdit...

---

### Post by ShibaOn on 2010-07-12
Hi all!

I found the solution. The trouble was be in write_data_to_disk function in document.c. It's fixed in 0.19 version of geany: [http://www.mail-archive.com/geany-devel@uvena.de/msg00950.html](http://www.mail-archive.com/geany-devel@uvena.de/msg00950.html) Look at

```
-        * remote filesystem. */
-       if (! file_prefs.use_safe_file_saving || doc->priv->is_remote)
+       // GVFS can be buggy, so let user choose the behaviour
+       if (! file_prefs.use_safe_file_saving )//|| doc->priv->is_remote)
        {
```

So, the solution is in compiling and installing of fresh version of geany from [http://www.geany.org/Download/Releases](http://www.geany.org/Download/Releases) ALSO you must change **use_safe_file_saving** to **true** in $HOME/.config/geany/geany.conf

P.S. Sorry for my English )

---

### Post by rootrhift on 2010-07-12
It doesn't completely solve the problem for me.  In fact it is still unusable.

When trying to save a remote file named "test" on two different FTP servers (server1, server2):

```
With use_safe_file_saving = true:
  On server1 I get: 
    "Error Saving File
     Failed to create file '/home/MY_HOME/.gvfs/ftp as USER on
     [www.URL.com/PATH_HERE/test.I7AUFV':](www.URL.com/PATH_HERE/test.I7AUFV':) No such file or
     directory"
    And it writes a 0 byte file named "test.I7AUFV" and each
    subsequent attempt to save writes a new 0 byte file with a
    new seemingly random 6 alpha-numeric extension tacked on to
    it, but leaves the original "test" alone.
  On server2 it saves correctly.


With use_safe_file_saving = false:
  On server1 it saves correctly.
  On server2 I get:
    "Error Saving File
     Input/output error"
    And it writes a 0 byte file, essentially wiping all changes.
```

This is most certainly a bug with GVfs as shell commands on GVfs mounted remote file systems express weird behavior as well, but the solution is to use GIO, and this is why gEdit, Nautilus, etc. work.  Because GIO somehow works around the bug, and probably why no one cares to fix GVfs.

A guy named Alexi made a *great* patch and posted it to the mailing list that COMPLETELY solves the problem, but it only applies to revision 4788 on document.c and won't apply too far afterwards due to changes to document.c.  This patch uses GIO for file saving and is why it works.  I still don't understand why Geany isn't using GIO, maybe because this only affects a small number of users?  But, my argument is that by upgrading the version of Glib to use GIO is worth it, because that is what GTK+ guarantees to work to save files.

Be warned that saving can still fail, in particular on some FTP servers.

Here is the link to the patch to revision 4788 of document.c:
  
  [http://www.mail-archive.com/geany-devel@uvena.de/msg01324/40_file_saving.dpatch](http://www.mail-archive.com/geany-devel@uvena.de/msg01324/40_file_saving.dpatch)

Using this I have never encountered a problem.

And here is the link to the archived e-mail:

  [http://www.mail-archive.com/geany-devel@uvena.de/msg01324.html](http://www.mail-archive.com/geany-devel@uvena.de/msg01324.html)

I hope somebody can update this patch for 0.19 (or better yet the latest Git/SVN :D) as I am not competent enough with C and don't know Geany's codebase.

---

### Post by bluefoot on 2010-09-15
I am experiencing the same problem.

True. The Alexey patch does not work with geany 0.19.
Too bad.

---

### Post by rootrhift on 2010-09-15
Hey bluefoot,

There's been a little more chatter about it on the mailing list.

Nick has made a patch for 0.19, but I haven't tested it myself yet.

Here is the link to the mail archive:

[http://lists.uvena.de/geany-devel/2010-September/003103.html]("http://lists.uvena.de/geany-devel/2010-September/003103.html")

and the link to the patch (which is at the bottom of the post):

[http://lists.uvena.de/pipermail/geany-devel/attachments/20100910/70217315/attachment.obj]("http://lists.uvena.de/pipermail/geany-devel/attachments/20100910/70217315/attachment.obj")

Note that Nick says that it doesn't make back-ups, so if you rely on that consider yourself warned.:)

Hopefully I'll get a chance to check it out soon as running 0.19 would be really nice.  Let me know if you apply it and how it goes.

---

### Post by bluefoot on 2010-09-16
> **rootrhift said:**
> Hey bluefoot,

There's been a little more chatter about it on the mailing list.

Nick has made a patch for 0.19, but I haven't tested it myself yet.

Here is the link to the mail archive:

[http://lists.uvena.de/geany-devel/2010-September/003103.html]("http://lists.uvena.de/geany-devel/2010-September/003103.html")

and the link to the patch (which is at the bottom of the post):

[http://lists.uvena.de/pipermail/geany-devel/attachments/20100910/70217315/attachment.obj]("http://lists.uvena.de/pipermail/geany-devel/attachments/20100910/70217315/attachment.obj")

Note that Nick says that it doesn't make back-ups, so if you rely on that consider yourself warned.:)

Hopefully I'll get a chance to check it out soon as running 0.19 would be really nice.  Let me know if you apply it and how it goes.

I am regularly on Fedora 13, but now I am on Ubuntu 10.4. And the patch works (at least, as I said, on ubuntu).

Thanks for the help.

---

### Post by bluefoot on 2010-09-21
Now I am getting segmentation fault. Trying to recompile.

---

### Post by bluefoot on 2010-09-21
> **bluefoot said:**
> Now I am getting segmentation fault. Trying to recompile.

no need to recompile.
some plugin is doing this. starting geany with -p and it works.

---

### Post by Bobly on 2010-10-29
> **guywithcable said:**
> Odd. You should try using SFTP (SSH) instead of FTP. I use SFTP to edit files on my website's server, and I haven't had this error with Geany. Plus, SFTP is more secure than FTP :)

To set it up, just install SSH from Synaptic, then you can configure it in /etc/ssh/

Resurrecting as this thread comes up in searches about the problem.


A fix is to connect to the server with Nautilus using SFTP (SSH) instead of FTP after which Geany will properly overwrite instead of appending.

---

