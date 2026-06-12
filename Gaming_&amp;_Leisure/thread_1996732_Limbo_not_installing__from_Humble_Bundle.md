---
title: "Limbo not installing  from Humble Bundle"
date: 2012-06-04
forum: Gaming &amp; Leisure
---

### Post by Reboot.Revival on 2012-06-04
I bought the Humble Bundle package and I can't get Limbo to install.  I tried the tar.gz fisrt but got errors in the terminal so I tried the .deb package.  The ubuntu software center popped up and said "cannot install 'python:i386'".  Sword and Sworcery installed through .deb package and so did the other games through various ways.  

Any help?

---

### Post by thatguruguy on 2012-06-04
> **Reboot.Revival said:**
> I bought the Humble Bundle package and I can't get Limbo to install.  I tried the tar.gz fisrt but got errors in the terminal so I tried the .deb package.  The ubuntu software center popped up and said "cannot install 'python:i386'".  Sword and Sworcery installed through .deb package and so did the other games through various ways.  

Any help?

You might try the "Download for Ubuntu" link on the Humble Bundle page.

---

### Post by Reboot.Revival on 2012-06-04
after I click buy(on all of them) it tells me that it cannot load the page.  I cannot get passed that. I have all the games installed except limbo and they all have problems.  Bastion is black(minus the pointer) with sound; Amnesia wont get past the first few screens, crashes at loading;  SuperBrothers and psychonauts wont start at all.

---

### Post by thatguruguy on 2012-06-04
> **Reboot.Revival said:**
> after I click buy(on all of them) it tells me that it cannot load the page.  I cannot get passed that. I have all the games installed except limbo and they all have problems.  Bastion is black(minus the pointer) with sound; Amnesia wont get past the first few screens, crashes at loading;  SuperBrothers and psychonauts wont start at all.

Which version of Ubuntu are you running? What kind of hardware do you have?

---

### Post by Reboot.Revival on 2012-06-04
fixed Bastion

I am on Ubuntu 12.04.  ASRock ext3 gen3, i5 at 4.4ghz, 8gb ram, temporarily without graphics card, just running the onboard z68 chipset.  which should be fine.

---

### Post by Reboot.Revival on 2012-06-04
I decided to just install steam and use the product key. So I am only gonna use Bastion on Ubuntu and the other 4 will go on Steam.   Not worth the hassle.

---

### Post by thatguruguy on 2012-06-04
> **Reboot.Revival said:**
> fixed Bastion

I am on Ubuntu 12.04.  ASRock ext3 gen3, i5 at 4.4ghz, 8gb ram, temporarily without graphics card, just running the onboard z68 chipset.  which should be fine.

Actually, I'd say that the lack of a graphics card is your primary problem.

---

### Post by Carborundum on 2012-06-04
> **thatguruguy said:**
> Actually, I'd say that the lack of a graphics card is your primary problem.
It's not something that would cause the problems the OP is having though. And the Intel HD4000 integrated in that CPU is easily powerful enough to run all the games from the HIB V.

---

### Post by Perfect Storm on 2012-06-04
It's not the card that's the problem, more likely poor intel driver problem in linux.

---

### Post by Carborundum on 2012-06-04
> **Artificial Intelligence said:**
> It's not the card that's the problem, more likely poor intel driver problem in linux.
Except that

1. Support for Ivy Bridge graphics is actually pretty good.

and

2. Bad drivers wouldn't cause problems during installation.

---

### Post by Perfect Storm on 2012-06-04
Pretty good compared to what? For previous intel driver releases; Yes. Compare to Windows intel driver; No. Still it still recommendable to use ATI or Nvidia for gaming.

I was referring to if the game got installed and running.

---

### Post by thatguruguy on 2012-06-04
> **Carborundum said:**
> Except that

1. Support for Ivy Bridge graphics is actually pretty good.

and

2. Bad drivers wouldn't cause problems during installation.

He said in a later post that he had all games installed, and was describing graphics problems.  Here's the quote:
> **Reboot.Revival said:**
> after I click buy(on all of them) it  tells me that it cannot load the page.  I cannot get passed that. I have  all the games installed except limbo and they all have problems.   Bastion is black(minus the pointer) with sound; Amnesia wont get past  the first few screens, crashes at loading;  SuperBrothers and  psychonauts wont start at all.

---

### Post by Carborundum on 2012-06-04
> **Artificial Intelligence said:**
> Pretty good compared to what?
Compared to open source AMD and NVIDIA drivers.

> **thatguruguy said:**
> He said in a later post that he had all  games installed, and was describing graphics problems.
Even so, his GPU should be able to handle all of those games without issue. The problem isn't the GPU or the drivers, it's the games themselves.

---

### Post by Perfect Storm on 2012-06-04
> Compared to open source AMD and NVIDIA drivers.

