---
title: "Help deleting certain files..."
date: 2009-06-10
forum: General Help
---

### Post by cypherus on 2009-06-10
I am using Motion to record video using Ubuntu.  There are two things I am trying to do, but can't seem to find an easy answer on how to accomplish.

First, I want to delete old video files past a certain date, in this case older than April.  The file names are saved with relevant date and time info like this: 06-10-2009-08-22-30.avi.  The files are also saved in multiple folders and subfolders so I'll need to be recursive in my search and removal.

Second, I want to set up a system to automatically delete older files like so:

April
Week 1 Delete
Week 2
Week 3
Week 4

May
Week 1
Week 2
Week 3
Week 4

June
Week 1

So when the first week of the new month records, the first week of two months ago is removed. Then week two, and so on and so forth.

Thank you in advance for the help.

---

### Post by reeseslover531 on 2009-06-10
This sounds like the job for a bash script, Check [this ]("https://help.ubuntu.com/community/Beginners/BashScripting")wiki page out for how to script using bash

---

### Post by cypherus on 2009-06-10
It does sound like a job for a bash script...I've used them in the past.  However, I don't have the knowledge to write a bash script specifically for this task.

---

### Post by cypherus on 2009-06-10
Can anyone please help me with this?  I went in the IRC chatroom for Ubuntu and received no help.

---

### Post by Legace on 2009-06-10
This is not exactly what you're looking for, but should do:

```
find /dir/to/search -mtime +50 -exec rm {} \;
```

This is how it will work:
It will search **/dir/to/search** for files modfied **at least** 50 days ago (change **+50** to the amount of days you want) and then delete the files it found. (note, it won't delete directories. to add the -r switch to rm: **rm -r**).

Change **mtime** to **atime** if you want "last accessed" instead of "last modfied".

Hope this helps :)

---

### Post by iponeverything on 2009-06-10
> **cypherus said:**
> I am using Motion to record video using Ubuntu.  There are two things I am trying to do, but can't seem to find an easy answer on how to accomplish.

First, I want to delete old video files past a certain date, in this case older than April.  The file names are saved with relevant date and time info like this: 06-10-2009-08-22-30.avi.  The files are also saved in multiple folders and subfolders so I'll need to be recursive in my search and removal.


```
find /motion_directory -mtime +90 -type f -delete 
```

This command find and remove any file that has not been modified in 90 days. Run it with "-ls" instead of "-delete" first just you know what its going to delete. To get it delete a directory:

```
find /motion_directory -mtime +90 -type d -delete 
```


Second, I want to set up a system to automatically delete older files like so:

April
Week 1 Delete
Week 2
Week 3
Week 4

May
Week 1
Week 2
Week 3
Week 4

June
Week 1

So when the first week of the new month records, the first week of two months ago is removed. Then week two, and so on and so forth.

Thank you in advance for the help.[/QUOTE]

---

### Post by cypherus on 2009-06-10
> **iponeverything said:**
> ```
find /motion_directory -mtime +90 -type f -delete 
```

This command find and remove any file that has not been modified in 90 days. Run it with "-ls" instead of "-delete" first just you know what its going to delete. To get it delete a directory:

```
find /motion_directory -mtime +90 -type d -delete 
```


This doesn't bring up a single file to delete unfortunately...

I ran ```
find /motion_directory -mtime +90 -ls
```

---

### Post by cypherus on 2009-06-10
Is there a way to pipe this to grep? Like this?

> ls -l -R | grep 'DATE RANGE' | rm *

or something to that effect?

---

### Post by iponeverything on 2009-06-10
:) Replace /motion_directory with the directory where your Motion video files live.

---

### Post by cypherus on 2009-06-10
>  Replace /motion_directory with the directory where your Motion video files live. 

Thanks! I did that already when you first gave me instruction.

---

### Post by iponeverything on 2009-06-10
```
find /Your_Motion_Files_Directory_Path | grep `date --date '3  weeks ago' +%m-%d-%Y` | awk '{print "rm "$1}'
```

Ok, I can get a bit more creative. To understand the above command, just look at the parts. 

Replace /Your_Motion_Files_Directory_Path with the path to your Motion video files and run.
```
find /Your_Motion_Files_Directory_Path
```

To see what grep is greping for, run:

```
echo `date --date '3  weeks ago' +%m-%d-%Y`
```

Replace '3  weeks ago' with whatever you want.. The date command is quite good at figuring it out. Even things like 'second tuesday' work. Do a "man date"

This just builds a command line with the output of grep command
say that grep matched /Some/Dir/06-10-2009-08-22-30.avi it would print out:
 ```
awk '{print "rm "$1}'
```

```
rm /Some/Dir/06-10-2009-08-22-30.avi

```

Note that this command:

```
find /Your_Motion_Files_Directory_Path | grep `date --date '3  weeks ago' +%m-%d-%Y` | awk '{print "rm "$1}'
```

Will not delete anything until you add a 

```
|sh
```

to the end of it.

---

