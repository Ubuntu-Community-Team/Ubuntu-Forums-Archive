---
title: "Graphics card configuration"
date: 2007-07-06
forum: Dell  Ubuntu Support
---

### Post by kpmwrestler on 2007-07-06
hello, i just installed Ubuntu Studio 7.04 today (on an external hard drive, if that matters), on my Dell Optiplex GX260 

2gb ram
3ghz dual core cpu
256mb graphics card (integrated intel card)
and my monitor's resolution is 10280x1024

you would think with a computer this powerful, (especially since ubuntu doesn't even need half what this computer has to run smoothly), there would be no choppy graphics or anything, but i tried out the screen savers and all the ones that were even the slightest bit 3D or had quick movements  were quite choppy.  And then i tried moving windows around and even that was choppy.  i was thinking about installing Compiz Fusion, but i knew i had better get it to work better with my graphics card first.  how would i install the correct driver, or configure my graphics card?  I don't see any menus in the "System" menu where i can configure the card/monitor.

I have used PCLinuxOS and Opensuse for a long time (and have tried out or occasionally used at least 20 others), but i am new to Ubuntu.  I'm not afraid of using the terminal if that's what it takes.

---

### Post by ridgeland on 2007-07-06
My first thought is the bottle neck is the external hard drive.
Did you play with Studio Ubuntu from the LiveCD / Install CD before jumping to an install?
Did screen savers work there?
Do screen savers work from the internal hard drive for other Linux OS?
Why not partition the internal hard drive to have space?

---

### Post by moffa on 2007-07-07
I would say that your drivers for you video card need installation / tweaking. Check xorg.conf to see what driver you are using

---

### Post by kpmwrestler on 2007-07-07
well, studio doesn't have a livecd, its just an installation, so i couldnt try it out before installing.  it's not like regular ubuntu.

the screensavers work fine in all the other distros and in opensuse i can play unreal tournament just fine.


the reason to put it on an external hdd is to try out studio first to see if I should stick to ubuntu and install the studio window theme, or if studio is more what i want.

---

### Post by kpmwrestler on 2007-07-07
> **moffa said:**
> I would say that your drivers for you video card need installation / tweaking. Check xorg.conf to see what driver you are using

	Identifier	"Generic Video Card"
	Driver		"vesa"

---

### Post by jongkind on 2007-07-07
The vesa driver is the problem. You need to use the i810 driver (opensource driver with 3D acceleration). 
[LIST]
[*]It is in the repositories (xserver-xorg-video-i810). 
[*]To have adequate support for your screen resolution you also need to install i915 driver. You can more read about this here:[ https://help.ubuntu.com/community/i915Driver]("https://help.ubuntu.com/community/i915Driver")
[*]And finally you need to adjust xorg.conf by replacing Identifier Driver "vesa" by Driver "i810"
[/LIST]

---

### Post by kpmwrestler on 2007-07-07
where would i get the site for the repositories?

---

### Post by kpmwrestler on 2007-07-07
wait, i went into synaptic and searched for xserver-xorg-video-intel and it said that the following packages must  be removed:


xserver-xorg-video-i810


so that means it is already installed right?

would that mean all i have to do is go into the xorg.conf and change it to that i810?

---

### Post by kpmwrestler on 2007-07-07
ALRIGHT!!! I got it!

i just changed the driver in xorg.conf and then did what it said here [https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver)

IT works. no more choppy!!!

so before i install compiz fusion, i would  like to know if it is stable yet or if it is still in the development stage?

---

### Post by jongkind on 2007-07-07
The i810 driver might be a bit to 'old' for Compiz. If so, you can try the xserver-xorg-video-intel driver. This one is more recent and it is also in the repositories (e.g. via synaptic). In that case you need to change your xorg.conf: substitute "i810" by "intel".

---

### Post by kpmwrestler on 2007-07-08
oops, i installed the xserver-xorg-intel driver and changed it in the xorg.cong and when i restarted, right after i logged in, it said "digital input error, the optimal display is 1280x1024 @ 60Hz" 

but it was on 1280x1024 @ 75 hz before.  did i forget to configure something?

---

### Post by jongkind on 2007-07-09
You can verify what the optimal resolution & refresh rate of your monitor is (probably in the specifications section of the manual) and adjust the monitor section of your xorg.conf.  Here is an example:

Section "Monitor"
    Identifier     "Dell 1907 FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

If that is not successful you can employ the i810 driver.

---

### Post by phenest on 2007-07-15
I'm also getting choppy graphics rendering on Feisty. I have the i810 driver installed and 915resolution and everything looks good but screen savers perform quite badly. This is a Philips X56 laptop with 1Gb RAM. I tried the intel driver which didn't make a difference. I have noticed that when the mouse moves or gets animated or when there is CD drive activity, the screen savers run smoothly for that period.

What gives?

---

### Post by kpmwrestler on 2007-07-24
whats your graphics memory?

---

### Post by phenest on 2007-07-26
Up to 224Mb shared.

---

