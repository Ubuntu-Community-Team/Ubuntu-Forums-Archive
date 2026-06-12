---
title: "java, repositories, and the like..."
date: 2007-09-18
forum: Debian
---

### Post by tcoffeep on 2007-09-18
Hey all,
I'm just getting into Debian, and I can't seem to figure out how to install Java and the such. Is there any online tutorials on how to do this? Beyond that, is there some sort of "non-free" or similar repositories I should add?
Just trying to figure things out. I've tried googling it, but that didn't help much. If anyone would be willing to help, I'd owe you big. :)

---

### Post by rsambuca on 2007-09-18
You can get a list of the mirrors at [this site]("http://www.debian-multimedia.org/").

---

### Post by tcoffeep on 2007-09-18
And that includes the nonfree repositories?

---

### Post by tubasoldier on 2007-09-18
You might also take note that like Ubuntu, Debian does not include the community repository by default in the sources list. It is acually present, you just need to uncomment the lines in the sources.list.

---

### Post by jdhore on 2007-09-20
deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) stable main contrib non-free
deb-src [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) stable main contrib non-free

deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) stable main

Add those 3 lines to your sources.list (of course substituting stable for whatever version you run) and you'll have everything you want or need as far as drivers, non-free stuff, non-free multimedia stuff, etc.

---

