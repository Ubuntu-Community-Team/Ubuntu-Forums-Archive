---
title: "HELP, i need help"
date: 2007-03-01
forum: Desktop Environments
---

### Post by HoMe_CaNiBaL on 2007-03-01
I there.

I need help. My computer cant run linux... From October that i've been using linux, but with freezes, alot of freeze, and have always to do hard reset. I've test with metacity and the computer freezes again. Computer works great on Windows, very stable, i dont understand why computer freezes..

I love linux, but with my computer i cant run it. My specs are

Pentium 4 2.8 HT
Asus P4C800 DLX
Aopen Gf 6600gt 128Mb AGP
2x 512Mb Ram Kingston DDR400
160Gb IDE Seagate
120Gb IDE Seagate

Some problems with my hardware?

Software:

Edgy 6.10 with 2.6.17.11-generic  ( install linux-686 )
Nvidia 97.46

Thanks

---

### Post by Sqwishy on 2007-03-01
!what... your specs are FINE! Ubuntu and beryl will run on almost any computer that can run windows xp! Is there any pattern of when your computer freezes? Like was it after you opened a certain app or something?

---

### Post by dannyboy79 on 2007-03-01
look thru each of these file either with the log viewer or by just using gksudo gedit xxxxx
example: gksudo gedit /var/log/syslog

and look thru for anything that sticks out, like errors and such. does this occur using the live cd as well? did you test your ram using the live cd? are your hard drives ok? is your power supply ok?

/var/log/dmesg

/var/log/syslog

/var/log/messages

/var/log/kern.log

/var/log/Xorg.0.log

/var/log/auth.log

and maybe even /home/username/.xsession-errors


post back with anything that you find that you think may be wrong, actually copy and paste it here so we can see it. we'll try to help.

---

### Post by HoMe_CaNiBaL on 2007-03-01
I think that i have good specs, but, i can't understand why computer freezes.

With Beryl running, computer freezes after minimize, or maximize. After a animation!

With Metacity, freezes at 5:00 am, with Utorrent e amule running. I leave computer at 1:30 am.

To install ubuntu i need some options to run live cd/install ubuntu.

To start ubuntu i do:

" linux noapic irqpoll isa_pnp_reserve=18 ". Have something to do with this?

Sorry my english, i'm portuguese, i hope you understand.

---

### Post by HoMe_CaNiBaL on 2007-03-01
> **dannyboy79 said:**
> look thru each of these file either with the log viewer or by just using gksudo gedit xxxxx
example: gksudo gedit /var/log/syslog

and look thru for anything that sticks out, like errors and such. does this occur using the live cd as well? did you test your ram using the live cd? are your hard drives ok? is your power supply ok?

/var/log/dmesg

/var/log/syslog

/var/log/messages

/var/log/kern.log

/var/log/Xorg.0.log

/var/log/auth.log

and maybe even /home/username/.xsession-errors


post back with anything that you find that you think may be wrong, actually copy and paste it here so we can see it. we'll try to help.

My computer is FULL stable with windows xp. My system have 1year on "my hand", its the same after that day.

Like i say on my other post,to run live cd/install, i have to do some tricks, because appear me
"cdrom appear to be confused" so i have to do "linux noapic irqpoll isa_pnp_reserve=18" to start.

Power supply its a Aopen with very good lines. At this moment i'm working, but when arrive home, i'll see that files.

---

### Post by dannyboy79 on 2007-03-01
ok, again, check the files I suggested to see if there are any issues. that's all I can suggest.

---

### Post by bigken on 2007-03-01
when a pc freezes like this usually bad video drivers I would try using something like [ENVY]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by dannyboy79 on 2007-03-01
he has already stated that he is using nvidia 9746 which is the latest nvidia driver. i suppose he could've installed it wrong though. envy is aweome, i used it and it worked EXCEPT that since I didn't have xserver-xorg-dev installed it didn't work. so just make sure you have that installed first before you run it. i don't know why tseliot just doesn't include that in his script but anyway. good luck

---

### Post by HoMe_CaNiBaL on 2007-03-01
Hi there. I'm at home now!

Ok i leave you the files at attachment, and a screenshot from nvidia drivers.

The last freeze was at 28 Feb 4:50 am!

I hope you can help me! Thanks

EDIT: another freeze... when moving data from usb pen to computer 02/03 1:30 am

