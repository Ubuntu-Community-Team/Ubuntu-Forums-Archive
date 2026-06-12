---
title: "Ati Graph Errorrrrrr!!!!"
date: 2007-06-05
forum: Gaming &amp; Leisure
---

### Post by mu:te on 2007-06-05
I'VE HAD ENOUGH!

For the last days I've been trying to set up my graph card driver properly so I can play the worlds famous World of Warcraft..

Little did I know when I installed Ubuntu for the first time that its a damn crap..

I've spend over all more than 50 hours trying to install any driver at all but it seems to all that it is impossible!!

I've followed every guide step for step, did EVERYTHING that I was suppose to do but no matter what, IT DOESN'T FREAKING WOOOOOOOOOOOOOOOOOOOORK!!!!!!!!!!!!!!!!!!!

The latest guide I "tried" to follow was this one

[http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)

Seems nice but still.. IT DOESN'T WORK!

I also tried [http://gentoo-wiki.com/HOWTO_ATI_Drivers](http://gentoo-wiki.com/HOWTO_ATI_Drivers) - Doesn't work..

So I ask for the laaaaast time before I format my computer back to Windows - Is there really ANYTHING/ANY guide that I could follow that is going to WORK! ?

--

Useful infos:
ATi Radeon x300 64MB!

glxinfo |grep direct
Xlib: extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

---

### Post by hikaricore on 2007-06-06
bye

---

### Post by mu:te on 2007-06-07
> **hikaricore said:**
> bye

What an nice way to enlarge the Linux community.

---

### Post by hikaricore on 2007-06-07
You flat out say you're going back to windows unless someone helps you.

After the bad grammar, spelling, and excessive use of caps and exclaimation points, I decided the "linux community" was better off.

---

### Post by Cappy on 2007-06-07
All you should need to do [If you have Ubuntu 7.04] is go to (System-->Administration-->Restricted Drivers Manager) and click the checkbox.
There's no way you can play the game without the closed source drivers.

[http://gentoo-wiki.com/HOWTO_ATI_Drivers](http://gentoo-wiki.com/HOWTO_ATI_Drivers)
There's no way that would work, it's not an Ubuntu guide.

---

### Post by forscheezee on 2007-06-08
Starting with a clean 7.04 Ubuntu install i followed this guide: 
[URL="https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a"]https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-99489608eb537a1a0346cdd3ad34209d7887714a
[/URL]
If you still get the Mesa error run: [B]sudo depmod -ae
[/B]
Then try:  **fglrxinfo**

Worked for my 9600XT...

---

### Post by mu:te on 2007-07-14
> **hikaricore said:**
> You flat out say you're going back to windows unless someone helps you.

After the bad grammar, spelling, and excessive use of caps and exclaimation points, I decided the "linux community" was better off.

Are you some kind of racist? Because if so, I believe that the Ubuntu forum is better out without you.

I'm not from the USA, GB nor any English speaking country so yeah, you're right, my English isn't perfect, does that make me a bad person?

And yes I'm getting kind of tired of having non-stopping problems all day long so I though that someone might be able to help me, but what did I get? Bye? Just absolutely terrific work man..

Well you know what they say.. make the hell of it son!

---

### Post by Cappy on 2007-07-14
> **mu:te said:**
> Hikaricore, thank you for bumping my thread so others could find it and help me out. 

My grammar and spelling are not very good because english is not my native language and my english skills are not as developed as someone who lives in an english-speaking country.

I still can't get it to work because <insert problem here>.


I fixed your post. I even added a sarcastic line free of charge.

---

