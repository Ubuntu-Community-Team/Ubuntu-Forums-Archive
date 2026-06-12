---
title: "Compiz or Beryl"
date: 2007-06-22
forum: Desktop Environments
---

### Post by microsoft92sucks on 2007-06-22
I'm hoping to get a big system upgrade to day. If I do I'll big taking what part's I can from a HP and Dell and making the best pc I can. I think the specs are going to be something like

I'm not sure what the CPU is but on window's system spec's or manager or something (this is my brothers pc I'm buying from him it's not my window's) said 2.69ghz 2.59ghz like it's got two CPU or something it's few years old so I don't now if it's it's duo processor or what.
about 756 ram
don't know graphics's 
2 80 gig HDDs 

and that's all I know and I'm hoping and thinking my brother's going to sale me his dell. So in the case he.(Which is very likely because he's getting a laptop and already told me he would.) does I'm wanting to set up a dual monitor with compiz or beryl. And look up at my  starting day for this site that's about as long as I've been using Linux. So I'm not great at this sort of thing. So my question would I be better of with Compiz or Beryl? (I'm only going to want a few plugin but the thing I want the most is the cube Desktop.) And how do I do this with dual monitor and Compiz or Beryl?

---

### Post by Ultra Magnus on 2007-06-22
Have you tried either before - fiesty comes with the compiz cube and wobbly windows already so you just need to go system -> preferences -> desktop effects and choose what you'd like - Beryl has allot of cool effects but some of them are quite useless, I actually prefer the desktop wall to the cube - then there is the new compiz fusion! - Its very new - basically beryl/compiz merged - but it has some nice looking stuff.

Try compiz, as you will already have it, if you fancy tryout some more effects then you can get beryl and compiz fusion by putting these lines into your /etc/apt/sources.list file

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

code: sudo apt-get update

They say on the beryl web site that it runs ok on 256 RAM - on my old computer it ran alright but quite slowly - Hope that helps!

I don't know about compiz but beryl has an option for dual monitors

edit - some effects are a bit buggy, but the main ones work fine

edit2 - actually you can get beryl without putting the lines in the file but just doing

sudo apt-get install beryl beryl-manager

but you don't get all the extentions

---

### Post by tomaasj on 2007-06-22
tried this: system -> preferences -> desktop effects

activate workspaces on a cube: what happens on my laptop is that Desk 2 disappears from window and nothing else.

---

### Post by praxis22 on 2007-06-22
Beryl is very "weird" about the graphics card it uses. It really needs hardware acceleration, it's also pretty much much beta software, but then by this token so is Vista :)

It may all come down to what display driver you're running and how much support you're getting from your graphics chip. there is actually an option in beryl-settings that says something about warning on Nvidia hardware about black screens, perhaps that's what you hit?

This might help:
[http://wiki.beryl-project.org/wiki/Troubleshooting_Xgl](http://wiki.beryl-project.org/wiki/Troubleshooting_Xgl)

This one was also quite useful to me, even though it's from Suse, and not Ubuntu specific:
[http://en.opensuse.org/Beryl](http://en.opensuse.org/Beryl)

Good luck!

---

### Post by Ultra Magnus on 2007-06-22
Beryl can be made to work with practically any grapics card but some take more effort than others - Wierdly enough, intel integrated cards seem to work the most effortlessly - I have a brand new totally unsupported ATI card and after allot of work and looking around I managed to get beryl and fusion to work - If it doesn't work try googling something like  - beryl followed by your graphics card or computer name, there is bound to be someone who has got it sorted already.

---

### Post by microsoft92sucks on 2007-06-22
ok thanks for the help I got alot of work to do to make a brand new computer out of two old one's so I'll let you all know how it goes tomorrow. Thanks again for the help.

---

### Post by zero244 on 2007-06-22
I like the beryl effects and the free themes you can install and change to your liking.
And beryl is finally running very stable for me.
I know many purists thing beryl is mostly eye candy..........but hey its fun eye candy. Plain ole Metacity is rock stable but pretty plain.

---

### Post by oomingmak on 2007-06-25
> **Ultra Magnus said:**
> Beryl can be made to work with practically any grapics card but some take more effort than others - I have a brand new totally unsupported ATI card and after allot of work and looking around I managed to get beryl and fusion to work
What card do you have? and which instructions did you use to get it to work?

---

### Post by microsoft92sucks on 2007-06-26
I got that Dell but mest it up right after so I'm going to have to what for compiz or beryl till I get the Dell fixed.:cry::cry: It really sucks but hopfully I'll get it fixed soon.
But thanks again for the help.
Here's more info and what happend to the Dell.
[http://ubuntuforums.org/showthread.php?t=482460](http://ubuntuforums.org/showthread.php?t=482460)

---

