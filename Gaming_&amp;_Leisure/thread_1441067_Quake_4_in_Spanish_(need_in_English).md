---
title: "Quake 4 in Spanish (need in English)"
date: 2010-03-28
forum: Gaming &amp; Leisure
---

### Post by bigseb on 2010-03-28
So I installed Quake 4 using the Linux installer from the id software ftp server. Went really smoothly only now when I start the game its all in spanish. How do I change it to English?

---

### Post by bigseb on 2010-03-28
Went to the config file and changed "spanish" to "english"... now it says nothing ie just "#str_103489" (or whatever)...

HELP!

---

### Post by bigseb on 2010-03-28
Got it sorted. 1st time I just opened the file , found where it said "spanish",backspaced and typed "english".

Wrong.

Now I typed this in the terminal: 

echo "seta sys_lang \"english\"" >> ~/.quake4/q4base/Quake4Config.cfg

and it works!

---

