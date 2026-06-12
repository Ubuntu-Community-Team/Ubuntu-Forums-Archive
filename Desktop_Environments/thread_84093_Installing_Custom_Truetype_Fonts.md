---
title: "Installing Custom Truetype Fonts"
date: 2005-10-30
forum: Desktop Environments
---

### Post by Chiaro on 2005-10-30
Hello,

I've been using Ubuntu for a week now and I've installed the MSCoreTTF font package already. I downloaded the ps2 ttf font from [www.dafont.com](www.dafont.com), and I want to install it for The GIMP, Firefox and others.

I've already installed it for openoffice via "sudo cp btseps2.TTF /usr/share/fonts/truetype/openoffice/".

How do I make it show up for everywhere else?

-Chiaro

---

### Post by emendelson on 2005-10-30
Copy it to ~/.fonts

If that directory doesn't exist, create it. Don't forget the dot before "fonts".

---

### Post by Luggy on 2005-10-31
> paul@ubuntu:~$ mkdir ~/.fonts
mkdir: `/home/paul/.fonts' exists but is not a directory


What gives?

---

### Post by Ingla on 2005-10-31
Go to Places>Home 
when you're in, press CNTRL+h to show hidden files. Look for a directory .fonts.
If it's there, copy the fonts into it.
If it's not there, try right click and make a new directory, naming it .fonts ***while hidden files are still showing.***

---

### Post by sciurus on 2005-11-01
So it isn't necessary or advisable to follow the steps at

[http://www.paulandlesley.org/linux/xfree4_tt.html](http://www.paulandlesley.org/linux/xfree4_tt.html)?

1) create a directory and download the font to it  /usr/local/share/fonts/ttfonts
2) install ttmkfdir
apt-get install ttmkfdir
3) run ttmkfdir
cd /usr/local/share/fonts/ttfonts
ttmkfdir -o fonts.scale
4) Create fonts.dir
head -1 fonts.scale > fonts.dir
tail +2 fonts.scale | tac >> fonts.dir
cp fonts.dir fonts.scale

---

### Post by flibble on 2005-11-01
That document's dated "Revision 1.1 25 June 2001" and is for Xfree 4.3 on Debian. We're using a version of xorg, 5 years later. 

Maybe for historical background, but I wouldn't pay much attention to that doc for the specifics of file names, locations, directories etc...

---

### Post by keron on 2005-11-01
I believe you need to do
code]fc-cache[/code]
after copying a font to a font-folder. Atleast if you do it the non-gui-way... And restart the program that should show the font.

---

