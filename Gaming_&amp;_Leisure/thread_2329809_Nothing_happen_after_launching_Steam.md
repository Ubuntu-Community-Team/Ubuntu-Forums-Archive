---
title: "Nothing happen after launching Steam"
date: 2016-07-05
forum: Gaming &amp; Leisure
---

### Post by foxl18 on 2016-07-05
Hi,I am new to linux. Yesterday,I installed Steam from the official website:[http://store.steampowered.com/about/](http://store.steampowered.com/about/) 
everything went well
but after launching it,it just pop up sth like "updating Steam..." .Then,it disappeared and nothing happened... Normally, it should ask me to login the existing account or create a new one.
But it does nothing.I tried to remove and reinstall it. Still the same situation. ](*,)Why is it like this?:confused::confused:

---

### Post by ajgreeny on 2016-07-05
Please use the default font when posting to the forum.

Using large, bold fonts is deemed to be shouting, is frowned on, and will often put off people from answering.

---

### Post by oldrocker99 on 2016-07-05
Read this first:[http://ubuntuforums.org/showthread.php?t=2324804](http://ubuntuforums.org/showthread.php?t=2324804) and check out the links.

The **best** way to (hopefully) fix the problem and install Steam properly is ```
remdir -p -v .steam && sudo apt-get install steam
```

---

### Post by QIII on 2016-07-05
Would you also please tell us which release of Ubuntu you are using and what graphics hardware you are using?

---

### Post by foxl18 on 2016-07-05
[SIZE=2]I am really sorry for being such impolite.Thanks for reminding and correcting me.[/SIZE]

---

### Post by uRock on 2016-07-05
OPen your home folder, then hit Ctrl+H to show hidden directories, then go to Home/.steam/steam/ubuntu12_32/steam-runtime/i386/lib/i386-linux-gnu/ and delete libstdc++.so.6. Open a terminal and start steam. 

Small font isn't being friendly either.

---

