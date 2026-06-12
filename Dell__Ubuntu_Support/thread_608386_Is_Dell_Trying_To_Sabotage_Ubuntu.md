---
title: "Is Dell Trying To Sabotage Ubuntu?"
date: 2007-11-09
forum: Dell  Ubuntu Support
---

### Post by bunted on 2007-11-09
I have been a staunch supporter of Ubuntu for the last few years.  I was the very first person to order a Dell E1505n with Ubuntu installed (well, at least according to the CSR I spoke with).  So after time and time again of my arguing for free software, my father decided to purchase a Dell Ubuntu notebook as well.  This was an amazing step for my MCSE'd father and I encouraged his new purchase and the opening of the new free sofware horizon he was approaching.

A day ago, my father's e1520n arrived and he immediately got me on the horn.    Trying to change the video driver through the desktop interface crashed the machine.  Even a dpkg-reconfigure of the xserver would crash for some reason.  We had to manually edit his xorg.conf file just to set the driver as something besides vesa.  After troubleshooting his non-existent Desktop Effects, it seems that the Intel X3100 graphics card is blacklisted by compiz.  My father just payed $1600 for all of the bells and whistles.  However, the bells and whistles that make Ubuntu a real, modern OS (eyecandy) are impossible with any of Dell's notebook offerings, because you only have one.  There is no other laptop choice beyond the 1520 and no other video card choice besides the X3100.  So, in essence, it is impossible to run Ubuntu at it's full fancy capacity with offered Dell hardware.

Now don't get me wrong, I have read about hacks that let you use compiz with this graphics card, however, is it too much to ask that Dell releases a product that just works?  These kinds of hacks for a brand new machine that should function out of the box, as it has been certified by Dell Engineers for Ubuntu, is absolutely absurd.  Besides, even though my father is MS and Novell literate, he is basically linux inept.  You should have heard the hour conversation explaining limited user privilege and sudo . . .  

I have also run into problems with my own 1505n.  With the i810 display driver, I was unable to use a resolution higher than 1024x768.  With the intel driver, you lose the Fn+F8 functionality for multiple monitors.  Even so, an external monitor only clones to the same resolution as the desktop.  My tv-out has never worked.  Sound in SDL games is scratchy and when I plug my headphones in with a mostly white screen I get noise in the audio as well.

I let the problems with my first laptop go, chocking them up to a first generation offering.  More time and exposure to different Dell Ubuntu offerings give me more reasons to speculate on why Dell would put buyers into such a paradoxical, hopeless situation, which seems to sabotage Ubuntu's gaining any real notebook market share, but it still leaves me having to return my father's laptop, and possibly having to buy another with a MS license fee attached.  This entire situation makes me very frustrated.  So I ask my fellow Ubuntu forums posters for any solution for this predicament.  I am definitely going to return this notebook, because I refuse to help Dell's bottom line anymore.  Is there any real solution for getting my father a new laptop that runs Ubuntu with full hardware compatibility without filling the pockets of Microsoft?  We are looking for similar specs as the 1520.  I just hope he doesn't have a sour taste in his mouth after this . . .

---

### Post by saru411 on 2007-11-10
if you dont wish to purchase a dell, you could always purchase a system 76. they have been supporting ubuntu for awhile now, even before dell got the ubuntu bug. i understand your issues with not wanting to support MS, but they control almost 100 percent of the laptop market. your only good options are researching and installing ubuntu yourself over a copy of MS or purchasing from the wonderful people at system 76. they have a sub forum here just like dell. look under the main categories.

