---
title: "setting AGP mode in fglrx?"
date: 2005-07-25
forum: Gaming &amp; Leisure
---

### Post by aaso on 2005-07-25
is it possible to set the AGP mode of ATI cards?

currently my AGP device gets set to 8x, but then my hardware freezes, both on WINXP and Ubuntu,

I was wondering if I could force this to 4x, because then my 3D won't freeze within moments

---

### Post by grim42 on 2005-07-25
I don't think this can be set in the current Linux ATI drivers. There may be a BIOS setting you could try?

What video card do you have -- is it 4x or 8x? What does the motherboard support? Are you sure that this is the reason it's freezing?

---

### Post by aaso on 2005-07-25
No I can't set it in BIOS unfortunately..

it's a VT8377 KT400 AGP host, so it should accept up to 8x

the card itself is a mobility radeon 9700 and should also be 8x 

I never succeeded in running it 8x tho, not even with most
recent catalysts available, once set to 8x it will crash any
3D app I try to run within a couple of seconds. I will get 
acceleration but almost instant freeze as well. Complete lockup,
hard reboot needed.

Once I set the AGP to 4x under Windows, the app/game will
keep on running with nice accel. And my laptop won't crash.

So I'm not 100% sure it's this, but I reckon it's where I need
start looking when downgrading AGP means no crash.

---

### Post by grim42 on 2005-07-25
Is this a laptop?

I would assume that a laptop should work at 8x if that's the hardware it comes with. It could be a fault with the hardware?

Unfortunately I don't know a lot about the settings for the ATI drivers. I suspect this may require some kernel config changes or using a different agpgart module.

See this "Linux ATI Radeon Howto" link which mentions AGP 8x and 4x, specifically with reference to a VIA KT400 chipset.

[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=22](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=22)

---

### Post by aaso on 2005-07-26
yeah thanks for the link; it mentions the problem indeed for the KT400 chip, but in combination with the 2.4 kernel? in 2.6 it should be working properly, and that's what it does, I don't get errors i just get a hard freeze..

It probably is hardware related, I've stumbled across some not-linux-related discussions about the graphic card itself running agp 8x, stating this doens't work so well in practice as it does in theory

---

### Post by aaso on 2005-07-27
[QUOTE=grim42]
I suspect this may require some kernel config changes
[/QUOTE]

like in the character devices?

would it be possible to force the agp to V2 instead of V3 (8x)

i'm at work so I can't try yet but I'm dying to know the answer

---

### Post by grim42 on 2005-07-27
What I meant was possibly having to recompile the kernel with some different config options -- I'm only guessing though.

There must be a way to force v2 instead of v3 but I don't know what it is -- sorry that I'm not being terribly helpful.

Try posting your question in the Hardware Help section -- there's probably someone there who knows more about this.

---

### Post by aaso on 2005-08-01
Someone found the following for me, and it works! 

[http://www.abit-usa.com/products/graphics/documents/agp30_final_10.pdf](http://www.abit-usa.com/products/graphics/documents/agp30_final_10.pdf) 
From the table in the documentatin page 49, bit 0:2 are controlling the AGP mode. Using the AGPMask option, you can change the mode by masking those bits.



AGPMask:
0x00000001 = AGP 1x disable (force 2x and/or 4x)
0x00000002 = AGP 2x disable (force 1x and/or 4x)
0x00000004 = AGP 4x disable (force 1x and/or 2x)
0x00000010 = fast writes disable
0x00000200 = Sidebanding disabled

AGPv3Mask:
0x00000001 = disable AGP 4x (force 8x)
0x00000002 = disable AGP 8x (force 4x) 

So the last option was the one I needed...thanks for thinking with me!

---

### Post by grim42 on 2005-08-02
Hey that's great to know! Thanks for the feedback -- this might come in handy sometime for me too!

---

