---
title: "Problems with Tar"
date: 2006-09-05
forum: Desktop Environments
---

### Post by PCalitrack on 2006-09-05
Hey guys,

For some reason I am no longer able to untar files. I am trying to install themese for Gnome from GNOME-Look.org, yet it seems like my tar thing is broken. I did use the ">" command for some C programming yesterday. I am wondering if maybe that redirected my standard input elsewhere and maybe I have to change my standard input back to the keyboard? I'm confused...

> >tar -xvvzf ColdPlastic.tar.gz 

gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Error exit delayed from previous errors

> >tar -zxf 13548-Gnome_MacOS-X_Aqua_Theme_20040730.tar.gz 

gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Error exit delayed from previous errors

---

### Post by kidders on 2006-09-06
I doubt that's the problem ... ">" is an operator that only performs redirects on a per-command basis.

The references to stdin you quoted are from the **gzip** tool, not **tar**. **tar**'s -z option tells it to pass archives through **gzip**, which seems to be running out of data sooner than it expects.

If I were you, I'd do the two-step process one step at a time (ie untar and *then* gunzip your archive ... or is it the other way round?!), firstly to satisfy yourself about your > redirection issue, and secondly, so you can get **gzip** to confirm that your archives are okay.

I suspect however that they're not and that you should try downloading them again.

---

### Post by PCalitrack on 2006-09-06
Thanks for the quick response. I tried to do the gzip first and here's what I got:

> >gzip -dv xournal.tar.gz 

gzip: xournal.tar.gz: unexpected end of file

What do you mean by confirming my archives are ok? Are you talking about the individual tar.gz files I downloaded or the files that run gzip/tar?

---

### Post by kidders on 2006-09-06
Hmm. Nasty.

What I meant was that gzip has many options that can be used to check whether your archive is intact, such as "-t" (test) or "-l" (list). If they were to tell you that you're archives are alright, then you **know** something's gone funny.

Is there any way you can compare what you've downloaded with what you ought to have downloaded? I'm willing to bet your archives are corrupted :-(

In the unlikely event that there really is a problem with your gzip utility, I've attached one for your reference. If you can gunzip it, your gzip is fine.

What I'm expecting is:

```

tar -xzf test.tar.gz
   (works okay)

tar -xzf ColdPlastic.tar.gz
 gzip: stdin: unexpected end of file
 tar: Child returned status 1
 tar: Error exit delayed from previous errors

```

---

### Post by PCalitrack on 2006-09-06
The output from those cases were exactly what you predicted. The test file worked just fine, but the other gave me the same output. The thing is that I have downloaded 4-5 different tars from 2 different websites, and none of them will unzip. I downloaded the files through mozilla's download manager. Also, I am still unclear what archive you refer to?

---

### Post by kidders on 2006-09-06
Oops sorry ... I guess I'm posting back too quickly without reading what I'm typing!! (I need a proofreader lol)

Basically, the error messages indicate that the .tar.gz files you downloaded are corrupt and need to be re-transferred. The purpose in posting a sample .tar.gz was to verify that it was your themes that are the problem, and not your archive tools.

The text of the error messages (unexpected end of file) tells you that your themes are corrupt because you didn't finish downloading them for some reason. Here are two obvious ones:

[LIST=1]
[*]You closed the download mgr too soon
[*]You tried to download too much in one go and the server kicked you off
[/LIST]

Sorry for being unclear ... (it's nearly 6am here!) It does seem odd that ALL of your archives are corrupt though, doesn't it!

One final suggestion: Did you use the "file" tool to confirm that your themes are in fact .tar.gz's and not some other kind of archive?

---

### Post by PCalitrack on 2006-09-06
Wow, I really feel retarded. You are exactly right. The files were not downloaded in full, or they were corrupt. Maybe, it has something to do with me downloading them directly to my external hard drive, because when I download them now to my regular HD, they untar just fine. Thanks so much for your help. I really appreciate it. SOLVED.

---

### Post by kidders on 2006-09-06
Glad you tracked down the problem :-)

The only suggestion I have about external devices is to be careful to dismount them correctly before removing them. If you can't guarantee that, add the "sync" option to your /etc/fstab.

Quick explanation ...

On most operating systems, write operations are often performed asynchronously, for performance reasons. In practice, this means that saving a file may not actually write all of it permanently to your disk for a while. In Linux, Windows and others, there are ways of overriding this behaviour. Linux's is the "sync" flag; adding it to the mount options for a removable device forces writes to happen on the spot, making it safer to "unsafely" unplug things (ie without properly dismounting them).

---

### Post by mydrac on 2007-05-03
thanks for the help.

---

