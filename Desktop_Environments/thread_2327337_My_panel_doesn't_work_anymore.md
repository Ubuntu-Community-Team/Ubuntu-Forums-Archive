---
title: "My panel doesn't work anymore"
date: 2016-06-09
forum: Desktop Environments
---

### Post by Evil Wayz on 2016-06-09
I am running Ubuntu 16.04 LTS, with the 4.4 generic kernel.  I am also using Cinnamon 3.0 as my desktop.  I had a problem with bluetooth, and the person in launchpad assigned to my bug report told me to try running a mainline kernel to help find the bug.  Well it didb't work, so I followed the directions to go back to my old kernel, and everything worked again, even bluetooth.  But now my panel doesn't work. When I open a program with alt-f2, it shows up on the bar, and the clock works, and all the panel indicators are there.  It just acts like my mouse isn't there.  I have tried to create a new panel, and it also refuses to let my mouse pick a new area to place it.  I have tried everything, including reinstalling Cinnamon, reverting to 2.8, and purging and and reinstalling.  I still have this problem.

I hate Unity, and GnomeFlashback is slow.  Before I upgraded to 16.04 from 14.04.4 Cinnamon 3.0 worked just fine, and so did bluetooth.  So there's some step I'm missing.

One other weird thing, when i hit the "windows" key the main menu pops up like it's supposed to.  but if i click on anything in it, it just disappears.  I think this is mouse related, somehow the panel isn't seeing the cursor when it passes over the panel.

---

### Post by T.J. on 2016-06-11
Has the Cinnamon panel been set into edit mode?  You can find out by using the opposite button on the panel for a popup.  If it has, turn off edit mode and the panel should behave once again.

---

### Post by Evil Wayz on 2016-06-11
It's not in edit mode.  It's like the panel doesn't see the mouse cursor.

---

### Post by T.J. on 2016-06-11
> **Evil Wayz said:**
> I am running Ubuntu 16.04 LTS, with the 4.4 generic kernel.  I am also using Cinnamon 3.0 as my desktop. 

Are you sure you are not mistaken about the version?  As far as I know, the highest supported version in Ubuntu is 2.8.6. Cinnamon 3.0.4 is the current upstream release, but it has not been integrated or even tested for Xenial.  Debian has it in Debian Testing, but it probably won't be in Ubuntu until the next release.  If you are using a custom version or PPA such as "[FONT=inherit]embrosyn/cinnamon"[/FONT], it is likely that no one here can help you unless they are also using it. 

You really shouldn't be using a PPA, unless you are a developer, and understand how to clean the package manager. All PPA are a "use at your own risk" proposition.  PPAs can break your Ubuntu install beyond repair, and force you to reinstall everything.  Unless you are absolutely sure about what you are doing, I recommend you revert to Cinnamon 2.8.6.

---

### Post by Evil Wayz on 2016-06-11
I was using 3.0 in Ubuntu 14.04 from the day they released it.  It worked fine. And reverting to 2.8 doesn't fix the problem.

---

### Post by T.J. on 2016-06-12
> **Evil Wayz said:**
> I was using 3.0 in Ubuntu 14.04 from the day they released it.  It worked fine. And reverting to 2.8 doesn't fix the problem.

That, of course, is your decision, and it's okay, but it makes it very hard to help you.   You are using a custom package (PPA). I can't help you without using the same version, which is why I made the recommendation.

  Can you at least tell me the origin of your installed package?

---

### Post by Evil Wayz on 2016-06-12
> **T.J. said:**
> That, of course, is your decision, and it's okay, but it makes it very hard to help you.   You are using a custom package (PPA). I can't help you without using the same version, which is why I made the recommendation.

  Can you at least tell me the origin of your installed package?

Sure can!  Initially, in 14.04, I used this ppa: ppa:embrosyn/cinnamon.

It worked fine in 14.04.  When 16.04 came out, I made the mistake of not waiting for the point release.  But Cinnamon 3.0 still worked.  It wasn't til a kernel change that bluetooth stopped working.  The guy assigned to my bug report asked me to try a mainline kernel which borked my system.  After I got it working again, this happened.  The kernel in question was 4.6.  So I tried reverting to 2.8, that didnt work, so I purged all of cinnamon and started over from scratch.  DIdn't work.

So i purged everything again   and this time I tried this ppa:  ppa:samoilov-lex/cinnamon-stable 

Same thing.  The panel works.  Applets appear on it, and newly opened programs appear , as do notifications.  And when I create a new account, bluetooth even works.  But I can't get anything on the panel to recognize there is a mouse cursor over it.  

There is some remnant on my system that is causing this.

---