---

### Post by HoMe_CaNiBaL on 2007-03-02
goes up....

---

### Post by dannyboy79 on 2007-03-02
*wells heres something weird in your dmesg about your cpu, shouldn't it be running HT?
CPU: Hyper-Threading is disabled
[17179573.396000] CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
[17179573.396000] CPU1: Intel(R) Pentium(R) 4 CPU 2.80GHz stepping 05
[17179573.396000] Total of 2 processors activated (11269.52 BogoMIPS).
[17179573.500000] checking TSC synchronization across 2 CPUs: passed.
[17179573.504000] Brought up 2 CPUs

It says HT is disabled but it found 2 cpu's? This most likely isn't related to your freezes but I just wanted to point it out.

*According to the syslog, around 4:50, this is all that's recorded:
Feb 28 04:51:07 canibal-desktop dhclient: No DHCPOFFERS received.
Feb 28 04:51:07 canibal-desktop dhclient: No working leases in persistent database - sleeping.
Feb 28 04:57:19 canibal-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Feb 28 04:57:27 canibal-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
Feb 28 04:57:36 canibal-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Feb 28 04:57:47 canibal-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Feb 28 04:58:05 canibal-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Feb 28 04:58:20 canibal-desktop dhclient: No DHCPOFFERS received.
Feb 28 04:58:20 canibal-desktop dhclient: No working leases in persistent database - sleeping.
*So that doesn't tell us anything unfortunately.
*According to your syslog, your system was halted at 1:16 p.m. per this info here:
Feb 28 13:16:44 canibal-desktop gdm[4445]: Master halting...
Feb 28 13:16:45 canibal-desktop init: tty1 process (3999) killed by signal 15
Feb 28 13:16:45 canibal-desktop init: tty2 process (4000) killed by signal 15
Feb 28 13:16:45 canibal-desktop init: tty3 process (4001) killed by signal 15
Feb 28 13:16:45 canibal-desktop init: tty4 process (4002) killed by signal 15
Feb 28 13:16:45 canibal-desktop init: tty5 process (4003) killed by signal 15
Feb 28 13:16:45 canibal-desktop init: tty6 process (4004) killed by signal 15
Feb 28 13:16:49 canibal-desktop hcid[4730]: Got disconnected from the system message bus
Feb 28 13:16:51 canibal-desktop exiting on signal 15
*Is your internet working for you? Cause in your syslog I found this:
Mar  2 00:30:35 canibal-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Mar  2 00:30:43 canibal-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Mar  2 00:30:58 canibal-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Mar  2 00:31:16 canibal-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Mar  2 00:31:34 canibal-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
Mar  2 00:31:36 canibal-desktop dhclient: No DHCPOFFERS received.
Mar  2 00:31:36 canibal-desktop dhclient: No working leases in persistent database - sleeping.
*Which leads me to believe that you're not getting an ip which would prevent you from *internet access and network capabilities? Nevermind, I see that you have eth1 as well. If *you don't use eth0, I would comment it out if I were you. At least my interfaces file only *has 1 interface in it anyway. Your call, I guess I can't say what eth0 is anyway?
*It also states this in your syslog?
Kernel command line: root=/dev/hda1 ro quiet splash linux noapic irqpoll isa_pnp_reserve=18
Misrouted IRQ fixup and polling support enabled
Mar  2 00:29:33 canibal-desktop kernel: [17179569.184000] This may significantly impact system performance
*I can't speak about it though? I use the noapic and that's all.
*The messages file only shows this at 4:51a.m.:
Feb 28 04:51:20 canibal-desktop -- MARK --
*Which means nothing, --MARK-- just means, hey, I am on. It doesn't mean anything!
*The only thing in kern.log is this:
Feb 28 04:05:11 canibal-desktop kernel: [17274060.204000] hdd: cdrom_pc_intr: The drive appears confused (ireason = 0x01
*So that doesn't tell us anything. 
*our Xorg.0.log file looks ok, but a few things stand out. ALso, why did you add the *options in your Xorg.conf for like this stuff:
Option "RenderAccel" "0"
Option "AllowGLXWithComposite" "True"
Option "AddARGBGLXVisuals" "True"
*his stuff showed up in the Xorg.0.log file, and I didn't any of these option used in this 
*guide: [http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy). So try your machine with all extra *options commented out. It's worth a shot. This sticks out as well:
(**) NVIDIA(0): Disabling RENDER acceleration
*Although it does say this:
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
*I only wanted to look at your auth.log to see if some1 was hacking your box and causing these crashes. That log shows nothing and you're not being hacked.
*Your xsession-errors doesn't show anything either?

I can't really tell you what to do here? How did you install the Nvidia Drivers? You could try to use Envy, you it first to uninstall nvidia drivers. then shutdown and restart, then use Evny to install the drivers. Then see what happens or here is a guy who has the same card as you and got beryl working, check it out: [http://www.linuxquestions.org/questions/showthread.php?t=521743&page=2](http://www.linuxquestions.org/questions/showthread.php?t=521743&page=2)
good luck

---

### Post by hizaguchi on 2007-03-02
I don't understand system logs at all, but my computer's motherboard was going bad, causing the hard drive to occasionally fail to read and write (could be similar to your "confused" cdrom?).  99.99% of the time, Windows would just ignore the problem and run fine, but Linux froze up hard every 5 minutes or so.  I was confused until I installed FreeBSD, which caught the problem and kept running, but threw up a very descriptive error message on tty1.  If that sounds like it could be related to your problem, you might try installing a BSD and see what happens. :confused:

---

### Post by bigken on 2007-03-02
just batting th  ball about I here have you tried another video adapter even a pci one would do I have had boards in the past that have frozen and found that it has being a bad agp or pci-e port its worth giving it a shot :)

