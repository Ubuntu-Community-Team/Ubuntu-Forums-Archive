---
title: "choosing pictures for glslideshow screensaver?"
date: 2006-07-10
forum: Desktop Environments
---

### Post by delfick on 2006-07-10
hello

I couldn't find the answer to this question when i searched, so sry if it is already asked somewhere....:D

Basically, i want to know...how can you set which pictures are used for the glslideshow screensaver...(with gnome screensaver)

thnx

---

### Post by DJ Scribblinni on 2006-07-10
I personally don't like what Ubuntu did with the screen saver setup.  But if you do a ```
xscreensaver-demo
``` you will see a tab at the top label 'Advanced.'  There you will see a Image Manipulation section where you can modify where the screen saver grabs images.

---

### Post by ebash on 2006-07-10
> **delfick said:**
> hello

I couldn't find the answer to this question when i searched, so sry if it is already asked somewhere....:D

Basically, i want to know...how can you set which pictures are used for the glslideshow screensaver...(with gnome screensaver)

thnx

You have to create a folder named 'Pictures' in your home account and place your pictures there. There is no way to change the folder name, it must be called exactly 'Pictures' no matter the language/locale that you are using.

---

### Post by delfick on 2006-07-10
the pictures folder doesn't seem to work :'(
but xscreensaver-demo did...thuogh it seems to have trouble picking different pictures...

also... how can i get xwinwrap to use these pictures?

thnx

---

### Post by Nathaniel on 2006-08-07
To settle this once and for all:

Backup old "backgrounds"-directory, and link to a new one
> # cd /usr/share
# mv backgrounds/ backgrounds.old
# ln -s <your picture-directory> backgrounds


Edit GLSlideshow settings
> # nano -w /usr/share/gnome-screensaver/themes/glslideshow.desktop

You'll want to edit the line with "Exec=glslideshow -root" in it. Mine looks like this
> Exec=glslideshow -root -zoom 90 -duration 15 -pan 15 -fade 2 -clip
This will give you a GLSlideshow that starts off showing 90% of the picture and pan to 100% for 15 seconds. It will then fade over to the next picture for 2 seconds. "-clip" can be substituted for "-letterbox" if you don't want your pictures cropped to fit the screen.
More commands can be found by doing "man glslideshow".

I hope this settles it until the Gnome-people get their heads out of the sand and accept that not everyone wants to see a slideshow with only one picture, or see GLtext that ONLY tells you what kernel you're running :)

---

### Post by ariadacapo on 2006-09-27
Nathaniel,

this is really helpful. Works perfectly for me. Thanks!

---

### Post by quackking on 2006-10-09
I have Edgy Beta 2. There is no directory /usr/share/gnome-screensaver/themes. Where is this preferences file kept in Edgy?

---

### Post by Zwendel on 2006-10-10
Interesting,
where can we find all the settings we can use in that exec command for the glslideshow?
Thanks.

---

### Post by jleigh on 2006-11-25
By adding the imageDirectory argument to the ~/.xscreensaver file you don't have to change the backgrounds dir.

```
$ cat .xscreensaver
imageDirectory: /home/james/Media/Photos/
```

```
$ dpkg -S glslideshow.desktop
xscreensaver-gl: /usr/share/applications/screensavers/glslideshow.desktop
```

---

### Post by sciurus on 2006-11-25
> **jleigh said:**
> By adding the imageDirectory argument to the ~/.xscreensaver file you don't have to change the backgrounds dir.

```
$ cat .xscreensaver
imageDirectory: /home/james/Media/Photos/
```

```
$ dpkg -S glslideshow.desktop
xscreensaver-gl: /usr/share/applications/screensavers/glslideshow.desktop
```

Are you using gnome-screensaver? I didn't think it used the xscreensaver settings.

---

### Post by SentientFluid on 2007-10-03
> **Zwendel said:**
> Interesting,
where can we find all the settings we can use in that exec command for the glslideshow?
Thanks.

```
man glslideshow
```

> **quackking said:**
> I have Edgy Beta 2. There is no directory /usr/share/gnome-screensaver/themes. Where is this preferences file kept in Edgy?

In Edgy and Feisty you want:

```
gksudo gedit /usr/share/applications/screensavers/glslideshow.desktop
```

---

### Post by High Camp on 2007-10-20
Hi All

Just thought I'd share my experience thus far. I just upgraded to Gutsy and was missing the ability to change the folder were the pics are stored. I made a file called ~/.xscreensaver and just put the image directory specifier in there as posted previously and that changed the directory were it pulls the pics from (no need to change the backgrounds folder or anything).

Keep in mind I'm running Xubuntu with Ubuntu also installed so no guarantee it'll work for anyone else but I would try this solution first since it's quick and easy.

---

### Post by Laenny on 2007-10-23
Hello dear fellow Ubuntu Users!

I managed to set up glslideshow in Ubuntu 7.10 to use my personal imageDirectory by creating an appropiate .xscreensaverrc with xscreensaver-demo. 

BUT: Currently I have the issue that glslideshow only randomly picks a single picture from that directory and slides between that single image, resulting in a very boring slide show.

Any ideas, what might be causing this? 

I had been using OpenSUSE 10.2 before, and there glslideshow randomly chose pictures and slided between all of them ...

Thanks in advance,
Carsten

---

### Post by High Camp on 2007-10-25
Hello Laenny

Have you tried doing what Nathaniel suggested in post #5 of this thread ([http://ubuntuforums.org/showthread.php?p=1351165#post1351165)?](http://ubuntuforums.org/showthread.php?p=1351165#post1351165)?) The reason I ask is I'm wondering if it's simply displaying the one picture for too long. Also, is it always the same picture or is it a different picture each time the screen saver starts up? I am by no means an expert on this but if you have set the parameters as Nathaniel suggested then my next thing would be to completely remove it and install it again.

Hope that helps and let me know if you need more help,

---

### Post by DJ_Peng on 2008-03-17
> **Nathaniel said:**
> To settle this once and for all:

Backup old "backgrounds"-directory, and link to a new one


Edit GLSlideshow settings

You'll want to edit the line with "Exec=glslideshow -root" in it. Mine looks like this

This will give you a GLSlideshow that starts off showing 90% of the picture and pan to 100% for 15 seconds. It will then fade over to the next picture for 2 seconds. "-clip" can be substituted for "-letterbox" if you don't want your pictures cropped to fit the screen.
More commands can be found by doing "man glslideshow".

I hope this settles it until the Gnome-people get their heads out of the sand and accept that not everyone wants to see a slideshow with only one picture, or see GLtext that ONLY tells you what kernel you're running :)
Awesome post! I'd click on the Thank You button if there was one on your post. This is the info I've looked for on every reinstall and I've finally bookmarked it so I can have it handy.

---

