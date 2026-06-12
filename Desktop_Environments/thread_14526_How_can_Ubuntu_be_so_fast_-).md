---
title: "How can Ubuntu be so fast? :-)"
date: 2005-02-08
forum: Desktop Environments
---

### Post by tnilsson on 2005-02-08
I have mostly been a Mandrake Linux user. It is quite fast compared to
Fedora Core 3.
I have noticed that Ubuntu is so much faster than Mandrake on the Pentium 3 platform. Ubuntu is not optimized for 586 nor does it use prelink... how can it be so
fast?

Regards,
Tomas
 =D>

---

### Post by Adrenal on 2005-02-08
Its called magic
...n00b

---

### Post by paul cooke on 2005-02-08
[QUOTE=tnilsson]I have mostly been a Mandrake Linux user. It is quite fast compared to
Fedora Core 3.
I have noticed that Ubuntu is so much faster than Mandrake on the Pentium 3 platform. Ubuntu is not optimized for 586 nor does it use prelink... how can it be so
fast?

Regards,
Tomas
 =D>[/QUOTE]

and that's with the stock 386 kernel still??? you can upgrade to the 686 kernel for running on the PIII platform quite easily...

sudo apt-get install linux-686 (only for x86 machines---check uname -a to compare)

and reboot after that finishes succesfully...  :D

---

### Post by tnilsson on 2005-02-08
I am running with the i686 kernel now... and it is even faster.
The Ubuntu Gnome style looks so nice! :-)

---

### Post by rufius on 2005-02-08
[QUOTE=tnilsson]I have mostly been a Mandrake Linux user. It is quite fast compared to
Fedora Core 3.
I have noticed that Ubuntu is so much faster than Mandrake on the Pentium 3 platform. Ubuntu is not optimized for 586 nor does it use prelink... how can it be so
fast?

Regards,
Tomas
 =D>[/QUOTE]
 I've used Mandrake, Redhat, and Fedora in the past and the general performance of the RPM based distros seemed a bit *floated*. For a while I was using Mepis, another debian based distrobution and it was far faster than the said distros. Ubuntu is the same way and I suspect its because of the debian base. :)

---

### Post by recmar on 2005-02-08
Well, my ubuntu is even slower than WinXP. I've installed it on my laptop (AMD Athlon XP 2400+, graphics VIA on-board, 768 RAM) and it runs veerrry slow. I really don't know where the problem is. Anybody can help me.?

---

### Post by brainstuff on 2005-02-08
Hi
I'm a noob and proud! I'm pretty sure I'm running the .386 kernel on a Celeron 500 Thinkpad with 128Mb...D'y'all reckon this is the right one for me? Seems to run nicely enough considering the weakness of the machine.
cheers
brain

edit: to the chap with the Athlon and slowness problem - can't help, but I had a similar problem with  Ubuntu running slower than Win2K on another (admitedly pretty slow) lappy I have - Vaio Pentium 300 with 128Mb of RAM. Did some basic tests like how fast Opera and Word / Open Office Word started. Win2K won hands-down on that machine, so my Dad ended up staying with M$ this time round :(

---

### Post by Poldi on 2005-02-08
[QUOTE=recmar]Well, my ubuntu is even slower than WinXP. I've installed it on my laptop (AMD Athlon XP 2400+, graphics VIA on-board, 768 RAM) and it runs veerrry slow. I really don't know where the problem is. Anybody can help me.?[/QUOTE]

ahem, what exactly do you mean with slow here? 

slow / fast is pretty meaningless if you don't specify a usecase for comparison. the regular click-response I get from operating Gnome desktop is rather instantly or nearly so (on a P2-266 with a 2,5 MB NeoMagic graphic card, 256MByte RAM) so you must be comparing some kind of applications... this might make sense where you use the same applications like, say, on different Linux distributions (applying the same filter in GIMP) but what are you comparing between WinXP and Ubuntu?

copying files might be a fair test between the two, but only for the filesystems, whatever it's worth. I cannot come up with a regular real-life task that would not be executed instantly on your killer-machine, be it on WinXP or Ubuntu.

now gaming might be an issue...

will you clarify what exactly you are talking about?

kind regards,
Carsten

---

### Post by az on 2005-02-08
Mandrake and Fedora kernels are patched with crap.

---

### Post by tnilsson on 2005-02-08
My hardware configuration on my slowest machine is:

IBM Thinkpad T20, P3 700 MHz, 256 MB ram.
I feels like a new laptop when I am running Ubuntu... fast!!
I have never seen openoffice start so fast and everything else is fast.

 =D>

---

### Post by recmar on 2005-02-08
Screen drawing is going very slow, i get all kinds of artifacts while draging windows around and general mouse responce seems slugish. I thought that maybe i wasn't using the correct video driver but anything else than vesa wan't work with my laptop. Changing usage of kernel frame buffer doesn't work as well.

