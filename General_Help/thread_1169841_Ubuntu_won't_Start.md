---
title: "Ubuntu won't Start"
date: 2009-05-25
forum: General Help
---

### Post by Sparky-da on 2009-05-25
hi guys..
I'm new here.
and I hope I'm posting my problem in the right section.."if not"..my apologiez in advance.
 
 
my problem is:
 
I'm pretty new to [COLOR=darkorange]Ubuntu[/COLOR]...I'm using [COLOR=darkorange]ubuntu[/COLOR]-9.04-desktop-i386 running on computer desktop H.P
 
I have been trying to install the moniter driver in [COLOR=darkorange]Ubuntu[/COLOR]..I couldn't..I got bored and I switched off the P.C.
 
and now I'm trying to boot [COLOR=darkorange]Ubuntu[/COLOR]..but invain.
I get the first load.
then comes a black screen filled and mixed with white dots and sometimes green and it completley HANGS!
 
I have attached a picture of the screen.

---

### Post by whoop on 2009-05-25
Please post information about your monitor and videocard.

---

### Post by s.fox on 2009-05-25
Hi and welcome to the forum,

Have you tried safe mode?


First you need to enter Grub menu by pushing ESC when your PC boots. There you can select the safe mode.

-Ash R

---

### Post by Sparky-da on 2009-05-25
> **whoop said:**
> Please post information about your monitor and videocard.
 
hi whoop.
 
it's
 
Intel(R) 82865g Graphics Controller
Intel Corporation
DAC Type: Internal
1280 x 960 (32 bit) (60Hz)
 
moniter : Dell D1025HE
 
Main Driver : ialmrnt5.dll Version:6.14.0010.4396
 
is this what have you asked for?

---

### Post by Sparky-da on 2009-05-25
> **Ash R said:**
> Hi and welcome to the forum,
 
Have you tried safe mode?
 
 
First you need to enter Grub menu by pushing ESC when your PC boots. There you can select the safe mode.
 
-Ash R
 
Hello Ash R..Thanks for being concerned and dropping by.
 
Do you mean Recovery mode? "If yeah"
I tried it and I tried to Auto repair graphic problems.
no good!
 
I also tried writing df -h and startx in the Grub command prompt.
 
It gave me Error 27: Unrecognized Command.
 
 
 
any other suggestions?

---

### Post by Sparky-da on 2009-05-26
I got over this by reinstalling[COLOR=DarkOrange] Ubuntu[/COLOR] from [COLOR=Red]Wubi[/COLOR]..
but I'm having another serious problem still..
I'll post a new thread..
because others who are having same problem can get through it.
thank you guys again.

---

### Post by KhurramM on 2009-05-26
Just to avoid some problems, **always install root and swap on primary partitions of your hard**.

Hope u like and stick to linux.

---

### Post by Sparky-da on 2009-05-26
> **KhurramM said:**
> Just to avoid some problems, **always install root and swap on primary partitions of your hard**.

Hope u like and stick to linux.

thanks man..I really appreciate that..and yeah I'll try to do that.

---

