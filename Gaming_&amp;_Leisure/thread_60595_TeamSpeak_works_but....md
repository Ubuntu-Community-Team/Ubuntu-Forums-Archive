---
title: "TeamSpeak works but..."
date: 2005-08-28
forum: Gaming &amp; Leisure
---

### Post by Drakx on 2005-08-28
Hi guys

I have teamspeak working how ever when i try to play ut2004 or for that matter any app/game there is no sound while teamspeak is running but teamspeak runs fine

here is some info

```
drakx@Ixl2:~$ lsmod | grep snd
snd_intel8x0           29984  1
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  1 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm
drakx@Ixl2:~$
``` 

and

```
drakx@Ixl2:~$ lspci | grep audio
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
drakx@Ixl2:~$
``` 

and


```
drakx@Ixl2:~$ ls /dev/*dsp* -l
crw-rw----  1 root audio 14, 12 2005-08-28 17:32 /dev/adsp
crw-rw----  1 root audio 14,  3 2005-08-28 17:32 /dev/dsp
drakx@Ixl2:~$ ls /dev/*dsp*
/dev/adsp  /dev/dsp
drakx@Ixl2:~$
``` 

any one know what the problem is ?

thanks for the help

---

### Post by evilghost on 2005-08-28
Teamspeak doesn't use ALSA and directly allocates /dev/dsp.  Your soundcard doesn't support hardware mixing, so when running TS you can't use software mixing because TS has locked /dev/dsp.

The solution is to:

1) Not use TS

**or**

2) Upgrade your soundcard.

Now, the Sound Blaster Live 5.1 (emu10k1) is pretty much **the** sound card to use with Linux.  The newer Sound Blaster Live 24Bit does not support hardware mixing but rather relies on Win32 DirectPlay for mixing.

If you have a Sound Blaster Live 5.1 (Chipset of emu10k1) slap it in and watch your troubles vanish.  If you don't, they are somewhat difficult to find.  I did end up winning 10 of these cards from Ebay, so if you want one I'd be more than happy to sell you one for $10 (which is inclusive of shipping, if you live in the USA).

Hope this helps, I went down this road a few months ago, and after finally securing a emu10k1 card, I decided to go ahead and try to grab a few extras on Ebay so I could pass them around.

---

### Post by Drakx on 2005-08-29
[QUOTE=evilghost]Teamspeak doesn't use ALSA and directly allocates /dev/dsp.  Your soundcard doesn't support hardware mixing, so when running TS you can't use software mixing because TS has locked /dev/dsp.

The solution is to:

1) Not use TS

**or**

2) Upgrade your soundcard.

Now, the Sound Blaster Live 5.1 (emu10k1) is pretty much **the** sound card to use with Linux.  The newer Sound Blaster Live 24Bit does not support hardware mixing but rather relies on Win32 DirectPlay for mixing.

If you have a Sound Blaster Live 5.1 (Chipset of emu10k1) slap it in and watch your troubles vanish.  If you don't, they are somewhat difficult to find.  I did end up winning 10 of these cards from Ebay, so if you want one I'd be more than happy to sell you one for $10 (which is inclusive of shipping, if you live in the USA).

Hope this helps, I went down this road a few months ago, and after finally securing a emu10k1 card, I decided to go ahead and try to grab a few extras on Ebay so I could pass them around.[/QUOTE]
 I would love to buy one off you but im in the uk, so guess thats out the window :D, thanks for the repliy and advice i know some one with a soundblaster live 5.1 not too sure if its emu10k1 chip. is there any where to look on the card and find out ?

cheers

EDIT

What would you charge for shipping to the uk ?

---

### Post by evilghost on 2005-08-29
Sorry to hear you're in the UK :)

Hmm, honestly, I have no idea what shipping costs are.

You can tell if the card is an EMU10k1 by looking on the card, and reading the chipset.  Most will say something like emu10k1-sef or emu10k1-nef.

The key is the "emu10k1"

As far as shipping costs, I don't want to make money off the deal, I'd rather just help out a fellow Ubuntu user.  If shipping is expensive, I'll just give you the card for free and ask you to pay shipping costs.

What's your address?  Want to PM me?

How many other Ubuntu users do you have, or Linux users, who are in a similiar situation?  How many do you think you'll convert?  I ask, because I'm sitting on 10 cards that are rare and the panacea of Linux hardware mixing and gaming and could send more than just one.  I don't want to exhaust my supplies too quickly, I'd probably send a max of 3 as long as you promise to be as generous with them as I'm going to be.

---

### Post by Kemotaha on 2005-08-29
evilghost,

I would like to buy one of those cards from you.  Let me know how I can get you the money.  I am in UT, USA.

Nathan

---

