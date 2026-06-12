---
title: "Konqueror video previews"
date: 2005-12-14
forum: Desktop Environments
---

### Post by medgno on 2005-12-14
Back when I last used kde (3.3 ish) I remembered that video files would have a frame from the file as a thumbnail image. Now that I give 3.5 a try I can't seem to get this to happen. I'm at my wit's end trying to figure out how to get this to work, so if someone could please point me in the right direction (or correct my memory) I would really appreciate it.

---

### Post by GoldBuggie on 2005-12-14
That should be the options in
konqueror->settings->configure konqueror->previews & meta data

Check some boxes in the local protocol tree. The ones I got check are Applications, file, fonts, home, locate, media, remote, system, tar, zip

---

### Post by medgno on 2005-12-15
I already had file enabled, and all the other filetypes I have are thumbnailing correctly, it's just the movie files that are not working. Do I need to install something like kplayer or kmplayer to get it to work? I've got kaffeine, but that's not doing the trick.

---

### Post by GoldBuggie on 2005-12-15
ok had a look and found where to change it:D

konqueror->view->preview->"Check the thing you want to have a preview of; in your case video"

---

### Post by GeneralZod on 2005-12-15
Have you installed the kde-multimedia packages?

---

### Post by medgno on 2005-12-15
Thank you GeneralZod! That worked perfectly.

---

### Post by FedeXX on 2006-05-01
I've already checked the boxes (in view/preview too) and i've kde-multimedia installed, but still i can't see any video preview :|

---

### Post by t.rei on 2006-05-04
Same Problem as FedeXX :(
Darn, thats like one of the last few things I want to get working - It's not essential, but I sooo want it. 
I dont have anything like the "video" or "movie" or something checkbox in the view->preview menu of my konq... I guess I'm missing something here?

*edit*
Ok, I did some desperate google searching and found something about video-previews not working in FC4 due to this feature being moved into the package "kdemultimedia-extras-nonfree" wich gives me the shivers. Also - there isn't even a "kdemultimedia-extras" in ubuntu? Anyone confirm my fears of video-previews in Konqueror being gone?

*edit2*
Ok, now I feel like... erm... like something dirty was done to me:
After relogging my previews are there... *cough* Not used to this "You must restart your machine now" syndrome. ;)

---

### Post by FedeXX on 2006-05-05
[QUOTE=t.rei]Same Problem as FedeXX :(
Darn, thats like one of the last few things I want to get working - It's not essential, but I sooo want it. 
I dont have anything like the "video" or "movie" or something checkbox in the view->preview menu of my konq... I guess I'm missing something here?

*edit*
Ok, I did some desperate google searching and found something about video-previews not working in FC4 due to this feature being moved into the package "kdemultimedia-extras-nonfree" wich gives me the shivers. Also - there isn't even a "kdemultimedia-extras" in ubuntu? Anyone confirm my fears of video-previews in Konqueror being gone?

*edit2*
Ok, now I feel like... erm... like something dirty was done to me:
After relogging my previews are there... *cough* Not used to this "You must restart your machine now" syndrome. ;)[/QUOTE]

That worked for me too.... :D This is the first "windows like" problem solving on linux... :P

---

### Post by anacron on 2006-05-26
what i had to do was just ```
sudo apt-get install kdemultimedia
```
(im using breezy, so breezy repositions) and then restart konqueror, that's about it, oh and i also enabled those meta thingies, but i don't know if they did do anything because i added them before downloading the package..

---

