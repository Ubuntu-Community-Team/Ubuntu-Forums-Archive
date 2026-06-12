---
title: "Compiz vs. Metacity"
date: 2009-02-05
forum: Desktop Environments
---

### Post by marcusesses on 2009-02-05
I just have a question about window managers. 

I know that Ubuntu comes pre-packaged with Compiz, but what is the difference between Compiz and Metacity? I'm thinking of removing Compiz because I don't really need fancy effects, but I was wondering if there is any good reason to keep it.

I know that Compiz allows you to do cool effects like the cube, or animation, and that Metacity is a pretty simple window manager, but, like I mention above, is there any good reason to keep Compiz at all?

Sorry for the noob-ish question, but I figure having both is a bit of a waste space if they both do essentially the same thing.

Thanks!

---

### Post by spazz135 on 2009-02-05
well it all depends on what you like and what your favorite themes are in every enviroment. Me i am not a new user to ubuntu at all i just signed up on the forum though. So tell me what you like for it to look like and i will tell you witch one is better or more convientint
:D

---

### Post by marcusesses on 2009-02-05
I don't know....I don't really know what either of them are capable of

But I don't much fancy special effects (rotating cubes, etc, etc...)

So metacity would probably suit my needs...but what does compiz offer that metacity doesn't?

I'm just curious about what other people think about this...

---

### Post by Yashiro on 2009-02-06
If you look past the stupid effects compiz can actually do alot more. Set rules for windows, sizes, positions etc. If you don't use these features just remove it and use Metacity.

---

### Post by mcduck on 2009-02-07
Metacity only does what a window manager is supposed to, manages your windows.

It has themes, and you can change it's button layout through gconf-editor. That's pretty much all. ;)

---

### Post by Montblanc_Kupo on 2009-02-07
Compiz makes it easier to do certain things. One thing I found is that it's easier to quickly add custom button commands in compiz than using gconf.

Also, if you like widgets, compiz allows you to add screenlets (which are a little nicer than desklets).

Compiz will give you 3D rendering API controls to all your window operations as well... so things like scaling can have mipmapping applied (smoothing of textures so they don't get blocky). 

I find compiz, with a functioning 3D accelerator card, to be a little smoother when doing simple things like moving windows even. 

With a larger monitor, sometimes text or images can be a little small... so being able to zoom the entire screen the with mousewheel and a modifier key is a great function.

Also being able to use a different modifier along with the mousewheel allows Me to make My windows become more or less transparent... this is nice if you need to be looking at something underneath a window over and over while working... say in the terminal or a word processor.

Personally, I like emerald skin manager better than metacity.

I like the effects, personally... and I haven't found that they slow My machine down at all since they use the 3D card to do the work... you're going to give up about 40MB of ram to have compiz running... but I haven't seen any major ramifications from it... and after I cleaned out the useless services that ubuntu has installed by default... I regained that and more.

Compiz gives you options... if you need the extra system resources... then I can see removing it... but it does give you a lot more options if you want it.

---

### Post by marcusesses on 2009-02-07
> **Montblanc_Kupo said:**
> Compiz makes it easier to do certain things. One thing I found is that it's easier to quickly add custom button commands in compiz than using gconf. 

Really? How so? I recently added a couple custom commands and it was pretty straightforward....but that's because I found out how to do it online : P

> **Montblanc_Kupo said:**
> Also, if you like widgets, compiz allows you to add screenlets (which are a little nicer than desklets).

Compiz will give you 3D rendering API controls to all your window operations as well... so things like scaling can have mipmapping applied (smoothing of textures so they don't get blocky). 

I find compiz, with a functioning 3D accelerator card, to be a little smoother when doing simple things like moving windows even. 

With a larger monitor, sometimes text or images can be a little small... so being able to zoom the entire screen the with mousewheel and a modifier key is a great function.

Also being able to use a different modifier along with the mousewheel allows Me to make My windows become more or less transparent... this is nice if you need to be looking at something underneath a window over and over while working... say in the terminal or a word processor.

Personally, I like emerald skin manager better than metacity.

I like the effects, personally... and I haven't found that they slow My machine down at all since they use the 3D card to do the work... you're going to give up about 40MB of ram to have compiz running... but I haven't seen any major ramifications from it... and after I cleaned out the useless services that ubuntu has installed by default... I regained that and more.

Compiz gives you options... if you need the extra system resources... then I can see removing it... but it does give you a lot more options if you want it.

Ok, here's a quick question then...what are the useless services that Ubuntu installs by default? That's part of the reason for my initial question...I want to remove anything that I won't really be using...and from the sounds of it, I'll probably be keeping metacity and compiz...

---

### Post by eaidoido on 2009-02-07
anyone have info on the differences in speed and performance?

---

### Post by Montblanc_Kupo on 2009-02-09
> **marcusesses said:**
> Really? How so? I recently added a couple custom commands and it was pretty straightforward....but that's because I found out how to do it online : P

It's not terribly hard to do with gconf... but it's far easier to do with compiz... mostly due to just quickly locating it. The nice thing is that if you add a command in one, it's reflected in the other since they are changing the same thing.

This is what I do. Right click the compiz icon in My panel, choose "settings manager". Click the "general" button which is the very first choice in the settings manager. Then over to the right you have a tab for "commands". The nice thing about doing it this way is you don't have to type in the key sequence, you can simply tell it to "grab" it and just press what you want. 



> Ok, here's a quick question then...what are the useless services that Ubuntu installs by default? That's part of the reason for my initial question...I want to remove anything that I won't really be using...and from the sounds of it, I'll probably be keeping metacity and compiz...

I should have written that more clearly. Services that were useless to ME. I don't have a printer so having printing services are pointless. I don't have a laptop... so having services that manage the battery are useless. I basically poked around a bunch online until I found out what the services were for and disabled a bunch of them. There's a great program called "Boot-up Manager" or BUM... it not only tells you what is running, and lets you enable / disable them... but it gives descriptions for nearly all of them so you know if you need them or not. Very helpful.

---

### Post by Montblanc_Kupo on 2009-02-09
> **eaidoido said:**
> anyone have info on the differences in speed and performance?

I can't give you any hard numbers, but after hearing so many people complain about "wasting resources on eye candy"... I actually think that it runs better with compiz enabled... it makes better use of the video card... I think it has better compositing / rendering api's and makes things smoother. I don't have a high-end system by any means and I haven't noticed any negative effect of having compiz running with all it's eye candy turned on.

The one caveat is that some applications (very very few) can conflict with it... mostly games.

---

