---
title: "Did dellfand ruin my vostro 1310?"
date: 2008-09-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Nathaniel22 on 2008-09-01
Hello people,

I've installed Ubuntu 2 days ago and wanted to try dellfand for fan-regulation ([http://dellfand.dinglisch.net/](http://dellfand.dinglisch.net/)). But the first time I started the tool, it turn my fan on maximum power and froze the vostro. I had to shut it down by holding the power button. Now there is a serious problem: the fan doesn't turn off anymore, it's running nonstop. 

I though it would be a good idea to formate + reinstall the system to lose all software that is manipulating the fan. But it didn't help. The fan is still running, no matter how warm the CPU is.

I've seen that dellfand doesn't work on vostro 1510, so I was expecting a failure on my 1310 too. But I didn't expect such a thing. How is that possible? I mean I got rid of all Software but something is still taking over the fan-control. Is it something in the Bios? Didn't thought dellfand is manipulating the Bios... :(

Is there anything I can do to fix this issue?

---

### Post by Twitster on 2008-09-01
Hmm, that's interesting. I'd recommend calling up Dell. If you can, try and get away with this without saying it was the software that you ran on your computer. As for a solution, I can't help you there, but calling up is probably a good bet if it's a major hardware issue.
Is there any other software you can find that will change the fan speed? It could be that somewhere in your motherboard that setting from dellfand has remained? 
Note that they are very insistant with their "Do not use this software until you have read the disclaimer. "
Hmm, try looking at the source code. If at all possible (and you're a very good programmer) try to half the setting that the software defaults to, and then compile? Could be worth a shot. 
Let me know how it goes!

Edit: Oh and, on the link you supplied, it says that the software takes away the control from the BIOS. Try reinstalling your BIOS. [http://www.computing.net/answers/windows-me/how-do-i-update-my-bios-/45766.html](http://www.computing.net/answers/windows-me/how-do-i-update-my-bios-/45766.html)

---

### Post by Nathaniel22 on 2008-09-01
I think I will try to flash a new BIOS. Too bad I have to install Windows for that again :/

There seems to be now way to flash the Bios of a Vostro with Ubuntu.

---

### Post by japhyr on 2008-09-02
I've been looking at upgrading my BIOS to see if it helps with some screen resolution problems, but haven't taken the plunge yet.  Anyway, there is a site that offers possibilities for upgrading BIOS on Dells from within ubuntu:

[http://direct2dell.com/one2one/archive/2007/12/05/37446.aspx]("http://direct2dell.com/one2one/archive/2007/12/05/37446.aspx")

Might poke around and see if anything there helps.  If you do reinstall/ upgrade BIOS from ubuntu, I'd be curious to here how it goes.  (Nothing like experimenting with someone else's machine!)

---

### Post by Nathaniel22 on 2008-09-02
Phew guys, when I started the Vostro today the problem was gone. The fan seems to work properly again and I didn't do anything that could've changed it. Guess I got lucky.

---

