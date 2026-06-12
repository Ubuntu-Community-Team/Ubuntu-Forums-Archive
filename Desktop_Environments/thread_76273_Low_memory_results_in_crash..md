---
title: "Low memory results in crash."
date: 2005-10-14
forum: Desktop Environments
---

### Post by NewWithoutClue on 2005-10-14
Someone either link me to a place where i can learn about making KDE/Linux use less memory, or share their thoughts on the subject.
Five times my box crashed when executing another application ( and no it isnt the same app every time ).

Currently running applications ( GUI ):
1) Konqueror.
2) Gaim.
3) xmms.

Current memory usage:
( Information obtained via KDE System Guard )
122,888 used, 3,132 free.

And i know more processes exist.
Tell me what i dont need?
Explain tricks to lower memory usage?
Post a link?
ignore this and leave?
Your choice :) 

P.S Wether you choose to help me or not, i will not give up on Linux and/or Kubuntu.

Thanks,
Paul.

---

### Post by alexcg on 2005-10-15
I'm having the same difficulties. AFAICT this is really two problems. One is that something on the system is eating all the memory, and I'm still trying to find out what. The second is that the 2.6.12 (686) kernel is a bit too trigger happy about killing processes that take up memory.

Switching to a different kernel can help fix the second problem, but I'm still searching for a solution to the first

---

### Post by PaganHippie on 2005-10-15
What are your system stats? How much physical memory do you have? I believe (iirc) that 256 MB is considered the minimum for (K)Ubuntu; if you're running 128 MB (as your post suggests), you can expect problems. 

RAM is relatively cheap. Upgrade if you at all can. More will never hurt you. A large(r) swap space won't do you any harm, either.

---

### Post by NewWithoutClue on 2005-10-15
Swap? over 500 mb's.
I know that i should have more RAM, but that doesnt answer my question about what i could do about it ( software wise ).
thanks,
Paul.

---

### Post by GeneralZod on 2005-10-15
This shouldn't be happening, even on 128MB :)

How much swap is in use at the moment of crashing?

---

### Post by NewWithoutClue on 2005-10-15
The most I have ever seen in use ( Swap ) would be about 50 mb's ( give or take 10 mb's ) . Which leeds me to another question.. Is there a way to make Linux/Kubuntu use more Swap and less RAM? When it crashes I'm forced to manually reboot the box; there is no hope of recovery, depite what I thought. Thanks, Paul.


Edit: I have just found the command "sysctl -w vm.swappiness=x" from 
[http://wiki.linuxquestions.org/wiki/FAQ_-_Linux_problems]("http://wiki.linuxquestions.org/wiki/FAQ_-_Linux_problems")
If you think you ahve the same problem as i, click that click and read a little. ( remember i'm still new to. ). I set it to 90, don't know of the affects yet, but will let you know. something tells me this wont be an answer to my problem but it's a start.

---

### Post by manishsingh4u on 2006-03-30
Well,
      I don't think it's all because of 128 MB RAM only.
My PC is -
1) P-III, i686 copermine processor. 
2) Intel 82810E Vesta Motherboard
2) Hyundai 128 MB SD RAM (133)
3) 4 MB onboard VGA display.

I have Kubuntu 5.10 over this PC and it works just fine.
Anyway, you can minimize the RAM usage by using 

1) Simple color schemes, window decorations, styles effects under KMenu -> System Settings -> Appearance.
2) Disabling services that you don't really use etc. 

That's what I am trying to do to my installation as it runs a little slower than SuSE 9.1 (my favourite) on the same hardware.

---