It's irrelevant. A gamer with AMD/ATI or Nvidia card will diffidently go with restricted drivers.

---

### Post by Carborundum on 2012-06-04
> **Artificial Intelligence said:**
> It's irrelevant. A gamer with AMD/ATI or Nvidia card will diffidently go with restricted drivers.
What's irrelevant is this entire discussion; his GPU and its drivers are *good enough* to handle the relevant games. The problem lies somewhere else.

---

### Post by Perfect Storm on 2012-06-04
> **Carborundum said:**
> What's irrelevant is this entire discussion; his GPU and its drivers are *good enough* to handle the relevant games. The problem lies somewhere else.

Be my guest to find his non-driver issue for these games.

---

### Post by Carborundum on 2012-06-04
> **Artificial Intelligence said:**
> Be my guest to find his non-driver issue for these games.
I never said it isn't a driver issue. Doesn't have to be a *display* driver issue though. Limbo and S&S both have known audio issues. In Limbo it's related to Wine, in S&S it's a missing library on 64-bit systems.

It could of course be related to the display driver; we certainly don't have enough info to rule that out. My point is that the lack of a dedicated GPU isn't necessarily the most likely cause of the problems.

---

### Post by thatguruguy on 2012-06-04
> **Carborundum said:**
> I never said it isn't a driver issue. Doesn't have to be a *display* driver issue though. Limbo and S&S both have known audio issues. In Limbo it's related to Wine, in S&S it's a missing library on 64-bit systems.

It could of course be related to the display driver; we certainly don't have enough info to rule that out. My point is that the lack of a dedicated GPU isn't necessarily the most likely cause of the problems.

I installed S&S today from the USC, and it works just fine on my MthTV box running Mythbuntu 12.04.  I've noticed that sound won't work in Limbo if I kill the X server (Alt+print screen +k) and log right back in (that's a lot faster than a reboot).

However, the problems the OP reported still sound like video card-related problems.

---

### Post by Carborundum on 2012-06-04
> **thatguruguy said:**
> However, the problems the OP reported still sound like video card-related problems.
I'm curious as to how you manage to deduce that given the information available.

---

### Post by thatguruguy on 2012-06-04
> **Carborundum said:**
> I'm curious as to how you manage to deduce that given the information available.

The fact that Bastion wouldn't display anything, and the fact that Amnesia is known to work poorly on integrated graphics (e.g., it works fine on my Mythbox with an NVidia card, won't start on my laptop with integrated graphics).

But, mostly, because they sound like graphics card problems.

---

### Post by Carborundum on 2012-06-04
> **thatguruguy said:**
> The fact that Bastion wouldn't display anything, and the fact that Amnesia is known to work poorly on integrated graphics (e.g., it works fine on my Mythbox with an NVidia card, won't start on my laptop with integrated graphics).

But, mostly, because they sound like graphics card problems.
I will give you Bastion, which the OP has apparently managed to fix. I seem to recall reading something about a missing texture for Intel cards in relation to that game. Edit: Indeed, [this]("http://ubuntuforums.org/showpost.php?p=11990023&postcount=69") was most likely the problem.

Amnesia is known to not work at all with integrated graphics older than Sandy Bridge; as Ivy Bridge most definitely isn't that, I wouldn't immediately jump to the conclusion that the GPU is at fault. 

Other than that, the only information provided is "won't start at all", which obviously isn't enough to say anything about what the problem might be.

---

### Post by thatguruguy on 2012-06-04
> **Carborundum said:**
> 
Amnesia is known to not work at all with integrated graphics older than Sandy Bridge; as Ivy Bridge most definitely isn't that, I wouldn't immediately jump to the conclusion that the GPU is at fault. 

First of all, the intel drivers for Linux are not on par with the intel drivers for Windows. 

Secondly, I haven't seen anything that indicates that Amnesia runs on any integrated graphics hardware at all for Linux, and a brief google search didn't reveal anything to me. If you have something you could point me to, I'd gladly re-evaluate my position.

Thirdly, all of these games are graphics-intensive. It still seems the most likely culprit, and it's the easiest one to rule out. A $50 NVidia card would be able to give us an answer.

---

### Post by Lord Burghley on 2012-06-04
> **Reboot.Revival said:**
> after I click buy(on all of them) it tells me that it cannot load the page.  I cannot get passed that. I have all the games installed except limbo and they all have problems.  Bastion is black(minus the pointer) with sound; Amnesia wont get past the first few screens, crashes at loading;  SuperBrothers and psychonauts wont start at all.

I believe I might have a partial solution. I just ran "sudo apt-get install libpulse0:i386" and SuperBrothers (which wouldn't run at all after install, as mentioned in the OP's second post), started up just fine.

I got the idea from [this Ubuntu Forums post.]("http://ubuntuforums.org/showthread.php?t=1993267")

Anyway, I hope this helps at least a little. :)

---

