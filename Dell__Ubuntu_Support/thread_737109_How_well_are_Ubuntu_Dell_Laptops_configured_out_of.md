---
title: "How well are Ubuntu Dell Laptops configured out of the box?"
date: 2008-03-27
forum: Dell  Ubuntu Support
---

### Post by Tuxoid on 2008-03-27
I know that this topic has been brought up quite a bit (and I have read those posts), but I'm not convinced. Call me crazy, but Dell laptops pre-installed with Ubuntu 7.10 too good to be without some type of catch. I have used Ubuntu on my LG P1 Express Dual laptop (installed it myself), and it has been a bumpy ride (some ups and downs) in terms of configuration and getting it to "just work". After my hard drive died, I basically said, "this is ridiculous, I need something actually works". As you can probably tell, I was frustrated at the time, but still, I don't want to do anymore wacky configurations to get things working.

I started looking at the Dell laptops that come pre-installed Ubuntu 7.10. Definitely seems better than what I got in terms of my laptop's hardware (especially after customization). I just want to know how well they are configured out of the box and how usual is it that their configurations break. On my LG laptop, the most major configuration break was when I upgraded Feisty to Gutsy. My SDL-Dependant apps completely broke and for some odd reason were fixed by installing libsdl from source code. Not to mention, my recording settings were extremely awkward, and it took 5 hours after my initial Feisty installation to figure out how to get sound playback to work.

Just anyway, I just want to know if anyone has had their pre-installed Dell laptop configurations break for any unusual reasons or if there was anything (excluding peripherals) that for some didn't work out of the box. I am aware of things that are obviously going to break a system configuration. I'm asking about anything that broke your system, but seemed like routine enough that it shouldn't have. Remember, I'm talking about laptops with Ubuntu pre-installed by Dell. Not Desktops or instances where you've a DIY installation or had a friend install it.

---

### Post by brownknight on 2008-03-27
I got a pre-installed Ubuntu from Dell the moment they release it with 7.04. I have an Inspiron E1505 and everything works out of the box including the multimedia buttons on front and the media home button at the top. Upgraded it to Gutsy and Im now using Hardy Heron Beta and everything still works without a flaw. One problem that I think affects many laptops wether from Dell or not is the suspend/hibernate. Suspending or hibernating manually works 100% but closing the lid gives you a hit and miss experience.

---

### Post by notwen on 2008-03-27
I ordered a Inspiron 1420n soon after Dell began offering their machines pre-loaded w/ Ubuntu.  Know that I have had a couple of small issues, but none that I have not been able to resolve.  I highly recommend it for anyone after a PC/laptop that 'just works'.  For more details on some possible issues you may run into w/ these pre-installed machines check out the [Dell Linux Wiki]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10").  They list the issues, provide workarounds/fixes and even offer custom Ubuntu images including any additional hardware drivers for the specified machine.  I have since wiped my factory Feisty install to install the new Gutsy image provided and have had zero problems.  

I would recommend a Dell N-Series system if you have the slightest bit of experience w/ Linux, but if you're easily intimidated by CLI, then you may wish to consider another option.  [System76]("http://www.system76.com/") offers systems w/ Ubuntu pre-installed w/ outstanding customer/technical support.  They even maintain a small sub-forum here on ubuntuforums.  Best of luck while shopping around for your new laptop.  =]

---

### Post by Tuxoid on 2008-03-27
Thank you very much. I also looked at system76 but I'm not to up on 64-bit. Does the word size effect how easily it operates? Also, the Dell laptop that I've been looking at seems to have more customization options than the System76 laptop I looked. System76 also doesn't seem to have a kind of payment plan like (i.e. it looks like you pay the full machine upfront). If they do, I guess I just misunderstood their website. I'm okay in the Terminal, but I much prefer the GUI. That's my comfort zone. I know any software from source needs a CLI install and that's fine. I'm okay with some CLI stuff, but I have a close cut-off point (especially on a bad day). I'll check the Dell Wiki and maybe give System76 another look as well.

---

### Post by Tuxoid on 2008-03-27
ya, those issues mentioned on the DellWiki don't seem like a big deal at all. They give system specific instructions that are simple to understand. Sounds great! :popcorn:

---

### Post by TonyLB on 2008-03-27
Don't know about the pure Ubuntu machines, but I need Windoze unfortunately (some proprietory stuff that wine won't handle).  Bought their latest XPS M1330 with (ugh)Vista.  One small partition for Vista (40gb, Vista used 20) and did a straight install with Ubuntu 7.10.  

Went like a dream, everything just works including the webcam and wireless network, with WPA encryption.  Card reader fine, multimedia controls fine, haven't tried the fingerprint thing.  The only issue is Compiz, which doesn't like the intel graphics chip.  There's a workaround, but personally I couldn't care about compiz anyway.

Tony

---

### Post by notwen on 2008-03-27
Glad you've browsed over the Dell Linux Wiki.  You may want to contact some of the System76 staff that respond to issues here about payment options they offer or if they can direct you to someone who knows.  The System76 sub-forum is [here]("http://ubuntuforums.org/forumdisplay.php?f=158").  I know they are always active on browsing their sub-forum.  Again good luck w/ your future purchase.

---

### Post by Gringexican on 2008-03-27
Since you've already read most of the posts I won't rehash too many things.  My Inspiron 1420n worked PERFECTLY the moment I got it... So far I haven't had any serious hardware issues (thank God).  The only thing close to that was some software issues (that I stupidly caused) that made it imposible for Ubuntu to talk to the hardware..  It was all fixable via Terminal using a LiveCD.  Even if you don't like the "default" Dell install (their partitioning scheme SUX), it comes with the CD so you can install it yourself then get the restricted drivers to run some of the lappie specific items.

I've not looked into Sys76 very seriously ($ was an issue for me) but a friend had one and loved it.  I saw they have some nice offerings on their site.

If you go with the 1420n, you ought to really like it.  I've heard the m1330 still has some annoying issues that Dell is working on -- but that is probably also a great box.

My primary gripe about my 1420n is that touchpad... there's not an easy way to turn it on and off for the times when you actually want it active.  sometimes the lil bugger starts making my locator arrow jump all over the screen if my hand accidentally brushes it.  My old HP had a button for activating or setting the touchpad dormant.

---

### Post by niteshifter on 2008-03-29
I've been using a 1420n (with Nvidia video / hi-res panel and Intel 3945 wireless, no built-in bluetooth) since early January.

Problems (minor):

Suspend was iffy - but hibernate works great, which I prefer, YMMV. Suspend died completely when I set the power-up password in the BIOS (enters suspend state, does not resume). Maybe fixable, I just don't care (it's a security issue for me). Hibernate still works. 

Bluetooth: No problems with my USB adapter, but couldn't do OBEX with anything. FIxed by downloads from the repos of gnome-vfs-obexftp and gnome-bluetooth. The first fixed up transfers with my phone (RAZR V3), the second transfers with my Palm TX.

"Excessive" SMART Load_Cycle_Count on hard drive. In quotes because this depends - a lot - upon how you use the machine. Fixable if it bothers you, detailed in other posts here.

Other than those three minor issues, no problems with the hardware, nor with the factory installed software. Dell gets bonus points from me on this one - no hub needed for power-hungry external drive (WD Passport, 1A load).

---

