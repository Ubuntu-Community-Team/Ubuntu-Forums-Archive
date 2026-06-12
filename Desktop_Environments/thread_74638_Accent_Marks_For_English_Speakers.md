---
title: "Accent Marks For English Speakers?"
date: 2005-10-12
forum: Desktop Environments
---

### Post by schnarff on 2005-10-12
Hello,

I've got what may be a very rare question here. I'm a native English speaker, and I've never used a keyboard layout besides the standard 104-key US-English. However, I also speak French, and I've suddenly started sending a fair amount of e-mail in French. The problem I'm faced with is that French can be difficult to understand without the proper accent marks, but in order to get characters with accents, I must insert them as special characters in Thunderbird (or whatever app I'm using, for that matter).

Is there a simple way in Hoary to create keyboard shortcuts that will allow me to insert accented characters? For example, could I map my left Windows key such that hitting "LeftWin"-"a" would create an "a" with an accent aigu, and my right Windows key to have "RightWin"-"a" make an "a" with an accent grave? I've looked in System->Preferences->Keyboard Shortcuts, System->Preferences->Keyboard, etc., and while I´ve seen layouts that look like they might do the trick (i.e. International w/dead keys), they don´t seem to actually do the job. I may of course be missing something, or just not know how to produce these characters; if that´s the case I´d appreciate some information on how to use the different layouts.

Thanks,
Alex Kirk

---

### Post by Olav on 2005-10-12
With the "dead key" keyboard layout enabled, you can simply type:

['][e] to get é
[`][e] to get è
[^][e] to get ê
["][e] to get ë

etc.

A tricky one would be the cedilla. You have to hold the right Alt key while you type a comma, and then type the letter c (the only character in French to ever get a cedilla) to get ç.

Just type a space after the apostroph, quotation mark or whatever, if what you want is not an accented character but just the sign itself, like this:

["][ ] to get "

When programming or writing HTML, where you have to do lots of quotation marks, this can be very annoying. For that purpose you can put a keyboard layout switcher on the Gnome panel. Personally I am so used to using dead keys all the time that I find it difficult to *not* type spaces after quotes, so I just leave the layout the same.

---

### Post by Olav on 2005-10-12
Playing with the keyboard settings I just found an alternative, which you may find even better (even when I don't):

First you enable your normal "U.S. English" layout:

[INDENT][[IMG]http://img418.imageshack.us/img418/3812/screenshot200510121934462sz.th.png[/IMG]](http://img418.imageshack.us/my.php?image=screenshot200510121934462sz.png) (click)[/INDENT]

Then you designate your right Alt key (or one of the alternatives) as your "Compose" key:

[INDENT][[IMG]http://img412.imageshack.us/img412/2969/screenshot200510121934551sq.th.png[/IMG]](http://img412.imageshack.us/my.php?image=screenshot200510121934551sq.png) (click)[/INDENT]

From then on, you can type:

[right alt + '][a] to get &#225;

This configuration does not interfere with the normal use of the apostroph and quote mark.

---

### Post by Commuto on 2006-03-07
For the ones doing this without any success :(, there is indeed some king of anoying bug in 5.10. Have a look at [http://bugzilla.ubuntu.com/show_bug.cgi?id=15372](http://bugzilla.ubuntu.com/show_bug.cgi?id=15372) for a fix :D

---

### Post by fakie_flip on 2007-02-27
> **Olav said:**
> 
...
From then on, you can type:

[right alt + '][a] to get á

This configuration does not interfere with the normal use of the apostroph and quote mark.

That worked, but how can I type

```
¿
```

and

```
ñ
```

---

### Post by holdie on 2007-03-02
not sure about the upside down question mark, but pressing

*compose* + *~* + *n* will get you *ñ*

---

### Post by holdie on 2007-03-02
ah, just figured out the question mark, just press 
*compose* + ? + ? again

same goes for other punctuation ¡

---

