---
title: "World of Goo help"
date: 2012-08-08
forum: Gaming &amp; Leisure
---

### Post by exkend on 2012-08-08
Hello, could anyone help me get world of goo up and running on ubuntu 12.04 amd64. It seems to have installed properly but nothing happens when I try opening it. I got from the humble indie bundle if that means anything. 
 Thanks

---

### Post by oldrocker99 on 2012-08-08
OK, I tried from the command line after it wouldn't start from the menu for me either.:
oldrocker99@oldrocker99-desktop:/opt/WorldOfGoo$ ./WorldOfGoo
Segmentation fault (core dumped)

It looks like World of Goo crashed! If you need support, please include the
contents of the log file in your problem report.
The log file is stored at: /home/oldrocker99/.WorldOfGoo/WorldOfGoo.log

So, I then entered

oldrocker99@oldrocker99-desktop:/opt/WorldOfGoo$ ./WorldOfGoo.bin64
 (you may need the .bin32 file)

...and it ran just fine.

A bit o' trouble here; it ran just fine from the menus under earlier Ubuntu distros.

---

### Post by BigSilly on 2012-08-10
I always install the [GooTool]("http://goofans.com/gootool") from their website (it's free), and then set it up from there. I have to use this because I have a widescreen monitor and the Tool gives you the settings for this. You'll need OpenJDK 6 for it to work (in the repos).

What you have to note, if you make any changes, is that World of Goo will ask you to install it to a different directory. I always make a "Games" folder, and in that a "World Of Goo" folder, and that's where I stick the install. Then, you need to install "Main Menu" from the repository, and in that you can point the executable to the new location. So mine would be in /Home/Games/World Of Goo, and it's the WorldOfGoo binary you need, not the bin32 or bin64 one. Just browse to it in Main Menu.

Hope this helps. If not, keep us posted.

---

