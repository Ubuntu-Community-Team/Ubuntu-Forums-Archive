---
title: "3 monitor setup"
date: 2006-09-09
forum: Desktop Environments
---

### Post by theuni on 2006-09-09
i've been trying and trying for months to get this setup, so i'm finally resorting to asking for help. I've seen all the multi-monitor posts all over these forums and the net, but none have helped me with my setup.

I have 3 monitors. they're all the same. Ideally, i'd like all 3 setup so that i can maximize windows without spanning more than 1 monitor. that seems impossible from everything i've tried. I have an nVidia 6600gt PCIe and an old ATI pci card. As soon as i enable the 2nd card and use a "RightOf" in the serverlayout, it makes it so that windows span screens 1 and 2. I know that mixing ati and nvidia probably makes things difficult...

The 3rd monitor i use exclusively for my WinXP VM (vmware), so it wont bother me if i cant drag windows to/from that monitor. It seems like the only way i'll be able to do what i want is to have 2 concurrent X sessions going, 1 for the 2 left monitors, and 1 for the VM. that's fine too, i just can't figure out how to get that going. Any help or ideas would be appreciated.

TheUni

---

### Post by Miademora on 2006-09-09
I have 1 display left (onboard nv) and 2 right (pcie nv).

Maybe you can use something from my xorg.conf although its only 2 nvidia cards.

---

### Post by theuni on 2006-09-09
Thanks for the reply.

On your 2-monitor PCIe card- Do windows span both monitors? Or are you able to mazimize per-window? I'd like it to act like 2 seperate monitors, rather than 1 stretched.

---

### Post by Miademora on 2006-09-09
When i maximise a window it fits to 1 screen. THis is working for all screens here. With X and XGL.

Only downside i have here is that some desktopicons move out of the screenspace on the displays with smaller resolution. Im using a 17-19-17 setup.

---

### Post by theuni on 2006-09-09
well, i'm getting there

I now have 3 monitors... cloned. heh

it's exactly how i want it, but i want 3 seperate screens, not clones of the other. here's my xorg.conf. any thoughts?

Edit-

Wow, i'm retarded. forget to edit out some of the changes i robbed from your xorg.conf. looks like i may have it figured out afterall.

---

### Post by Miademora on 2006-09-09
Dont know why they are cloned but this part looks weird to me.

```
	Screen 0	"Screen12"
	Screen 		"Screen11" LeftOf "BigScreen"
	Screen 1	"Screen21" RightOf "BigScreen"
```

You have no Screensection called "Bigscreen". Shouldnt it be something like this?

```
	Screen 0	"Screen12"
	Screen 		"Screen11" LeftOf "Screen12"
	Screen 1	"Screen21" RightOf "Screen12"
```

What does your /var/log/Xorg.X.log say? No errors?

---

### Post by theuni on 2006-09-09
yea-

I realized that as soon as i posted. I copied that part from yours and forgot to edit it completely.

OK, here's the deal. I've actually got it working! thanks so much. Only 1 problem remains.

The middle monitor is perfect. The ones left and right of it are the wrong resolution. they're set right, but everything looks stretched. The middle is correctly at 1680x1050. The left and right seem to be 1280x1024. everything seems right as far as i can tell.

Here's the latest xorg.conf

Any ideas?

---

### Post by Miademora on 2006-09-09
Since you have 3 similiar displays i see no problem.

You might need to look at /var/log/Xorg.X.log to see if any errors come up.

As you can see in my conf i had to force some modes to make my right screen come up in the right solution.

```
Option "ModeValidation" "NoEdidModes, NoVertRefreshCheck, NoHorizSyncCheck, NoEdidMaxPClkCheck, NoMaxPClkCheck, NoEdidDFPMaxSizeCheck"
```

---

### Post by theuni on 2006-09-09
you rock!

everything works beautifully now. Dyslexia was the issue before. mixed up 1680x1050 w/ 1650x1080 in a couple places, heh.

Only thing now is that everything is sooooo sloooooow. Before with twinview, it was snappy. Now when scrolling down a website, there's a few second pause. Glxgears works happily, but it seems to be chugging. I'm running a p4 3.2ghz w/ a 6600gt for these 2 monitors. i think it should handle it ok. Any idea why she's chugging so badly?

TheUni

---

