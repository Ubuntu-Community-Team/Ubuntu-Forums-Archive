---
title: "[SOLVED] How do I get 915resolution to load at startup?"
date: 2007-09-02
forum: Desktop Environments
---

### Post by staticvoid on 2007-09-02
I read the readme and I cannot find where to put the code to get my patch to load at startup. I'm sure there is an easy fix for this... Do I need to put "915resolution 34 1280 768 24" in some "run level"? what is that by the way? where is my boot.local file? Thats where the readme said to put this line of code, but he is using opensuse...:confused:


staticvoid

---

### Post by Gremlinzzz on 2007-09-02
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by staticvoid on 2007-09-03
Ahhhh, Thank you. I will deffinatly bookmark those. Hehehe, no need to post anything here I guess since I've got the manual :) I got it to work. For those interested:

put "915resolution 45 1280 768" (or whatever you have) into "bootmisc.sh" i think its in /etc/boot or something....search for it.

bye! and thanks again Gremlinzzz!

static voidzzz

---

