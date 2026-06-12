---
title: "time is of the esssence"
date: 2007-02-22
forum: Forum Feedback &amp; Help
---

### Post by nathanclarke on 2007-02-22
Earlier today I posted what might be described as a rant, (title - on the edge). My rant and plea for help were sent 'to jail' by *** Taurus (?). He didnt get it.

My problem is that nothing seems to work with ubuntu, namely my Ipod software and Nokia PC suite, both of which work fine with Windows. For the record, my rant did actually include a geniune plea for help.

Could someone please give me some advice on how to get Ubuntu to be more compatable with most things that are designed for, I guess, Windows or Mac.

Oh, and Taurus, you may have thought my rant was idiotic and impatient but, quite frankly, I have more inportant things to do with my two weeks leave. I have just come back from Iraq ( I am a Corporal in the British Army) for the third time and am off to Afghan in just over a month. I dont really want to spend it trying to make a bloody operating system work.

---

### Post by oldone on 2007-02-22
Nathan - I too have lost it with Ubuntu and these forums lack of help or some know it all moderator lose it with zero patirence when they know it and have it working and the masses are having a little to a hell of a lot of trouble getting this to work and trying to give linux and Ubuntu a fair shot.  Thanks for all you hard work over there and be safe.

I work with a lot of US military from majors to colonels to special ops and chopper pilots, and I hear and know of the horror that is Iraq and Afghanistan.

best wishes,

oldone!

the holier than though snobs and mods are not fair at all to the new people - but I thought it was linux and ubuntu for all - alll humans that is....not just the annointed ones!

---

