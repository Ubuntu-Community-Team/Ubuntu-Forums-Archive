---
title: "Inspiron 2500 switches off randomly?"
date: 2007-12-30
forum: Dell  Ubuntu Support
---

### Post by phaeussler on 2007-12-30
Hi all,

I've successfully installed Ubuntu 7.10 on my old Inspiron 2500 laptop. Unfortunately I now have the problem that the laptop switches itself of randomly from time to time. I cannot recognize any reason why and when it happens. It seems to happen out of a sudden.

I already switched ACPI off in GRUB but the problem still exists. Does anyone have an idea what could be the problem?

Many thanks in advance and best regards,

pascal

---

### Post by jlm3030 on 2008-01-11
I am sorry I don't have a solution but I am also having the same problem. I switched from Suse to Ubuntu because of the problem and have been fine until the release of gutsy.

---

### Post by phaeussler on 2008-01-11
hi,

thanks very much for your reply. So it seems that we are the two lost out there with this problem. Well at least no I know that I am not the only one :-)

Be sure, if I find a solution I will let you know.

Can you describe me briefly what you have already tried to fix it?

I removed any acpi support in the kernel and also uninstalled acpi and power management packages. Unfortunately this did not help so far.

I am still not sure if it might be a problem with my wlan pcmcia card. It is an old netgear model and I had a lot of trouble with it. I needed to block the kernel module for the realteck chip support and use the ndis-warpper together with the windows driver instead. It works but maybe it is not stable?

Best regards
pascal

---

### Post by JimFritzMI on 2008-01-11
Rest assured you two are not alone. I just installed Unbuntu last night, same problem you bot describe.

Although it seems to have stopped now that it sat for a few hours being off. Is it possibly a heat issue?

---
Thanks,
Jim

---

### Post by phaeussler on 2008-01-12
Hi Jim,

so we are at least three now :-)

well, my laptop sometimes works fine for some hours. Sometimes ist takes 2-3 days until it happens again. But I can always be sure that it indeed will happen again, its only a question of time.

A heat issue is an interesting aspect. Nevertheless, yesterday evening  my laptop "dit it" right 1 minute after I booted up. So at this time everything should have been pretty could in the laptop.

One thing I observed so far: The problem never occurred when the laptop is idle. I.e. when it is running but I do nothing with the laptop, the problem never occurred. So from this observation I would come to the conclusion that it may *not* be a power management issue.

During the last weeks I the problem occurred several times when I was installing packets with synaptic. I am wondering if it has to do something with the hard disc or drivers related to the disc since installation means heavy disc activity. This would also explain why it is unlikely to happen when the system is idle...

best regards
pascal

---

### Post by ashdezign on 2008-01-12
I have been having the same problem on an Inspiron E1505 running Gutsy Gibbon.

No clue what might be causing it

---

### Post by jlh on 2008-01-12
I have this problem running Gutsy on a Thinkpad T30.  I've also tried the acpi=off fix.  It seemed to work for several days, but then the problem recurred.

Even stranger, I ran Gutsy for two months without any of this.  The random crashes began around Christmas.  

I also have boot troubles: instead of booting normally to the splash login, I get a boot into the terminal.  Not always.  Sometimes.  Also began around the same time.  

My hypothesis is that some update is messing up something.

---

### Post by jlm3030 on 2008-01-14
One issue that I have always had with linux on my inspiron 2500 is that the fan closest to the edge of the computer never runs. I have always wondered if the to problems are related. The fans seem to be a bios function and is not run by linux but I don't understand why they would work in windows and not linux. But I can tell you that the issue of switching off ramdomly happens less with older kernals. 
I also have had problems with it switching of right after booting up so the overheating should be ruled out. I hope some of this information can help us get or computers working correctly.

---

### Post by phaeussler on 2008-01-17
Hi all,

it seems to me that we must consider that we perhaps do not all face the same reason for our random switch-offs. Still I am not really a step further. 

The only thing I tried is that I replaced my wlan PCMCIA card. I used the MA521 before and as I already posted, it only worked with the windows driver and NDIS wrapper. With the original driver from ubuntu, the card causes the system to completely hang.

Since I observe the switch-offs not when the system is idle and more often when I install something, I thought that it indeed might be my construction with the MA521 which might be instable.

