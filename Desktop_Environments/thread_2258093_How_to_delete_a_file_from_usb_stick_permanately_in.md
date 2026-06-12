---
title: "How to delete a file from usb stick permanately in kde"
date: 2014-12-24
forum: Desktop Environments
---

### Post by remmas-sido on 2014-12-24
Hi guys 
I'm using kubuntu and I was wondering if there any option to delete a file permanately from usb stick because I watch on my satelite receiver which is connected to my led by HDMI cable a lot and I would appreciate if I don't have to format my usb drive every time 
Thank You

---

### Post by beep3 on 2014-12-24
Not sure if I understand the second part of your question correctly (everything after "because") but Shift-Delete should bypass the rubbish bin.

If you find that files you delete are still kept in hidden folders on the USB stick you could delete them from the command line.

---

### Post by yancek on 2014-12-24
I don't know what you are actually referring to either.  The standard method I have used in the years I have used KDE (in addition to the one mentioned above) is to right-click the file if you are in a graphical environment and select Delete.  Not having more information, it is difficult to know what you are doing.  Is this some kind of data flash drive?  Is it a LiveCD install of Kubuntu on a flash using something like unetbootin or Universal USB Installer?  If the latter, it's a read-only fileystem and you can't delete anything or add anything that will remain on reboot.  More specfics on the actual situation would be useful.

---

### Post by remmas-sido on 2014-12-25
> **beep3 said:**
> Not sure if I understand the second part of your question correctly (everything after "because") but Shift-Delete should bypass the rubbish bin.

If you find that files you delete are still kept in hidden folders on the USB stick you could delete them from the command line.

What's the command line to delete the files which are in hidden folders?

---

### Post by flaymond on 2014-12-25
You can view the hidden files in the USB using command line -

Firstly, make sure you cd to the USB path/directory.

```
cd <path>
```


Then, type this to view all files in it including hidden files.


```
ls -a
```

You can remove/delete the file using this command -

```
rm <filename>
```

or if you want to delete blank folder

```
rmdir <filename>
```

or folder with contents.

```
 rmdir -rf <filename> 
```



Do you want to remove all files and folder in the USB?:-k

If so, go to the USB path

Then type this

```
 rm /path/to/directory/*  
```

Example:

rm home/user/USB/* - The star/* mean all in the folder/directory

If it failed to rm all, just add -r after the rm code (rm -r)

Hope that help!

# Caution - rm command wil delete your files, not moving it to Trash. It also not prompting you of what file you want to delete permanently.


You can type man rm to read more about rm command or simply read from here(just the same one) - [http://manpages.ubuntu.com/manpages/karmic/en/man1/rm.1.html](http://manpages.ubuntu.com/manpages/karmic/en/man1/rm.1.html)

---

### Post by sudodus on 2014-12-25
Do you want to make more free space, or do you want to remove any traces (if someone might 'borrow' your pendrive)? The methods would differ for those cases.

---

### Post by CantankRus on 2014-12-25
After you delete files on your usb device make sure to empty trash while the usb is mounted 
otherwise they will remain in the usb's hidden trash folder.
or
use shift+delete to bypass trash when deleting.

---