### Post by kinematic on 2007-02-22
if you want compatability with mac/windows apps linux isn't the right choice(there are great linux alternatives for (almost)every windows program)
linux is not windows and it will always do things in a  different way.
that said there are linux apps for use with your ipod.....gtkpod,amarok and if i remember correctly rhythmbox(don't know of others because i don't have an ipod).
as for your nokia pc suite....you maybe able to get it to work with wine(i think it's in the multiverse repository).
wine is basically a program the mimics the windows api inside a linux environment so that you can run some windows apps.
it doesn't support every windows app and it's still in heavy developement so you'll just have to see if it works.

---

### Post by inCursorated on 2007-02-22
linux has software solutions for almost anything you need. The Ipod shouldn't be too much trouble, at least. i used to use gtkpod but have been using Amarok which is pretty nice (similar to iTunes). the only thing (i encountered) is that you may have to manually run mount/umount/eject commands. 

check the [wine application DB]("http://appdb.winehq.org/") to see if you're Nokia program might work.

---

### Post by kinematic on 2007-02-22
and on a side note.....the people on this forum don't owe anyone anything.
we give up some of our free time to help complete strangers.
and yes....sometimes we may be somewhat annoyed if we see the same question again and again or if someone starts ranting.
we're only human.....keep that in mind.

---

### Post by justin whitaker on 2007-02-22
> **nathanclarke said:**
> My problem is that nothing seems to work with ubuntu, namely my Ipod software and Nokia PC suite, both of which work fine with Windows. For the record, my rant did actually include a geniune plea for help.

Could someone please give me some advice on how to get Ubuntu to be more compatable with most things that are designed for, I guess, Windows or Mac.

Nathan, chill. Seriously. Taking on admins in public is a good way to get the thread jailed. 

Let's break the problem down into easily digestible bits. 

First, you have a connection issue. If your iPod doesn't mount, look for usbmount in synaptic. That is a user application which basically automounts anything attached to the computer via usb. I was having this issue with my iPod mini, and this fixed it. 

Next, you need software. 

Crossover Office runs iTunes 4.x (don't remember which one), but even then, it does not recognize iPods when attached. The store and everything else works, so it's not completely  worthless. 

Instead, you can use: gtkpod to sync your iPod, rythmbox or banshee to handle your tunes and sync to an iPod, ipodder to do the whole scrape/autodownload podcast thing. 

There is also [Floola]("http://www.floola.com/modules/wiwimod/"), which apparently can sync any iPod or iPod like phone. 

Have no idea about Nokia phones, but there should be something out there.

---

### Post by nickoli_02 on 2007-02-22
Your problem seems to be that you want software that is designed for Windows or Mac to be able to work in Linux. Well, you're pretty much out of luck there, because Linux isn't Windows. Linux will not run Windows applications (unless you use wine), the same way Windows won't run Linux applications (unless you get them to work with cygwin). 

Now, on to your troubles. Check out [this]("https://help.ubuntu.com/community/IPodHowto") page for some info on getting your iPod to work. If you still have troubles, post a detailed description of the problems you're facing.

As for the Nokia PC Suite, I'm assuming this is for connecting your Nokia cell phone to your computer? This is most likely a Windows application, and like I said above, Windows applications won't work in Linux. Try searching the forums for your cell phone model, there may be support for it or there may not be.

Learning how to use Linux requires a certain amount of patience. If you're serious about using Linux you're going to have to realize that proprietary devices most likely won't "just work" out of the box. Extra configuration and troubleshooting is often needed to get these devices working. If you don't have this sort of patience, Linux probably isn't for you.

---

### Post by justin whitaker on 2007-02-22
Some links for Nokia on Linux:

[http://www.gnokii.org/](http://www.gnokii.org/)
[http://tuxmobil.org/phones_linux_nokia_other.html](http://tuxmobil.org/phones_linux_nokia_other.html)
[http://ubuntuforums.org/showthread.php?t=34740](http://ubuntuforums.org/showthread.php?t=34740)

Best of luck!

---

### Post by nickoli_02 on 2007-02-22
> **oldone said:**
> 
the holier than though snobs and mods are not fair at all to the new people - but I thought it was linux and ubuntu for all - alll humans that is....not just the annointed ones!

Try to understand that the help you're asking for is from people who are volunteering their time to help you out. If your problem is not very common then it may take a little more time for someone with more knowledge to come along and read your post. Also, polite and detailed posts will receive polite and detailed responses 9 times out of 10. No one is here to personally attack anyone for being new to Ubuntu, for the most part we're glad you've made the switch and want you to keep using Ubuntu.

---

### Post by bodhi.zazen on 2007-02-22
> **nathanclarke said:**
> Earlier today I posted what might be described as a rant, (title - on the edge). My rant and plea for help were sent 'to jail' by a yank called Taurus (?). He didnt get it.

My problem is that nothing seems to work with ubuntu, namely my Ipod software and Nokia PC suite, both of which work fine with Windows. For the record, my rant did actually include a geniune plea for help.

Could someone please give me some advice on how to get Ubuntu to be more compatable with most things that are designed for, I guess, Windows or Mac.

Oh, and Taurus, you may have thought my rant was idiotic and impatient but, quite frankly, I have more inportant things to do with my two weeks leave. I have just come back from Iraq ( I am a Corporal in the British Army) for the third time and am off to Afghan in just over a month. I dont really want to spend it trying to make a bloody operating system work.

> **oldone said:**
> Nathan - I too have lost it with Ubuntu and these forums lack of help or some know it all moderator lose it with zero patirence when they know it and have it working and the masses are having a little to a hell of a lot of trouble getting this to work and trying to give linux and Ubuntu a fair shot.  Thanks for all you hard work over there and be safe.

I work with a lot of US military from majors to colonels to special ops and chopper pilots, and I hear and know of the horror that is Iraq and Afghanistan.

best wishes,

oldone!

the holier than though snobs and mods are not fair at all to the new people - but I thought it was linux and ubuntu for all - alll humans that is....not just the annointed ones!

To both of you, I am sorry you have found your experience with Ubutnu frustrating.

Please keep in mind a few tings :

First, as has been pointed out Linux is not windows. In general programs written for windows do not run well on Linux.

Two things that may help :[list=number][*][http://doc.gwos.org/index.php/AppHelper](http://doc.gwos.org/index.php/AppHelper)
[*][http://pcmech.com/show/os/917/](http://pcmech.com/show/os/917/)[/list]

Wine can sometimes run windows applications, but it will take time to configure most programs. See here for wine : [http://doc.gwos.org/index.php/HowToWine](http://doc.gwos.org/index.php/HowToWine)


=====================


The other point I would make it please keep in mind we are all volunteers here. While I can understand your frustration, the tone of your posts, as with most human interactions, will influence the type of response you get.

Honey attracts more flies then vinegar so to speak.

IMO the Ubuntu forums is one of the most welcoming and helpful to new users and I do not see the level of arrogance implied by oldone.

Try posting on some other forums (shop around) if you do not take my word for it.

/rant

With all that in mind you have already been given some good advice by other posters. If you have further questions, feel free to ask.

---

### Post by oldone on 2007-02-22
thanks for the 2 links - the first is better though. also I am a mac dude and not a windows dude. so windows does not apply to me. running all macs in my house for 6 years wireless out of the box and not 1 crash -  not 1 crash across 4-5 macs  does not compare to struggling weeks on end for 15 hrs a day and still no wireless with ubuntu.  

thanks!

---

### Post by nickoli_02 on 2007-02-22
> **oldone said:**
> thanks for the 2 links - the first is better though. also I am a mac dude and not a windows dude. so windows does not apply to me. running all macs in my house for 6 years wireless out of the box and not 1 crash -  not 1 crash across 4-5 macs  does not compare to struggling weeks on end for 15 hrs a day and still no wireless with ubuntu.  

thanks!

It's not linux's fault you haven't been able to get wireless working in Ubuntu. It's the wireless card manufacturer's fault for not supplying a driver for the card to be used under linux. If your card is not very popular then you will have even more trouble finding a driver for it. 

If it's possible, Intel wireless cards are pretty well supported under linux. Mine worked right out of the box.

---

### Post by nathanclarke on 2007-02-23
Thanks to all for your advice. Will try wine for the Ipod and look elsewhere for help with the Nokia PC suite situation. Oldone, your right. We newbies are obviously not deserving of these veterans time and patience. But never the less, there are those that will spare a minute or two. *snip*

But thanks again.

Ah! A side note to bodhi.zazen. 1. A *snip* will attract more flies than honey. 2. You cant always ask people to be polite and patient. Everyone is different. Being different makes us human. Ubuntu for all!! except the impatient ones. 

Impatients and orders is how I get my job done.

Thanks again

---

### Post by lyceum on 2007-02-23
Quick reply, 

1. Taurus is a good guy, just doing his "job"

2. Checkout the links in my signature, first line, they are there to help get new users started.

3. If you want it faster try these:

[Automatix](http://www.getautomatix.com/) for easy installing.

[Crossover Linux](http://www.codeweavers.com/products/cxoffice/) the easy way to install Windows programs. Linux is not Mac or Windows, so you need something like WINE to make it run, but Crossover is easier. It costs $$'s, but there is a free 30 day trail.

-edit- 
looks like Automatix's site is down right now. Sorry.

---

### Post by bodhi.zazen on 2007-02-23
> **nathanclarke said:**
> Thanks to all for your advice. Will try wine for the Ipod and look elsewhere for help with the Nokia PC suite situation. Oldone, your right. We newbies are obviously not deserving of these veterans time and patience. But never the less, there are those that will spare a minute or two. *snip*

But thanks again.

Ah! A side note to bodhi.zazen. 1. A *snip* will attract more flies than honey. 2. You cant always ask people to be polite and patient. Everyone is different. Being different makes us human. Ubuntu for all!! except the impatient ones. 

Impatients and orders is how I get my job done.

Thanks again

Just to clarify, you are welcome on the Ubuntu forums.

However, there is a code of conduct which you are expected to follow :

[http://www.ubuntuforums.org/faq.php?faq=policy#faq_forum_guidelines](http://www.ubuntuforums.org/faq.php?faq=policy#faq_forum_guidelines)

There is a difference between being welcome on the Ubuntu forums and expectations of civil behavior.


=======================


Second, I think you missed the point. You seem to take the stance that the end justifies the means. Your background in the military may serve you well, but (fortunately) the Ubuntu forms is not the military and you may find a change in strategy well help you get the help you need from the volunteer staff.

Try it and see. Make two posts asking for help on say configuring wine.

Make the first one *&%$.

Make the second one as pleasant as you can.

See which one give you the results you want.

You may also find that a similar approach has very broad applications in life.

---

### Post by Hendrixski on 2007-02-23
:-/ forgive some of us if we get a bit fed up at new users on the forums.  Some of us have answered the same questions a few too many times and reach a level where we tell users that they should just bug off and read the manual.  Don't let that stop you from asking questions though.  Someone WILL answer you.  :)

---

### Post by BigBabyDaddy1968 on 2007-02-23
> **Hendrixski said:**
> :-/ forgive some of us if we get a bit fed up at new users on the forums.  Some of us have answered the same questions a few too many times and reach a level where we tell users that they should just bug off and read the manual.  Don't let that stop you from asking questions though.  Someone WILL answer you.  :)
This is true of most online forums I've ever seen.  As for this forum in particular, I can say even the RTFM replies are far more polite than at many others.  For example, if one were to post a rant-like post on the iaudio forums, the poster, depending on how new they are, gets banned almost immediately.  On Mistic River (where I'm a bit of an old-timer :)), we sometimes play with trolls a bit before getting them banned.  Just my proverbial .02.

---

### Post by aysiu on 2007-02-23
Ask politely for support, and you'll get it.

Rant, and you'll get rants back.

Rant rudely, and you'll get jailed.

Moderators are users like you. We are not gods, and we are not necessarily programmers or Ubuntu gurus.

If you have only two weeks' leave, don't install a new OS. Run out in the sunshine. Go play.

P.S. Since this seems to have more to do with the forum itself and not Ubuntu, I've moved it here.

---

### Post by xpod on 2007-02-23
> I have just come back from Iraq ( I am a Corporal in the British Army) for the third time and am off to Afghan in just over a month. I dont really want to spend it trying to make a bloody operating system work

Why dont you just get the laptop,a live cd and take it back over yonder with you when you go?
You could sit figuring your wireless and s**t out when the tallytubbys aint keeping you busy.

At least then you could go out now an enjoy your precious leave...no???
Dont they give you much better operating systems to play with in the army btw:twisted: ???

---

### Post by wesley_of_course on 2007-02-23
Wesley here ;

  " If it is not broken, tweak it... Remember if you break Ubuntu you get to keep both pieces."


         I like that - hadn't noticed it before !

---

### Post by viper on 2007-02-23
" If it is not broken, tweak it... Remember if you break Ubuntu you get to keep both pieces."



:)  love this quote...........very clever it certainly pertains to us!!!

---

