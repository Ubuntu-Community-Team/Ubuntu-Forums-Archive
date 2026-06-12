---
title: "Language problem"
date: 2005-08-28
forum: Desktop Environments
---

### Post by cazz on 2005-08-28
When I start Ubuntu today I have discovery that is now Swedish/English in menu and that.
Yesterday it where the menu Swedish

Very strange so I think I maybe have to download some language pack from Synaptic.

When I mark "language-pack-sv" it say
*Depends: language-pack-sv-base but it is not going to be installed * 

When I try "language-pack-sv-base" it say
[I]Depends: locales but it is not going to be installed
Depends: language-pack-sv but it is not going to be installed [/I] 

Very very strange

I now that yesterday I work with Winetool and did have some problem that I think is something about the language so I have change something.

I every try install "locales localeconf" with apt-get but then Ubuntu say
Depends: glibc-2.3.2.ds1-20ubuntu14

I maybe have to old glibc?
I have mark in Synaptic glibc but I think that is only 2.2

What shall I do??

---

### Post by weekend warrior on 2005-08-31
Sounds strange, maybe try to remove the Swedish packs completely and then everything will be in default English. Then reinstall the Swedish packs. See if that works.

---

### Post by Vinze on 2005-09-23
[QUOTE=cazz]When I start Ubuntu today I have discovery that is now Swedish/English in menu and that.
Yesterday it where the menu Swedish

Very strange so I think I maybe have to download some language pack from Synaptic.

When I mark "language-pack-sv" it say
*Depends: language-pack-sv-base but it is not going to be installed * 

When I try "language-pack-sv-base" it say
[I]Depends: locales but it is not going to be installed
Depends: language-pack-sv but it is not going to be installed [/I] 

Very very strange

I now that yesterday I work with Winetool and did have some problem that I think is something about the language so I have change something.

I every try install "locales localeconf" with apt-get but then Ubuntu say
Depends: glibc-2.3.2.ds1-20ubuntu14

I maybe have to old glibc?
I have mark in Synaptic glibc but I think that is only 2.2

What shall I do??[/QUOTE]
 I have the same problem, with the only difference that I have this with en_GB. When I login, it says "language en_GB.UTF-8 is not found, using system default, or something like that. When I try to install the English language pack, and, as you said, it says it depends on language pack English base which is not going to be installed. That then depends on locales which is not going to be installed, and that one depends on glibc-2.3.2.ds1-20ubuntu14. When I search for glibc it doesn't find anything!

---

### Post by cazz on 2005-09-23
I reinstall the system so now it work again

---

### Post by Vinze on 2005-09-23
[QUOTE=cazz]I reinstall the system so now it work again[/QUOTE]
 Hmm... Well, you know, I don't really feel like reinstalling everything now I got it configured :P . Though now you say it, I got this problem after I had a broken package of libc6 on my system, which required a lot of packages including ubuntu-desktop to be removed, which I accidentally did (don't ask me how). Then I could just reinstall it, one way or another, but I had a few problems, such as this.

---

### Post by cazz on 2005-09-23
mm yes but I have to reinstall. 
Not for that problem. 
I did make a misstake so I have to resinstall my Ubuntu    :-?  
I hope you find a solution for that problem.

---

### Post by Vinze on 2005-09-23
[QUOTE=cazz]mm yes but I have to reinstall. 
Not for that problem. 
I did make a misstake so I have to resinstall my Ubuntu    :-?  
I hope you find a solution for that problem.[/QUOTE]
 Yeah, I hope so too :D Thanks. If there's anyone that can help?

---

