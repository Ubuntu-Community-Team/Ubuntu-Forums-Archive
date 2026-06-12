---
title: "What happens when you upgrade to newer distro?"
date: 2009-04-20
forum: General Help
---

### Post by shelbyvision on 2009-04-20
I have had Gutsy Gibbon on my computer since I first started using Linux. Now I see that Gutsy is going by the wayside. I have a few questions:

1. Is Ubuntu like windows in that each newer version requires a faster and more powerful computer?

2. If I upgrade, what happens to all the files and programs I have collected, that would take many hours to recover or replace if they are lost?

3. My update manager has at the top "New Distribution Release '8.04 LTS' is available", with an upgrade button. Would that by my best option for non-disruptive upgrade?

4. If I'm getting along just fine with Gutsy, is there any reason to change?

I will appreciate any input you can give.
Steve

---

### Post by Therion on 2009-04-20
> **shelbyvision said:**
> 1. Is Ubuntu like windows in that each newer version requires a faster and more powerful computer?
In short, no.  There may be some incremental requirements but very incremental.

> **shelbyvision said:**
> 2. If I upgrade, what happens to all the files and programs I have collected, that would take many hours to recover or replace if they are lost?
You have a couple options if you decide to upgrade.  You can do it "online" via the Update Manager which is the officially suggested method or, you can do a fresh install from a CD.  Doing an online upgrade via the Update Manager should keep everything intact (installed applications, settings, et al. -- everything is the same, just updated), emphasis on "should" since there are no guarantees in Life.  Whether tis better to upgrade online or to a fresh install is somewhat debated.  I suggest doing fresh installs, personally, but that's me, and again the issue is debated.  It's a choice you'll have to make yourself.

> **shelbyvision said:**
> 3. My update manager has at the top "New Distribution Release '8.04 LTS' is available", with an upgrade button. Would that by my best option for non-disruptive upgrade? 
For a non-disruptive upgrade, yes.  Assuming all goes well with it.

> **shelbyvision said:**
> 4. If I'm getting along just fine with Gutsy, is there any reason to change?
I tend to fall into the camp of suggesting that "If it ain't broke, don't fix it", but I rarely *follow* that advice myself.  Still, if you don't have compelling reasons to upgrade and you're happy with Gutsy, stick with Gutsy.  Bear in mind though that at some point in the not tooooo distant future, Gutsy will no longer be officially supported.  Hardy Heron, however, being a long-term-support release (LTS) will be supported well into the future.  Just something to think about.

---

### Post by aeiah on 2009-04-20
theres no real reason to change, but you'll start to find that there's less and less new software and updates available to you. you'll always of course be able to compile stuff from source with gutsy but you may find yourself having to upgrade all the dependancies too as time goes on. the new release will be version 9.04. 8.04 is a long term release so it'll be supported for quite a while though.

i run gutsy (version 7.10 isnt it?) and have kept it without upgrading purely because i have things configured just the way i like, but i will be reinstalling ubuntu with version 9.04 in a few weeks time when it comes out and the dust settles. ive already found that new software can be more awkward than it needs to be to install and look forward to the ext4 filesystem's speed and other improvements.

i think as far as your existing software and upgrades go: ubuntu will endeavour to upgrade all of your software as it upgrades your operating system. if you have software that wasn't installed via a repository then i expect it may break during an upgrade but it just depends what it is i suppose.

id say do one of two things:

:: if things are running fine and you dont want to have to deal with any problems, just dont upgrade

:: if you want to upgrade, id go for version 9.04 instead of 8.04. i know 8.04 is a long term support release but you'll find little difference between 7.10 and 8.04. if all you want is bugpatch support then i suppose 8.04 will do.

you can upgrade to 8.04 with the click of a button, but i suggest a fresh install if you're jumping ahead by any more versions than that.

---

### Post by shelbyvision on 2009-04-20
Thanks for the advice. I'm going to do some backing up just to be safe, and go for the upgrade button, that sounds like the most trouble-free option. See you on the other side, hopefully.

---

### Post by CMJ Tech on 2009-04-20
> **shelbyvision said:**
> I have had Gutsy Gibbon on my computer since I first started using Linux. Now I see that Gutsy is going by the wayside. I have a few questions:

1. Is Ubuntu like windows in that each newer version requires a faster and more powerful computer?

2. If I upgrade, what happens to all the files and programs I have collected, that would take many hours to recover or replace if they are lost?

3. My update manager has at the top "New Distribution Release '8.04 LTS' is available", with an upgrade button. Would that by my best option for non-disruptive upgrade?

4. If I'm getting along just fine with Gutsy, is there any reason to change?

Steve

I just started using linux about a month and was finally able to get my system working with 7.10 yesterday.  I had the exact same questions.  Please post how the upgrade goes for you.  I am a little gun shy about upgrading myself, since I just got my system working.
Thanks!

---

### Post by apparle on 2009-04-20
> **CMJ Tech said:**
> I just started using linux about a month and was finally able to get my system working with 7.10 yesterday.  I had the exact same questions.  Please post how the upgrade goes for you.  I am a little gun shy about upgrading myself, since I just got my system working.
Thanks!

you are funny.......why didn't you check the version you had was the latest before installing it. At least you should have checked the website.

---

### Post by Therion on 2009-04-20
> **shelbyvision said:**
> Thanks for the advice. I'm going to do some backing up just to be safe, and go for the upgrade button, that sounds like the most trouble-free option. See you on the other side, hopefully.
Many people have had nothing but very successful upgrades using the Update Manager.  I've had nothing but problems with it.  It's just one of those things.  

Good luck to you sir! <snappy salute>

Chances are, things will go just fine, but if the install seems "glitchy" you might want to consider doing a fresh installation from a CD.

---

### Post by shelbyvision on 2009-04-20
Well, I tried the upgrade button, and it does its thing for a while, and then gives me this (see attachment). Apparently it doesn't like some of the unofficial software I have. I uninstalled those which I don't really need, with no change in results. The only programs I have that might be causing a problem are Fontmatrix and Truecrypt, since they do not appear in "Add/Remove Applications" even though they are installed. Is there a sure way to tell what programs are a problem?

---

### Post by CMJ Tech on 2009-04-20
> **apparle said:**
> you are funny.......why didn't you check the version you had was the latest before installing it. At least you should have checked the website.

7.10 is what works with my system.  I started with 8.10 but I had problems with the display drivers not working.  I tried to upgrade to 9.04 but after the upgrade the system would not reboot.  That is when I decided to install 7.10.

---

### Post by igneousquill on 2009-04-30
> **shelbyvision said:**
> Well, I tried the upgrade button, and it does its thing for a while, and then gives me this (see attachment). Apparently it doesn't like some of the unofficial software I have. I uninstalled those which I don't really need, with no change in results. The only programs I have that might be causing a problem are Fontmatrix and Truecrypt, since they do not appear in "Add/Remove Applications" even though they are installed. Is there a sure way to tell what programs are a problem?

You can only upgrade to Ubuntu 9.04 from Ubuntu 8.10.  If you are working from Gutsy and really want to upgrade, the way forward for you is a fresh install.

---

