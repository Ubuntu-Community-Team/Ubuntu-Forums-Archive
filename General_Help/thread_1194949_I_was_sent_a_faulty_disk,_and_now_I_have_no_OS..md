---
title: "I was sent a faulty disk, and now I have no OS."
date: 2009-06-23
forum: General Help
---

### Post by Russ M. on 2009-06-23
I have a serious problem. I am using the Live CD to access the internet - because I have no Operating System to use on the hard drive. I never did have another copy of Windows XP Pro, that's what was previously on this PC. It's a 2004 Dell PC. I can install anything else, I'm sure of that. I've tried to use the disks feature to test to see if it's faulty, and it isn't able to finish that it errors close to the middle of the check.

I am completely new to Ubuntu, but a friend on deviantART told me about it, so I decided to check it out. However I tried to install it, erasing WinXP, but it just isn't working. It claims it's installed, but when I try to boot without the disk, I get nothing, but an error that says I need to choose a boot device.

Also, Firefox (on the live CD) can't keep up with my fast typing... and I refuse to take ages to type. This is ridiculous. I followed instructions on the CD to install, but it just errors every time I try. I came here becuase I don't know what else to do. If I don't have to get another disk, I won't. But I need an OS installed on this PC within a week or 2's time, because if I don't... I can't work. 

I work on a computer, that's my job. I work for Oblivion Gaming Inc. I want to get back to work, and get some projects done. We're going to start making our first RPG, and I can't be apart of it, if I can't get this thing going. So I hope y'all can help me.

I don't know my computer specs, or how to get them without MS WinXP running. So that's out of the question. I appreciate your help though - if you do help me.

My boss is willing to send me his copy of Ubuntu, and maybe another copy of WinXP - but if he doesn't have to, then I don't wanna have him do that. Cause I'll feel like I'll have to repay him back somehow, and that's because I'm a good hearted person. It'd feel right to repay him back.

---

### Post by Cheesemill on 2009-06-23
It definately sounds like your hard disk is broken.
Get yourself a new one.

---

### Post by Mighty_Joe on 2009-06-23
> **Russ M. said:**
> I've tried to use the disks feature to test to see if it's faulty, and it isn't able to finish that it errors close to the middle of the check.

So you have a bad hard drive. An operating system can't do anything about that. 
Do you feel comfortable [installing a new one yourself?]("http://lifehacker.com/137179/hack-attack-how-to-install-a-hard-drive") If not, pay someone to do it.  Those are your options.
BTW, you should have a sticker somewhere on your computer case that says "Windows XP" and "Product key".  That's your license to have XP installed.  It doesn't matter how you come by getting the install media (beg, borrow, "find"), you can install it with that key and you are legal. I love Ubuntu, but sometimes (especially when working) it's just easier to use what everyone else is using.

---

### Post by masux594 on 2009-06-23
Do you have al look to your boot sequence? But, i don't understand what you mean.. Do you want to install ubuntu or not?

Sysc, A

---

### Post by adam_kimber on 2009-06-23
If you want to try Ubuntu again you might find it agreeable to your tastes or maybe not. if not then you will need to install XP / Vista / whatever again anyway! 

I had probelsm installing Januty off a CD. Turned out that my burner did not like the blank media i was feeding it and was burning duff disks even though the burn process completed properly and I was playing them back in the same drive. 

Some people are claiming you HDD is broke. I thought that when my install failed due to an I/O error etc. Try another CD of Ubuntu you might find it works this time.....

---

### Post by Bucky Ball on 2009-06-23
You need to go into your BIOS and stop it from trying to boot from the CD driver perhaps? You want the hard disk first.

Could you please be a bit more detailed about your error message. I don't really understand what suggests a broken hard drive here. I would say it is a grub menu problem (bootloader pointing at the wrong device) or the issue I mentioned first up.

Nothing wrong with the CD itself or you wouldn't be able to use the LIVE version, obviously.

When you are in the LIVE version, could you open a terminal (Applications->Accessories->Terminal) and paste this in:

```
locate /grub/stage1
```

and

```
fdisk -l
```

and copy the results back here, please. :)

Also, go to System->Administration->Partition Editor and have a look at your drive. If you can access it there, unlikely it is dead.

---

### Post by muteXe on 2009-06-23
It might indeed be your hard disk, as your live cd appears to be working okay.
Just out of interest, why did you wipe your windows?  You could have dual-booted to see if you were happy with ubuntu whilst still retaining your windows os.

---

### Post by Bucky Ball on 2009-06-23
> **muteXe said:**
> It might indeed be your hard disk, as your live cd appears to be working okay.

? What is indicating a broken hard drive? Be more specific. It's broken because the optical drive works? OP not even sure what's on their hard drive where just yet. Bit more investigation required.

