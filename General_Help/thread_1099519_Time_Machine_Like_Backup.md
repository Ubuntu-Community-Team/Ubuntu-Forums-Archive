---
title: "Time Machine Like Backup?"
date: 2009-03-18
forum: General Help
---

### Post by Agg23 on 2009-03-18
Is there a backup program like Time Machine that does incremental backup?  Something that backs up a file every time its changed?

---

### Post by mafsi on 2009-03-18
> **Agg23 said:**
> Is there a backup program like Time Machine that does incremental backup?  Something that backs up a file every time its changed?

there are scripts for this

---

### Post by CrusaderAD on 2009-03-18
> **Agg23 said:**
> Is there a backup program like Time Machine that does incremental backup?  Something that backs up a file every time its changed?

Yes indeed. It's called Keep.

```
sudo apt-get install keep
```

I made some instructions at the end of this thread here:

[http://ubuntuforums.org/showthread.php?t=902366]("http://ubuntuforums.org/showthread.php?t=902366")

Keep only backs up changes files, which is nice cause the backup won't take nearly as long. sbackup (Simple Backup) is another choice, but I like Keep much more.

---

### Post by DGortze380 on 2009-03-18
rsync

---

### Post by KeyserSoze93 on 2009-03-18
```
echo "0 * * * * rsync -av /home/user /media/backup_drive" >~/crontab && crontab ~/crontab
```

Do an incremental backup from /home/user to /media/backup_drive every hour.

Obviously you can fine tune it, but that lays down the basic idea.

---

### Post by danleweb on 2009-05-06
You can try [Back In Time]("http://backintime.le-web.org/").

---

### Post by kpkeerthi on 2009-05-06
> **danleweb said:**
> You can try [Back In Time]("http://backintime.le-web.org/").
@danleweb
I owe you a beer for pointing this. Exactly what I was looking for. I'm going to put Backintime to test. 

I looked at the screenshots and really liked its usability and how cleverly the rsync's mystic options have been masked with simple, plain, readable texts on the UI.

Are you the author of this application? If you are, I owe you another beer for writing this. :popcorn:

---

### Post by megamania on 2009-05-06
> **danleweb said:**
> You can try [Back In Time]("http://backintime.le-web.org/").
The program looks very nice.

Since it looks like you are the author, I would like to ask you how it handles the retrieval/restore of files.

In other words, the power of Time Machine lies in the ability to browse through different versions of the files, making it very easy to recover a specific version of a document or a picture. How is this handled in Back in Time?

---

### Post by danleweb on 2009-05-06
Yes I am the author, send me the beers :)

Just use "Snapshots" list to select the snapshot you what to browse.
The you can browse the snapshot like in a file manager. Keep in mind that snapshot are read-only.
You can copy/paste from Back In Time to Nautilus (or maybe other file managers too).
If you want to restore something just select it and press "Restore" button (toolbar in snapshot view).

---

### Post by megamania on 2009-05-06
> **danleweb said:**
> Just use "Snapshots" list to select the snapshot you what to browse.
The you can browse the snapshot like in a file manager. Keep in mind that snapshot are read-only.

So it looks like I can't look for a specific file unless I know (or guess) where it is, and I can't easily find all the revisions of a specific file, right?

If I am right, would it be difficult to implement such a function? I think it would be enough to create a complete list of all files on all snapshots, and search through it. Or maybe I'm just daydreaming...

---

### Post by danleweb on 2009-05-06
You need to browse for a file (there are quick access to special folders, bookmarks and saved directories). When you select a file you can see all snapshots where it can be found. You can event make a diff for an item between different snapshots.
For more information just try it.

---

### Post by klepto on 2009-05-07
I've been using Back In Time ever since it was mentioned by Lifehacker. 
It works really well for me but what I want to know is when it is time to restore
some folders how do I know which snapshots are complete and which are incrementals? 

Thanks much,  I hope this program stays active in devlopment!

---

### Post by Windsurfer619 on 2009-05-07
Holy crap danleweb is the MAN

---

### Post by colau on 2009-05-08
> **raptormanad said:**
> Yes indeed. It's called Keep.

```
sudo apt-get install keep
```

I made some instructions at the end of this thread here:

[http://ubuntuforums.org/showthread.php?t=902366]("http://ubuntuforums.org/showthread.php?t=902366")

Keep only backs up changes files, which is nice cause the backup won't take nearly as long. sbackup (Simple Backup) is another choice, but I like Keep much more.
I did this.
```

aptitude install simplebackup

```
Would anyone please tell how to use this?
And is the link you gave is ok now?

---

### Post by geirha on 2009-05-08
> **colau said:**
> I did this.
```

aptitude install simplebackup

```
Would anyone please tell how to use this?
And is the link you gave is ok now?

Never tried it myself, but looking at the list of files: [http://packages.ubuntu.com/jaunty/all/simplebackup/filelist](http://packages.ubuntu.com/jaunty/all/simplebackup/filelist) , it has man-pages, so try reading them. ```
man simplebackup
```

---

### Post by bodhi.zazen on 2009-05-08
There is also dirvish

dirvish : [http://www.dirvish.org/](http://www.dirvish.org/)

---

