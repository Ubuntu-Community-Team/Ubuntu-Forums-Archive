---
title: "system restore possible?"
date: 2009-01-24
forum: General Help
---

### Post by HarmonicaGoldfish on 2009-01-24
I am having some strange activity on my ubuntu 8.10/studio blended system.

It is described in [this thread]("http://ubuntuforums.org/showthread.php?t=1049275"). Part of it was solved (yay) but most of it wasn't.

Is it possible to do a 'system restore' type of thing like I used to do on  windows?

---

### Post by Yashiro on 2009-01-24
Do you have a backup to restore to?

Sadly Ubuntu does not have a 'built in' backup system yet.

---

### Post by cariboo on 2009-01-24
One of the former moderators create a system restore program, but I can't seem to find a link to it. The Linux way of doing things is to do a backup of all your important files daily. I personally use grsync to backup my home directory to my server. Backing up my home directory using grsync after the initial backup takes less then 5 minutes and runs in the background. Sbackup is also a good choice you can set the time it runs and what it backs up, it is pretty simple to use. Both are available in the repositories.

Jim

---

### Post by HarmonicaGoldfish on 2009-01-24
Ah. No, there is nothing to backup to. Now I know. Thanks for the recommendations, I'll look for them.

---

### Post by mb_webguy on 2009-01-24
While this suggestion is put forward entirely too often and is generally frowned upon as an answer, you could reinstall.

If there's an issue that you simply can't seem to fix, it's generally safe and relatively simple, if a bit time consuming, to back up the /usr and /home directories, reinstall Ubuntu, and then restore the backup information as needed.  However, this is a bit like using a bomb to swat a fly -- it may get the job done, but there's almost certainly a simpler and easier way to do it, assuming you can figure it out.

Also, while backing up the /usr and /home directories will grab most of what you want to keep (namely installed applications and personal information), depending on what specific applications you have installed and what modifications you've made to your system, there may be some other directories or files you would need to backup as well (such as MySQL databases, which are by default located in /var/lib/mysql).

But as others have said, there is currently no built-in system restore feature in Ubuntu.  Of course, that's balanced by the the fact that fixing problems in Linux, which is usually a matter of (re)installing a few packages or making a few edits to a configuration file, is generally easier than in Windows (which you may not appreciate until you've had to hunt through the Windows registry to edit and remove problem entries).

---

### Post by Yashiro on 2009-01-24
Fixing either OS is equally fiddly and tiresome. You can usually get away with less reboots on Linux thats about it.

---

### Post by HarmonicaGoldfish on 2009-01-25
Question - do you think a re-install will fix the video display issues? I have recently uploaded a bunch of data to dropbox, an online, er, dropbox :) for files and such in anticipation of a re-install. But I would like to be rather sure that it will fix things before I go ahead with a reinstall.

Also, I recently received my membership card from the free software foundation. It includes a copy of [gNewSense ]("http://www.gnewsense.org/static/homepage/")- a totally free gnu/linux distribution. Anyone heard of it? I was thinking of giving it a try if I had to reinstall anyways.

---

### Post by SunnyRabbiera on 2009-01-25
> **HarmonicaGoldfish said:**
> Question - do you think a re-install will fix the video display issues? I have recently uploaded a bunch of data to dropbox, an online, er, dropbox :) for files and such in anticipation of a re-install. But I would like to be rather sure that it will fix things before I go ahead with a reinstall.

Also, I recently received my membership card from the free software foundation. It includes a copy of [gNewSense ]("http://www.gnewsense.org/static/homepage/")- a totally free gnu/linux distribution. Anyone heard of it? I was thinking of giving it a try if I had to reinstall anyways.

Eh gnusense is alright, but stick with what you have.
These days having a good medium to backup on is a good idea no matter the oS, turst me I have seen windows system restore fail and its worse then having to reinstall Ubuntu from the troubles I had.

---

### Post by shredder12 on 2009-01-25
I don't think you should switch to gnewsense..
I haven't tried it and it could be a good distro but you should keep this in mind that it doesn't support non free softwares..
many non free softwares support were removed from the ubuntu kernel which include support for some wlan cards.. 
So, there could be possible hardware issues with this distro..
and for more information you can read the following page..
[http://en.wikipedia.org/wiki/Gnewsense](http://en.wikipedia.org/wiki/Gnewsense)

---

### Post by HereInOz on 2009-01-25
If you are unsure as to whether a reinstall will fix the video display issues, and no one can tell you, why not disconnect the current HDD, grab an old HDD (8gb will do), stick it in the machine and run a quickie install to see what happens.  

That way, if it doesn't fix the video issues, you will know, and you will still have your original system to mess around with and hopefully resurrect.

---

### Post by mozkill on 2009-01-26
> **Yashiro said:**
> Do you have a backup to restore to?

Sadly Ubuntu does not have a 'built in' backup system yet.

Everyone who uses Linux should be required to have and use a copy of CloneZilla   to ghost your Linux installation.

[http://clonezilla.org/screenshot/?in_path=/01_Clonezilla](http://clonezilla.org/screenshot/?in_path=/01_Clonezilla)

---

### Post by HarmonicaGoldfish on 2009-01-26
Thanks for the recommendations everyone. I'm actually thinking of reinstalling 8.04. I've been having connectivity issues with 8.10 anyways. 

I've got no idea how to put in some HDD to test things out ... this is possible in a laptop?

---

### Post by mozkill on 2009-01-29
> **HarmonicaGoldfish said:**
> I've got no idea how to put in some HDD to test things out ... this is possible in a laptop?

I dont understand your question.

---

