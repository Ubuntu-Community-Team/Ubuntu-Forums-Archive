---
title: "Shopping - any dell laptop recommendations?"
date: 2008-09-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bmdavis on 2008-09-18
After a successful 2 years of ubuntu and the inspiron 6000, I'm looking to get a new laptop.

Any suggestions?  Video cards to look for?  Certain builds that are best? Processors?

Thanks guys, 

    bmdavis

---

### Post by Bucky Ball on 2008-09-18
Dell uses the generally problematic Broadcom wireless cards in the Studio 15 but despite this, people seem to be getting their wireless connections up!

---

### Post by notwen on 2008-09-18
I have had a Inspiron 1420n since their first initial releases w/ Ubuntu Feisty pre-installed and have been very happy.  I have since upgraded from Feisty to Gutsy and from Gutsy to Hardy.  I would suggest looking into the Inspiron 1525n, only for the reason that it has been available w/ Ubuntu longer than the XPS and Studio machines.  

Only hardware I would recommend is Intel wireless, other than that Hardy pretty much covers most of the previous issues involving graphics chipsets.  Check out my thread [here]("http://ubuntuforums.org/showthread.php?t=762770"), it has lots of useful info and links regarding Dell's Ubuntu machines from the past and present.  Be sure to post any questions and good luck w/your future purchase.  =]

---

### Post by superm1 on 2008-09-18
> **Bucky Ball said:**
> Dell seems to use Broadcom wireless cards in the Studio 15 which, at this point, seem extremely problematic.
Other than an issue with SSH through NAT, how so?

---

### Post by aidave on 2008-09-18
I have a Dell 1420n, and while I do like it, I cant recommend it if you want Suspend/Resume, since that feature does not work reliably.  I think that may be only true with 1420n and NVIDIA cards, but I am not sure.

---

### Post by notwen on 2008-09-18
> **aidave said:**
> I have a Dell 1420n, and while I do like it, I cant recommend it if you want Suspend/Resume, since that feature does not work reliably.  I think that may be only true with 1420n and NVIDIA cards, but I am not sure.

Hit or miss on my 1420n as well w/ Intel graphics.  Kinda had off and on luck w/ it from Feisty, to Gutsy and now on Hardy even.  One day. =]

---

### Post by wgarider on 2008-09-18
I bought a 1525 at Best Buy last month - price was better than what was avaialble online at the time. It came with Vista Home something but I wiped that in favor of using the Dell Ubuntu ISO that loads 8.04.1

Only issue I had was getting the wireless working and in hindsight, that was probably my doing.

---

### Post by Talon2 on 2008-09-18
> **bmdavis said:**
> 
Any suggestions?


[http://configure.us.dell.com/dellstore/config.aspx?oc=dncwxa1&c=us&l=en&s=dhs&cs=19&kc=productdetails~laptop-inspiron-9](http://configure.us.dell.com/dellstore/config.aspx?oc=dncwxa1&c=us&l=en&s=dhs&cs=19&kc=productdetails~laptop-inspiron-9)

---

### Post by Bucky Ball on 2008-09-19
> **superm1 said:**
> Other than an issue with SSH through NAT, how so?

My bad. I was helping someone and researching and ripping my hair out (eventually a more experienced head joined in) only to discover a post saying the OP had been trying to connect through a secure school network. They got the machine home and all worked fine immediately!

I might just add, thanks for your fantastic work and contribution to the community appreciated by myself and I am sure many others re wireless and other things. :)

---

### Post by pauljw on 2008-09-19
> **bmdavis said:**
> After a successful 2 years of ubuntu and the inspiron 6000, I'm looking to get a new laptop.

Any suggestions?  Video cards to look for?  Certain builds that are best? Processors?

Thanks guys, 

    bmdavis

I have been extremely happy with my new Studio 1535.  Everything worked right out of the box.  Wifi, built in webcam, everything.  I highly recommend this machine with linux pre-installed.

---

### Post by anjilslaire on 2008-09-19
So, the standard "Dell wireless" cards they ship in most laptops are good to go now?
That's nice to hear :)

---

