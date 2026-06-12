---
title: "Inten Graphics 4500HD- X3 Game(Linux) on Ubuntu 13.04"
date: 2013-06-06
forum: Gaming &amp; Leisure
---

### Post by Saibagen on 2013-06-06
[COLOR=#333333][FONT=UbuntuRegular]Dear Community,


Yesterday I tried to install_ X3: Reunion_( Linux Distribution) on **Ubuntu 13.04(32 bit)**. My computer(**Notebook/Laptop**) uses the_** Intel Graphics 4500HD**_. 
Ubuntu's driver *alternative- installed:*** Intel® Ironlake Mobile x86/MMX/SSE2** (This driver was there, when I installed Ubuntu. I also used the Intel Updater, but the Intel Updater keeps informing me, that I already have the newest driver installed) 
My first question:
***Is my graphics driver correct?***[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I ask because, after I installed _X3: Reunion_( Linux Distribution) the game hasn't been able to start. I have already searched the Internet **for many many hours**. 
Even so I haven't been able to find any answer to the error- messages I get starting X3(check below). I am not sure if it's my driver or a bad game install( I already tried to re-install the game) I have heard that there are others who experienced similar issues on Linux, trying to install games.
Maybe someone can help me?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]When I start the game launcher, I get this error:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Gtk-WARNING **: Failed to load module "liboverlay-scrollbar.so": liboverlay-scrollbar.so: cannot open shared object file: No such file or directory
libGL error: failed to load driver: i965
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
libGL error: failed to load driver: swrast
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
^Cx3 2.5.01-sse2, built for i386
**Let's call it, Error 1.**
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]When I click on Start Game I get this error: 

[/FONT][/COLOR]
{
    [0xb7772400]
    /lib/i386-linux-gnu/libc.so.6(vsprintf+0xa4) [0xb6bce9f4]
    x3() [0x817ed00]
    x3() [0x81539d5]
    x3() [0x81773b2]
    x3() [0x80cc251]
    x3() [0x81515fa]
    /lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xf5) [0xb6b7f935]
}
[COLOR=#333333][FONT=UbuntuRegular]**Let's call it, Error 2.**[/FONT][/COLOR]
[FONT=UbuntuRegular][COLOR=#333333]I use Ubuntu [/COLOR][/FONT]**13.04 ( 32BIT ARCHITECTURE)** 
[FONT=UbuntuRegular][COLOR=#333333]That's what I know. [/COLOR][/FONT]
[FONT=UbuntuRegular][COLOR=#333333]I am obviously new to the Linux World. Well, I used Linux in the 90' when Microsoft wasn't the Monopolist. But, Linux changed. I love the new Ubuntu Interface( Dashes). I just started to learn the basics of the Terminal- never thought I'd say this( I love Desktop Unities Desktop environment.), but the Terminal can make life easier, sometimes ^^ [/COLOR][/FONT]
[COLOR=#333333][FONT=UbuntuRegular]All I need is this game..... I'd like to play it once in a while. But, I'm not experienced enough to solve these errors. One more thing. Even that I get "Error 1" when opening the launcher, the launcher itself runs fine. When I click on "Start game" I actually get two messages. Error 2 in the terminal and the following message in the launcher(lgp): Error opening video. There is no VESA driver installed, your graphics adapter or the VESA driver doesn't support the resolution. Further information can be found in the manual.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Well, I already read the "manual"( I wouldn't call it a manual, though). I thought VESA was used in Nvidia Graphics? xD
I chose the 1600X900 resolution- my native resolution. - Yes, I already tried to change the resolution. Once I start the game with another resolution, the error disappears. But the game does not work![/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]So, basically. What are these errors?( Error 1, and 2) Is my Graphic Driver correct? ( Intel 4500 HD) Why doesn't this game start? ( X3: Reunion)
The TOP question: How to run the game? 
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Can You help me? I'd be glad, if someone would try to help me. I am sick of trying, trying and trying. I need an expert, a freak, a Linux Doctor! Is it you?^_^
Dear Doctors: Try to be precise and understanding. When you post a Terminal command, post it like this:
Bla bla bla, you have to type in Sudo. This means you have to type in:
Sudo sh bla bla et cetera

This will make it easier ^^ 

Thanks in advance for any help! \(^_^)/[/FONT][/COLOR]

---

### Post by Cvxcvgg on 2013-06-06
I'm not sure if this is the problem, but I noticed that Error 1 said "built for i386" and something about a failure to load i965. I read that it is related to the architecture, but it may just be a driver issue after all.

---

### Post by Saibagen on 2013-06-22
Yes, thank you.
I already mentioned that I run Ubuntu 32 architecture, so this is not the case. The library is fine.
Whatever. This topic has no future as nobody knows anything.
Thank you.
Goodbye!

---

### Post by Ranko Kohime on 2013-06-22
i965 has nothing to do with CPU architecture; it is the Intel integrated graphics found in older examples of the Celeron processor.

Now, Cvxcvgg, when I search for X3, (I hadn't heard of it before), Wikipedia tells me that it's from 2005.  Which means it may be hard linked against libraries which have been updated, or no longer exist in 13.04.

Please run "lshw -c video", and look for the bolded line below:
```
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
**       configuration: driver=i915 latency=0**
       resources: irq:42 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:5000(size=64)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```
I run HD3000 graphics, so my driver will be different, but you should see the i965 referenced.  If not, then that is the problem you'll need to resolve first.

---

### Post by oldfred on 2013-06-22
Is this a new computer? As those require 64bit and the newest drivers. But then an old game may not work?

       Intel Haswell - Linux support June 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU](http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU)

---

### Post by Ranko Kohime on 2013-06-24
> **oldfred said:**
> Is this a new computer? As those require 64bit and the newest drivers. But then an old game may not work?

       Intel Haswell - Linux support June 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU](http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU)
The OP's first post includes the term "Ironlake", which is an older Intel codename, ca. 2010, and two generations from the current bleeding edge.

---

### Post by dannyboy79 on 2013-06-26
> **Saibagen said:**
> Yes, thank you.
I already mentioned that I run Ubuntu 32 architecture, so this is not the case. The library is fine.
**Whatever. This topic has no future as nobody knows anything.**Thank you.
Goodbye!
why come here and ask a question if you're going to turn around and post what you did? If you want help, we'll first need to understand what GPU you're using. Please return the following information. 
```
lspci
```

```
lshw -class display
```

when you give us the above information we may be able to better assist you.

---

