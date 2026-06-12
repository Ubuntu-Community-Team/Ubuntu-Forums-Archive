---
title: "What goes here?"
date: 2009-01-17
forum: General Help
---

### Post by buccaneere on 2009-01-17
/media/windows didn't work. 

Help?

---

### Post by orlox on 2009-01-17
Dont know precisely how ntfs-config works, so im not sure if this is your problem but...

Does the folder /media/windows exists?

---

### Post by hikaricore on 2009-01-17
As with orlox I'm not familiar with this configuration tool but how about we try this.

Open a terminal and type:

> sudo mkdir /media/windows

Then try the process again.

---

### Post by lavinog on 2009-01-17
how are you getting that screen?
what version of ubuntu is this?
my ntfs drives automatically mount when I click on removable drives under places. (I am using intrepid)
if you are trying to mount a drive as a non super user you have to mount them in your home folder.

---

### Post by buccaneere on 2009-01-17
Yeah, media/windows exists; it the 30.7 G drive. Do I need to RE-name the drive? :confused:

---

### Post by lavinog on 2009-01-17
> **buccaneere said:**
> Yeah, media/windows exists; it the 30.7 G drive. Do I need to RE-name the drive? :confused:

cant hurt to try
also try mounting it to /media/windows2

---

### Post by orlox on 2009-01-17
Have you tried mounting it by hand???

Do you have any error message that could be relevant??

---

### Post by buccaneere on 2009-01-21
> **orlox said:**
> Have you tried mounting it by hand???

Do you have any error message that could be relevant??

Yup. No problem manual mount. Click the icon; DONE/MOUNTED.

I want it to AUTO-MOUNT, and I need to know what the mount point is, that it mounts by when I manual mount.

Then I can enter that into the space in the GUI, post #1.

ANYBODY?

---

### Post by orlox on 2009-01-22
If you want it to automount, and you have the mount point created, then you can forget the GUI configuration tool, and directly edit your fstab. Add this line to the file /etc/fstab:

```
/dev/<your partition>     /media/<mount point>     ntfs-3g     defaults,locale=en_US.utf8   0    0
```

Obviously, replace <your partition> with the name of your partition and <mount point> with the mount point.

Put that, restart your computer, and see if the drive is mounted. If that works, then afterwards you can refine the locale in case en_US gives you problems...

---

### Post by hyper_ch on 2009-01-22
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by buccaneere on 2009-01-22
> **hyper_ch said:**
> It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

This is from Ubuntu Forums Code of Conduct:
> These, along with any generally condescending posts will be moved or removed at the moderators discretion.


If you have a problem of your own, make a thread about it, or take it to a moderator/administrator. Do NOT 'clog up' my thread (or others') with your useless banter, until you have a title of some sort under your username.

Your post is reported...

---

### Post by bodhi.zazen on 2009-01-22
hyper_ch has good intentions and I would not want to see you two get off on the wrong foot.

His post may have been direct, but he raises some good points.

It appears you are (have) received assistance directly related to your problem and so all is well, no harm done.

You certainly may post any way you wish, but keep in mind we are all volunteers and the intent of hyper_ch is to guide you on getting advice faster, which at the end of the day makes your experience here better.

I do not feel his intent was to offend and I hope you do not take his advice in that way.

---

### Post by hyper_ch on 2009-01-22
another one just made it to my ignore list :)

---

### Post by buccaneere on 2009-01-23
> **hyper_ch said:**
> another one just made it to my ignore list :)

Promise?

(sounds too good to be true)

---

### Post by buccaneere on 2009-01-23
/media/windows didn't work. 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=100109&d=1232168484

> 
Does the folder /media/windows exists?
Yes.

> 
Open a terminal and type:

Quote:
sudo mkdir /media/windows
Then try the process again.
An error returned; I don't remember what it was...

> 
how are you getting that screen?
Applications/system tools/NTFS configuration tool (with partition UNmounted)

> 
Have you tried mounting it by hand???
Yup. Works every time. I want it to mount on boot tho'.

> 
If you want it to automount, and you have the mount point created...
I have not created a mount point. I want to use the default mount point that the system uses when I MANUALLY mount.

Anybody got other ideas how to find out what the default mount point is that the system uses when I manually mount?

---

### Post by taurus on 2009-01-23
You must create a mount point for it if you want it to mount automatically each time you boot Ubuntu.  The ntfs-config can do that for you except you have to tell it what mount point you want to use.

---

### Post by LowSky on 2009-01-23
If you want it to mount as the systems mounts it just type in the default system mount point

---

### Post by hyper_ch on 2009-01-23
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by buccaneere on 2009-01-23
> **hyper_ch said:**
> It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

You said you were gonna' ignore me. Just more idle banter? Idle promise?

What is your problem dude?

---

### Post by overdrank on 2009-01-23
Please do not create multiple threads on the same issue. 
 There is no reason to create another thread with the same title, As users with often offer help that you may have already tried and may cause confusion. :) Threads merged

---

### Post by buccaneere on 2009-01-23
> **taurus said:**
> You must create a mount point for it if you want it to mount automatically each time you boot Ubuntu.  The ntfs-config can do that for you except you have to tell it what mount point you want to use.

Sounds great!

I'll just use the default mount point that the system uses when I manually mount.

How do I determine what that is, to put it into the GUI?

Edit bodhi.zazen : Yikes, please do not attach such large screenshots, use thumbnails ;)

---

### Post by Dragonbite on 2009-01-23
I'm not sure whether Ubuntu defaults mounted drives to the 
[INDENT]/mnt
or
/media[/INDENT]
directories (put in a CD and see where cdrom0 appears?). 

Once you've determined which directory you want to place it in then make a directory (and you can call it just about anything) in there and set the /etc/fstab to mount the ntfs to this new directory.

If you want an icon on your desktop you can open Nautilus to /media(mnt), drag the new directory onto your desktop with the middle-click and select "Link here".

Hope this helps! :)

---

### Post by mc4man on 2009-01-23
Maybe this has become more complicated than should be.
By default volumes are mounted to media/"volume label of the partition"

If you haven't given the volume a label previously then ntfs-config will ask you for the mount point.

It's far easier to label your partition first, then ntfs-config will do everything for you, no need to create a mount point, edit fstab, or anything thing else, the mount points will be shown in ntfs-config, just click add and apply.

To label see here or do in windows (control panel -> administrative tools -> computer management -> disc management -> properties of the partition

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)
same procedures used to label internal drives as external (in this case ntfsprogs

then run ntfs-config

---

