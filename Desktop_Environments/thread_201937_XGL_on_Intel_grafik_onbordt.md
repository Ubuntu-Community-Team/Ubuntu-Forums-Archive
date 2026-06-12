---
title: "XGL on Intel grafik onbordt"
date: 2006-06-22
forum: Desktop Environments
---

### Post by NeoNmaNDK on 2006-06-22
Hallo all.

i have a IBM laptop R50e model whit onbordt grafik cart ist 64mb share ram and i will get XGL on it bot can i doe it?

if i can how doe i?

if i will get my grafik cardt name how can i type to my console to get this info?

i hob you can help me pepole.

---

### Post by johnc4510 on 2006-06-22
1.I don't think that is a powerful enough card to run XGL
2.
3.type in:lspci
The line that shows VGA controller is your video card

---

### Post by Ubuntuud on 2006-06-22
You write English as if you're Dutch :). But I can understand. There isn't some command to give you the answer. Could you be a bit more specific on what model graphics card you got?

I wouldn't expect it to run as a nvidia though...

---

### Post by NeoNmaNDK on 2006-06-22
[QUOTE=Ubuntuud]You write English as if you're Dutch :). But I can understand. There isn't some command to give you the answer. Could you be a bit more specific on what model graphics card you got?

I wouldn't expect it to run as a nvidia though...[/QUOTE]

82852/855GM interen driver from Intel

i im not duech bot danish ;)

---

### Post by thasheep on 2006-06-22
I don't think you'll get XGL working very well but aiglx should be ok. Both support compiz (the good graphics). See this thread [http://www.ubuntuforums.org/showthread.php?t=145068](http://www.ubuntuforums.org/showthread.php?t=145068)

---

### Post by splitsch on 2006-06-23
Hello!
chek this out:
[http://doc.ubuntu-fr.org/applications/aiglx](http://doc.ubuntu-fr.org/applications/aiglx)
I have a r50e too, but I couldn't make it work anyway, even aiglx...but I didn't search a lot !

Bye

---

### Post by hartl_vienna on 2006-06-23
I also have a Thinkpad R50e. I installed AIGLX with the compiz-quinn packages.  It runs really good. :D 

You can use this manual: [http://www.ubuntuforums.org/showthread.php?t=145068]("http://www.ubuntuforums.org/showthread.php?t=145068")

---

### Post by morphir on 2006-10-04
> **hartl_vienna said:**
> I also have a Thinkpad R50e. I installed AIGLX with the compiz-quinn packages.  It runs really good. :D 

You can use this manual: [http://www.ubuntuforums.org/showthread.php?t=145068]("http://www.ubuntuforums.org/showthread.php?t=145068")

you got AIGLX to work on r50e (with i855GM) running ubuntu dapper ???

How?? Jez, could you post your **entire xorg.conf** in this thread? please!

I have been trying and _struggling_ for days getting AIGLX to work(so I can use Beryl/Compiz)](*,) 

hartl_vienna: I beg you man;)

---

