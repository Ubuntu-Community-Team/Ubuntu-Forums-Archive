---
title: "Can you have Emerald Themer without Beryl?"
date: 2007-05-23
forum: Desktop Effects &amp; Customization
---

### Post by iceportal on 2007-05-23
I've got Compiz and Compiz-Settings installed (default desktop-effects plus the settings manager). I do not have Beryl installed, because last time I installed it, the contents of windows would not show up.

What I'm wondering is, can I install the Emerald Themer for Compiz? So I can have great-looking themes without needing to use Beryl? Or is Beryl a requirement of the Emerald Themer?

And... If it IS possible to install the Emerald Themer without requiring Beryl (just Compiz), how can I accomplish this?

And... This is the kicker... Can I accomplish this WITHOUT using the Terminal?

(If terminal use is required, that's fine... But I'm writing a tutorial for the Average Joe User, and I'm doing my best to avoid the terminal at all costs, since that's one of the biggest fears Windows users have of Linux, and a big reason they refuse to switch. They'd rather use Windows than have to learn how to use the Terminal.)

---

### Post by iceportal on 2007-05-23
Ah, and in case anyone's curious, you can see the current status of my Ubuntu Experiment here:

[http://ubuntu.gridrunners.com]("http://ubuntu.gridrunners.com")

It's basically an experiment to see just how user-friendly Linux can be, and to see if I can accomplish everything I need without using the command terminal. (Basically... Windows users are afraid of using a command prompt, which is a big reason they avoid Linux. I'm hoping to dispel the rumor that it's impossible to get what you want out of Linux without using the terminal.)

---

### Post by iceportal on 2007-05-23
Nobody has anything to say? No ideas?

---

### Post by eks on 2007-05-23
You can try searching the forums. ;)

Searching ["emerald with compiz"]("http://ubuntuforums.org/showthread.php?t=423743&highlight=emerald+with+compiz") can yeld you excellent results.


eks

---

### Post by iceportal on 2007-05-23
Thanks... Gotta think about search strategy next time. :-)

---

### Post by crimesaucer on 2007-05-23
If I remember correctly, you can use an Emerald theme in Compiz if you change the .emerald to a ".whatever" that the Compiz themes come packed as.

Then import it in as you normally would.

---

### Post by kpolice on 2007-05-23
> **crimesaucer said:**
> If I remember correctly, you can use an Emerald theme in Compiz if you change the .emerald to a ".whatever" that the Compiz themes come packed as.

Then import it in as you normally would.


You don't remember correctly.

---

### Post by crimesaucer on 2007-05-23
Ughh...actually all you had to do for certain Emerald themes offered on Gnome-Looks.org last fall, was to change the .emerald name and replace it with the name for Compiz. I also believe it had to do with certain theme engines, but not others.

EDIT- It used to also say that on the Compiz page from back in October, plus I've read it in ubuntu forums that you used to be able to just change the .emerald part to use themes in either Beryl or Compiz. But things change a lot with Beryl and Compiz and the merger so it is different now.

---

### Post by crimesaucer on 2007-05-23
@ kpolice- Maybe you were trying to be funny...but it sounded pretty rude.

> **kpolice said:**
> You don't remember correctly.

So read this thread, post #18: [http://ubuntuforums.org/showthread.php?t=409235&highlight=compiz+emerald+themes](http://ubuntuforums.org/showthread.php?t=409235&highlight=compiz+emerald+themes)

You USED to be able to do it a last October...but Beryl and Compiz have changed a lot. I have read it in Gnome-Looks.org and Xfce-Look.org in the Bery/Emerald sections for people trying to install .emerald themes into Compiz.

After things changed in Compiz and Emerald, you had to do this: [http://forum.compiz.org/viewtopic.php?t=700&](http://forum.compiz.org/viewtopic.php?t=700&)

Now you need to do this: [http://ubuntuforums.org/showthread.php?t=423743&highlight=changing+.emerald](http://ubuntuforums.org/showthread.php?t=423743&highlight=changing+.emerald)

I might have been pretty far off of the current builds of Compiz and Compcomm and the Feisty Compiz, but back last October/November when I was deciding which one to install, Beryl or Compiz, I went with Beryl because I didn't want to have to rewrite all of the .emerald themes, and do all of the work arounds for the Beryl plug-ins that had just came out. Then Emerald went to a SVN 1.5 version before the stable 1.5, and then a SVN 2.0 version before the stable 2.0, and then a SVN 3.0, which is the one I currently use.

---

### Post by crimesaucer on 2007-05-23
edit.

---

### Post by strumluff on 2007-05-23
Guys guys, I got just the solution for you man, you can use emerald with compiz see here: [Linky]("http://ubuntuforums.org/showthread.php?t=423743")

note: it is only for compiz 0.3.6 (standard in feisty repos)

Its simply a slightly modified emerald package. Works a treat for me and I compiled it for amd64, if you run 64bit ubuntu check out the last couple of pages of the thread where I posted the amd64 debs, otherwise all you need is the first page.

As its just 3 debs you don't need to use the terminal, wayhey :P
Ofcourse if you want the emerald themes to load with every startup then you will need to include the start script that is used which kills gtk-window-decorator and then loads emerald.

---

### Post by crimesaucer on 2007-05-24
> **strumluff said:**
> Guys guys, I got just the solution for you man, you can use emerald with compiz see here: [Linky]("http://ubuntuforums.org/showthread.php?t=423743")

note: it is only for compiz 0.3.6 (standard in feisty repos)

Its simply a slightly modified emerald package. Works a treat for me and I compiled it for amd64, if you run 64bit ubuntu check out the last couple of pages of the thread where I posted the amd64 debs, otherwise all you need is the first page.

As its just 3 debs you don't need to use the terminal, wayhey :P
Ofcourse if you want the emerald themes to load with every startup then you will need to include the start script that is used which kills gtk-window-decorator and then loads emerald.

Yeah, that seems like the only way that I saw anyone making Emerald work with Compiz. I put it in my 3rd link down, with the "now you have to do this" part.

I don't even use Compiz and was only trying to help.

It used to be, that back when Compiz forked, and Compiz-Quinn soon became Beryl, that you could use either .cwgd themes or .emerald themes with either Window Manager as long as you changed that part before importing the theme.

But both projects went there own ways, and since I've been a Beryl user since November, I was unaware of how much trouble people were having with Compiz and Emerald themes until yesterday.

---

### Post by strumluff on 2007-05-25
Well now Beryl and Compiz will be merging again, give the teams a good 6 months and I believe we'll see some good improvements especially bug and compatibility related.

---

