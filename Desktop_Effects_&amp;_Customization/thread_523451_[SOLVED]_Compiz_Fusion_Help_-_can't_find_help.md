---
title: "[SOLVED] Compiz Fusion Help - can't find help"
date: 2007-08-11
forum: Desktop Effects &amp; Customization
---

### Post by scb0825 on 2007-08-11
Hello,

I am new to ubuntu, and recently tried to install Compiz Fusion. I got it installed, but it never works correctly... Sometimes when launching it will lock up my system, other times I get no window borders, etc. My system is a P4 2.8, 512, nVidia FX 5900 Ultra, with ubuntu on the secondary 80gig drive.

After spending several days reading through the forums, and various places on the internet trying different things I am almost to the point to where I want to give up. I have nearly decided to reinstall ubuntu and start over, although I do not want to do this. 

My questions are...

1. What is the BEST way to remove Compiz Fusion and restore ubuntu back to its original state?

2. What is the BEST way/guide to install Compiz Fusion on Feisty? Even though I am new to ubuntu I am not new to IT. I am not scared of the CLI, and can follow directions. I just need to know which freakin' guide to use! 

**update - In my frusterating search to find a legit guide I came across this video and attempted its instructions. I now have a "Compiz Fusion Icon" under Applications\System Tools\ menu. Any idea how to remove this as well and start over new?
[http://www.youtube.com/watch?v=4uNQcD82mhk](http://www.youtube.com/watch?v=4uNQcD82mhk)


I will appreciate any and all help. 
Thanks! 

- Steve

---

### Post by quadomatic on 2007-08-11
I can't give you much of a solid answer to either question, as I'm not an nVidia user, but I'd guess this is a pretty good guide for Compiz Fusion

[http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)

As for fixing that problem with compiz not having borders, I think that's because you need to start emerald (that was the problem I had anyway, I think).

Try running this in a terminal to start compiz fusion:

```
compiz --replace -c emerald
```

I hope this helps, good luck!

---

### Post by speedup on 2007-08-12
Hi, you may try to check Synaptic Package Manager. You'll be able to see the Compiz entry just mark it for removal.

---

### Post by scb0825 on 2007-08-24
> **scb0825 said:**
> Hello,

I am new to ubuntu, and recently tried to install Compiz Fusion. I got it installed, but it never works correctly... Sometimes when launching it will lock up my system, other times I get no window borders, etc. My system is a P4 2.8, 512, nVidia FX 5900 Ultra, with ubuntu on the secondary 80gig drive.

After spending several days reading through the forums, and various places on the internet trying different things I am almost to the point to where I want to give up. I have nearly decided to reinstall ubuntu and start over, although I do not want to do this. 

My questions are...

1. What is the BEST way to remove Compiz Fusion and restore ubuntu back to its original state?

2. What is the BEST way/guide to install Compiz Fusion on Feisty? Even though I am new to ubuntu I am not new to IT. I am not scared of the CLI, and can follow directions. I just need to know which freakin' guide to use! 

**update - In my frusterating search to find a legit guide I came across this video and attempted its instructions. I now have a "Compiz Fusion Icon" under Applications\System Tools\ menu. Any idea how to remove this as well and start over new?
[http://www.youtube.com/watch?v=4uNQcD82mhk](http://www.youtube.com/watch?v=4uNQcD82mhk)


I will appreciate any and all help. 
Thanks! 

- Steve

I have installed Trevino's latest repos using this thread. All seems well...

[http://ubuntuforums.org/showthread.php?t=533407](http://ubuntuforums.org/showthread.php?t=533407)

---

### Post by puner on 2007-09-09
Hey guys, sorry to dig a old thread but I searched the forums and found this thread that relates to my problem.

Basically i too want to remove CF because of common problems:

1) It doesn't load on system start
2) When I manually load it, my desktop goes black and i can no longer change the wallpaper.
3) When CF is off, i cannot access alt+tab to switch between windows, but i CAN when CF is on.

So since iam a newbie iam using Synaptic to remove the program.

CF is listed there, but there are a lot of files that go along with the program. I want to know if i supposed to remove them as well.

[Screenshot]("http://img47.imageshack.us/img47/3590/screenshotsynapticpackamm8.png")

---

### Post by isaacj87 on 2007-09-09
This is how I do it:

In Synaptic, do a search for "compiz"

If you have Compiz Fusion installed from Trevino's Repo, there's going to be 15-17 packages installed...this includes Emerald if you have that installed. 

Hope that's helpful...just remove the packages related to compiz and you're good to go! :)

---

### Post by puner on 2007-09-09
Alright I removed anything to do with CF, restarted and it's gone.

Now the default "Desktop Effects" isn't there.

Under System>Pref

When I first installed ubuntu there was Desktop Effects.

Also Alt+Tab still doesn't work.

---

### Post by isaacj87 on 2007-09-09
Go back into synaptic and search for desktop-effects

---