this is their home page [http://www.system76.com/](http://www.system76.com/)

i wish your father the best in his free as in freedom software experience

---

### Post by kinemagician on 2007-11-10
Thanks for pointing out to system 76. Howevere, they do not ship outside USA and Canada.
Do you know of any system 76 equivalent in Europe?
Thanks,
Ettore

---

### Post by shomboli on 2007-11-10
I've had a Dell i8500 laptop with XP-Pro on it for 4 years. I recently discovered Ubuntu, and installed Feisty Fawn (7.04) on a 2nd disk in the module bay a month ago.. It took many hours of online research to get all the hardware working with Ubuntu, but I did it, and upgraded pretty smoothly to Gutsy Gibbon (7.10) 2 weeks ago, and figured out how to dual boot, too. I'm impressed by the speed the laptop boots and runs at in Ubuntu compared to XP-Pro. Of course, it's not loaded up with as much bloated software in Ubuntu.

BTW, I'm an old retired chap, too; I retired from a career as an IBM computer tech.

---

### Post by bunted on 2007-11-10
> **saru411 said:**
> http://www.system76.com/[/url]

i wish your father the best in his free as in freedom software experience

Thanks for the info saru.  A similar hardware config is actually a little cheaper from System76 than from Dell.

Any more options?

---

### Post by tturrisi on 2007-11-10
>  Is Dell Trying To Sabotage Ubuntu?
Absolutely not!
First of all, realize that there's no such thing as "works out of the box" when it comes to Linux, even the Linuxant boxes have issues and require user hacks.  Dell is simply trying to capture a portion of a very small market (pre-installed linux comps).  

Your father (and you) would have been better off ordering a different Dell comp from the Dell Business site configured with exactly what you want for much less money.  

I recently purchased a Dell notebook after doing my research.  I paid $1300 for a system that is far more robust than the 15xx Dells.  Yes, it required some hacking, but the effort is well worth it.  details:
[http://members.cox.net/tonyt/d830/](http://members.cox.net/tonyt/d830/)

Dell would not be offering linux comps unless they felt that it was economically viable for them to do so.  It remains viable because there are no support costs for them.  And the hardware they use is of the cheaper quality. (less expensive for them)

---

### Post by Linicks on 2007-11-10
Another UK outlet:

[http://www.linuxemporium.co.uk/products/laptops/](http://www.linuxemporium.co.uk/products/laptops/)

Nick

---

### Post by aysiu on 2007-11-10
> **tturrisi said:**
> Absolutely not!
First of all, realize that there's no such thing as "works out of the box" when it comes to Linux, even the Linuxant boxes have issues and require user hacks. Sure there is.

As a matter of fact, all three computers (one Dell laptop, two eMachines desktops) I've installed Ubuntu on have worked out of the box.

My Dell Inspiron 500m worked "out of the box" with both Ubuntu 7.04 and Ubuntu 7.10. I mean everything--laptop hotkeys, resume from suspend to RAM, sound, screen resolution.

---

### Post by JBAlaska on 2007-11-10
After recently getting my hands on a older laptop (Compaq Presario 2500) and giving it a new lease on life with Gutsy, your post got me thinking about a brand new shiny lappy.

I found this link ```
http://www.linuxcertified.com/linux_laptops.html
```

I have no idea about these boxes, but they might be worth looking at. (Also they have a link at the bottom of the page for Lenovo ThinkPads with Linux).

---

### Post by bluedragon436 on 2007-11-10
Honestly I have a D610 that I installed Ubuntu on and after doing a few small tweaks I have had not issue at all with being able to run Ubuntu at its max capabilities, with the exception that my standby and hibernate doesn't work....  so I don't think Dell is trying to sabotage anything, and if i can say anything Dell was not the one I though would be the first to try and promote Ubuntu.....at least they are giving it a chance....I know of at least four people who have purchased the preloaded Dell's and have had no issues.....

---

### Post by bunted on 2007-11-10
> **bluedragon436 said:**
> I don't think Dell is trying to sabotage anything.

Then why would they offer the 1420n with other graphics cards when you order Windows, but not Ubuntu?

---

### Post by aysiu on 2007-11-10
> **bunted said:**
> Then why would they offer the 1420n with other graphics cards when you order Windows, but not Ubuntu?
Maybe the graphics cards they offer with Windows are not Linux-compatible?

---

### Post by tturrisi on 2007-11-11
> **aysiu said:**
> Sure there is.

As a matter of fact, all three computers (one Dell laptop, two eMachines desktops) I've installed Ubuntu on have worked out of the box.

My Dell Inspiron 500m worked "out of the box" with both Ubuntu 7.04 and Ubuntu 7.10. I mean everything--laptop hotkeys, resume from suspend to RAM, sound, screen resolution.

...untile the next Ubuntiu release, when something will break because changes are made to packages or kernels or HAL, or when upgrading existing packages, including any security upgrades.  There is always the likelyhood of something not working as a result of updates and upgrades.

---

### Post by aysiu on 2007-11-11
> **tturrisi said:**
> ...untile the next Ubuntiu release, when something will break because changes are made to packages or kernels or HAL, or when upgrading existing packages, including any security upgrades.  There is always the likelyhood of something not working as a result of updates and upgrades.
I was responding to your statement that > there's no such thing as "works out of the box" when it comes to Linux I didn't see that everything *always* works.

Just so you know, though, the Gutsy upgrade was a flawless one for me. I know other people have had issues with it, though.

---

### Post by PmDematagoda on 2007-11-11
Personally I've had a very good experience using Ubuntu on non-Dell PC's as I have managed to install Ubuntu/Kubuntu/Xubuntu on 6 different PC's with no problems at all.

So basically it all comes down to the fact that the hardware of the PC must be Linux-compatible, some of it could also depend a little on the flavour of Ubuntu you try to use since the pre-installed programs can make a difference.

---

### Post by nooblot on 2007-11-11
> **bunted said:**
> I have been a staunch supporter of Ubuntu for the last few years.  I was the very first person to order a Dell E1505n with Ubuntu installed .
LOL  and where have you been ? Fedora forum ?  :)
and I just started with Ubuntu and I already have more posts than you hahah

[QUOTE=bunted]....My father just payed $1600 for all of the bells and whistles.  .....[/QUOTE] :shock: wow $1600 and didn't get the nVidia but the default Intel card ??? :???:

Incredible.....not much of a " bells and whistles" I guess.

---

### Post by kuja on 2007-11-12
> **nooblot said:**
> LOL  and where have you been ? Fedora forum ?  :)
and I just started with Ubuntu and I already have more posts than you hahah

 :shock: wow $1600 and didn't get the nVidia but the default Intel card ??? :???:

Incredible.....not much of a " bells and whistles" I guess.

There's more to things than a high post count...


There's also more to a computer than a graphics card. Looking at it from a different perspective, I would venture to guess that the intel X3100 probably consumes less power so you'll get more battery life. The additional cost could have been incurred by upgrading other hardware too (screen, ram, cpu, hdd) or by adding paid support.

---

### Post by satbunny on 2007-11-12
My Dell arrived last week and it did require final configuration with regard to language, location. I then upgraded from 7.04 to 7.10, had to tell it my graphic card and monitor, then installed the nvidia proprietary driver using Restricted Driver Manager and all worked fine.

This is a UK sourced N Inspiron 530.

It is not a laptop. I have found Acer laptops and Lenovo Thinkpads very easy to install Ubuntu on from scratch.

I do recognise your annoyance though..

---

### Post by Linuxratty on 2007-11-13
You'd think it...This is what happened to me:

 I posted this at Dell's idea Storm.
People who use Windows get a restore disk,people who use Linux should get a restore disk as well.
I just bought a Dell last week...The update manager stopped working in Ubuntu.. So I went to the Ubuntu forums and pasted in the correction into the terminal which should have fixed the problem.-
It did not work.
I reinstalled the OS.
The machine would no longer go on line.
I finally end up at Dell tec support for Linux where I'm told there are missing drivers..So since Dell already knows about this,why are the drivers not installed on Ubuntu or supplied on a recovery disk,along with instructions for people new to Linux?
Anyway, I'm sent to a web page to download the drivers. Lucky for me a friend has let me borrow her computer,or I'd be up the creek without a paddle. I have yet to burn the disk though,as I'm only a guest on said computer.

I have to wonder who else this has happened to and if they can't download the drivers,what have they done? Have they set the machine on the curb for trash pickup?
This foul up is going to make a lot of people really unhappy and Dell needs to have fixed this before they decided to load Linux on their first box. There is no excuse for such inept sloppiness on the part of a professional company.
Had I known about this, I NEVER would have bought a Dell.

Anyway,I just so you know,Dell did provide a video drivers disk with Ubuntu...The problem was the disk had only Windows drivers....Which is useless..
Somebody at Dell needs to get a clue.

---

### Post by cheetaux on 2007-11-14
Dell has a "remastered" Ubuntu 7.04 ISO image available for download at [http://linux.dell.com/wiki/index.php/Ubuntu_7.04]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04")
The ISO image should include all of the drivers, etc. needed to reinstall Fiesty Fawn.

They are supposedly working on a "remastered" Gutsy image.

---

### Post by satbunny on 2007-11-14
AAAAAH!

Well my machine went tits up after upgrading to Gutsy so I tried to reinstall.
The machine is having some very weird issues but 10% of the time it manages a proper reboot. On one of those I reinstalled 7.04 from the disc in the box.

But oh dear! No network....

sigh..

Having said that Dell support are very good when you've paid for them.. 

I agree though, a simple disc image reinstall in the box, which just avoids all the reinstall issues and writes a totally installed system onto the box if you screw up.
Telling people about the issue would help as well, since some people are going to want to put other distros on these machines some day and this issue will cause them problems.

I can't say that Dell are trying to sabotage anything, it's early days for them and there are bound to be some hiccups..

---

### Post by 504harry on 2007-11-14
> **tturrisi said:**
> Absolutely not!
First of all, realize that there's no such thing as "works out of the box" when it comes to Linux, even the Linuxant boxes have issues and require user hacks.  Dell is simply trying to capture a portion of a very small market (pre-installed linux comps).  

Your father (and you) would have been better off ordering a different Dell comp from the Dell Business site configured with exactly what you want for much less money.  

I recently purchased a Dell notebook after doing my research.  I paid $1300 for a system that is far more robust than the 15xx Dells.  Yes, it required some hacking, but the effort is well worth it.  details:
[http://members.cox.net/tonyt/d830/](http://members.cox.net/tonyt/d830/)

Dell would not be offering linux comps unless they felt that it was economically viable for them to do so.  It remains viable because there are no support costs for them.  And the hardware they use is of the cheaper quality. (less expensive for them)

Hi, . . . may I add...?
I really thought Ubuntu worked "from the box" - take for example the Live CD which (slowly) manages to do most things and Firefox does a reasonable job on the Internet. Sure there are issues with Scanners and not all "popular" printers are easily confirured and some not at all. So issues with software is my gripe where Authors have tried to become so like Win, they have copied all the inconveniences and missed the opportunity to create a New Way.
However, things like USB-support appears pretty good, to the extent that many folks "should" be able to switch-on their computer and produce some useful work.

At present, the market for Linux is pretty small. This is largely caused the the wasteful "parallel effort" whereby the brains of the movement are not working towards the same goal. Er, IMHO, that is.
Given that Linux is "niche" then you can't expect Dell ( or anyone else), to get everything sorted out - - even if they knew how to.
Ubuntu strikes me as beinig the best chance that Linux has ( to be a viable alternative to Win) - and I guess that MS is so big that many fear their License Conditions and their "forever" SP update regeme. When I say "forever" of course that is upward of four years...IMHO.

I haven't the technical knowledge, but have a sneeky suspicion that Dell ( and other "brands") PC's are somehow not "quite PC's" - having very slightly non-standard addressing - just enough to make customers come back to "Support" - with their wallets.   Does anyone know if **modern **Dell Notebooks are really easy to configure - being standard PC's...?

It's my belief that the co-operation of Dell and Ubuntu can only be a Good Thing, although initially there may be issues. I understand that any Dual-Boot should install Win fiorst, then Ubuntu - can anyone confirm this IS possible on Dell, or does it come with Ubuntu-alone,  thereby preventing a dual-boot laptop?
Also I presume that the answer to the above really hinges on the "standardisation" of the Dell PC.

---

### Post by tturrisi on 2007-11-15
> I haven't the technical knowledge, but have a sneeky suspicion that Dell ( and other "brands") PC's are somehow not "quite PC's" - having very slightly non-standard addressing - just enough to make customers come back to "Support" - with their wallets. Does anyone know if modern Dell Notebooks are really easy to configure - being standard PC's...?
They are standard pcs.
Not sure what you mean by 'standard addressing', the hardware is pc hardware.
Dell Linux support is free, afaik there is no paid support for these pcs, unless Dell includes a paid support option at purchase time.
These pcs don't come w/ any Windows, just ubuntu.

Dell is partnered w/ may hardware vendors and software vendors.  Their biggest partner is MS, thus Dell won't go full swing into the linux desktop market else they could jeopordize their business.

---

### Post by satbunny on 2007-11-15
In that sense, all PCs are slightly variant to each other.
That is the nature of the open PC architecture and the organic way that stuff has been added.
I have found Dell PCs very easy to install Linux on, our University is full of them. Which I why my problems with a Dell bought with Ubuntu on is ironic!

---

### Post by kuja on 2007-11-15
> **tturrisi said:**
> They are standard pcs.
Not sure what you mean by 'standard addressing', the hardware is pc hardware.
Dell Linux support is free, afaik there is no paid support for these pcs, unless Dell includes a paid support option at purchase time.
These pcs don't come w/ any Windows, just ubuntu.

Dell is partnered w/ may hardware vendors and software vendors.  Their biggest partner is MS, thus Dell won't go full swing into the linux desktop market else they could jeopordize their business.
They off paid support for the hardware, I should know, as many letters and phone calls I got with them trying to sell it to me. Rather than offering software support directly they give you the option to get proper software support through canonical when you buy it.

---

### Post by bluedragon436 on 2007-11-18
I understand having issues with a few components on laptops, and I know that some video cards are not Linux compatiable as of yet...they are working on it though that much I do know.  Dell is still working out some kinks, but all things considered they are doing a pretty decent job, seeing as how they are one of the only mainline companies offering any Linux OS from the factory.  There is going to be small kinks to work out no matter what OS it runs, I have had more issues to work out with some of the MS based OS equiped products then I have with Ubuntu thus far, I realize every computer setup is different depending apon the models, as well as the OS's...

---

### Post by fragos on 2007-11-19
I just purchased an Ispiron 1420n w/7.04 installed and everything works great.  All the necesary drivers are there for the miscelanious proprietary buttons, WiFi switch and SD reader.  The Intel 3100 and Wifi card were selected for this model because they have good Linux support.  WiFi even works with roaming.  I choose to wait until Dell tells me 7.10 is ready for my laptop.  Doing otherwise has resulted in problems for those of little patience.  It is common for laptops to use proprietary hardware for some device specific features.

---

### Post by magaio on 2007-11-20
Bunted, I have some suggestions for your problems. Obviously I can't solve the problem about things "just working". But I probably don't need to add any comments about the fact that this is a noncommercial, decentralized operating system on competing, commercial, proprietary hardware.

For your resolution woes concerning the Intel graphics chip, did you try:

```
sudo apt-get install 915resolution
```

Many intel chips' bios do not directly support the high or widescreen resolutions of LCD panels--you probably knew that though.

If you have a sigmatel sound card, you might try the following to relieve your scratchy sound and weird recording:

**append to /etc/modprobe.d/alsa-base:**

```
options snd-hda-intel model=ref
```

**append to /etc/modprobe.d/options:**

```
options snd-hda-intel position_fix=1
```


These fixes worked for me on my E1505n laptop--Iearned about them by studying, searching, and failing many attempts. It was painful but now I am a lot stronger for it. Sorry for your disappointment, but that's what you get when you throw a noncommercial OS to the commercial hardware wolves--I feel your pain. I have come to terms that older folks don't want to learn computer science just to do the simple tasks, so I recommend a more mainstream OS.

I am quite happy with how far Ubuntu has come and I wish you the same happiness. In addition, I am happy to fill Dell's pockets in this case because, with the two exceptions above, it did "just work", and they are indirectly supporting FOSS with the sales of these linux machines. In my eyes, Mac just works and is beautiful but I want the freedom to know and learn about every aspect of my operating system. Not everyone wants that freedom. Remember: With freedom comes danger and responsibility. Good luck to you and yours.

---

### Post by canoemoose on 2007-12-19
> First of all, realize that there's no such thing as "works out of the box" when it comes to Linux, even the Linuxant boxes have issues and require user hacks. Dell is simply trying to capture a portion of a very small market (pre-installed linux comps).


Oh, right.  I have installed 6.06 on 4 desktops and a laptop, it worked out of the box.  I have installed 7.04 on a desktop assembled out of 2 other desktops (spec in sig) and it worked out of the box. Hmm.

---

### Post by satbunny on 2007-12-19
Oddly I installed 6.06 to 7.10 on my last Dell 'out of the box' and it was only the new Dell that I had problems with..

---

### Post by fragos on 2007-12-19
Just downloaded Dell's 7.10 DVD and installed it on my 1420n.  There didn't appear to be an upgrade path with the DVD so I did a new factory install.  So far so good.  It's busy installing updates from the Ubuntu repositories right now using WiFi which worked without additional configuration.  Everything worked with the pre-installed 7.04 so I expect 7.10 will be the same.

---

### Post by bunted on 2008-01-27
Just an update.

My father returned that piece of crap from dell and ordered a new notebook from system76.  No problems.  They rule.

---

### Post by motoperpetuo on 2008-03-31
i got a dell desktop with ubuntu preinstalled a little over a week ago, my logic being that it would "just work out of the box" since, after all, it's designed to work with linux, right?

no such luck there. it was mostly great, but had one major problem: it couldn't boot linux live CDs. Gparted, clonezilla, puppy linux, or the Ubuntu or Mint live CDs would either error out with cryptic references to loops and tty, or (even stranger) boot to dell's restore partition. windows CDs booted just fine, for some reason.

largely due to some good troubleshooting ideas from dell ubuntu support line (everyone there was great, and very helpful) it finally occurred to me to try wiping the hard drive. this was a last-ditch effort before returning the computer to dell. i had to use a windows CD to do it (which was irksome), but after the hard drive was wiped, i was able to install linux mint and clone my hard drive with clonezilla.

still, it seems unlikely that dell is trying to sabatoge ubuntu. indeed, i haven't seen any complaints about this happening on other 530n desktops. so maybe i just got "lucky"? i'd definitely like to hear about how others have fared with preinstalled ubuntu computers from dell.

---

### Post by fragos on 2008-03-31
1420n with 7.04 worked great.  I upgraded to 7.10 with the Dell DVD and everything still worked.

---

### Post by natehall on 2008-04-01
I'm doing this post on Factory Installed 1420 and I'm in agreement with Fragos. I love this machine and Ubuntu. ( GIMP is my favorite part )

---

### Post by notwen on 2008-04-01
I recieved my Inspiron 1420n on August 1st of 2007.  I had no issues out of the box and I upgraded to Gutsy sometime after New Years w/o any issue.  Any of the small problems I've came across Dell had listed on their Linux Wiki provided workarounds/fixes and were very easy to do.  I am very happy w/ my purchase and would recommend it to anyone who is comfortable w/ Linux enough to where they can copy and paste some commands into a terminal.  

+1 for Dellbuntu  =]

---

### Post by LeoSolaris on 2008-04-01
I had an amusing time ordering a Dell just before New Years last year. I had been using an older laptop with Gusty, but it broke, so with some scrapped up Christmas money, and the tail end of my college loans, I managed to get an Inspiron 1520. I didn't know at the time that Dell had Ubuntu preloaded laptops, or I would have looked at them...

The really amusing part came when I was talking to the online help person about having them partition my hard drive so I did not have to do it. She asked why I wanted it and I told her that I intended to put Linux in a couple of the partitions and she told me that it would violate my EULA with Windows to put Linux on my machine, then closed my chat session! I really hope she got fired. She did not even mention that there were Ubuntu preloaded Dells. 

To tell you the truth, I am rather surprise that I ended up buying a Dell after that. I get the feeling that this was a case of the right hand not knowing what the left is up to. 

I am rather glad that I got a Windows one and installed Ubuntu through, since I was able to get a pretty decent graphics card and a wireless N rather than G integrated (Not a bit of issue with it in Ubuntu, too.)  

After telling the Customer support person about that help person I initially chatted with, they gave me a $250 voucher and even applied it to the remaining credit on my system. Let me pay it off by January. All in all because I got a Windows system through Dell, I got a $1,500 laptop for around $750 or so. I count it as a pretty good buy, since it ended up being just $250 more than the EEE I was originally eyeballing.

---

### Post by MedellinManDem on 2008-04-01
Aside from a few minor issues, my Vostro 1500 works beautifully with Gutsy.

**** Microsoft.

---

### Post by chaos315 on 2008-04-16
I have two dell laptops and have gutsy on both of them, my older one does not have windows on it, but my m1330 has gutsy and vista on it. I have had a few problems with it, but nothing that was not easily fixed. While encouraged by dells willingness to preinstall ubuntu, I am stupified by their unwillingness to pair compatible hardware. I know that it exists because we all use this hardware (maybe with a few hacks). But dont you think that they could do a few of these since it is a brand new machine? I believe that no matter what - a brand new computer should work right out of the box. Period. I don't know what the results are, but I know that even this m1330 comes with some different hardware in the linux version than the MS one that I bought. Obviously this hardware works, and if I (a noob) can do it, then certainly the brainchildren at dell should be able to. I am a noob to linux, not business, dell stands to lose money if windows pulls support from them. They cannot make money based on linux box sales and we all know that gates is evil, so is windows forcing dell to sabotage ubuntu?

---

### Post by inphektion on 2008-04-18
I have no idea why'd you'd even buy one pre installed with Ubuntu.  You are so limited to choice at that point and getting one with XP is no more more money.  then just install ubuntu over it formatting drive or use as dual boot.

---

### Post by starcannon on 2008-04-18
I had a 1420n with x3100, while overall 3d performance was not so hot, compiz worked excellent for me out of the box.

That said, I would note that for a few dollars more the nvidia option makes all the difference, I bought my mom a 1420n with the Nvidia 8400m gs in it and 2gb of ram, only spent $865 and it is absolutely fantastic.

Best bet, as with any computer, any operating system, research then buy, I'd also note that a major reason why the intel 3100 is being pushed as a linux gpu is because intel opened up their drivers, open source is cool, but when it comes to gpu drivers I've really never seen it work out, nice closed nvidia drivers thats what I like. He still has a phenomenal computer, and with a little tweaking it will run compiz (just wait for 8.04 release its got a better x anyway)

GL

---

### Post by MikeyMike01 on 2008-04-19
XPS M1530 works fine with Gutsy, only thing that required effort was internal microphone.

:guitar:

---

