---
title: "Compiz questions"
date: 2009-04-03
forum: Desktop Environments
---

### Post by Daremo_06 on 2009-04-03
So I have my new video card (Nvidia 9400gt) installed and I believe I have the latest drivers setup properly at this point (Nvidia 180.44 - 30Mar09), or I hope I do.  I have noticed some things about Compiz and can't quite figure out whats going on.

When I go to Preferences>Appearance>Visual Effects, its set to Normal.  I click on Extra and sometimes a little popup shows up saying something about searching for drivers, it stays at 0% but the scroll bar still advances.  That lasts about 5-10 seconds then it goes away.  Other times, nothing happens.  So then I'll click on "close" and notice that Compiz is now making my windows wobble.  (one of the most annoying default features ever, imho)  So I go into Compiz and turn it off.  Last night I was installing some GTK themes and doing some general desktop configuring, or attempting to and a few times I went back into Visual Effects and it would be set back to "Normal".  So I'll turn it back to "Extra" and the damn wobbly windows is back.  So what gives?

I suspect I don't have something configured quite right in the NVIDIA driver?  Or a library or something else that I should have grabbed in Synaptic, problem is I don't know what that thing might be.

I followed the install guide thats in the cafe here in the forums, but I have noticed other posts mentioning things about the Restricted Driver and also running Envy to install them.

So whats going on?

---

### Post by gettinoriginal on 2009-04-03
First, check under System, Administration, Software Sources, Ubuntu Software tab, and make sure that all four boxes are checked.  If they are, check in Synaptic to see that ubuntu-restricted-extras is installed.

---

### Post by zoldiel on 2009-04-04
Generally if you are going to customize Compiz you should not change the Visual Effects settings after compiz is enabled, unless you want to disable the effects or set them to the defaults for normal or extra. When you set it back to extra it in the Appearance preferences window it will overwrite your configuration and change it to the default for extra, which is wobbly windows, desktop wall, animations and some others, thus anything you did in ccsm will have to be redone.

---

