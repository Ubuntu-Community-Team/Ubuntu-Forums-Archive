---
title: "Lyx reconfigure fails, how to get beamer going?"
date: 2008-10-21
forum: Education &amp; Science
---

### Post by keenPenguin on 2008-10-21
Hi, 

I would like to use Lyx with the beamer package, so I tried to find how to get things going. The only helpful thread seems to be [http://ubuntuforums.org/showthread.php?t=393565](http://ubuntuforums.org/showthread.php?t=393565) , where it is suggested to install the latex-beamer package and then to Tools->reconfigure the Lyx software. 

I'm using Ubuntu 8.04, and I installed Lyx 1.5.3 from the standard repositories. I am wondering why latex-beamer does not appear there at all. Also, when I clicked on reconfigure (just to try it) Lyx replied:

The system reconfiguration has failed.
Default textclass is used but LyX may not be able to work properly.
Please reconfigure again if needed.

What might be wrong here?

kP

---

### Post by parktownprawn on 2008-10-22
Did you try install latex-beamer? What happens if you type

```
sudo apt-get install latex-beamer
```?

---

### Post by keenPenguin on 2008-10-22
Thank you parktownprawn,

you were right, after installing the beamer package and reconfiguring Lyx there are no more complaints!

To try beamer, I made new file from the "beamer-conference-ornate-20min.lyx" template. Unfortunately, Lyx refused showing me the DVI and gave me the following error output:

[[img]http://www.abload.de/thumb/lyxfonterrorszwn.png[/img]](http://www.abload.de/image.php?img=lyxfonterrorszwn.png)

Maybe you have an idea on what's wrong here?

kP

---

### Post by parktownprawn on 2008-10-22
looks like you are missing fonts - if you are using texlive try 
```
sudo apt-get install texlive-fonts-extra  texlive-fonts-recommended  
```
and then reconfigure lyx

---

### Post by keenPenguin on 2008-10-22
Thank you, that did the job! I have also found an entry in the German ubuntuusers Wiki ([http://wiki.ubuntuusers.de/Lyx](http://wiki.ubuntuusers.de/Lyx)) which recommends to do the very same thing! For me, it's kind of crucial to get Lyx working, so thank you very much parktownprawn!

kP

---

