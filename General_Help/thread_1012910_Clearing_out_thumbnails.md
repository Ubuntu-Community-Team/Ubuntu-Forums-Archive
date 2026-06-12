---
title: "Clearing out thumbnails"
date: 2008-12-16
forum: General Help
---

### Post by rapattack1 on 2008-12-16
Hi how do I find and clear out thumbnails? I do a lot of stuff with Gimp and I suspect there must be quite a bit of stuff to clear. Also I use Fspot to transfer images from my camera so there might be something there too. I have never cleared files in linux but read somewhere I could. Just not clear on where the damn directory is. Thanks!

---

### Post by ibutho on 2008-12-16
Thumbnails are stored in subdirectories of ~/.thumbnails. You can navigate to that directory and delete them. If you are used to a GUI, you may need to configure Nautilus to show hidden files.

---

### Post by rapattack1 on 2008-12-16
Hi yes I use the gui most of the time. How do I show hidden files?

---

### Post by yabbadabbadont on 2008-12-16
View->Show hidden files

(or hit Control-h)

---

### Post by samden on 2008-12-16
In Nautilus, View menu -> Show Hidden Files

---

### Post by em4r1z on 2008-12-16
You may want to set the maximum size of the thumbnails folder instead of clearing it every now and then.
Delete the thumbnails folder, open the Configuration Editor (gconf-editor), navigate to this key and change its value to the desired integer (it represents megabytes):
/desktop/gnome/thumbnail_cache/maximum_size

---

### Post by rapattack1 on 2008-12-17
I haven't been able to find the thumbnails folder. Also I do not know how to do those commands to change the maximum size.

---

### Post by drs305 on 2008-12-17
If you open nautilus and click on your home folder, do you see any folders or files beginning with a period (.), for instance *.gconf*  If you can't see any, in nautilus select View, Show Hidden Folders. Perhaps you are not looking in the right place. Use this command to open nautilus in the .thumbnails folder:
```

nautilus $HOME/.thumbnails

```
There are two files: fail and normal. 

For automatic limiting of thumbnails, refer to the next part of this post.

> **rapattack1 said:**
> Also I do not know how to do those commands to change the maximum size.

Open a terminal (Applications, Accessories, Terminal). Type in:
```
gconf-editor
```
At that point, the gconf-editor will launch.
Click on Desktop to expand it, then Gnome, then thumbnail_cache.

Now in the right pane you can set the maximum number of days or the maximum size. If you click on each option an explanation is shown below.

---

### Post by rapattack1 on 2008-12-17
Do you mean thumbnailers?
By option do you mean the things that are listed below thumbnailers? I do not understand what is mentioned in the right pane in reference to what i am clicking on in the left pane.

---

### Post by kpkeerthi on 2008-12-17
```
find ~/.thumbnails -type f -mtime +7 -exec rm '{}' ';'
```
* Keeps the thumbnails used in the last 7 days and removes the rest.

---

### Post by rapattack1 on 2008-12-17
Oh great that seems to have done the trick. Took a whole minute to clear them! Thanks so much!!!

---

### Post by drs305 on 2008-12-17
> **rapattack1 said:**
> Do you mean thumbnailers?
By option do you mean the things that are listed below thumbnailers? I do not understand what is mentioned in the right pane in reference to what i am clicking on in the left pane.

The options are in the right pane of the "thumbnail_cache" folder, not the "thumbnailers" folder below it. In the 'thumbnail_cache' folder, in the right pane are options for the maximum number of days or the maximum size in megabytes.

If you would prefer to just run a command rather than make the changes via the gconf-editor app, keep reading for an alternative way of doing this. Using gconf-editor or running the commands does the same thing - changes the gconf settings.

You liked the command presented in post #10. If you would like to set it so all thumbnails older than 7 days are deleted, you can run this command. 
```

gconftool-2 --type string --set /desktop/gnome/thumbnail_cache/maximum_age '7' 

```

It does by the command line what I was trying to describe in the previous post. You can set the value (number of days) to any number you would like - 7 may be a bit short (the default is 180) but that is up to you.

To set the maximum size (in megabytes), this is the command (default is 512, which is what I have left in the command):
```

gconftool-2 --type string --set /desktop/gnome/thumbnail_cache/maximum_size '512' 

```

---

### Post by rapattack1 on 2008-12-17
Yes I can't see that thumbnail_cache folder.
I did that command that set's it to clear more than 7 days like you mentioned. I like that one because do so much editing. Thanks!

---

### Post by AggravatedGestalt on 2010-04-22
It seems to me that these "thumbnails" can be accessed and safely deleted through Places/HomeFolder/.thumbnails

I often just delete the entire file when I want to clean up.

---

### Post by rapattack1 on 2010-04-22
There are 3 folders under that directory fail, large and normal. Do i delete them and everything in them? Thanks for this!

---

### Post by john newbuntu on 2010-04-22
Install bleachbit . That will clean some crud.

As far as your question goes, kill em all.

---

### Post by rapattack1 on 2010-04-22
I installed bleachbit but i guess i have top run it with sudo as there us a lot of this is the list:
```
applications-eo.omf' /usr/share/omf/add-applications/add-applications-eo.omf
[Errno 13] Permission denied: '/usr/share/omf/add-applications/add-applications-de.omf' /usr/share/omf/add-applications/add-applications-de.omf
[Errno 13] Permission denied: '/usr/share/omf/add-applications/add-applications-lt.omf' /usr/share/omf/add-applications/add-applications-lt.omf
[Errno 13] Permission denied: '/usr/share/omf/add-applications/add-applications-is.omf' /usr/share/omf/add-applications/add-applications-is.omf
[Errno 13] Permission denied: '/usr/share/omf/add-applications/add-applications-vi.omf' /usr/share/omf/add-applications/add-applications-vi.omf
[Errno 13] Permission denied: '/usr/share/omf/add-applications/add-applications-lv.omf' /usr/share/omf/add-applications/add-applications-lv.omf
[Errno 13] Permission denied: '/usr/share/omf/add-applications/add-applications-cv.omf' /usr/share/omf/add-applications/add-applications-cv.omf
[Errno 13] Permission denied: '/usr/share/omf/gnibbles/gnibbles-ca.omf' /usr/share/omf/gnibbles/gnibbles-ca.omf
```

---

### Post by john newbuntu on 2010-04-22
Under applications->system tools, you have the sudo version too.

---

### Post by rapattack1 on 2010-04-22
Oh that is odd because when i first installed it it was only as user. Only one icon in that menu. Now the root version is there. Odd. Anyway i ended up running it via the terminal as sudo.
After i did it an odd thing popped up saying that i didn't have enough space on the hard drive or something and that i would have to uninstall some things. I thought that was odd because there was no way i could fill an 80gig hard drive.
Anyway Bleachbit did clean over 300mb of crud. Thanks!!!
I just ran Gparted and it said that the hard drive has only used 9.97gb. Well i did move the biggish video files fromt he primary drive before i checked there.
The secondary drive says 6.85gb used after i moved the files there so that is odd.

---