Upon investagating i have noticed that simply moving a window brings my CPU utilization up to 100%, which makes me think that the card is doing absolutly nothing.

---

### Post by nocturn on 2005-02-08
[QUOTE=recmar]Screen drawing is going very slow, i get all kinds of artifacts while draging windows around and general mouse responce seems slugish. I thought that maybe i wasn't using the correct video driver but anything else than vesa wan't work with my laptop. Changing usage of kernel frame buffer doesn't work as well.

Upon investagating i have noticed that simply moving a window brings my CPU utilization up to 100%, which makes me think that the card is doing absolutly nothing.[/QUOTE]


Hmmm, maybe someone with a similar card can help you.  I bet the video driver is the cause of your problems, VESA is dog slow...

If there is no free driver around, you can consider snappy (a middleware driver for Xfree and Xorg).

---

### Post by kamstrup on 2005-03-09
[QUOTE=recmar]Screen drawing is going very slow, i get all kinds of artifacts while draging windows around and general mouse responce seems slugish. I thought that maybe i wasn't using the correct video driver but anything else than vesa wan't work with my laptop. Changing usage of kernel frame buffer doesn't work as well.

Upon investagating i have noticed that simply moving a window brings my CPU utilization up to 100%, which makes me think that the card is doing absolutly nothing.[/QUOTE]
 Which exact card do you have, what chipset does it use? System->Admin.->Device Manager, should tell you. When you know this try googling around...

---

### Post by cliff58 on 2005-03-09
Well, going back to tnilsson's question, I think that most of what he had been using ran on the 2.4 or earlier kernel. The 2.6 kernel is quite an improvement as far as speed goes, at least in my limited experience. Plus Ubuntu seems to have a little less going on in the background, and that's always a plus.  :-D

---

### Post by gylf on 2005-03-09
[QUOTE=recmar]Screen drawing is going very slow, i get all kinds of artifacts while draging windows around and general mouse responce seems slugish. I thought that maybe i wasn't using the correct video driver but anything else than vesa wan't work with my laptop. Changing usage of kernel frame buffer doesn't work as well.

Upon investagating i have noticed that simply moving a window brings my CPU utilization up to 100%, which makes me think that the card is doing absolutly nothing.[/QUOTE]

Is powernowd enabled?  If so I would try disabling it and just see if the CPU throttling is being goofy.

---

### Post by mseney on 2005-03-13
I was using Ubuntu Hoary 5.04 on a Pentium III 800Mhz 256K L2 Cache machine and realized I could use the 686 Kernel and noticed a difference when changing from the 386 Kernel to the 686. Now are all the packages I'm getting for the 386 Platform? How does using these compare to say using from the source like a Gentoo system? One last question, I switched motherboards, RAM, and CPU. Here is the before and after:

[Before]
Intel Pentium III 800 Mhz 256K L2
Maxtor 80G ATA133 running @ ATA66 due to older MBoard
512MB PC100
NVIDIA RIVA TNT2

[After]
Intel Pentium 4 1.7 Ghz 256K L2
Maxtor 80G ATA133 running @ ATA100 due to the newer MBoard
1GB PC133
Matrox 32M AGP Dual-Head

The Questions??? 
How does changing chipset affect the already built kernel and programs? Would I get more out of the newer hardware by reinstalling Ubuntu all over again?

---

### Post by kamstrup on 2005-03-13
[QUOTE=mseney]
The Questions??? 
How does changing chipset affect the already built kernel and programs? Would I get more out of the newer hardware by reinstalling Ubuntu all over again?[/QUOTE]

No. Sticking to i686 packs over i386 gives you a little edge, but as long as you don't go about and *compile* stuff yourself, you won't get further optimizations. Your old PIII is also i686 compliant and Hoary has installed the proper i686-packages, where applicable, for you already.

There might be P4 kernels floating around in the repos? They could give you another speed boost.

FIXME: libc and kernels are the only architecture-optimized packs around? - I'd love to see a i686 X.org package, like Dropline has :-)

---

### Post by bored2k on 2005-03-13
I had to load XP to do some semi-professional dvd authoring on Sony Architect . Boy is Ubuntu fast ... I just realized that O_x

edit  - also, the forum's fonts/layout looks UGLY here :O.

---

### Post by Dana on 2005-03-14
What does this tell me as a newbie?

uname -a

Linux thinkpad 2.6.8.1-3-386 #1 Tue Oct 12 12:41:57 BST 2004 i686 GNU/Linux

---

### Post by bored2k on 2005-03-14
[QUOTE=Dana]What does this tell me as a newbie?

uname -a

Linux thinkpad 2.6.8.1-3-386 #1 Tue Oct 12 12:41:57 BST 2004 i686 GNU/Linux[/QUOTE]
 If you know that command youre not newbie :P
