---
title: "Menumaker problems: ./mmaker: command not found"
date: 2009-09-06
forum: Desktop Environments
---

### Post by Bucky Ball on 2009-09-06
Hi. I am using Openbox (not Gnome-Openbox) and attempting to install MenuMaker.

I got it happening on my own machine last night with the help of this site:

[http://urukrama.wordpress.com/openbox-guide/#Menus](http://urukrama.wordpress.com/openbox-guide/#Menus)

But am having problems on my wife's computer. I have menumaker extracted and am in the appropriate folder. When I issue this command in a terminal:

```
tar xzvf menumaker-0.99.7.tar.gz
```I get this error message everywhere:
```

Cannot utime: Operation not permitted
```
I can get to the right place to run menumaker by issuing:
```
cd menumaker*
```... but when I try to run Menumaker I get this:

```
anna@Lounge:/media/musicvid/Debs/menumaker-0.99.7$ ./mmaker OpenBox3
bash: ./mmaker: Permission denied
anna@Lounge:/media/musicvid/Debs/menumaker-0.99.7$ sudo ./mmaker OpenBox3
sudo: ./mmaker: command not found

```Any ideas? Love to get this going as just getting obsessed with OpenBox! Ask for more info if required.

---

