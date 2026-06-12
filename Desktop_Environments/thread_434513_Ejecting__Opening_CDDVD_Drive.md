---
title: "Ejecting / Opening CD/DVD Drive?"
date: 2007-05-06
forum: Desktop Environments
---

### Post by strixy on 2007-05-06
Sorry if this is a silly question, it's late so I'm going to post a question and go to bed.

I have a lovely tower with a concealed CD drive bay. It's hidden behind a panel you see, which makes poking the eject button a little difficult without a paper clip or a big hammer. I would like to know how to open it.

I've tried right clicking on the icon in Nautilus, but it won't open if there isn't a CD in there.

I've gone though gconf-editor to see if there was anything I could tweak.

I've searched these forums, but it must be one of those things everyone already knows (except me).

Silly question, but if anyone has a tip, I would be grateful!

---

### Post by zek725 on 2007-05-06
open terminal

enter the following code:
```
eject
```

---

### Post by strixy on 2007-05-06
Ok, that works.

#-o

---

### Post by merlyn on 2007-05-08
Another option would be to browse to the "Computer" directory in Nautilus, right click on the icon for your CD/DVD drive and select eject from the drop down menu.

Cheers.

---

### Post by strixy on 2007-05-08
> **merlyn said:**
> Another option would be to browse to the "Computer" directory in Nautilus, right click on the icon for your CD/DVD drive and select eject from the drop down menu.

Cheers.

No luck.  That works if there is media in the drive but, "I've tried right clicking on the icon in Nautilus, but it won't open if there isn't a CD in there." It says something like, "unable to mount media in drive"... that might have something to do with not having any media in the drive ;)

---

### Post by merlyn on 2007-05-08
True enough, sorry I misinterperated your original post and thought you were refering to ejecting once media was in the drive.

Of course it goes without saying that you need to open the drive first to be able to place media in the drive.

Sorry.

---

### Post by strixy on 2007-05-08
> Of course it goes without saying that you need to open the drive first to be able to place media in the drive.


Don't worry - I gave the same advice to my wife and she said the same thing I said back to me. She's enjoying this thread a little too much ;)

---

### Post by thelocust on 2007-05-09
What about loading the drive?

---

### Post by TheTux on 2007-05-09
may you should assigned shortcut to eject command. That would be easier

---

### Post by strixy on 2007-05-09
I made a shortcut on her menu bar, and I'm setting up a hot key on her remote this weekend (It's an iMON VFD remote... wish me luck!) and then I'll be getting into the whole MyTH TV thang...

I also discovered in another post here in the forums that ALT-END should do the trick as well, though I haven't tested it personally.

---

