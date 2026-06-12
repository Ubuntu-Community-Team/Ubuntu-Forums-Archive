---
title: "Incorrect timestamp for Nautilus copy+paste function"
date: 2005-06-12
forum: Desktop Environments
---

### Post by jiyuu0 on 2005-06-12
I've noticed that i'm getting this problem quite often.

Using Nautilus, when I copy and paste a folder from one location to another, the timestamp is incorrect at the new location

e.g.
drwx------  5 chua chua 16384 1970-01-01 07:30

Anybody else got this b4?

---

### Post by Alexander Kirillov on 2005-06-13
[QUOTE=jiyuu0]I've noticed that i'm getting this problem quite often.

Using Nautilus, when I copy and paste a folder from one location to another, the timestamp is incorrect at the new location

e.g.
drwx------  5 chua chua 16384 1970-01-01 07:30

Anybody else got this b4?[/QUOTE]
 Same here. Funny - works fine with files, doesn't work with folders. 
Maybe we should search GNOME bugzilla...

---

### Post by lonetree on 2005-07-02
I found that this is not only in ubuntu. I have tested with Novell Suse Linux, and also Fedora Core 4, all gives the same problem. I found that this only happen in network shared folders, or I may be wrong. I also notice that in windows, it also has this problem when you copy folders to network share folders. However, I'm much more concern on the files copied over. Each time I copy some files to network share folders, the time and date will change to something like 01/01/1980 21:08 etc. Also, I don't know if anyone of you also encounter this, it seems that the file size is also reported wrongly, a file size of 12kb can be reported as 830.2 MB. when I view it with nautilus. Wierd.

I'm not very technical in troubleshooting this, hope someone can find out this problem. My feeling is samba may be the culprit, but I'm sure. It's making me going round and round now.

Really hope someone can detect this problem and help solve it.

Thanks

Regards,

---

### Post by lonetree on 2005-07-03
Like to correct myself. I notice that when I copy the folders (with files) from one directory to another, the date of the folder does change to 1970/01/01, as well as the time, but the file's date and time not touch at all. Therefore I think I was wrong that Samba is the culprit.

However, I think the worse case I encounter now is the network shared folders, when I copy my files and folders from  my ubuntu to a windows shared folder, all the date and time change to 1970/01/01. Hope someone really can solve this problem, or am I the only one facing this problem now.

Please voice out. This problem is killing me now, I  am using this shared folder for backups (not a windows box, it's a LANDISK acting as a windows file server -NAS). I cannot accept the fact that the dates are changed, I won't know which is the latest or earliest file I created.

:-(

Regards,

---

### Post by lonetree on 2005-07-03
Last test I did.

KDE on Fedora (didn't want to make my ubuntu with KDE). Found that using KDE to copy files and folders on local machine has the same problem too. And needless to say, wen copying to network folders, it also changes the time. 

Now what is the actual problem? Samba? Gnome? KDE? or the Kernel?

Shall wait for some expert to review this. Hope this will resolve soon.

Regards,

---

### Post by lonetree on 2005-07-17
hmmmm, seems that no one is interested about this issue.

---

