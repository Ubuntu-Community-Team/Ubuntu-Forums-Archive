---
title: "No equivalent to Windows US International keyboard layout?"
date: 2010-10-08
forum: Desktop Environments
---

### Post by robfuller on 2010-10-08
Hello,

The only thing I miss about Windows is the US International keyboard setting. Is there really no equivalent in Ubuntu?

The current Ubuntu US International keyboard setting is just not the same. "whodoesitwant" explained the difference last year ([http://art.ubuntuforums.org/showthread.php?p=7762169](http://art.ubuntuforums.org/showthread.php?p=7762169)), and it has been asked about before (e.g. [http://ubuntuforums.org/archive/index.php/t-476775.html](http://ubuntuforums.org/archive/index.php/t-476775.html)). Does anyone know if there are plans to implement a Windows-like keyboard setting?

This may seem petty, but it's a real nuisance if you've learned to touch type in Windows. At the moment the best I can find in Ubuntu is the US International (AltGr dead keys) layout, but it's awkward and slow using the right-hand alt key.

Does anyone have any thoughts on this? How difficult would it be to implement?
Rob

---

### Post by amastronardi on 2010-10-08
I have 10.10 RC with US international with deadkeys and can reproduce the behavior of US International as stated in wikipedia: [http://en.wikipedia.org/wiki/Keyboard_layout#US-International](http://en.wikipedia.org/wiki/Keyboard_layout#US-International)

How does Windows implement US International? What do you see as missing in ubuntu implementation of US international keyboard?

Regards.
AM

---

### Post by robfuller on 2010-10-09
The description on Wikipedia is incomplete. This post has a good explanation of the difference: [http://art.ubuntuforums.org/showthread.php?p=7762169](http://art.ubuntuforums.org/showthread.php?p=7762169)

Essentially, both Ubuntu and Windows US International keyboards replace ' and e by é, and " and o by ö (and so on).

But the difference is that in Windows, if I type ' and s or ' and l, the system knows that those letters don't normally use diacritics, and so it sensibly produces 's or 'l (as in words like "it's" or "I'll"). But the Ubuntu US International keyboard instead produces the strange characters &#347; and &#314;.

Even more strangely, in Maverick, if I type ' and t (as in "don't" or "can't"), nothing appears at all. I have to type a space after the apostrophe to get 't.

Do you see what I mean?
Rob

---

### Post by robfuller on 2010-10-19
I take it the lack of replies means that nobody has worked on a keyboard like this?

From looking at my /usr/share/X11/xkb/symbols/us file, I understand the difficult: I want ' and ` and " and other keys to act sometimes as dead keys, but sometimes not, depending on which character follows them. Is it possible to achieve this in Ubuntu?

Rob.

---

### Post by halfbeing on 2011-03-07
> **robfuller said:**
> But the Ubuntu US International keyboard instead produces the strange characters &#347; and &#314;.


You mean &#347; as in &#346;r&#299; Lank&#257;? ;)

---

### Post by robfuller on 2011-03-07
Yes, I do... But to be honest, I don't use that character very often (by which I mean never!). The Windows USA international keyboard is great for typing most European languages, and the keyboards offered in Ubuntu are very awkward in comparison. I won't be able to use Ubuntu seriously until it has a way to mimic the international keyboard.

---

### Post by Tamhvm on 2011-04-04
I have also had this problem with Ubuntu and other Debian-based distros. However, I arrived to a nice solution, which combines the findings from several pages around the Web with a lot of testing and experimentation.

*Win US Intl for Linux* is a series of scripts I wrote to solve the issue of having problems with the Linux's native US Intl keyboard layout, just as the OP wrote. I use it mainly because my mother language is Spanish, and I still use lots of English forums, texts, chats and so on (like this site).

To note: This is actually similar (not totally equal) to the behavior of Windows XP US - International keyboard layout.

You can go to [http://t.tam.x10.mx/en/win-us-intl-4-linux/]("http://t.tam.x10.mx/en/win-us-intl-4-linux/") to check it out. I'm in the process of making it better, by adding more XCompose entries for several other borderline cases, among other changes.

[SIZE="1"]EDIT#1: Edited to update the web address.[/SIZE]

---

