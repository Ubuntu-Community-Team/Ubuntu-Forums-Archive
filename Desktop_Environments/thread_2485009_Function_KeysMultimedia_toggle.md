---
title: "Function Keys/Multimedia toggle?"
date: 2023-03-17
forum: Desktop Environments
---

### Post by bugbear6502 on 2023-03-17
I recently purchased a new HP laptop - I'd been using my previous Dell Vostro for 14 years, so I figured I was overdue an upgrade.

Installing Lubuntu 22.04 LTS went fairly smoothly.

But I've just hit a snag. I don't really watch media on my laptop, but I do use Inkscape, which is quite function key heavy.

As it stands at the moment, the "top row of keys" perform their multimedia role (louder/quieter, brighter/dimmer, etc) when pressed.

If I press the Fn key, the "top of of keys"  work as function keys, acceptable to Inkscape.

I would like to change this so I get the function keys "all the time", and can have the multimedia things via special sequences.

Googling led me to many references to "fnmode" and "apple_hid" but this information seems to apply to Apple keyboards only.

QUESTION: how to I permanently configure things so I get function keys by default?

INFORMATION:

Machine: HP Laptop 17-cp0021na 17.3" AMD Ryzen™ 5, 16GB RAM, 512GB SSD, FHD, Blue

lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.2 LTS
Release:        22.04
Codename:       jammy

uname -r
5.19.0-35-generic

---

### Post by The Cog on 2023-03-17
This may be of no help to you at all, but its worth a try. My acer laptop has an option in the BIOS setup to select the default action for those keys - function or multimedia.
I'm not aware of how to map it in the OS, but it would probably involve "setxkbmap -option $something".

---

### Post by ne29914 on 2023-03-17
This is odd, if I understand you corretly.
On my HP with Lubuntu, the F1...F12 keys are just that, nothing else (function depends on active program).
Pressing "fn" invokes the secondary function, eg, brightness, volume etc.
Your machine seems to have it in reverse?

---

### Post by guiverc on 2023-03-17
Alas I know what you mean... 

I purchased some new (*second hand*) hardware earlier this year, which included a HP Envy laptop, which has its Fn/media keys reversed (*by default*).

I used it for some QA-testing (Lubuntu 22.04.2 & *lunar*) but I decided I didn't like the *feel & **reduced-size *keyboard & given I already knew I needed a newer screen for external monitor as it wouldn't use my old analogue-VGA, I mostly put it aside.

On booting it and entering into BIOS/uEFI setup, under ***System Configuration*** there is a ***Action Keys Mode*** option on mine which lets me select if I want the function keys to be *function keys* or *action keys* (ie. if Fn is required for action or function key).  Doesn't your machine have something like that?

*Note:  I don't know my device well, having put it aside & pretty much ignored it thus far.*

---

### Post by ne29914 on 2023-03-17
Inteesting. Never heard of this before.

---

### Post by scoob8000 on 2023-03-23
I have an older laptop like that.  You need to hold down the function key in order to use any of the F1-F12 keys.    So switching tty's, I need to ctrl-alt-function-fx.    It's a pain that I've never found a workaround for..

---

### Post by bugbear6502 on 2023-03-24
Changing BIOS worked. And the BIOS setting was called "action keys". Googling that jargon led me to this helpful page.

[https://support.hp.com/us-en/document/ish_5878386-5878448-16](https://support.hp.com/us-en/document/ish_5878386-5878448-16)

---

