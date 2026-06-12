---
title: "Strange behavior of dual boot NUC8i7BEH"
date: 2019-09-30
forum: Desktop Environments
---

### Post by Frantic_Earthling on 2019-09-30
I have just done a fresh install of Windows 10 and Ubuntu 18.04 LTS in dual boot on a Intel NUC8i7BEH which I equipped with 16Gb DDR4 RAM and a 500Gb NVM SSD.

The good news is, everything works fine. 
It works fine unless... I make a change in the config of either Win10 or Ubuntu 18.04.
Whether that change is big or minor makes no difference. 

Here is what happens. 

Say I modify the sleep time in Win10, or I map a NAS on Win10, or on Ubuntu, or I install a new piece of software, what happens is that after I switch off my NUC, when I switch it back on, it subsequently directly boots into the OS which I last modified without offering a boot choice.

In other words, if I modify or add something in Win10, the next boot takes me directly in Win10. 
Then if I switch it off without modifying anything, when I switch it back on, it starts on the Win/Ubuntu boot choice.

If I modify or add something in Ubuntu, the next boot takes me directly in Ubuntu. 
Then if I switch it off without modifying anything, when I switch it back on, it starts on the Win/Ubuntu boot choice.

I can't find any reasons why this should be happening.

What do you think?

---

### Post by Frantic_Earthling on 2019-10-02
OK. Let me add something new to my post (although I did not get any answers).

Everything works fine now.

It is still a mystery why the above-mentioned problem arose, and why after a few days it disappeared, but I can now report that my dual-boot install with Win10 and Ubuntu 18.04 LTS on an Intel NUC8i7BEH work fine.

:)

---

### Post by vin944 on 2019-11-20
I was gonna post that maybe the multi boot menu was coming and going too quickly so you didn't actually see it.  I have the same NUC and I have had nothing but trouble with it using Ubuntu 18.04.  It reboots all the time randomly.  I'm on my second install of Ubuntu (first was 19.04) on a new HDD hoping that would clear it up but nope.  Sometime it will be fine for days then all of a sudden reboot city.  It never reboots when I'm using it just when I leave it.  Either I have a bad NUC or something wonky with the install.  I never shut mine down (never shut other machines down in the past) but I don't think that is an issue.  Prior to the NUC I had a Shuttle which was fine for 10 or so years, never reboot on it's own and I never shut it down.  I don't see much online except check logs, update BIOS, etc.  I did all that.  I don't think many people put Ubuntu on the NUC (could be wrong) so I should install windows and see how things go.  Glad Firefox has a restore session feature, lol.  Sounds like your NUC is fine with Ubuntu.  Do you ever leave it turned on for extended periods?

---

