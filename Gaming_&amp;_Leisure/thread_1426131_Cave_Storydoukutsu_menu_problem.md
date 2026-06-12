---
title: "Cave Story/doukutsu menu problem"
date: 2010-03-09
forum: Gaming &amp; Leisure
---

### Post by Oreo_King on 2010-03-09
So I went and downloaded the Linux version of Cave Story (doukutsu) and I created a launcher for it in my menu but for some reason it doesn't work.

When I click on it a very small window temporarily opens up but soon closes.

The game runs flawlessly when I go into it's folder and click on the executable.

Anyone got any  ideas on how I can fix this?

---

### Post by CharmyBee on 2010-03-09
The working folder/directory is not set.

---

### Post by Oreo_King on 2010-03-09
So how would I go about setting the working folder, CharmyBee?

---

### Post by Oreo_King on 2010-03-11
Well after doing some digging on my own I discovered that a bash script  might solve my problem, which it did.

Basically I opened up gedit and wrote the following:

> #!/bin/bash
cd ~/doukutsu && ~/doukutsu/doukutsu
doukutsuThat's assuming that your Cave Story folder  (doukutsu) is in your Home folder. If not edit the script to wherever  yours is.  Save it where ever you want. Right-click on it go to  Properties then from there Permissions and make it an executable. Test  it out to see if it works.

Then go to the menu, right-click and go to edit menu. Make a launcher  and browse to where you saved the bash script file.

Add an icon (if you want) and enjoy.

---

### Post by Infinite Indefinite on 2010-03-28
Thank you so much Oreo_King.  I had exactly the same problem, and using your script (with a little modification), I managed to solve it.

(The little modification was the removal of the third line, because I had given doukutsu the permission to run as a program).

Thanks again.  This was very helpful.

Incidentally, it can also be downloaded from:

[http://www.cavestory.org/downloads/linuxdoukutsu-1.01.tar.bz2](http://www.cavestory.org/downloads/linuxdoukutsu-1.01.tar.bz2)

I've also attached a png image that can serve as an icon for the launcher.

---

### Post by Perfect Storm on 2010-03-28
Even more simpler, in the launcher write;

```
sh -c "cd ~/doukutsu/doukutsu && ./doukutsu"
```

---

