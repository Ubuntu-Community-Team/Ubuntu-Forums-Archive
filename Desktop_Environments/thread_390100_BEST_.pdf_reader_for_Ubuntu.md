---
title: "BEST .pdf reader for Ubuntu"
date: 2007-03-21
forum: Desktop Environments
---

### Post by stchman on 2007-03-21
Hello all.  I am asking the opinions of the forum community as to what is the best .pdf reader for Ubuntu.

I tried a few and have come to the conclusion that for Ubuntu Adobe is the best .pdf reader.  Evince while functional is somewhat lacking and looks fuzzy.

Adobe seems to have the best functionality and works with printers.  I know that since it is not open source that many will think it bad, but I am a "just works" kind of guy.


I wish that Foxit would make their reader for linux as it absolutely rocks on windows.

---

### Post by Sluipvoet on 2007-03-21
Personaly I think kPDF is the best.
But it's written for KDE, so some GNOME/XFCE-users might prefer something else.

---

### Post by Lord Illidan on 2007-03-21
Adobe Reader...it is the official one and performs pretty well in Firefox too.

That said, evince is not bad.

---

### Post by kerry_s on 2007-03-21
Epdf is a light alternative to evince, but it has no printing.

---

### Post by stchman on 2007-03-21
Also are there any free .pdf editors out there for Ubuntu?

Thanks

---

### Post by stokedfish on 2007-03-21
Kpdf.

---

### Post by moore.bryan on 2007-03-21
> **stokedfish said:**
> Kpdf.
*for writing text into a pdf, not just flipping pages around?  i've always been told to gimp the pdf and write that way...*

---

### Post by futz on 2007-03-21
> **stchman said:**
> I wish that Foxit would make their reader for linux as it absolutely rocks on windows.
I run Foxit Reader with a simple little wrapper shell script in Wine. Works great. You have to use the old Foxit Reader that didn't have an installer.

The wrapper is for when you want to double-click on a pdf file in Nautilus or other program and have it open in Foxit Reader. The exact syntax of the call for this I can't remember, but if you can't figure it out just yell and I'll get it for ya.

Here's the wrapper:
```
#!/bin/sh
ROOT_DRIVE="Z:\\"
for arg
do
	wine "/home/futz/FoxitReader.exe" "${ROOT_DRIVE}$(echo "$arg" | sed 's/\//\\/g')"
done

```

For just starting the program with no file, call it with a launcher command like this:
```
wine /home/futz/FoxitReader.exe %U
```
I think you can dispense with the ' %U' part. Probably not necessary. Of course replace '/home/futz/' with your own directory to suit where you put the program.

Here's a good icon for your launcher:
[ATTACH]27980[/ATTACH]

Their new version WILL NOT work. At least I haven't got it to work yet.

Foxit has a linux version, but it's at the VERY rough alpha stage. You don't wanna use that thing yet.

Adobe Acrobat reader for linux sucks, in my opinion. Buggy and not nice to use.

---

### Post by stchman on 2007-03-21
> **stokedfish said:**
> Kpdf.

I will have to give that try, but I cannot see it being better than Acrobat.

---

### Post by futz on 2007-03-21
> **stchman said:**
> I will have to give that try, but I cannot see it being better than Acrobat.
Acrobat on windows is good, except for the horribly LONG load times. But on linux it's terrible. It's buggy and the keyboard shortcuts are wrong (I have my habits, ya know :mrgreen:)

Anyways, on windows I always used Foxit. Fast loading and good enough for 99% of pdf reading. So when I moved to linux I missed it terribly. Took me a while to figure out how to make it work. During that while I used all the usual linux pdf readers. Hated them all. Wanted Foxit.

But it's all down to personal preference. If you like adobe's linux reader then that's what's best for you.

---

### Post by stchman on 2007-03-21
> **futz said:**
> Acrobat on windows is good, except for the horribly LONG load times. But on linux it's terrible. It's buggy and the keyboard shortcuts are wrong (I have my habits, ya know :mrgreen:)

Anyways, on windows I always used Foxit. Fast loading and good enough for 99% of pdf reading. So when I moved to linux I missed it terribly. Took me a while to figure out how to make it work. During that while I used all the usual linux pdf readers. Hated them all. Wanted Foxit.

But it's all down to personal preference. If you like adobe's linux reader then that's what's best for you.

I went to the add/remove to install Acrobat reader and it flies.  I double click a .pdf file and 2 seconds later I am reading it with Acrobat.  I agree that Acrobat on Xp sucks but on Ubuntu it seems to be far better.

Are all your applications loading slowly?  I had a bout with that but was able to fix it.

Hopefully Foxit will make a .pdf reader for Linux as good as the one for Windows.

---

### Post by futz on 2007-03-21
> **stchman said:**
> I double click a .pdf file and 2 seconds later I am reading it with Acrobat.  
Speed isn't everything. Proper reading controls are important. I forget what bugs there were that irritated me, but they're there too. Between the bugs and the bad keyboard controls, I soon had enough of it and dumped it.

> Are all your applications loading slowly?
Nope. Why would they?

> Hopefully Foxit will make a .pdf reader for Linux as good as the one for Windows.
Would be nice, but meanwhile running in wine works fine.

---

### Post by dzqm on 2007-08-17
This is for the guy who complained about Adobe Acrobat Reader's horrible load times in Windows. Here's a PC Magazine link with tips on how to fix that- [http://www.pcmag.com/article2/0,1759,1663395,00.asp](http://www.pcmag.com/article2/0,1759,1663395,00.asp)
Though this tip was for v6.0, it worked for me in v7.x too. Can't say if it'll work in v8.x though.
I wish I could do something like this in the Linux version of the Acrobat Reader. Shall try and update this post.

> **futz said:**
> Acrobat on windows is good, except for the horribly LONG load times. But on linux it's terrible. It's buggy and the keyboard shortcuts are wrong (I have my habits, ya know :mrgreen:)

Anyways, on windows I always used Foxit. Fast loading and good enough for 99% of pdf reading. So when I moved to linux I missed it terribly. Took me a while to figure out how to make it work. During that while I used all the usual linux pdf readers. Hated them all. Wanted Foxit.

But it's all down to personal preference. If you like adobe's linux reader then that's what's best for you.

---

### Post by Jasper84 on 2008-02-26
[quote=futz]I run Foxit Reader with a simple little wrapper shell script in Wine. Works great. You have to use the old Foxit Reader that didn't have an installer.[/quote]
Cool. Will give it a try :)
Evince is pretty good, but i think it is not configurable enough. AFAIK you can not invert the color scheme. (white on black text) Also when i had a slower computer, i noticed it can be slightly slow in some cases. (Although not agruvatingly) As for adobe, i dont know for linux, but for it windows loads god-awfully slow. It is closed source, and i remember seeing ads on it, 'nuff said.

---

### Post by hugh on 2008-02-26
Adobe's reader is by far the best. It's not open source, but when a closed source program is so far ahead of its FOSS counterparts, I don't really care about the license. It's the same reason I happily run Office 2003 in Wine under Ubuntu.

---

