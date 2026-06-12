---
title: "Should I buy a Dell Ubuntu laptop?"
date: 2007-07-28
forum: Dell  Ubuntu Support
---

### Post by muadnu on 2007-07-28
I'm going to buy a new laptop, and since I want to load Ubuntu on it, Dell sounds like an obvious choice. But I have a couple of concerns, and couldn't find answers for them.

First, I'd like to get the Inspiron 1420N, but it doesn't have the option of adding an Nvidia video card. I'm not really crazy about needing to add a video card, but I do need a good support for using dual monitors, something better than xinerama, so that I can easily switch between single and dual monitors. I think Nvidia drivers allow this, and I could never make it work with an Intel integrated video card in my old Inspiron 700m. Maybe the pre-installed version of Ubuntu on the 1420N with the Intel video adapter allows this? The E1505N can be loaded with an Nvidia card, but it's bigger than what I'm looking for.

Second, I've read posts about problems trying to do a fresh install of Feisty Fawn. I'm not planning on doing one, but what about when new versions come out? Should we expect Dell to give support for these laptops and the next versions of Ubuntu? Again, I couldn't find anything about this.

Last, there's not a big difference in price between the 1420N and the 1420, which brings Windows Vista. Even though I'll have to install some version of Windows at some point, I'd rather install XP myself than getting Vista plus all the corresponding junk pre-installed... But, on the other hand, I can get an Nvidia card for the 1420 (128 MB, 8400 GS), and hopefully it would work...

Any suggestions?

---

### Post by smithno on 2007-07-28
I have a 1410N and love it! I don't play games, but the video is fine from my point of view. My previous laptop was an old Averatec that I had Kubuntu 6.10 on it. A couple of days after 7.04 came out, I did a normal updated and it when it finished, the Averatec was running 7.04. I expect the same thing to happen when the next version of (K)Ubuntu comes out. It's not a Dell thing, it's an Ubuntu thing that happens...

And from my point of view, I love my 1420N, so you SHOULD buy one!!!

---

### Post by deserthowler on 2007-07-29
I love my 1420n too.  No issues with the video but I don't play games.  Unless you
1> are lucky
2> investigate thoroughly
you might run into problems off the shelf with some laptops. 

Apparently Dell doesn't feel the drivers for other video cards are suitable.  I looked at the 1420n when it first came out and it included a choice of video cards which they have since eliminated.

As to updates, I'm sure Dell will have the driver updates in place.  They have a lot invested in this project.  The rest is up to the Ubuntu team.

Earl

---

### Post by rillip on 2007-07-29
Edit: in retrospect I don't think the comment was really appropriate for the Dell Ubuntu Support forum, didn't realize where I had stumbled into... oops!

---

### Post by muadnu on 2007-07-29
The 1420N does sound like a great option. But I'm still thinking of getting the 1420 and installing Ubuntu myself. I'm not sure how much work it'll take, but I guess it should be possible to get almost everything going, given that the 1420N is supposed to work, and I don't have a problem working on it... But I'm not sure, since both options have good things:

Pros for the 1420: Nvidia graphics support, Windows pre-installed (that I'll need to install for my wife anyway).
Cons: Windows pre-installed :roll:, have to get Ubuntu to work and some things may not.

Suggestions?

And, by the way, how does Beryl work with the Intel graphics on the 1420N?

---

### Post by Syke on 2007-07-30
> **muadnu said:**
> And, by the way, how does Beryl work with the Intel graphics on the 1420N?

That might depend on which features you enable. While the Intel X3100 graphic chip is a good chip, the drivers for it are still quite buggy. You'll likely have to wait till Gutsy before you can go all out on Beryl on that system.

---

### Post by strabes on 2007-07-30
If you want good dual monitor support just get the 1420 with vista, wipe it, and install ubuntu. if you have any problems booting from the live CD just use the alternate CD. I don't even bother with the live CDs because the alternate CDs are faster to install because you don't have to load the whole OS just to install it.

---

### Post by muadnu on 2007-07-30
I was almost going to buy the Inspiron 1420 (Windows), but now I got a coupon that leaves the Vostro 1400, with the same configuration, some $300 cheaper than the 1420. But I haven't found many reviews on the Vostro, and none about it running Ubuntu. I think it's just a modified version of the Inspiron, so I guess it should work fine... Maybe someone knows?

And actually, for some $100 more I get the same configuration on the Latitude D630, which is tempting too...

---

### Post by ubermenschx on 2007-08-03
Did you get this to really work? I just bought the 1420 and Ubuntu wouldn't load. I tried Ulitimate Ubuntu and Gutsy with only problems. The linux technicians at Dell couldnt help either. However, I found a thread in here that had a "walk-through" but too many steps for my level. Any clean/easier walkthroughs?

---

### Post by apswartz on 2007-08-03
> **ubermenschx said:**
> Did you get this to really work? I just bought the 1420 and Ubuntu wouldn't load. I tried Ulitimate Ubuntu and Gutsy with only problems. The linux technicians at Dell couldnt help either. However, I found a thread in here that had a "walk-through" but too many steps for my level. Any clean/easier walkthroughs?

ubermenschx,
what exactly do you mean by "wouldn't load?" Can you boot off the LiveCD? Does that work? Did you do an install and now it won't start?

If you did an install...
1. Did you leave Windows on the computer and set up a dual boot, or did you wipe Windows off and set up Ubuntu as your only OS?

2. What do you see when you boot up? How far do you get? Does it quit at the same place on each reboot?

---

### Post by ubermenschx on 2007-08-04
When attempting to load the OS (w/ Vista still there) I got the splash screen, the place to choose to install Ubuntu but after that you soon get a init10 error. I recall something about video driver not working. The walk through I saw for this had you starting with Ubuntu Alternate and loading a bunch of drivers/packages after with a script they tell how to build. It was too many steps for my experience. But I re-ordered the Ubuntu version of the 1420 and once I get it I will post the packages somewhere.

---

### Post by jmnormand on 2007-08-04
getting ubuntu to install on the 1420 is not a simple task.  most of the hardware does not work with the native fiesty drivers.  namely the graphics, cdrom, wifi, nic, sound ect...   if you are not comfortable with the command line and have a second comp with internet i would go with the pre installed ubuntu. 

this post should help
[http://ubuntuforums.org/showthread.php?t=509408&highlight=1420n+install](http://ubuntuforums.org/showthread.php?t=509408&highlight=1420n+install)

---