### Post by pah99 on 2008-09-23
I recommend a Studio 1535. Its an awesome laptop. However, you can build one cheaper with Vista than with Ubuntu (off of the Dell website). You also get more options (like back lit keyboard, which is awesome). If you build it with Vista, don't get the Dell N card as its not supported yet by Ubuntu. Other than that, its all good. After you get the laptop you can return the Vista license and get some cash back from Dell. So yeah, hope that helps.

---

### Post by fabietto0102 on 2008-09-23
Hi pah99,

so to be clear, you tell me you had absolutely no compatibility problems with the Dell Studio 15 and Ubuntu 8.04 in regards to wifi? I read many posts and some say to have a problem with the Dell Wireless 1397 Mini Card (802.11 b/g). Is it the same wifi card as yours? I am right about to buy the 499£ Studio 15 from dell.co.uk and don't wanna have problem with the wifi!
Thanks
Fabietto0102

---

### Post by pah99 on 2008-09-23
Um, no I apologize. For all who misunderstood. I bought my Studio with a Dell 1510 Mini N card. When I ran Ubuntu by means of live CD, it could not recognize the card. So, don't get the Mini N card. I believe that the a/g card is compliant with Ubuntu, but I would definitely look around on the forums to make sure.

---

### Post by superm1 on 2008-09-23
For the Studio 15:

The packages in the current 8.04.1 support the B/G variants of the Broadcom card.  The packages in the "proposed" component of 8.04.1 support the N variants of the Broadcom card.

Not to overly reiterate what I've mentioned in other threads, but if you want to support Dell continuing to put Ubuntu on these machines, and Ubuntu is available in your locale, buy them with Ubuntu.  This shows that Ubuntu is desired and should be put on more machines.

---

### Post by pah99 on 2008-09-23
Oh, I totally agree with you in that people should buy Ubuntu laptops and computers from Dell. However, what I said was that I got a better deal buying the laptop with Vista. If Dell wants people to buy the Ubuntu variants, then have the computers configured similarly. The only reason why i chose the Vista laptop instead of the Ubuntu one was because the Vista one had a back lit keyboard. That is the only reason. But this is going off topic, and so i apologize.

---

### Post by UncleOwl on 2008-09-24
Just got myself a Dell XPS M1330. Almost everything works out of the box (Intel graphics, sound, suspend, wireless, webcam). The fingerprint reader was easy to configure  with Thinkfinger using [this guide]("https://wiki.ubuntu.com/ThinkFinger") (later I also used the ghex2  editor to replace the standard login message in /lib/security/pam_thinkfinger.so - simple find-replace works, just keep the message length the same). The media player buttons also did not work at first try (don't have much use for them anyway, so I did not try very hard), but the volume buttons (up,down,mute) do work.

Overall, I'm pleased. The machine looks good, is light and plays nicely with the penguin. Did not even have to pay the Bill tax, it was sold to me without Vista (I don't do Windows since 2000). :)

---

### Post by fabietto0102 on 2008-09-24
Rather than encouraging Dell to build more of these Ubuntu Dell laptops by buying those machines, I would suggest to buy whatever the market has on offer and ask for a refund of the MS licence. In this way, you encourage Dell or other manufacturers to give the chance to opt for an OS free system from the beginning, right when you buy it. 

In other words, rather than choose between either Ubuntu or MS computers, the choice should be between MS computers and OS-free computers. This benefits both parts, included other distro users who of course don't really care about having Ubuntu preinstalled if they use, say, openSuse or Mandriva.

---

### Post by pauljw on 2008-09-24
> **fabietto0102 said:**
> Rather than encouraging Dell to build more of these Ubuntu Dell laptops by buying those machines, I would suggest to buy whatever the market has on offer and ask for a refund of the MS licence. In this way, you encourage Dell or other manufacturers to give the chance to opt for an OS free system from the beginning, right when you buy it. 

In other words, rather than choose between either Ubuntu or MS computers, the choice should be between MS computers and OS-free computers. This benefits both parts, included other distro users who of course don't really care about having Ubuntu preinstalled if they use, say, openSuse or Mandriva.

Sorry, can't really agree with this.  Look at all the problems different distros have in spite of having teams of devs to conquer compatibility issues.  This includes Ubuntu.  So for a system builder to be successful, they really need to pick one and make it work.  Dell did this with Ubuntu, I opened the box, plugged the machine in and it just worked, sound, video, DVDs, webcam, wifi, everything.

