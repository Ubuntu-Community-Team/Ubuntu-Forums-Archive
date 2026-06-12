---
title: "How to hot swap xbox orignal with pc to fix error 21"
date: 2009-01-24
forum: Gaming &amp; Leisure
---

### Post by hockey97 on 2009-01-24
Hi, I  have a error 21  on my original xbox. I want to know how I can hotswap the xbox hd to my pc and restore the files to the xbox hd?


I currently tried many ways. I seen vidoes and tutorials they all think it's easy to take off the ide cable in time and connect it to your pc and then boot into your OS.

I am using windows xp. I downloaded xbox360 explorer. I never was able to get passed the windows xp loading screen.

it would after an hour reboot.

Now currently my pc can't boot at all. I would turn it on. It would show my bios and all the post checks are good. Then it will got to a blank black screen with that dos looking text curser. 

That is where I am at right now. I can't boot into windows at all. Even when I put all the stuff back how it was.

Any Ideas???

---

### Post by hockey97 on 2009-01-25
Is this the wrong place for asking this question?

---

### Post by Shpongle on 2009-01-25
if it were me id just format the pc hd and install ubuntu, or if you really wanna keep windows or need to recover files . . . id try using a windows install disk to repair/recover the os


as for the xbox . . . .?????  best of luck

---

### Post by mattman on 2009-01-26
Check out [http://www.xboxscene.com/ ]("http://www.xboxscene.com/")
for everything Xbox related. They have a lot of tutorials on Xbox repair and modding.

---

### Post by HittingSmoke on 2009-01-26
> **hockey97 said:**
> Hi, I  have a error 21  on my original xbox. I want to know how I can hotswap the xbox hd to my pc and restore the files to the xbox hd?


I currently tried many ways. I seen vidoes and tutorials they all think it's easy to take off the ide cable in time and connect it to your pc and then boot into your OS.

I am using windows xp. I downloaded xbox360 explorer. I never was able to get passed the windows xp loading screen.

it would after an hour reboot.

Now currently my pc can't boot at all. I would turn it on. It would show my bios and all the post checks are good. Then it will got to a blank black screen with that dos looking text curser. 

That is where I am at right now. I can't boot into windows at all. Even when I put all the stuff back how it was.

Any Ideas???

Ok, so I'm assuming you tried to softmod your Xbox? You need to give some more detailed info on what you did to screw it up in the first place. Did you use a game or an audio CD or what?

Here's some very detailed info on soft modding which may help you out. [http://www.instructables.com/id/EYGFOOJ02REWT1KBL6/](http://www.instructables.com/id/EYGFOOJ02REWT1KBL6/)
The best way is using a music track from the HDD then pausing it. But what you're asking can only be done if you backed up your original data.

The easiest way to unlock the Xbox HDD is to use a mod chip, but due to the gray areas associated with this I'm not going to post any links.

That being said, this problem doesn't have anything to do with Ubuntu or even Linux... not really a good place to post it.

---

### Post by hockey97 on 2009-01-29
ok, currently I tried hotswaping my xbox hd with my pc a windows xp os.

and now after trying many times never got it to work. Now my PC won't boot.


after the post and bios I get a blank screen showing a dos text courser that just blinks and if I type anything nothing shows up on the screen...meaning text/typing.

I get no post errors. I see in my bios that it detects my harddrive and seems to be all physically ok.

I tried to pop in the windows xp cd to boot into setup to reintstall the OS.

well the cd wouldn't boot.

So I tried the floppy version which  I was able to boot into the setup and stuff but when I treid repair and also tried reinstall.

I get a error that says  no harddrive detected.

Yet my bios shows me that my hd is detected.

any Ideas???

it's a seagate 80gb Pata hd . Is their any tools that seagates allows me to download that can check out my hard drive condition and fix any problems the hd may have?

I know I have a seagate cd for my other pc that is a diagnostic tool that helps fix harddrive problems.

Should I give that a try?

---

### Post by lakotajames on 2009-01-29
You should try installing Ubuntu on the PC.  I am sure people on this forum would be more willing to help you if you were running Ubuntu.  You know, considering how this is a forum for Ubuntu?  And if you can't get xp to boot, you don't really have anything to loose anyway.  Right?

---

### Post by Burnasty on 2009-01-30
is the cd drive plugged into master.  I know you use master for the drive when hotswapping.  I would softmod with an exploit next time if i were you.  Get an action replay and you will save a lot of aggravation.

---

### Post by anjilslaire on 2009-01-30
too many hotswapping attempts may have damaged the IDE controller on your PC motherboard.

What you *should* have done was:

1. Remove the dvd drive from the IDE on the xbox, and power up the xbox. With no dvd drive, the xbox would have unlocked the hd and stopped after finding no dvd drive. You now have as much time as you need to swap the IDE.
2. Connect the IDE from your PC to the xbox hdd and boot your PC with xboxhdm.
3. Your xbox hdd is now unlocked and loaded via xboxhdm

---

### Post by hockey97 on 2009-01-30
Thanks for the replies. I poped in a seagate cd and reformated the hd.

after that I was only able to install ubuntu..... I found out my xp cd got fromatted by dos which was supposed to format the hard drive. The drive letters were messed up.

So I have no windows xp cd and that cd is not able to be over written.

So I got ubuntu on it. 

Now I opened my pc and took out the hd. I saw the jumper on it as master.

So I moved the jumper to the cable select mode. I have one ide cable which is for the dvd-rom and my pc hd.

I have an extra ide connector on my motherboard. I just don't have a extra ide cable.

so how can I swap my xbox hd with my pc and still have the dvd-rom connected to run the xboxhd program?

I will look around for any extra ide cable so I can put the dvd-rom on that second connector on the motherboard.

---

### Post by anjilslaire on 2009-01-31
> **hockey97 said:**
> I found out my xp cd got fromatted by dos which was supposed to format the hard drive. 

Uh, what?
> **hockey97 said:**
> 
Now I opened my pc and took out the hd. I saw the jumper on it as master.

So I moved the jumper to the cable select mode. I have one ide cable which is for the dvd-rom and my pc hd.


That's all you need. One IDE cable in your PC for your dvd-rom (to boot xboxhdm) and the free connector to swap your xbox hd onto. You do not want your PC hd involved or attached, at all.

---

### Post by hockey97 on 2009-02-04
Ok, thanks... So I will just burn the xboxhd thing on a cd and boot into it and then attach the xbox hd where the pc hd is. So the pc hd will not be connected at all in this process.

Ok, well currently I got ubuntu installed on my pc. I got dos to format my xp cd  by mistake. I wanted to format C: drive but yet DOS thought C: wad D: drive so instead of formatting the pc hard drive it formatted my cd.
So I got no xp cd. So I downloaded xp and tried buring it onto  a cd and Then tried poping it in. When I poped it in. It won't boot. I get a nboot error. So I can't get a working xp cd to install the OS back.

The reason is I later plan to install software to program logic chips.


Well....  one more question before I start.

Is this the best time to mod the xbox???

I heard that I need to put backup xbox files  into the c and e folders.

I was told that this is a good time to also put the soft mod stuff in those folders so it will be a modded xbox instead of a repaired xbox.

So if I can softmod now by putting the softmods in those folders.

Is their any tutorial or anything that will explain what files I need for a softmod and where to put them in?

Thanks for your help. I thank you guys for helping me out.

;)

---

