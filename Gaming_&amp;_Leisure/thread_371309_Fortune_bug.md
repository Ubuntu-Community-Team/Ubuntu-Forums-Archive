---
title: "Fortune bug?"
date: 2007-02-26
forum: Gaming &amp; Leisure
---

### Post by Nameless_one on 2007-02-26
I was looking at the datafiles for fortune today, and out of curiosity, I ran ```
fortune <some-offensive-datafile>
``` which should return a fortune from the datafile of that name, but it reported finding no fortunes. I tried many offensive datafiles and the same happened with all of them. I tried an inoffensive datafile, and it worked just fine. 

However, I know the offensie fortunes are there, because they appear quite often when I open new term9inal windows (I have added fortune to my .bashrc file). 

Is this a bug? 

I am on Edgy Eft, amd64 architecture, btw.

---

### Post by Duncan_Idaho on 2007-02-27
sorry for the offtopic, but how do you added fortunes to the .bashrc file?
how and in wich part?
thanks :)

---

### Post by kerry_s on 2007-02-27
link /usr/games/fortune to /usr/bin/fortune
sudo ln -s /usr/share/games/fortune /usr/bin/fortune

I use it in conky. :)

---

