---
title: "SourceForge - How can I upload files with Filezilla"
date: 2009-03-30
forum: General Help
---

### Post by dodle on 2009-03-30
I've been trying for a few hours to figure out how to upload my project's files to my sourceforge project page (project is already approved).  I haven't been able to find much useful information, only that I can use Filezilla.  But there are no instructions, at least none that I can find.  Any help would be much appreciated.

---

### Post by bodhi.zazen on 2009-03-30
Did you get a user name and password ?

---

### Post by dodle on 2009-03-30
I have a username and password for my account with sourceforge. Is there some others that I need? 

With Filezilla, I've tried inputting the following:

Host: sourceforge.net
Username: *******
Password: *******

...then hit "connect". But connection fails.  I'm assuming this is the wrong way to get connected.

**Edit:** I haven't been able to upload anything via the sourceforge website either, e.g I can't find a button that says "click here to upload your file".

---

### Post by dodle on 2009-03-30
I found some helpful information here:[http://apps.sourceforge.net/trac/sourceforge/wiki/SFTP]("http://apps.sourceforge.net/trac/sourceforge/wiki/SFTP"), and was able to upload my file with:```
: sftp
```But I would still like to be able to do it Filezilla, but my login doesn't work.

---

### Post by bodhi.zazen on 2009-03-30
Are you on Linux ?

If so, may I suggest gfpt ?

At any rate, see if this helps :

[http://wiki.filezilla-project.org/Using](http://wiki.filezilla-project.org/Using)

---

### Post by dodle on 2009-03-30
> **bodhi.zazen said:**
> At any rate, see if this helps :

[http://wiki.filezilla-project.org/Using](http://wiki.filezilla-project.org/Using)

Thanks, this helped.  I needed to use Site Manager instead of Quickconnect.

---

### Post by dodle on 2009-03-30
Are files uploaded to SourceForge not immediately available?  When I try to download my .deb, I get a page that says "The file is currently unavailable."

**Edit:** NVM, it's working.

---

