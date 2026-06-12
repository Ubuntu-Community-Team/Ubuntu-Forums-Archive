---
title: "How do I &quot;Force&quot; the &quot;Garbage Bin&quot; to empty?"
date: 2006-07-16
forum: Desktop Environments
---

### Post by handy on 2006-07-16
I have a drive that is near full, even though I have deleted most of the contents.  I am thinking that the Garbage Bin is not reporting the situation correctly.

I believe there is a way to **Force** the Garbage Bin to empty?

Any input on the topic is wellcome?

---

### Post by deeek on 2006-07-16
You can always go to the Wastebasket and check for hidden files by pressing Control+H or go to View->Show Hidden Files.  When you delete files in the Wastebasket window they are deleted permanently.

---

### Post by handy on 2006-07-17
> **deeek said:**
> You can always go to the Wastebasket and check for hidden files by pressing Control+H or go to View->Show Hidden Files.  When you delete files in the Wastebasket window they are deleted permanently.

Thanks Deeek,

The files were hidden in the offending drive's hidden *root*, Garbage Bin.

Today, I've learnt some more...

---

### Post by BrokeBody on 2006-07-17
> **handy said:**
> I believe there is a way to **Force** the Garbage Bin to empty?

Any input on the topic is wellcome?

```
sudo rm -fr $HOME/.Trash/
```

> **handy said:**
> Today, I've learnt some more...

And more... 8-)

---

### Post by PingunZ on 2006-07-17
next time you delete something do 
shift + delete it wont go to the garbage bin, it will be directly removed

Grtz PingunZ

---

### Post by jayemef on 2006-07-17
[FileLight]("http://www.kde-apps.org/content/show.php?content=9887") is an awesome utility for viewing your disks graphically. I've used it to pinpoint overly large directories. Also, on the plus side, I'm fairly sure it's available via apt:
```
$ sudo apt-get install filelight
```

---

### Post by handy on 2006-07-17
> **PingunZ said:**
> next time you delete something do 
shift + delete it wont go to the garbage bin, it will be directly removed

Grtz PingunZ

Just like in windoze!  I used to use that all the time... Cool! :KS

---

### Post by handy on 2006-07-18
> **jayemef said:**
> [FileLight]("http://www.kde-apps.org/content/show.php?content=9887") is an awesome utility for viewing your disks graphically. I've used it to pinpoint overly large directories. Also, on the plus side, I'm fairly sure it's available via apt:
```
$ sudo apt-get install filelight
```

Thanks, I just downloaded FileLight, it's great for a quickly seeing your disk usage...  Thanks :KS

---

### Post by LordMau on 2006-07-18
> **jayemef said:**
> [FileLight]("http://www.kde-apps.org/content/show.php?content=9887") is an awesome utility for viewing your disks graphically. I've used it to pinpoint overly large directories. Also, on the plus side, I'm fairly sure it's available via apt:
```
$ sudo apt-get install filelight
```

Was about to install but saw it was a KDE app. Any gnome equivalent?

---

### Post by handy on 2006-07-18
> **LordMau said:**
> Was about to install but saw it was a KDE app. Any gnome equivalent?

I don't know?

It sits well on my gnome system... :KS

---

### Post by ivalladt on 2006-07-18
> **PingunZ said:**
> next time you delete something do 
shift + delete it wont go to the garbage bin, it will be directly removed

Can it be done that the garbage bin is never used and files directly removed always without the need of pressing the shift key?

---

### Post by riivo on 2006-08-05
> **ivalladt said:**
> Can it be done that the garbage bin is never used and files directly removed always without the need of pressing the shift key?I am interested in the same thing

---

### Post by someguyouknow on 2006-08-05
you can add delete to the right click menu....
system settings>KDE components>file manager>behavior
then click on "Show 'Delete' context menu entries which bypass the trashcan"

---

### Post by der_joachim on 2006-08-06
As far as I understand, Handy uses Gnome, but I'll shoot anyway. Konqueror has a very nifty feature. Putting "trash:/" into the address bar shows you the trashcan. With a Ctrl-A and a Shift-Delete you can empty it by hand. 

About filelight: you can also use the *File Size View* in Konqueror by selecting in the menu the following options:
View -> View Mode -> File Size View.

Another alternative for filelight is Kdirstat. It is in the repos([homepage]("http://kdirstat.sourceforge.net/kdirstat/")).

---

### Post by handy on 2006-10-28
I just noticed in Edgy that Nautilus has the option to add **Delete** to the right mouse button menus, *this allows the user to Delete directly, bypassing the Garbage bin.*

I set it up on both my normal user & Root accounts.  I might change my mind about Root... :)

---

### Post by the ev on 2006-11-16
> **LordMau said:**
> Was about to install but saw it was a KDE app. Any gnome equivalent?

[JDiskReport]("http://www.jgoodies.com/freeware/jdiskreport/") is an excellent Java program that fits the bill, FYI.  I use it all the time: on Ubuntu Edgy, on the couch, in the bathroom, in my dreams...la di da di da...;)

---

