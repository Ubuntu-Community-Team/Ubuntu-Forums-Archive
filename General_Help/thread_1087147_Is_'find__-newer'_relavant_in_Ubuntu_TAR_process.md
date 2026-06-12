---
title: "Is 'find / -newer' relavant in Ubuntu TAR process?"
date: 2009-03-04
forum: General Help
---

### Post by sofasurfer on 2009-03-04
In my browsing and reading on TAR I came to this page... [http://book.opensourceproject.org.cn/distrib/ubuntu/unleashed/opensource/0672329093/ch17lev1sec3.html](http://book.opensourceproject.org.cn/distrib/ubuntu/unleashed/opensource/0672329093/ch17lev1sec3.html). It is a page in the book 'Ubuntu Unleashed 
By Andrew Hudson, Paul Hudson' [http://book.opensourceproject.org.cn/distrib/ubuntu/unleashed/](http://book.opensourceproject.org.cn/distrib/ubuntu/unleashed/)


The section on Incremental Tar contains this command...
sudo find / -newer name_of_last_backup_file ! -a type f print

I tried using it and it does not function properly. On reading 'man tar' it looks like 'find' has been replaced by     '-d, --diff, --compare' and 'newer' has been replaced by '-N, --after-date DATE, --newer DATE'.

Is this the situation?

The reason I ask is that the book is only a couple years old but 'man tar' seems to indicate that those commands are not relavant.

Have any of you used this book as a guide?

---

### Post by heindsight on 2009-03-04
Why are you looking at the tar manual for information about options to the find command?
Have a look at
```
man find
```

you'll see:
> -newer file
      File  was  modified  more recently than file.  If file is a sym&#8208;
      bolic link and the -H option or the -L option is in effect,  the
      modification time of the file it points to is always used.

EDIT:
If you want similar functionality for tar (ie only add files modified since the archive was last modified you can use something like:
```
tar -r -N $(date -r archive.tar) -f archive.tar /path
```
OR:
```
tar -A --newer-mtime $(date -r archive.tar) -f archive.tar /path
```

I'm not sure of the exact differences between -r and -A and between --newer-mtime and -N.
You could probably also just use:
```
tar -uf archive.tar /path
```
although I can't remember whether that only updates files that are already in the archive, or if it also adds files that were created after the archive was last updated.

---

### Post by sofasurfer on 2009-03-04
As you may know, there are many people such as me who just ain't graspin' the TAR stuff the way we would like to.

I have no trouble with a full backup with TAR but the incremental part seems to be very confusing. I actually think its because there are sooooo many tutorials out there and I (we) make the mistake of reading to many of them instead of just, like you say, reading the 'man' page.

I was able to create a incremental backup using the command... 
tar --create \
           --file=archive.2.tar \
           --listed-incremental=/var/log/usr.snar \
           /usr

...but I am not happy with the fact that I do not fully understand how it works or what it does, therefore I find myself constantly looking for a more understandable way.

There was know particular reason for reading the tar manual except that I found it and then decided to see what it had to say. This led to my question.

Thanks for your reply. I will study what you said and hopefully I will make progress.

---

### Post by heindsight on 2009-03-05
> **heindsight said:**
> 
If you want similar functionality for tar (ie only add files modified since the archive was last modified you can use something like:
```
tar -r -N $(date -r archive.tar) -f archive.tar /path
```
OR:
```
tar -A --newer-mtime $(date -r archive.tar) -f archive.tar /path
```

I'm not sure of the exact differences between -r and -A and between --newer-mtime and -N.


Well, I just had a look at the manual again, and at this: [http://www.gnu.org/software/tar/manual/index.html](http://www.gnu.org/software/tar/manual/index.html)
I should have read more closely before, -A concatenates 2 or more tar archives while -r appends files too an archive.

-N Looks at both status change time and modification time, while newer-mtime only uses modification time.

I was right about -u, it only updates files already in the archive.

In other words if you want to add files to an existing archive only if they changed or were modified since the archive was created, use:
```
tar -r -N $(date -r archive.tar) -f archive.tar /path
```

If you want to understand the listed-incremental option, have a look at the link I posted above, particularly at: [http://www.gnu.org/software/tar/manual/html_chapter/Backups.html](http://www.gnu.org/software/tar/manual/html_chapter/Backups.html)

---

### Post by sofasurfer on 2009-03-08
I have mastered adding the current date to the filename of my archive by using the command 'tar cvpzf "full-backup `date '+%d-%B-%Y'`.tar" /home/daryl/Pictures'. Thank you.

But when I try adding new files by using your command which I changed to 'tar -r -N $(date -r full-backup 08-March-2009.tar) -f full-backup created on `date '+%d-%B-%Y'`.tar" /home/daryl/Pictures' I get nothing.

Doesn't '(date -r full-backup 08-March-2009.tar)' check the date in my archive and then '-f full-backup created on `date '+%d-%B-%Y'`.tar' add the files to the archive?

Please explain.

---

### Post by sofasurfer on 2009-03-08
I'm studying the link you posted about incrementals (I had been trying to understand this before) and I have managed to save an incremental file and the .snar file. But I cannot for the life of me figure out where the ".snar" comes from. I mean what does it mean. It would make more sense to call it ".metadata" or ".CFD" for "changed file data".

Is there a way to read the .snar file?
Any idea where it comes from?

EDIT::
I found that there is a .snar (snapshot file) editor called 'tar-snapshot-edit' but it gives me a error on line 34. If I figure that out I may be able to view a snapshot file.

---

### Post by sofasurfer on 2009-03-08
I have now used the 'listed-incremental' option to archive directories and to add incremental archives. I have also listed the contents to verify their contents. I think this is a satisfactory method for me. At last I am making progress and feeling satisfaction.

---