---

### Post by regala on 2009-06-23
> **adam_kimber said:**
> Some people are claiming you HDD is broke. I thought that when my install failed due to an I/O error etc. Try another CD of Ubuntu you might find it works this time.....

Well, his bios disk tests fail, so I guess I don't understand your "conclusion".

---

### Post by muteXe on 2009-06-23
Yup. Apologies Bucky Ball, i got swept away with the crowd there for a second.  I blame my hangover.

@OP:  Do you have a mate that can download the ubuntu iso file for you?  Get him/her to check the md5 checksum ([https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)), then get him/her to burn it (very slowly) to CD.  Then try and install with that.

---

### Post by LowSky on 2009-06-23
Russ M, What error do you get exactly? Why did you want to try, was XP acting up. For your purposes using Linux might not be a good idea. Not booting can be a serious issue or a really easy one to fix, but we need to know the error.

Rule number 1 of working with computers: Always back up you data.
Rule number 2: Always back up your data. 
Rule number 3:  Never use a important machine to "try" something.

PS, Update your website, [http://www.obliviongaminginc.com/index.html](http://www.obliviongaminginc.com/index.html)

---

### Post by RJ12 on 2009-06-23
Are these games also gonna be made for Linux becuase otherwise if you have to do game testing Windows and Mac games do not natively run on Linux. Sure you can try Wine but it can be a pain in the ... to setup. Also most of the time you need a lot of hardware to do that.

---

### Post by Chronon on 2009-06-23
> **Russ M. said:**
> I've tried to use the disks feature to test to see if it's faulty, and it isn't able to finish that it errors close to the middle of the check.

Everyone seems to be taking this to be a sign of a bad hard drive, whereas I was interpreting this to mean that the LiveCD may have errors.  Isn't this a feature of the LiveCD where it verifies itself against an md5sum?

I have had LiveCDs that didn't verify but were able to boot and run off of the disk, while installation failed to produce a bootable system.

Russ M., can you clarify specifically which test you're referring to here?

---

### Post by Subban on 2009-06-23
> **Chronon said:**
> Everyone seems to be taking this to be a sign of a bad hard drive, whereas I was interpreting this to mean that the LiveCD may have errors.  Isn't this a feature of the LiveCD where it verifies itself against an md5sum?

That was my interpretation also, its his Live CD that has errors not the HD. I think getting the boss to mail over another copy would be the best choice. 

To the OP:
If you are working for a game company though, and you are working on windows games I can't understand the logic of wiping windows to install linux, unless you didn't realise that Linux is not Windows. Its as different to Windows as Mac OS X is.

---

### Post by LowSky on 2009-06-23
Where is this guy? All these questions and no response from the OP..

> **Subban said:**
> I can't understand the logic of wiping windows to install linux, unless you didn't realise that Linux is not Windows. Its as different to Windows as Mac OS X is.

A programmer who doesn't know the difference between Linux and Windows is a bad programmer and should not be coding video games

---

### Post by adam_kimber on 2009-06-23
> **regala said:**
> Well, his bios disk tests fail, so I guess I don't understand your "conclusion".

I have reread the OP and cannot see anything about disks failing bios test. From what I can tell he is talking about the disk check that is on the ubuntu install CD to see if the CD has been correctly burned. Though I might be interpreting it wrong! 


Can the original poster confirm whether the HDD fails a bios test or it was the Ubuntu install CD check that is failing?

---

### Post by adam_kimber on 2009-06-23
> **Chronon said:**
> Everyone seems to be taking this to be a sign of a bad hard drive, whereas I was interpreting this to mean that the LiveCD may have errors.  Isn't this a feature of the LiveCD where it verifies itself against an md5sum?

I agree with you on this point and think (see my previous post) that he has already run the LiveCD disk check.

---

### Post by james.brantley on 2009-06-23
[SIZE=3]I have been following this and I am curious where the OP went myself. All theses people willing to help and he just disappears?[/SIZE]

---

### Post by boof1988 on 2009-06-23
> **james.brantley said:**
> [SIZE=3]I have been following this and I am curious where the OP went myself. All theses people willing to help and he just disappears?[/SIZE]

The thread started only 6 hrs ago.  So maybe we need to have patience for them to post again.  It's not uncommon to ask the OP to have patience, so I don't think it's a big stretch to wait a little bit of time to get a response from the OP. :)

I'm just saying this in the interest of kindness and courtesy. :)

---

### Post by james.brantley on 2009-06-23
> **boof1988 said:**
> The thread started only 6 hrs ago.  So maybe we need to have patience for them to post again.  It's not uncommon to ask the OP to have patience, so I don't think it's a big stretch to wait a little bit of time to get a response from the OP. :)

I'm just saying this in the interest of kindness and courtesy. :)

[SIZE=3]You're absolutely right. I was not trying to be an -$$. Sorry if it was taken that way! Personally though, I try ride my posts out until I get an answer but that is just me.[/SIZE]

---

### Post by boof1988 on 2009-06-23
> **james.brantley said:**
> [SIZE=3]You're absolutely right. I was not trying to be an -$$. Sorry if it was taken that way! Personally though, I try ride my posts out until I get an answer but that is just me.[/SIZE]

I ride my posts as well... but I can't assume that everyone else has the time (capability) to ride their posts. :)  Thanks for the explanation.

Cheers...

---

### Post by james.brantley on 2009-06-23
> **boof1988 said:**
> I ride my posts as well... but I can't assume that everyone else has the time (capability) to ride their posts. :)  Thanks for the explanation.

Cheers...

[SIZE=3]Have a great day![/SIZE]

---

### Post by ahndoruuu on 2009-06-23
Well since the title of this post is that he was sent a faulty liveCD, I highly doubt its an issue with his HDD though he still needs to provide more information.

---

### Post by Bucky Ball on 2009-06-24
> **Chronon said:**
> Everyone seems to be taking this to be a sign of a bad hard drive,

Not everyone. Read the whole thread and my posts on this thread. The very first reply the OP got stated they had a faulty hard drive for some bizarre reason, so everyone jumped on board. There has never been a skerrick (scrap) of evidence to support it. Which I mentioned immediately (post #3 or #4 I think). 

It goes to show some people scan threads rather than read them, miss things and therefore confuse the issue. Please people: READ threads, not the first one and its reply; think about the issue(s) and if you can help or have some idea or clue, great. If you have no idea, don't post! Unthought-out replies and reading the first two posts in a twenty post thread only help to confuse the issue, confuse the OP (which is possibly where they've gone), and long threads totally derivative of the original problem. :-k

If you were a new user with a problem, inexperienced by the sounds of the OP, posted a question the best you knew how and wound up with 24 posts barely related to your question and not getting far toward fixing it, wouldn't you be confused? Having said that, the news about gaming on Linux may have turned the tables.

Thank you and good night.

---

### Post by Russ M. on 2009-06-24
My problem was an I/O error along with various others. I do have a small graphic anomaly, but it's not enough to cause it not to work.

It's not my hard drive, I assure you. And as for WinXP... this computer never had that sticker on it when I got it. I bought it off of a person in another city here. I got ripped off though, it costed 150, and it's only worth 50 bucks, with what it's got.

I didn't care though, I needed a PC and at the time I couldn't afford a better one. Hell I still can't, my boss hasn't paid me yet. So I just have to wait.

All of my friends live in another city, I don't have a car yet, so I can't drive myself, and my father won't drive me out there, cause he's lazy. I suppose I could try and ask my bro up in Springfield, to do it for me over the phone, and then he can send me the disk.

But first, I'll try having another disk sent to me from the main website, like I did the first time. That's how I got the disk in the first place. It was a faulty disk. I'm sure of it. Because the burn lines aren't hidden, the inner part of the disk is flooding out of it's place. If you look at the back anyway, but y'all can't see it of course. If I can, I'll have my step dad take a picture of it with his camera, and upload to the internet for me, from his PC, and I'll show you what I mean.

But before I do that, I'm gonna have another disk sent to me. That's probably the best thing to do.

---

### Post by Russ M. on 2009-06-24
> **LowSky said:**
> Russ M, What error do you get exactly? Why did you want to try, was XP acting up. For your purposes using Linux might not be a good idea. Not booting can be a serious issue or a really easy one to fix, but we need to know the error.

Rule number 1 of working with computers: Always back up you data.
Rule number 2: Always back up your data. 
Rule number 3:  Never use a important machine to "try" something.

PS, Update your website, [http://www.obliviongaminginc.com/index.html](http://www.obliviongaminginc.com/index.html)

The error that I saw most of the time was I/O error... the other errors, not so sure, it's all weird. Sometimes, I can't even use the Live OS on the CD... so I don't know. I posted already though with some info on what I am gonna try and do.

Why I wanted to try it, is simply because WinXP is **** on this crap computer, and I wanted to see how Ubuntu ran. If it would have worked, and ran better, I would have kept it. Now I was trying to install it along side XP, but I screwed up. So that's how this happened. Everybody screws up. Everything I had to back up on my hard drive, is already still on the net, for me to get back. So no need.

As for updating the website. I cannot do that yet, until my PC is back in working shape. Rob knows the deal, he's my boss at Oblivion Gaming Inc. I know the site is horrible, I didn't design it. I recently came on board, as part of the team. It'll be lookin' spiffy when I get a chance to get to it.

---

