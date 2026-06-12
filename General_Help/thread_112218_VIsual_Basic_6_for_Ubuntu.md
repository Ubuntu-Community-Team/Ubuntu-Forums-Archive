---
title: "VIsual Basic 6 for Ubuntu"
date: 2006-01-03
forum: General Help
---

### Post by Strike&gt;&gt; on 2006-01-03
I was wondering if it's possible to install VB6 on ubuntu. VB 6 because the programming course that i take in high school uses it.  If not, are there any solutions to get a free copy of a Windows Emulator legally.

Thank You.

---

### Post by ekravche on 2006-01-03
Not sure whether there is VB 6 for ubuntu, but what you can do is install a machine emulator such as VMWare, then make a windows image in VMWare by installing Windows in VMWare, and the install VB6 in your newly created vmware image.

---

### Post by magnusbb on 2006-01-04
VB6 should be possible to run in WINE. You can download the latest WINE from [www.winehq.com](www.winehq.com) 

I've had success with earlier versions of VB.

---

### Post by mip on 2006-01-04
Not really answering your question but you may find this interesting [http://gambas.sourceforge.net/](http://gambas.sourceforge.net/).

---

### Post by kakashi on 2006-01-04
thanks for telling about gambas. i am currently installing it. i have some questions
1. is it good
2. does it produce programs compatible to linux. 
i always missed the ease of gui making of vb that was not in linux.

to the first poster. 
1. vb is too advanced to run under wine. some feature or the other will be missing. 
2. qemu, vmware are good alteratives but vmware is costly and qemu is slower (both are muh slower than native) and you need a windows licence for it.

---

### Post by sciurus on 2006-01-04
[QUOTE=kakashi]
to the first poster. 
1. vb is too advanced to run under wine. some feature or the other will be missing.[/QUOTE]

This [seems]("http://appdb.winehq.org/appview.php?appId=94") to be largely untrue.

---

### Post by briancurtin on 2006-01-04
honestly, if you are learning VB6 in a class, just do it in windows. its not worth doing all of this crap just to have it go wrong one day when you really need it. if you dont know how to set it up on linux in the first place, you arent going to know how to fix it when shit hits the fan and you have a project due in 5 hours. sorry if that sounds condescending, but im just speaking the truth and id hate to see someone get burned by some stupid emulator

---

### Post by PlatinumPlus on 2006-01-05
[QUOTE=kakashi]thanks for telling about gambas. i am currently installing it. i have some questions
1. is it good
2. does it produce programs compatible to linux. 
i always missed the ease of gui making of vb that was not in linux.

[/QUOTE]
Gambas is quite good GUI is all there but it has a few components compared to VB. I used it with MySQL but the Result(Recordset) is readonly (had to modify my apps to use INSERT and UPDATE etc executed from the connection. The GUI is candy for my eyes but the syntax is quite similar.

---

### Post by Strike&gt;&gt; on 2006-01-05
True, i don't want to go through the trouble of reprogramming them if i ever screw up something , so i guess i would have to keep windows, sigh Bill Gates. But i think i will do it for the fun part anyways.:D 

and if i ever want to program in linux i will just use the right software for it. thanx for your help guys, those emulator sound good for other apps though.

---