---

### Post by dannyboy79 on 2007-03-02
well if he doesn't have the problem without Beryl and WITH the ubuntu nv driver, than it's not a hardware issue. It's a driver issue along with the composite or xgl of Beryl.

---

### Post by bigken on 2007-03-02
ye I agree as he said there are no probs in windows so its driver issue 
I would remove the old drivers and reinstall em but leave all the berly ect 
alone see how it goes :)

---

### Post by HoMe_CaNiBaL on 2007-03-02
dannyboy79, thanks for your reply.


At Xorg.conf i have:
**Option "RenderAccel" "0"*
i've test this to see i my computer continue freezing, but, it's the same.

Today i test start up my system without one of my dvd driver, and i see that my dvd-rom asus show's up 
**hdd: cdrom_pc_intr: The drive appears confused (ireason = 0x01*

The HT, i dont understand...i installed linux-686, i must install linux-686-smp? I thought it was the kernel, so i installed linux-686.

The eth0, i can disable, because i love my d-link ethernet card. Can be from ethernet0? Onboard ethernet? I disabled it.

At Feb 28, the system freezes at 4.50 am, and i herd reset computer at 1.15 pm, at this time i start using computer again...

I will try tonight testing without my dvd-rom Asus and see what happen!

I'm tired from freezes, and i dont want get back to windows xp.

Thanks

---

### Post by dannyboy79 on 2007-03-02
> **HoMe_CaNiBaL said:**
> dannyboy79, thanks for your reply.


At Xorg.conf i have:
**Option "RenderAccel" "0"*
i've test this to see i my computer continue freezing, but, it's the same.

Today i test start up my system without one of my dvd driver, and i see that my dvd-rom asus show's up 
**hdd: cdrom_pc_intr: The drive appears confused (ireason = 0x01*

The HT, i dont understand...i installed linux-686, i must install linux-686-smp? I thought it was the kernel, so i installed linux-686.

The eth0, i can disable, because i love my d-link ethernet card. Can be from ethernet0? Onboard ethernet? I disabled it.

At Feb 28, the system freezes at 4.50 am, and i herd reset computer at 1.15 pm, at this time i start using computer again...

I will try tonight testing without my dvd-rom Asus and see what happen!

I'm tired from freezes, and i dont want get back to windows xp.

Thanks

ok, well I was suggested that you comment out (which means to disable) all the extra options in your xorg.conf completely not just the 1, then restart and see if that helps.

yes, you need the -SMP kernel if you're using Dapper, if you're using Edgy than you want the generic kernel as that's what has the support for HT.
it has been posted before, here's what it said:
** For all those who visited this forum thread looking to use processor specific kernels, the current version (6.10 default/generic) has made the k7/686/686-smp kernels OBSOLETE (only for upgrades). I think it applies to all the other processor specific kernels.

**As proof, refer to the "uname -a" output (in Ub 6.10). It says SMP, i686 in the default installation.
Also In Synaptics Pkg Mgr (Ub 6.10), search for "linux-k7". It will describe as OBSOLETE by linux-generic. Same for linux-686/linux-686-smp.

so, install the generic kernel and see if your syslog stops showing that HT is disabled.

if eth0 is your onboard interface, just disable it either in the bios or in ubuntu interface file by commenting it out if you're not using it.

you still haven't answered me, how did you install the nvidia driver 9746?? if you didn't use envy, than this time use it. first uninstall, than install. try that. I hardly doubt it's your cd-rom or dvd-drive but you can try what you'd like.

---

### Post by HoMe_CaNiBaL on 2007-03-02
> **dannyboy79 said:**
> 
you still haven't answered me, how did you install the nvidia driver 9746?? if you didn't use envy, than this time use it. first uninstall, than install. try that. I hardly doubt it's your cd-rom or dvd-drive but you can try what you'd like.

i install using beryl script..

EDIT: I'm using Edgy. When i do 'uname -r' give me '2.6.17-11-generic', but i installed linux-686.

i'm try tonight, install nvidia driver using envy and

---

### Post by dannyboy79 on 2007-03-02
> **HoMe_CaNiBaL said:**
> i install using beryl script..

EDIT: I'm using Edgy. When i do 'uname -r' give me '2.6.17-11-generic', but i installed linux-686.

i'm try tonight, install nvidia driver using envy and

yeah, there's your problem. Edgy has depricated using the 686 or SMP kernel. THey have just put the support in the generic kernel, you want to reinstall that one for HT support.

---

### Post by HoMe_CaNiBaL on 2007-03-02
so, i reinstall linux using a new hdd, to prevent not loosing anything.

i leave the generic, and use envy script to install nvidia driver, and install beryl, and see what happen.

thanks

---

### Post by dannyboy79 on 2007-03-02
> **HoMe_CaNiBaL said:**
> so, i reinstall linux using a new hdd, to prevent not loosing anything.

i leave the generic, and use envy script to install nvidia driver, and install beryl, and see what happen.

thanks

NO, don't reinstall your ubuntu! you just want to go into synaptic and reinstall the generic kernel is what I am saying. you don't want to be using the 686-smp kernel cause for edgy they depricated those kernels so I don't know what you got as far as cpu support? just reinstall the generic kernel and you should be good as far as HT goes.

---

### Post by HoMe_CaNiBaL on 2007-03-02
Installing linux kernel generic will uninstall linux 686?

I hope that was the problem...

---

### Post by dannyboy79 on 2007-03-02
no, it will just make the linux-generic first in the grub menu (which as I said is optimized for your processor). if you want to remove the 686-smp kernel, you need to do sudo aptitude remove linux-686-SMP and that should remove it both from your computer and from your grub menu. Like I said, I dought that was why your computer is freezing, I am sure it's a driver and or hardware issue. reinstall nvidia using envy and tell me how it goes. You could also try out Ubuntu's nvidia driver, go to your /etc/X11/xorg.conf file and change driver   "nvidia" to driver   "nv" and see if beryl still works and no freezes? then that would tell you it's something to do with the nvidia driver and your hardware.

---

### Post by HoMe_CaNiBaL on 2007-03-02
Beryl doesnt work with nv driver. I try it in other machine!

In grub, linux-generic it is the first, i dont have (like dapper) 386 ou 686 kernel...Only appears me the generic.

When i work with Dapper, i install nvidia driver with Envy script, and i have freezes too...

---

### Post by dannyboy79 on 2007-03-02
> **HoMe_CaNiBaL said:**
> Beryl doesnt work with nv driver. I try it in other machine!

In grub, linux-generic it is the first, i dont have (like dapper) 386 ou 686 kernel...Only appears me the generic.

When i work with Dapper, i install nvidia driver with Envy script, and i have freezes too...

why did you tell me you're using the 686-SMP kernel then???? Well, obviously it's a hardware/driver/beryl issue than. Not sure what to tell ya then???? did you go to that l;ink I provided of the guy who has the same card as you working with beryl or wasn't he running beryl?

---

### Post by HoMe_CaNiBaL on 2007-03-02
dannyboy79, i do everything you said.

Uninstall Linux-686, reinstall linux-generic, envy script running, uninstall nvidia driver and then install nvidia driver.

Beryl running, and guess what!

FREEZE!

I test my memory using memorytest 86, and no errors.

I'm on metacity now, just for testing.

Help me please... I see Windows XP at the end of the tunel, and i'm on eyes closed.

---

### Post by bigken on 2007-03-03
you have to forget about beryl change your driver to vesa and see if your machine still freezes you need to eliminate the cause of the problem before you even think of running beryl I would also remove the ram chips one at a time and see what happens ram tests dont always find any faults

---

### Post by dannyboy79 on 2007-03-03
well if you can't run beryl doesn't mean you have to go back to winbloz does it!!! yeah, if you have more than 1 ram chip, take 1 out and test the other and so on and so forth. have you looked at launchpad to see if there are any bugs with your hardware? what about compiling your own kernel? there are still many thing to try if you have to have beryl. what about trying compiz or whatever the other 1 is that is similar to beryl. good luck

---

### Post by HoMe_CaNiBaL on 2007-03-03
My machine is running on metacity for now.

I dont know if it is stable, i'm working, but the computer its turned on since last night...

---

### Post by HoMe_CaNiBaL on 2007-03-03
```
homecanibal@canibal-desktop:~$ uptime
 00:24:27 up 22:32,  3 users,  load average: 0.31, 0.28, 0.15
```

22hours running on metacity.

Compiz... I try it out after i see what problem my computer have.

Thanks

---

### Post by HoMe_CaNiBaL on 2007-03-05
Hi there.

I find my problem... At sunday, i test all my hardware. 

My System         -            To Test 
Pentium 4 2.8 HT -            Pentium 4 3.0 HT
P4c800 dlx         -              P4c800 dlx
2x 512Mb DDR -               4x 512Mb DDR (4modules)
GF 6600GT 128mb -       GF MX 440 64mb

I test one by one, and all tests i had the same problem... FREEZES.

So i put my system up, and start testing...

I configure my BIOS and guees what. FULLY stable. I dont understand, i have the same settings, but i cant understand whats different to make my system fully stable.

I say that because yesterday i've been working all day, and never  freeze, today, the machine still working without any freeze.

At this moment, i'm working with Xorg 7.2, and i like it. The machine is fast, but after a few hours, xorg it occupies alot memory, 400/500mb... How can i solve that?

Thanks to everyone that help me.

---

### Post by dannyboy79 on 2007-03-05
could you maybe explain what you mean when you say, "So i put my system up, and start testing...". I don't know what that means?? Also, you probably want to start a new thread and title it appropriately, obviously put "Xorg 7.2, a memory hog?" in the title or something similar. Also, are you using Fiesty? I didn't think Xorg 7.2 made it in Edgy, if you're using Fiesty, than you want to be sure to post it in the Fiesty section as Fiesty isn't released yet so it's really only for experiementers and developers, so most likely you won't get much support help as it's not supported yet since it's still in development. I mean, you'll I am sure get help from other Fiesty users. Did you try google yet???

---

### Post by HoMe_CaNiBaL on 2007-03-05
> **dannyboy79 said:**
> could you maybe explain what you mean when you say, "So i put my system up, and start testing...". I don't know what that means?? Also, you probably want to start a new thread and title it appropriately, obviously put "Xorg 7.2, a memory hog?" in the title or something similar. Also, are you using Fiesty? I didn't think Xorg 7.2 made it in Edgy, if you're using Fiesty, than you want to be sure to post it in the Fiesty section as Fiesty isn't released yet so it's really only for experiementers and developers, so most likely you won't get much support help as it's not supported yet since it's still in development. I mean, you'll I am sure get help from other Fiesty users. Did you try google yet???

"put my system up" = turn on my system again, with my components.

Xorg 7.2 its from Trevino repository, i will try go back to xorg 7.1...

I'm using Edgy.

---

### Post by dannyboy79 on 2007-03-06
OK, so wait, this whole time you have been trying to use Xorg 7.2 with Beryl??? There might be your problem. I would set your Edgy back to the way it was at time of install, obviously minus software like samba, ssh, or things like that shouldn't affect graphics issue but for sure upgrading your xorg would. Try to use the default xorg with edgy and beryl and see what happens. good luck

---

