---
title: "How can i help keep Ubuntu optimized?"
date: 2009-02-13
forum: General Help
---

### Post by Macfunky on 2009-02-13
When i used windows and my computer slowed down i would run anti virus, anti spyware etc and defrag my computer. My computer would be much quicker afterwards. 

I know people are going to hate me for thinking "the windows way". I know linux distros are different but i want to know what ways are there that i can keep Ubuntu running well? My installation has slowed down a noticeable amount since i installed it a month ago (i didn't use wubi. It was a full install onto a hard drive. No virtual partitions). I have plenty of hard drive space. It is a 160GB hard drive and only a tiny amount is being used. Any ideas on what i can do and also why my computer might have slowed down?

---

### Post by x33a on 2009-02-13
either you run a lot of unneccesary applications which put load on your system, or it's just your paranoia :)

i have been running this system for the past 6 months, installed hardy in september, then upgraded to intrepid (no clean install) and still i don't feel any slowdowns.

the most you can do is,

1. go to system->preferences->sessions, disable any unwanted startup program.

2. go to system->administration->services, remove any unwanted service (if any).

3.open a terminal, 

sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean

---

### Post by Macfunky on 2009-02-13
Hey. Thanks for the reply. I just realized this minute what was wrong. I had a program running on start up that i didn't know i had. So obvious :P Anyways ill check out all of what you said. Anyone else have any tips for if i ever need them in the future? Cheers

---

### Post by Yashiro on 2009-02-13
In what way is it 'slower'?

---