> man uname
NAME
       uname - print system information

SYNOPSIS
       uname [OPTION]...

DESCRIPTION
       Print certain system information.  With no OPTION, same as -s.

       -a, --all
              print all information, in the following order:

       -s, --kernel-name
              print the kernel name

       -n, --nodename
              print the network node hostname

       -r, --kernel-release
              print the kernel release

       -v, --kernel-version
              print the kernel version

       -m, --machine
              print the machine hardware name

       -o, --operating-system
              print the operating system

       --help display this help and exit

       --version
              output version information and exit


---

### Post by Dana on 2005-03-14
Okay, technically I used a Linux distro for a couple years... several years ago. But I have forgotten more than I remember.  :???: 

Thanks for the additional information... guess I could have gotten that for myself but it was late and I was no longer thinking.

Dana

---

### Post by mseney on 2005-03-14
[QUOTE=Dana]What does this tell me as a newbie?

uname -a

Linux thinkpad 2.6.8.1-3-386 #1 Tue Oct 12 12:41:57 BST 2004 i686 GNU/Linux[/QUOTE]
[B]
That is telling you that you have a Kernel for the 386 Platform but are running on a 686 (Athlon, Intel Pentium III/4) If you try a 686 Kernel you will get better performance.[/B]

---

### Post by Dana on 2005-03-14
I'll probably wait now until Hoary is released to move to the i686 kernel. I don't recall, was there an option to use that kernel during the Warty installation? At one point a few weeks ago I was going to do this but couldn't identify the correct kernel... so I let it drop for the time being.

---

### Post by Miguel on 2005-03-14
Hi folks,

I'm on a Centrino laptop (Pentium-M @ 1,7GHz w/ 2Mb L2 cache). I'm using the latest 686 warty kernel (security reasons). Would I notice any increase in performance if I recompiled the kernel for the Pentium-M processor (I would also uncheck all things I'm sure I won't use). Or an improvement in battery life? 

It's a shame I should build the ATI drivers on my own after that.

Oh! Now that I'm on it, both GDM and Gnome are loading way slower than when I installed Warty. Has it anything to do with having IceWM (apt-get) and XFce 4.2 (from source) installed?

Thanks a lot

---

### Post by mseney on 2005-03-14
[QUOTE=Dana]I'll probably wait now until Hoary is released to move to the i686 kernel. I don't recall, was there an option to use that kernel during the Warty installation? At one point a few weeks ago I was going to do this but couldn't identify the correct kernel... so I let it drop for the time being.[/QUOTE]

**I personally never tried out Warty but on the Hoary install there wasn't an option to pick a 686 kernel, it defaulted to install the 386 kernel. It's not really much work to upgrade to the 686 afterwards since everyone takes approx 1-2 weeks getting everything setup the way they want it. I've done some reading and came to the conclusion that the speed enhancements one would gain from installing packages from source really isn't much (Not worth it). I doubt any of us would notice much difference if we were using say gaim installed from source as opposed to using the 386 .deb package. The kernel however is a different story so in that case get the one specific to your platform. Also a correction to an earlier post, use k7 for AMD Athlon and 686 for Intel PII,III, and 4 Processors. Best way to find the kernel you need is Synaptic. I use Synaptic sometimes and other times apt-get. Both work great!**

---

### Post by jdong on 2005-03-14
[QUOTE=tnilsson]I have mostly been a Mandrake Linux user. It is quite fast compared to
Fedora Core 3.
I have noticed that Ubuntu is so much faster than Mandrake on the Pentium 3 platform. Ubuntu is not optimized for 586 nor does it use prelink... how can it be so
fast?

Regards,
Tomas
 =D>[/QUOTE]

Hmm, I want to ask something: Why's Fedora so slow??

I haven't used Mandrake in a while, but Fedora has always been slow and laggy!

Ubuntu doesn't optimize much -- -march=i486, -mcpu=pentium4, no -O AFAIK.

BTW, 586 optimization actually makes code run SLOWER on i686's.

---

### Post by bored2k on 2005-03-14
[QUOTE=jdong]Hmm, I want to ask something: Why's Fedora so slow??

I haven't used Mandrake in a while, but Fedora has always been slow and laggy!

Ubuntu doesn't optimize much -- -march=i486, -mcpu=pentium4, no -O AFAIK.

BTW, 586 optimization actually makes code run SLOWER on i686's.[/QUOTE]
 "BTW, 586 optimization actually makes code run SLOWER on i686's."

Does that mean I should use linux-386 instead of linux-686 ? howcome ?

---

### Post by Miguel on 2005-03-15
I think it means that, given the same kernel, i586 optimized packages run slower than i386 packages on i686 machines. And probably that a i586 compiled kernel is slower than a i386 kernel on the same i686.

I also think you should stick with your linux-686.

---

