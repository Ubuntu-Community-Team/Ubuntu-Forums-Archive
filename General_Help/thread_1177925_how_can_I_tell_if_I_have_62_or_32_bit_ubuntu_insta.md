---
title: "how can I tell if I have 62 or 32 bit ubuntu installed ?"
date: 2009-06-03
forum: General Help
---

### Post by rreyes1316 on 2009-06-03
I have ubuntu installed from the iso I downloaded but also decided to order a free disk. Well . . .I installed the version mailed to me on a separate disk to experiment and as i was waiting for some apps to install I was looking at the disk sleeve. It does not say it is 64bit. Is there a command to find this our? lsb_release does not indicate this info.

---

### Post by PGScooter on 2009-06-03
Hi rreyes,

Try:

```

uname -m

```

---

### Post by QIII on 2009-06-03
In the terminal, type

file /sbin/init

If you get back a string that contains "ELF 64-bit" or similar, you have 64 bit installed.

---

### Post by Yingy on 2009-06-03
In terminal type in uname -m.  If you have 32 bit installed it will come up as i686.  If you have 64 bit installed it should read something like x86_64.

---

### Post by QIII on 2009-06-03
uname -m returns hardware information, I believe.

-m is the switch for machine.

---

### Post by rreyes1316 on 2009-06-03
DARN!!!! I received the 32bit. I swear I ordered the 64. Thats cool  . . . whatever. Still love it.

---

### Post by H2SO_four on 2009-06-03
Hey, i ran that -m thingy and i am only running 62 bit.  where is the other 2 bits?   jk :)

---

### Post by QIII on 2009-06-03
Which command did you use?

---

### Post by rreyes1316 on 2009-06-03
not funny, man! You teasing me? Hope you get a dead pixil--grrrrr:evil:

---

### Post by Muscovy on 2009-06-03
> **rreyes1316 said:**
> DARN!!!! I received the 32bit. I swear I ordered the 64. Thats cool  . . . whatever. Still love it.
  As far as I'm aware, 64 bit is pretty specialized and most computers can't or needn't run it.

---

### Post by rreyes1316 on 2009-06-03
I just went to order another free cd and I noticed it does not ask whether i want 32 or 64. My Bad. Since we are on the topic, whats the difference with the server and desktop? is it the same gnome environment?

---

### Post by rreyes1316 on 2009-06-03
> As far as I'm aware, 64 bit is pretty specialized and most computers can't or needn't run it.

I have been using Ubuntu now for about 2 months now. I am now a convert. Gave windows the boot--almost. Are you saying there is no real big difference between the two? Is this like dual vs single core? Since I have had a dual core I have not noticed much of a change. And now there are talks of 12 core! What the heck, I can barely use my second core.

---

### Post by QIII on 2009-06-03
Actually, the page does give you the option of 32 or 64 bit.

The selection is counterintuitively located below the "Begin Download" button.

It is 32 bit by default, so that is probably what you got.

Again:  i686 and x86-64 are microarchitecture terms referring to processor characteristics.

Could you go to System -> Administration -> System Monitor and click the System Tab?  You should get the type of processor(s) you have.

---

### Post by egalvan on 2009-06-03
> **rreyes1316 said:**
>  whats the difference with the server and desktop? is it the same gnome environment?

The server edition does not have a desktop environmemnt (GUI)...

strictly command line...


but you CAN install a desktop, if you want.

This is one way of getting 32bit GUI systems to recognize more than 4G of RAM...

---

### Post by michy99 on 2009-06-03
> **H2SO_four said:**
> Hey, i ran that -m thingy and i am only running 62 bit.  where is the other 2 bits?   jk :)

I used them for a shave and a haircut.

---

### Post by egalvan on 2009-06-03
> **Muscovy said:**
> As far as I'm aware, 64 bit is pretty specialized and most computers can't or needn't run it.

The only thing "specialized" about 64bit software is that it needs 64bit hardware to run...

And since almost all hardware is now 64bit, that puts it into the "everyday" class.

As for "needing" it, well, that's a personal issue.

Most folks don't even "need" 32bit ;)

---

### Post by rreyes1316 on 2009-06-03
I know what type of proc I have. It is the last upgradable proc for my motherboard and I wanted to get the most out of it before a major overhaul. That is why I wanted the 64bit. But now i get the impression it does not matter with linux--is that correct?

BTW, I have an AMD Athlon 64 FX-60 dual core 2.60ghz toledo core socket 939. How does linux handle overclocking?

---

### Post by QIII on 2009-06-03
> **egalvan said:**
> 
As for "needing" it, well, that's a personal issue.
 ;)

Long ago, Ford Pinto was about all one really "needed".  But it sure was fun driving a DeTomaso Pantera . . .

---

### Post by Soul-Sing on 2009-06-03
> **Muscovy said:**
> As far as I'm aware, 64 bit is pretty specialized  and most computers can't or needn't run it.

If you have a 64 bit system, there is nothing specialized or special using Ubuntu 64 bit.
- sun java and
- flash non-free are available
(for instance)

---

### Post by QIII on 2009-06-03
rreyes --

Your machine's architecture is 64 bit.  Most dual cores are, but yours specifies it.  It *could* run 64 bit Ubuntu, if you had a mind to using it.

If you're not interesting in doing another install, you probably won't notice a difference.

---

### Post by kuja on 2009-06-04
> **rreyes1316 said:**
> I know what type of proc I have. It is the last upgradable proc for my motherboard and I wanted to get the most out of it before a major overhaul. That is why I wanted the 64bit. But now i get the impression it does not matter with linux--is that correct?

BTW, I have an AMD Athlon 64 FX-60 dual core 2.60ghz toledo core socket 939. How does linux handle overclocking?

Hey, cool,  I had that processor in my last rig :) 

The motherboard is what handles the overclocking features really, no software tuning needed. You'll probably want to install lm-sensors to keep an eye on your temps,but that's about it. Oh, do be careful overclocking that proc, it runs really, really hot.

---

### Post by jdunn on 2009-06-04
> **rreyes1316 said:**
> DARN!!!! I received the 32bit. I swear I ordered the 64. Thats cool  . . . whatever. Still love it.

Meh...If your computer has less than 4GB of RAM, 64-bit doesn't get you much.

---

### Post by rreyes1316 on 2009-06-04
That was the last upgrade i thought about for the mobo I have. Not sure if i should take the plunge or just milk what I have before a complete overhaul.

As for the desktop vs server edition, why would I need to install the server cd to install an app? Here is what happened: I installed decryptor using wine. I have the 64 bit ubuntu 9.04 desktop and and I was prompted for the serve cd--fortunately I had it. i thought this was strange and wondered why it just did not install what it needed from the net. Any ideas? Anything else i should install desktop ver 9.04?

---

