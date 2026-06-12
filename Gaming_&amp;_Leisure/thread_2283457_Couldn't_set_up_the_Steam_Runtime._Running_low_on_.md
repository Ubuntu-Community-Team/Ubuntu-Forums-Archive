---
title: "Couldn't set up the Steam Runtime. Running low on disk space?"
date: 2015-06-22
forum: Gaming &amp; Leisure
---

### Post by orglce on 2015-06-22
Hello.

Recently when I was trying to open Steam I got this message. "Couldn't set up the Steam Runtime. Are you running low on disk space?". Just this, no logs or anything.
Before this, Steam was working just fine. And no, I am not running low on space. I have 90 Gb of free storage on my SSD. 
I have tried some things I could find on other forums but nothing has helped. I have ubuntu 15.04 64bit.

[IMG]http://shrani.si/f/M/DB/4tUY3AWz/screenshot-from-2015-06-.png[/IMG]

These are the solutions I tried:
 - [http://steamcommunity.com/app/221410/discussions/0/864978835568084247/?l=german](http://steamcommunity.com/app/221410/discussions/0/864978835568084247/?l=german)
 - [https://github.com/ValveSoftware/steam-for-linux/issues/2881](https://github.com/ValveSoftware/steam-for-linux/issues/2881)
 - I also tried purging and reistalling Steam
- I tried steam --reset but it gives me the same error

Thanks in advance!

---

### Post by orglce on 2015-06-26
I have resolved the problem. I didn't realize that i have installed Steam on my secondary hard drive. So, i just deleted the folder and run steam again. It asked me if i want to reinstall into ~/.local/share/Steam. And now everything works great.

---

### Post by erick11 on 2015-07-10
How you solve this?? 
How you managed to remove steam from the secondary hard drive??

Thanks

---

