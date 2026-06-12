---
title: "Restart prevents Windows from booting!"
date: 2012-09-20
forum: Desktop Environments
---

### Post by archangel2003 on 2012-09-20
First off, we have to keep and use Windows because some programs are not Ubuntu friendly, (the wife uses it for the taxes as well as the office and I need it for the CADD programs) and there are a few, very few, aspects that I like with Windows, so I keep it around.

Second, I will be seeking help when fixing this at the college where I'm taking classes. My computer operating system kung fu is anything but strong.
I just need to be able to point them in the right direction as Ubuntu has yet to break into Joliet Junior College.

First issue (almost the same as the second issue).

On my old computer (Compaq Presario) my daughter installed Ubuntu 10.04 LTS, and it was restarted by the wife from Ubuntu rather than shutting down and restarting as I always do.

That act seemed to have BUGGERED things up!

Now when we try to start Windows the Windows swirling squares start to come together like it's booting normally, then the screen jumbles, goes to purple and then Ubuntu is starting up.

That issue remains a P.I.T.A. as the programs the wife needs are not accessible until it get's fixed.

Now, the second issue is on my new Toshiba running Ubuntu 11.10.
We (the "computer savvy but new to Ubuntu" guy who was helping me get it installed) did the same thing shortly after installing11.10, while looking and tinkering around with it.
It took a few days of fighting the system to get it to where Windows would boot up again.

So I assume the "restart" option is deadly to the Windows boot up?
If so, they should fix that so the option is not available if there is Windows on another partition.

The remaining issue (that I can live with for now) is that now when I'm booting up Ubuntu, there is a real long "purple screen" pause after selecting the Ubuntu operating system that was not there before the restart issue killed the Windows boot up.
After the long pause the password and screen start up happens quickly like normal.
It's so long that it takes as long as Windows to boot up so I can no longer brag about the Ubuntu's superior boot up speed over Windows.

Oh and while I'm here, if I convert to 12.04 LTS, can I keep and leave everything I have with 11.10 there, or do I need to treat is like a new partition and SAVE EVERYTHING OFF THE 11.10 to reinstall into the 12.04 LTS?

---

### Post by jrog on 2012-09-20
Only responding to a few parts here (the ones that I can immediately address).

> **archangel2003 said:**
> So I assume the "restart" option is deadly to the Windows boot up?
If so, they should fix that so the option is not available if there is Windows on another partition.
No, it isn't, or at least it shouldn't be. I have never had the sort of issue you are indicating when dual-booting, and I've never heard of anyone else having that issue, either. It should be just fine to choose to restart on Ubuntu or Windows and then boot into the other OS.

> **archangel2003 said:**
> The remaining issue (that I can live with for now) is that now when I'm booting up Ubuntu, there is a real long "purple screen" pause after selecting the Ubuntu operating system that was not there before the restart issue killed the Windows boot up.
After the long pause the password and screen start up happens quickly like normal.
It's so long that it takes as long as Windows to boot up so I can no longer brag about the Ubuntu's superior boot up speed over Windows.
How long are we actually talking about here, when you say "real long?" 

In any case, there may be ways to get around this, but I'm mostly guessing as to the source of the problem. When you boot up and get to the grub boot menu, use the arrow keys on your keyboard to highlight the Ubuntu boot line, then hit 'e' on the keyboard (to edit the boot information), then arrow down to the line that begins with "linux" and, at the end of that line, add "nomodeset" (without the quotes). You might also try adding "nosplash", too. Let us know if that speeds things up. (It might also be helpful to know what graphics card you have in this machine.)

> **archangel2003 said:**
> Oh and while I'm here, if I convert to 12.04 LTS, can I keep and leave everything I have with 11.10 there, or do I need to treat is like a new partition and SAVE EVERYTHING OFF THE 11.10 to reinstall into the 12.04 LTS?
Upgrading to 12.04 will (obviously) change the versions of the programs you have installed, but otherwise, you should be able to keep everything (e.g., the files in your home folder can be left as it, etc.). It's still best to back-up everything first, though!

---

### Post by archangel2003 on 2012-09-20
As for long, after I select the Ubuntu rather than Windows from the selection screen, it is about 25 seconds of blank purple screen before the password screen starts to appear.

It used to be only a few short seconds before the password screen came up and I was in and surfing the net in something like 15 or 20 seconds total.

---

### Post by archangel2003 on 2012-09-21
I'm going to try the "nomodeset" without the " " and will see.
If I can still boot up, I'll try the "nosplash" as well.

If you don't see a post at least an hour after this one, things got worse and I cant boot up and get on line at all.

---

### Post by archangel2003 on 2012-09-21
I added the nomodeset and it screwed up the screen ratio, all the icons were HUGE and the AWN blew up!
For the next bootup the nomodeset was gone and things returned to normal.

Here is a picture of the boot menu.

I do see a "splash" in the menu.

I wonder is there is something there that can be deleted?

BTW, any changes there seem to disappear as soon as we shut down and restart.

Also, it takes 25 seconds or longer before the plain blank purple screen goes dark and it starts to go to the Ubuntu sign in screen.
More often than not, after the password is entered, it is up and running in less than 5 seconds.

---

