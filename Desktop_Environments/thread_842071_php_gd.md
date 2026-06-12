---
title: "php gd"
date: 2008-06-27
forum: Desktop Environments
---

### Post by ~Darkchaos~ on 2008-06-27
hi all

i come from a small remote part of fiji ...and adsl connection is not available for pcs running any form of linux much less ubuntu...

i suspect the reps here do not know bout linux.....

<!--/tale of woe -->


i love ur os...so much better then ...what was it ..doors???

any way i have an old 1ghz 256mb ram...40gb ..10/100 ethernet ..system...
6 months ago windows suddenly told me that 
driver_irql_not_less_or_equal

something along those lines...and google said i had problems with my RAM SLOTS...no more xp....

anyhoo...a quick install with ubuntu 6.06 from a pc user mag disc..and my new old pc was up and running....and apart ifor the occasional freeze of the mouse and keyboard where i need to restart the pc..everything is hunky dorey....

i went to an expensive net cafe with 1-2MB/s ADSL and downloaded ubuntu hardy heron in bout 1 hr  30 mins...coz i wanted to have php5 and mysql running on my pc to develop offline web pages for my mybb site....

anyhoo...it was all text based...so i couldn't use that --> see related question....


i then ..using the hardy cd ...installed php5 and mysql on ubuntu 6.06 using the cd as a repository...it worked


currently im also running VBA, VBA EXPRESS, wine+no$gba at near 100%....

I LOVE U GUYS....


<question section>
**_Question:**_
can i use the hardy heron server cd to install gd for captcha and stuff...if so how....

**_Question:**_
How can u guys afford to send anyone who requests a cd to them...postal charges an all...don't u make huge losses....

**_Question:**_
For normal users ..does ubunutu really need no antivirus....

**_Question:**_
do u really think my ram slots are broken...i rarely change ram..and my pc freezes up when i try to play music and video at the same time 

**_Question:**_
any fix for that ...see above....

**_Question:**_
can ...with some mondo sudo code work ...it be so that my pc uses memory from the swap first then ram..see my process monitor says 120-190mb ram used...18mb swap used...i wanna reverse that .. ill accept any performance loss....
<! --i know the above is a dumb request but worth a shot -->

**_Question:**_
can some one make a list of all the packages and dependencies for me to install
 xfce
comic sans ms font on my pc .....for firefox 2.0.0.14 installed manually

on a clean install of 6.06...manually without a direct adsl connection...
i download packages manually form packages.ubuntu from a netcafe and i have to travel at least a 10min walk for every dependency it needs and every dependency the dependencies need...i love ubuntu and its worth the effort....


any help will be appreciated .....

Am i the only member from FIJI

thanks for ur Great os..u rock :guitar:

---

### Post by Xiong Chiamiov on 2008-06-27
I can't answer all of these, but I'll see what I can do.

If it's [listed here]("http://packages.ubuntu.com/"), a package should be on the CD (I think).

Mark Shuttleworth made quite a bit of money selling Thawte to Verisign, so he can afford to do stuff like this.  That said, I believe most of the income comes from selling support.

Without getting into the reasons why, Linux does not need an antivirus.  If you're in the habit of receiving questionable files and sending them on to Windows users, you might check out the linux versions of avast! or ClamAV.  Just keep in mind that they are protecting against Windows viruses, not Linux viruses.

You can check your RAM (though it does take quite a while) by running the RAM test on the live CD startup screen.

You might be able to adjust how much swap space is used by adjusting the "swapiness", but I'm not sure.

I believe typing
```

aptitude install xfce -s

```
will show a list of dependcies (-s indicates simulate, so it won't actually install anything), but I'm not on *buntu atm, so I can't be sure.

Oh, and it's not really *our* OS, in the sense you mean.  Almost everyone here is a volunteer; we don't work for Canonical, but just help out answering questions because, well, we love it!

---

### Post by ~Darkchaos~ on 2008-06-27
> **~Darkchaos~ said:**
> hi all


**_Question:**_
do u really think my ram slots are broken...i rarely change ram..and my pc freezes up when i try to play music and video at the same time 

**_Question:**_
any fix for that ...see above....

**_Question:**_
can ...with some mondo sudo code work ...it be so that my pc uses memory from the swap first then ram..see my process monitor says 120-190mb ram used...18mb swap used...i wanna reverse that .. ill accept any performance loss....
<! --i know the above is a dumb request but worth a shot -->

**_Question:**_
can some one make a list of all the packages and dependencies for me to install
 xfce
comic sans ms font on my pc .....for firefox 2.0.0.14 installed manually

on a clean install of 6.06...manually without a direct adsl connection...
i download packages manually form packages.ubuntu from a netcafe and i have to travel at least a 10min walk for every dependency it needs and every dependency the dependencies need...i love ubuntu and its worth the effort....




> **Xiong Chiamiov said:**
> 
You can check your RAM (though it does take quite a while) by running the RAM test on the live CD startup screen.

You might be able to adjust how much swap space is used by adjusting the "swapiness", but I'm not sure.

I believe typing
```

aptitude install xfce -s

```
will show a list of dependcies (-s indicates simulate, so it won't actually install anything), but I'm not on *buntu atm, so I can't be sure.

Oh, and it's not really *our* OS, in the sense you mean.  Almost everyone here is a volunteer; we don't work for Canonical, but just help out answering questions because, well, we love it!

swapiness...please explain how to make the swap first and the ram second

i tried the ram memory test..but after 4 hours it just keeps repeating...it never stops....

i know bout the3 sudo XXXX way to install ...can someone just paste a complete list of all the dependencies for a clean install..to manually go to packages.ubuntu.org...and manually download whwat files thanks....

does anyone think switching from gnome to xfce help me with the freeze problems since xfce uses less ram



edit ...** and thanks for your reply**

---

