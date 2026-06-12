---
title: "using feh"
date: 2009-05-20
forum: General Help
---

### Post by frpaul on 2009-05-20
Hello everyone!
You guys have a huge community here, thats great!

I recently switched to Ubuntu from Windows XP. Itd happened several times before, I tried several distributions. I guess this time I finally stay with Linux, because I really liked Ubuntu, especially Aptitude. I hope to find some help on this forum in getting more efficient with this OS, so heres the most persistent questions:

1 I have to customize file associations in mc. Ive chosen 'feh' for viewing pictures, so I edited my ~/.mc/bindings this way:
Open=feh %s >/dev/null 2>&1 &
Probably I added too much options, so please correct me.
Now if I whant to see a number of pics, I highlight them in mc and <Enter> the 1st of them. The problem is - they go in loop. I would like feh to stop (or something :) when it reaches the end of the list. How its done, please?
Is there any other way to preload pictures, so I could move from one picture to another, knowing that I didnt reach the end of the list?

2 How do I make vim the default editor for mc instead of cooledit? I still dont get this run-mailcap thingy in detail.


Thank you for your time.
Regards.

---

### Post by megamania on 2009-05-21
> **frpaul said:**
> Probably I added too much options, so please correct me.
Now if I whant to see a number of pics, I highlight them in mc and <Enter> the 1st of them. The problem is - they go in loop. I would like feh to stop (or something :) when it reaches the end of the list. How its done, please?
Is there any other way to preload pictures, so I could move from one picture to another, knowing that I didnt reach the end of the list?

I can't help you much, but if you open a terminal and type "man feh" you will see all the options for that program.

---

### Post by frpaul on 2009-05-23
> **megamania said:**
> I can't help you much, but if you open a terminal and type "man feh" you will see all the options for that program.

Sure, theres lots of stuff in the man page and I honestly tried to understand it, but Im still weak in thechnical English. Probably have to experiment a bit with different keys. Thanks anyway.

---

### Post by frpaul on 2009-05-27
> How do I make vim the default editor for mc instead of cooledit? I still dont get this run-mailcap thingy in detail.
I've found solution to the second problem.
sudo update-alternative --config editor. 
Then choose from the list. I've chosen vim basic.
The same works for browser (Opera by default, which is quite strange to me).
sudo update-alternative --config x-www-browser
Now all html files start with firefox from mc.

---

### Post by kerry_s on 2009-05-27
use the "-t" option for thumbnails, you can click on the thumbnails.

---

### Post by frpaul on 2009-05-27
> **kerry_s said:**
> use the "-t" option for thumbnails, you can click on the thumbnails.

Thanks, I tried this, useful stuff. 
Also tried to preload 
feh -p ./*
Well... still doesnt stop at the end of the list. Probably should try -A option (actions). Just cant make up a command to quit feh when riching first file in directory again.

---

### Post by kerry_s on 2009-05-27
maybe you should try "eog" instead, it's more of a standard image viewer.
if you have gnome, it's already installed.

---

### Post by frpaul on 2009-05-28
> **kerry_s said:**
> maybe you should try "eog" instead, it's more of a standard image viewer.
if you have gnome, it's already installed.

Thank you, Ive already tries it before. The point is - eog doesnt stop on the last photo in the directiory either. And it takes quite a time to load images in comparison with feh. Probably Image Magic is the way to look?

---

### Post by kerry_s on 2009-05-28
> eog doesnt stop on the last photo in the directiory 

i don't understand this, the image viewer only shows the images in the current folder your in, it does not, leave that folder, so if it only shows the images that are there, how can it not stop?

---

### Post by frpaul on 2009-05-28
> **kerry_s said:**
> i don't understand this, the image viewer only shows the images in the current folder your in, it does not, leave that folder, so if it only shows the images that are there, how can it not stop?

well, if you knew irfan-view windows image browser you'd understand me better. Anyway. 
ls > somefile
we got there list of files, right?
I just want feh (or some other viewer) to stop when it reaches last file, or at least let me know when its going to show the first image again.
A pity it cant be done from outside the programm if it accepts no arguments of that kind.

---

### Post by kerry_s on 2009-05-28
> **frpaul said:**
> well, if you knew irfan-view windows image browser you'd understand me better. Anyway. 
ls > somefile
we got there list of files, right?
I just want feh (or some other viewer) to stop when it reaches last file, or at least let me know when its going to show the first image again.
A pity it cant be done from outside the programm if it accepts no arguments of that kind.

okay, now i know what you mean.
i usually just look at the number on the statusbar.(see pic)
and if you use the slideshow, you can uncheck loop in the preferences.

---

### Post by frpaul on 2009-05-29
> **kerry_s said:**
> okay, now i know what you mean.
i usually just look at the number on the statusbar.(see pic)
and if you use the slideshow, you can uncheck loop in the preferences.

Thanks, probably the second suggestion will work with eog. On the other hand there have to be feh config somewhere. If I find some solution, Ill post here.

---

### Post by megamania on 2009-05-29
Ok, you tickled my curiosity...  :-)

add the *--cycle-once* option and you'll be done.

---

### Post by frpaul on 2009-05-29
> **megamania said:**
> Ok, you tickled my curiosity...  :-)

add the *--cycle-once* option and you'll be done.

Great! 
Sorry, I should read feh --help first.
Theres nothing in the subject in man feh page, which is strange.
Thanks a lot!

---

