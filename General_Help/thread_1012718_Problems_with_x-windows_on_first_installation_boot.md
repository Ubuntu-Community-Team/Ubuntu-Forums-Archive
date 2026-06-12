---
title: "Problems with x-windows on first installation boot"
date: 2008-12-16
forum: General Help
---

### Post by Willberg on 2008-12-16
Hi there, I am trying to install  Ubuntu (ubuntu-8.10-desktop-i386) using wubi on to my Dell Inspiron 9400 laptop. 2 gigs of ram, 13 gigs free space before starting. ATI X1400 graphics card.

I have previously installed 8.04 the normal way without (m)any issues, to an external hard drive a few months ago.

The windows part of the wubi installation goes fine, and asks that I reboot, which I do. However, after selecting it in the windows-pick-your-OS-screen, and it says that it's loading some bootloader, it just hangs. This seems to be always the case if I restart my PC.

If I turn my PC right off, and then on again, I get a little further.

When I try a normal installation or a "live CD", I get the Ubuntu graphical loading screen, then the screen goes very black (somehow blacker than it was before!) and my PC does nothing.

When I try the verbose, or the safe graphics, or the power-fix-thingy one, I get complaints that it couldn't start an x-server after 60 seconds, and I am dumped to a prompt. Yes, even when choosing the safe graphics mode.

I know my graphics card isn't the most... standard thing, but it worked Just Fine (tm) when I installed the last version of Ubuntu from CD, so it seems odd (and is frustrating) that it doesn't work this time.

I have tried adding irqpoll and all_generic_ide to the second lines of all the boot options. I have no external hard drive attached (well, I turn it off).

Please... I don't want to have to upgrade to Vista ever... I need to get this working. 

Any help that anyone can offer me would be greatly appreciated, cheers

-Will

---

### Post by Willberg on 2008-12-16
*sigh*

It was because I had my second monitor plugged in. I'm 99% sure that this wasn't an issue when installing 8.04 from CD.

I'm afraid I know naught about the finer points of creating linuxes, but is there someone who would appreciate me replicating the error and sending an xorg log file to them?

---

### Post by ago on 2008-12-19
> **Willberg said:**
> *sigh*

It was because I had my second monitor plugged in. I'm 99% sure that this wasn't an issue when installing 8.04 from CD.

I'm afraid I know naught about the finer points of creating linuxes, but is there someone who would appreciate me replicating the error and sending an xorg log file to them?

Yes please, submit a bug in launchpad.net, check first whether the same issue was already reported.

---