I replaced it with an even older card, namely the NETGEAR MA401. This card works with the native ubuntu driver since it does not use the same chip as the MA521.

Since I replaced the card I did not encounter any random switch off again. Of course I am not convinced(!) that this realy was the problem. I expect the next switch off to happen every moment :-)

I will keep you posted on what is going on.

best regards,
pascal

---

### Post by phaeussler on 2008-01-17
Hi again,

there is another observation I experience: Since two weeks I use an external mouse (USB) with the laptop. I cannot remember that there had been a switch off when I used the external mouse.

Could the driver support for the build-in touch pad be instable? In this case it would again be clear why the switch off never happens when the laptop is idle and I do nothing with it.

Anyone of you made similar observations? In particular: Do you also observe random switch offs when your system is idle and you do not touch it?

best regards,
pascal

---

### Post by jlh on 2008-01-17
My problem is the opposite.  The crashes occur when the computer is idle, not when I am using it.  Or if I am simply streaming music, without launching other applications.

---

### Post by phaeussler on 2008-02-13
Hello all,

meanwhile three weeks passed since the last post to this threat. During this time my laptop did not "do it" anymore. I am not convinced yet, that the problem is realy solved, but it's the longest stable period I ever observed.

So if we assume that its solved on my box, then the solution was one of the following:

1) The use of an external mouse instead of the touch pad

or

2) The replacement of the NETGEAR MA521 wireless PCMCIA adapter with the NDIS wrapper

or

3) An regular ubuntu update that replaced something I don't know

Have you any new observations?

Best regards,
pascal

---

### Post by phaeussler on 2008-02-16
Hi all,

when I wrote my last post I had that bad feeling that the box will "do it again" as soon as I post to you that the problem might be fixed.

The box did it right this morning!!! ;-)

Again the switch off occurred during an update installation using synaptic. This was also often the case in the past.

It seems that I am no step further in this...

best regards
pascal

---

### Post by whatsthatmean on 2008-04-06
pascal
i have same prob with my dell insp 2500. random sudden shutdowns. started w/ xubuntu and now have same problem running linux mint. thought it was hardware at 1st (4 year old dumped juice on it. i replaced keyboard and touchpad) but now i wonder if its a soft issue. hoping new final release of ubuntu will help.
mike

---

### Post by phaeussler on 2008-04-15
Hi Mike,

two weeks ago I made a dist-ubgrade to ubuntu 8.04 beta. In the beginning I had heavy problems with the switch-off problem. It happened every 10-20 minutes.

As a first try I switched off acpi:
1) swiched off all acpi related services
2) added acpi=off noacpi to the grub menu.lst

Since I did this I did not get any random switch-off anymore! The strange thing is that I did all this when I used ubuntu 7.10, too, but there it did not completely solve the problem. Ok I am not sure that everything is really ok now but as I said above, since two weeks now everything is fine - just due to the consequent switch off of all acpi stuff.

Best regards,
pascal

---

### Post by phaeussler on 2008-05-09
hi all,

just a small update: Since I turned off all acpi stuff under hardy 8.04 I do not experience any random switch-offs any more. I am using the laptop frequently for weeks now and there was not even a single switch-off. It seems to me that it really was an acpi problem which I did not fully solve under gutsy 7.10.

My feeling is that it was not enough to add acpi=off no acpi to the grub entry. To me it seems that it was even necessary to disable the acpi support in the Gnome Services panel as well as the power management Gnome tools.

I hope you are successful, too.

Best regards,
pascal

---

### Post by jlh on 2008-05-09
Pascal,

How do you go about accomplishing this part:

"swiched off all acpi related services"

Thanks.

---

### Post by whatsthatmean on 2008-05-10
my random power downs have not occurred since i upped to heron. not one time. and i didnt have to change anything. 

figured out to increase the screen res
now all i need is sound
:)

---

### Post by phaeussler on 2008-05-17
> **jlh said:**
> Pascal,

How do you go about accomplishing this part:

"swiched off all acpi related services"

Thanks.

Hi,

I just used the GNOME tool you can in the "System" menu: "System" --> "System administration" --> "Services". In the tool you find a list that displays various services and check box icons to activate/deactivate them. I switched-off acpid and apmd.

I hope the names of the menu entries are correct. I have a German installation here in front of me and can only guess how the menu names are in English.

Best regards,
pascal

---