### Post by Tichondrius on 2005-08-29
Haha why would anyone waste SLI on 2x6600GT when even a single X800XL is better is beyond me. 

But seriously, what the hell is teamspeak ? I thought UT2004 has its own built in voice chat, as do many online games.

---

### Post by Kemotaha on 2005-08-30
[QUOTE=Tichondrius]Haha why would anyone waste SLI on 2x6600GT when even a single X800XL is better is beyond me. 

But seriously, what the hell is teamspeak ? I thought UT2004 has its own built in voice chat, as do many online games.[/QUOTE]
 Price for one.  Better compatibility in Linux for 2(this is a Linux forum ;-) ).  I still believe that ATI makes a better video card but until they can get them to perform in Linux, I am staying away. 

Teamspeak is a voice chat that can be used for any game.  It is a seperate program and it is used by a lot of people.  I use it for World of Warcraft, but I have to boot to Windows because I don't have a hardware mixer.  It is more commonly used for games like BF1942 and BF2.  I am not sure if UT2004 has its own built in voice but it really isn't that common.  

Hope that helps.

---

### Post by Drakx on 2005-08-30
[QUOTE=evilghost]Sorry to hear you're in the UK :)

Hmm, honestly, I have no idea what shipping costs are.

You can tell if the card is an EMU10k1 by looking on the card, and reading the chipset.  Most will say something like emu10k1-sef or emu10k1-nef.

The key is the "emu10k1"

As far as shipping costs, I don't want to make money off the deal, I'd rather just help out a fellow Ubuntu user.  If shipping is expensive, I'll just give you the card for free and ask you to pay shipping costs.

What's your address?  Want to PM me?[/QUOTE]

That is most kind of you :D and its most appreciated, ive sen you a pm i dont mind paying for the product if you would like to make a small proffit :D


> 
How many other Ubuntu users do you have, or Linux users, who are in a similiar situation?  How many do you think you'll convert?  I ask, because I'm sitting on 10 cards that are rare and the panacea of Linux hardware mixing and gaming and could send more than just one.

Its just me :( i keep trying to get others to try Linux out (infact ive to show some one this afternoon ubuntu :D so with a little look there will be one more[/QUOTE]

> 
  I don't want to exhaust my supplies too quickly, I'd probably send a max of 3 as long as you promise to be as generous with them as I'm going to be.

I would promise to be as generous if i knew some one else who needed one but i dont  :???: 


Thanks very much evilghost, you are a star :D

---

### Post by nickless on 2005-08-30
Damn :( Any germans here, who have some of those cards, too? :)

---

### Post by Drakx on 2005-08-30
OK ive been given a SB Live emu10k1-ecf will that work too ?

---

### Post by evilghost on 2005-08-30
[QUOTE=Kemotaha]evilghost,

I would like to buy one of those cards from you.  Let me know how I can get you the money.  I am in UT, USA.

Nathan[/QUOTE]

Kemotaha, PM me your address and I'll try to ship out out ASAP.  I say $10 for the card, plus the cost of shipping.  Sound fair?

[QUOTE=Drakx]OK ive been given a SB Live emu10k1-ecf will that work too ?[/QUOTE]

Excellent, I was afraid you wouldn't find one.  Yes, that card should work **perfectly** as the emu10k1 is the key.  If it doesn't work out, let me know and I'll look at shipping you one.

Since you're now running an emu10k1 card, be sure to read up on my UT2004 Howto, specificallyi the section talking about recompiling openal for support for the emu10k1 optimizations.

Here's the URL.

[http://ubuntuforums.org/showthread.php?t=49329&highlight=ut2004](http://ubuntuforums.org/showthread.php?t=49329&highlight=ut2004)

The section you want to key-in on is the **seventh** tweak.

---

### Post by Drakx on 2005-08-31
[QUOTE=evilghost]Kemotaha, PM me your address and I'll try to ship out out ASAP.  I say $10 for the card, plus the cost of shipping.  Sound fair?



Excellent, I was afraid you wouldn't find one.  Yes, that card should work **perfectly** as the emu10k1 is the key.  If it doesn't work out, let me know and I'll look at shipping you one.

Since you're now running an emu10k1 card, be sure to read up on my UT2004 Howto, specificallyi the section talking about recompiling openal for support for the emu10k1 optimizations.

Here's the URL.

[http://ubuntuforums.org/showthread.php?t=49329&highlight=ut2004](http://ubuntuforums.org/showthread.php?t=49329&highlight=ut2004)

The section you want to key-in on is the **seventh** tweak.[/QUOTE]
 Evilghost

Thanks for your input :D, guess i was lucky that a cusion of mine had just upgraded :D im sorry to have messed you around i found that ts and any other game i use all have sound.

Thanks very much im greatful for the help you provided :D

Drakx

---

