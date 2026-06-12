---
title: "Moving dashboard to the left"
date: 2014-02-02
forum: Desktop Environments
---

### Post by guillaume5 on 2014-02-02
Hi everybody,

I just moved from Windows 7 to Xubuntu.
Originally, dashboard is on top.
I have moved it to the left, but I have not managed to change the font orientation.
I had a good look around, but no one seems to have raised this point before.

How can I get the font to be horizontally aligned, as Windows does ?[ATTACH=CONFIG]250020[/ATTACH]


Thanks in advance

Guillaume

---

### Post by vasa1 on 2014-02-02
> **guillaume5 said:**
> ..
I just moved from Windows 7 ... as Windows does ?
Could you please, if possible, also post an image of how Windows 7 does a vertical panel?

---

### Post by guillaume5 on 2014-02-02
> **vasa1 said:**
> Could you please, if possible, also post an image of how Windows 7 does a vertical panel?d 

I wish I could ! I no longer use Windows 7, and considering your answer it looks like I am wrong !
Sorry about that, and please consider the following question:

" On dashboard, how can I get the font to be horizontally aligned ? "

---

### Post by The Cog on 2014-02-02
I don't think you can rotate the fonts. The closest I could find was this:
[ATTACH=CONFIG]250025[/ATTACH]

> ...and considering your answer it looks like I am wrong !
Not necessarily. Your error may be in assuming that people here know what win7 looks like.

---

### Post by vasa1 on 2014-02-02
> **The Cog said:**
> ... Not necessarily. Your error may be in assuming that people here know what win7 looks like.
Exactly, I'm curious to know how a longish line of text (say date and time) would be accommodated.

---

### Post by guillaume5 on 2014-02-02
> **vasa1 said:**
> Exactly, I'm curious to know how a longish line of text (say date and time) would be accommodated.

As far as I remember, time and dates switch on two or thre different lines. Days' names are shortened as well.
For instance, 14:47 Sunday February 2nd would turn into:
14:47
Sund.
Feb. 2nd

I am not sure for application icons.

---

### Post by vasa1 on 2014-02-02
@The Cog, do you think it's possible to wrap at least time and date by using **\n** to introduce line breaks?

So, 
%a %d %b  %I:%M = Mon 08 Oct 11:05 with \n would be
%a %d %b\n%I:%M

I'm not on Xfce now and so can't test it.

---

### Post by Toz on 2014-02-02
Depending on the version of Xfce you are using, the Panel may have a "Deskbar" mode (see Panel Properties). This mode will rotate the text. You can also use %n as a newline indicator to break up the line. So this custom format: ```
%R%n%a%n%b %d
```...in Deskbar mode looks like this:
[ATTACH=CONFIG]250027[/ATTACH]

---

### Post by vasa1 on 2014-02-02
> **Toz said:**
> Depending on the version of Xfce you are using, the Panel may have a "Deskbar" mode (see Panel Properties). This mode will rotate the text. You can also use %n as a newline indicator to break up the line. So this custom format: ```
%R%n%a%n%b %d
```...in Deskbar mode looks like this:
...
So does **%R** do some sort of magic to allow line breaks or something else?

Oops. Should have looked at **man date** first. It's explained there.

---

### Post by guillaume5 on 2014-02-02
Great ! This is just what I needed, many thanks to you three.
Using the deskbar mode (instead of the vertical one) made the font the right way around.
Using the code you gave me set up time and date nicely.
This is what I first got:
[ATTACH=CONFIG]250029[/ATTACH]

I had to keep a very large panel ("what I first called "dashboard") in order to accomodate for my name.
When rightclicking onto my name, I was offer an "icon" mode which was much better. Here is what I got:

[ATTACH=CONFIG]250030[/ATTACH]

Thanks again.

Guillaume

---

### Post by vasa1 on 2014-02-02
> **guillaume5 said:**
> ...
Thanks again.

Guillaume
Hey, I'm going to try the %n trick myself. So *thank you* for posting your query :)

---

