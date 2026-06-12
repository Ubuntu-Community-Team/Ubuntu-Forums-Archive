---
title: "chown details"
date: 2009-01-08
forum: General Help
---

### Post by zoomiest on 2009-01-08
Hello there, I have just installed a LAMP applicant tracking system (ATS), and I am having troubles using a feature, based on ownership of directories.

It has a mass-upload directory, in which one can put a bunch of files (resumes) then use the ATS to parse them, and import them.

The entire directory structure for the ATS has has been set to chown -R www-data:www-data [directory] so the webserver seems owns it. 

This makes it hard to jump in and upload a bunch of documents, then keep going.

QUESTION: Is there a way to leave www-data as the owner, and put me... in the same group as www-data... or something... somehow give me permission to upload files, without being the owner?

---

### Post by cmnorton on 2009-01-09
This question deals more with the apache development philosophy requiring the writing of tools and/or configuration of directories so you can have a local area in which to maintain web pages and then transfer them to the root owned apache directories.

I found one link:

[http://www.linuxquestions.org/questions/linux-newbie-8/setting-group-automatically-upon-file-creation-local-web-development-configuration-288857/?highlight=non-root+apache+directories](http://www.linuxquestions.org/questions/linux-newbie-8/setting-group-automatically-upon-file-creation-local-web-development-configuration-288857/?highlight=non-root+apache+directories)

There are probably many more links. You might want to ask a moderator to put this question into the Ubuntu server forum, given it deals directly with Apache.

One way I did this was to have a root-owned link under my home directory, and I was able to edit files that belonged to root, but did not have the actual root directory exposed to all who might write in it. There are probably better ways to deal with this.

Good luck.

---

### Post by pgmer6809 on 2009-01-09
> **zoomiest said:**
> Hello there, I have just installed a LAMP applicant tracking system (ATS), and I am having troubles using a feature, based on ownership of directories.

It has a mass-upload directory, in which one can put a bunch of files (resumes) then use the ATS to parse them, and import them.

The entire directory structure for the ATS has has been set to chown -R www-data:www-data [directory] so the webserver seems owns it. 

This makes it hard to jump in and upload a bunch of documents, then keep going.

QUESTION: Is there a way to leave www-data as the owner, and put me... in the same group as www-data... or something... somehow give me permission to upload files, without being the owner?

Yes you can belong to as many groups as you like. Or you (or root actually) can change your home group.
consult the usermod man page but essentially ```
usermod -g www-data zoomiest
``` will change your group from whatever it is now to www-data. Better change permissions and ownership of your home directory before you do that though.

Or you (root) can add you to as many groups as you like with:
```
usermod -G www-data,html-data,ATS-data zoomiest
```
Note upper case G, groups separated by commas, and a space before the login name. 
etc.
pgmer6809

PS 
if this is a real 'server' environment, you may find that it has some 'SELLINUX' features enabled.
SELINUX complicates things A LOT!. Mostly because the tools are too new and not well polished.
If SELINUX is in the picture (or APPARMOR about which I know nothing) then you will/might have to not only set the std linux file and directory permissions but also the 'security context'. 
Under SELINUX the starting point for this is the -Z option to the ls cmd, and the chcon cmd.

---

### Post by zoomiest on 2009-01-10
Thank you for the help. I can hand this but...

> ... Better change permissions and ownership of your home directory before you do that though.

Thanks for dumbing things down - what would I change my home directory permissions to?

If I put myself in the same group as www-data would that not merely give me access to the same directories? Why would that necessitate changing my own permissions?

---

