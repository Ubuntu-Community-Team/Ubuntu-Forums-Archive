---
title: "Emerald --replace does nothing :/"
date: 2010-06-05
forum: Desktop Environments
---

### Post by Henrywenry on 2010-06-05
Hello,

I'm running a recently installed version of 'buntu 9.10 and I installed emerald from the repositories. However when I run ```
emerald --reaplce
``` nothing happens..

The little cursor blinks in the box like it did when it worked under my old distro but nothing changes in the rest of the operating system. Running as root doesn't help.

Thanks in advance

---

### Post by dv3500ea on 2010-06-05
are you using compiz?
In which case you need to use [compizconfig settings manager]("compizconfig-settings-manager") and under effects -> window decorations you need to change command to ```
emerald --replace
```

---

### Post by Henrywenry on 2010-06-05
I installed compizconfig settings manager from the repositories and changed that line to emerald --replace.

 Same thing happens unfortunately. even after restart.

---

### Post by ajgreeny on 2010-06-05
In your System -Preferences menu there should be an entry for **Emerald settings manager**, or something similar, I don't bother with it any more since Lucid, so can't remember.

Open that and play with the emerald theme settings, and get more themes as well, and you may see a big difference.

---

### Post by Henrywenry on 2010-06-05
Unfortunately messing with the settings or changing theme doesnt help. 

When you type the command in a terminal it just sits there, blinking to itself, doing not alot. I toyed with the idea of it having something to do with my rather funny graphics card, but then the same version (i think) of emerald worked for me in Hardy Heron so i dont think that's likely

I dont really know what to do so any ideas welcome :)

---

### Post by VastOne on 2010-06-05
Are you sure that you have Visual Effects enabled?

---

### Post by deadlockedgamer on 2010-06-05
I just install compiz icon click the installed app then right click on the thing on the top and select emerald as the windows manager. just make sure effects are on first :)

---

### Post by Henrywenry on 2010-06-06
I think so. I couldnt see any check box or anything of a similar nature labelled visual effects, but all seemingly relevant items I have ticked.

I've included some screenshots of what I have and havn't got selected

---

### Post by realzippy on 2010-06-06
Can confirm that something is wrong with emerald.Strange thing is that sometimes it works,sometimes not...
figured out that it might be a compiz problem since *compiz --replace* in terminal dies without response;same randomness.Just saw that there is a kernel update,i'll give it a try.

---

### Post by ajgreeny on 2010-06-06
If you use System -Preferences -Appearance does it show compiz being used in the Visual Effects tab, or are none of the radio buttons selected.  On my system with compiz running (not emerald any more, though I used to use it) none of the buttons are selected, see screenshot.  I do have compiz in my startup applications with the command ```
compiz --replace
```and that gives me full effects as I set them in CCSM with no problem.

---

### Post by Henrywenry on 2010-06-06
Ah okay. It transpires that my stupidity knows no bounds. I have finally gotten emerald --replace to do something.

It turned out that two things were a miss: 1) I didnt have the proprietry driver for my graphics card installed, and 2) I didnt have visual effects enabled anyway.

after having enabled visual effects from System > Preferences > Appearance and installed the driver it all works now. thanks for everyone's help.

---

