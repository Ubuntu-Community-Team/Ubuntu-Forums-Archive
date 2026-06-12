---
title: "Installing nero"
date: 2006-05-06
forum: Desktop Environments
---

### Post by jdway on 2006-05-06
I just purchased a dvd burner and it came bundled with nero 6. Can I install this software in ubuntu or will it only work for windows?

---

### Post by GuitarHero on 2006-05-06
You could run it with [Wine]("http://www.winehq.com/")

---

### Post by aysiu on 2006-05-06
K3B is the best CD burning program I've come across.
Is there any reason you would want to use Nero, as opposed to a native Linux application?

---

### Post by jdway on 2006-05-06
The nero software comes with LightScribe so that I can burn the title of the movie onto the dvd.

---

### Post by Perfect Storm on 2006-05-06
As aysiu says. 
There's also gnomebaker, though if you insist using nero, there's nero-linux. I think it cost $20 or if you have registrastion code for your win-nero 6 or later you can use it to activate nero-linux. But beware there's no comparesion between the two.

---

### Post by jdway on 2006-05-06
OK. So I installed wine and got it configured but I am not sure how to install the nero software from the cd. Any suggestion?

---

### Post by aysiu on 2006-05-06
[QUOTE=jdway]OK. So I installed wine and got it configured but I am not sure how to install the nero software from the cd. Any suggestion?[/QUOTE] Is that you know in general how to use Wine, but there's something strange with Nero that's stumping you? If so, what errors do you encounter?

Or is that you don't know how to use Wine? If so, this may help:
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by jdway on 2006-05-06
I open the cd once I insert it into the drive and when I click on install.exe or setup.exe it gives this message:
couldn't display somedir/install.exe

Is there something I need to do in order to install from the nero disc.

---

### Post by aysiu on 2006-05-06
What happens when you right-click on the .exe? You can't open it with Wine?

---

### Post by aysiu on 2006-05-06
[QUOTE=jdway]The nero software comes with LightScribe so that I can burn the title of the movie onto the dvd.[/QUOTE] Have you looked into any of the CD-label-making programs available in the repositories?

cd-circleprint
kcdlabel

---

### Post by jdway on 2006-05-06
I figured out the problem. I had to configure my system to open .exe files with wine. And no other cd program has lightscribe.

---

### Post by jdway on 2006-05-06
Alright so now that I have nero installed and running, whenever I try to run it the initial screen shows but then it freezes. The terminal then spits out this error message. 

err:syslevel:_EnterSysLevel (0x7ee5ca60, level 2): Holding 0x7f8a4c80, level 3. Expect deadlock!
err:syslevel:_CheckNotSysLevel Holding lock 0x7f8a4c80 level 3
wine: Unhandled exception 0x80000003 at address 0x7fce2ef0 (thread 0009), starting debugger...

---