I was not an Ubuntu user prior to this purchase, but face it, linux is linux.  Because the system works so well, there's no need to attempt to put my "favorite" distro on here.  I'll just learn Ubuntu.  It's actually just learning Gnome rather than KDE for me.  I stand by my original post, this was a huge risk and undertaking for Dell to accomplish this with this level of success.  They should reap the reward from us, the linux community, which has been yelling for just this sort of dedication from a vendor.  

This is the key to getting linux on the desktop of the average computer user.  If linux doesn't come pre-installed, it will never make it to Main Street.  Not that I care about that ever happening.  I personally believe that the average user is better served by MS and would just as soon they stay away from linux.  But if all they have to do is plug in the machine and use linux, that opens the door to literally millions of people who are capable of using this OS.

---

### Post by superm1 on 2008-09-24
> **fabietto0102 said:**
> Rather than encouraging Dell to build more of these Ubuntu Dell laptops by buying those machines, I would suggest to buy whatever the market has on offer and ask for a refund of the MS licence. In this way, you encourage Dell or other manufacturers to give the chance to opt for an OS free system from the beginning, right when you buy it. 

In other words, rather than choose between either Ubuntu or MS computers, the choice should be between MS computers and OS-free computers. This benefits both parts, included other distro users who of course don't really care about having Ubuntu preinstalled if they use, say, openSuse or Mandriva.
I don't agree with this at all.  There is a development effort required for making these systems work.  Systems that aren't normally offered with Ubuntu that happen to work only happen to work because they share similar hardware configurations to the ones that there was an effort to get working.

By refunding your license you are delivering a message that you don't like the MS license that comes with the system, but you don't deliver any message that you want the system working well with another particular OS.

---

### Post by fabietto0102 on 2008-09-24
Thanks for your feedback on my comment, I hope I haven't make you upset too much. Fact is, however, that by buying a Studio (and, btw, so far in the UK shop Ubuntu is sold only on Inspiron and XPS) I get better value for money. I wanted so much to buy a pure Ubuntu Dell (God knows how much I hate to configure wifi, webcam etc all by myself: I had a Mac before and it was hell!), but comparing the 2 you don't get the same components. Even though you spare money on the MS licence, you end up paying good 100£ (200$) more for the same specifications. I don't get why and I don't get why they don't sell the studio at least OS-free, if not with Ubuntu.

Dell tracks the amount of click in their Ubuntu sites, and I tell you I went there so often to find a better deal that they understood people want Ubuntu. I guess they are smart enough to understand that MS based laptops offer better value for money. And given that you developers confirmed that the Studio 15 works great with Ubuntu, I don't see why I have to go for the Ubuntu laptop.

---

### Post by bmdavis on 2008-10-01
Thanks guys!

Ended up going with a refurbished vostro 1500 for $600.... core 2 duo, 2gb ram, installed the heron and everything worked instantly!! Only problem I have had is a very small one ( see - [http://ubuntuforums.org/showthread.php?t=935028&highlight=bmdavis](http://ubuntuforums.org/showthread.php?t=935028&highlight=bmdavis))

Sounds like more Dells are having less problems, so good to hear.  Loved the discussion, thanks for the help.

---

### Post by fabietto0102 on 2008-10-02
Hi Bmdavis,

congrats for your buy! Unfortunately I cannot help you with your lid/wifi problem, however it's normal having a small problem here and there if you use Ubuntu and you are not expert enough to fix it (like me!). I can tell you Ubuntu has improved a lot despite 8.04 who is for me a bit disappointing (I loved 7.10!). Let's cross the fingers for a better 8.10!!

I want to confirm for other possible Dell Studio buyers that everything worked out-of-the-box: Wifi & graphic card, microphone, webcam, card readers, volume buttons, etc. It's the first time I install Ubuntu on a machine and everything works without any tweaks. Great job, Ubuntu developers!

---

### Post by pah99 on 2008-10-04
I just wanted to correct a previous post. I have a Dell Studio 1535. The Dell 1510 mini N card is now supported out of the box by 8.10. It also gives me the proper resolution for screen, (ATI Mobility 3450 HD 256 MB) (although I can't install the video drivers yet as ENvy is still buggy). Other than that, everything works awesome. And just so you all know, 8.10 is awesome. I can't wait for the final release.

---

