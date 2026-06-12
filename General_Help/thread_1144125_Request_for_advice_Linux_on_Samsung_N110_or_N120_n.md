---
title: "Request for advice: Linux on Samsung N110 or N120 netbooks?"
date: 2009-04-30
forum: General Help
---

### Post by andyghall on 2009-04-30
Apologies in advance for the long post...



I've just purchased a new [Samsung N120 netbook]("http://www.samsung.com/us/consumer/detail/detail.do?group=computersperipherals&type=mobilecomputing&subtype=mininotebook&model_cd=NP-N120-KA02US") and would like to run Linux on it with a light-weight window manager (OpenBox, fluxbox, enlightenment, etc.), in the hope of obtaining a nippy, mobile, aesthetically pleasing, light desktop environment.



[B]I'd very much appreciate any forum member's thoughts on the questions at the end of the post.
[/B]




**[SIZE="2"]What I've found so far[/SIZE]**


I have searched the Ubuntu forums with the following terms to see if information on this already exists, with the terms **"N110"** and **"N120"**. The N110 contains similar components to the N120. 
I've also searched various forums dedicated to the hardware itself and found nothing.

It may be that there's little to be found on the Internet concerning this subject because the N110 and N120 run Linux like a dream and nobody has encountered any difficulties in doing so.
If that's the case, then why is there so much material dedicated to running various distros on other netbooks, such as the sprawling eee range or Acer machines?

The information I've gained so far has come from reference to other netbooks with similar components (google away). 
Also helpful have been [articles on the NC10]("http://nc10ubuntu.wordpress.com/category/workaround/") or NC20 (different ultra-portables made by Samsung),  which have general info about getting various laptop features like hotkeys and hibernate running, or [installing Linux from a USB flash drive]("http://www.debianadmin.com/ubuntu-netbook-remix-and-debian-lenny-on-the-samsung-nc10.html").




**[SIZE="2"]What I'd like help with[/SIZE]**


**Does anyone know of an existing source of info on this subject?**


Is anyone here who is running Linux on an n110 or n120 (or even anyone who wants to speculate) who:-

	[INDENT][/INDENT]- has any **advice on potential pitfalls**?
	[INDENT][/INDENT]- wants to **share their experiences**?


I use Ubuntu on my desktop and love it but bearing in mind that I want to squeeze as much performance as possible out of the Atom-powered machine:-
	[INDENT][/INDENT]- **xubuntu or netbook remix?**
	[INDENT][/INDENT]- would something like Gentoo (which I used before Ubuntu), be worth **compiling from source: would it give a noticable performance boost?**


**Would a rock-solid distro, like Debian, be more appropriate** if frequent future updates risk breaking various hacks required to get all the features running perfectly?






My gratitude to anyone who can help.

Cheers,

Andy

---

### Post by andyghall on 2009-04-30
(just posted so hope this won't be misconstrued as a shameless bump: thought a new post would be better than an addition to an already big post above)

Tenuous but could be promising.

From the only related [article]("http://www.linuxdevices.com/news/NS9758888812.html") I've been able to find...

"Samsung does not mention Linux support, but it should run fine on the netbooks. In fact, according to Laptop, the N110 (above left) is a replacement for Samsung's first netbook, the NC10, which was lauded by reviewers for having an excellent keyboard, and was apparently also a popular way to run Moblin, the Intel-sponsored Linux distribution."


--Edit--


Have had a thought. Installing a copy of Linux to a pen drive would be an excellent way to refine an installation without risking the functionality of the netbook.

Plenty of guides at [pendrivelinux.com]("http://www.pendrivelinux.com/index.php?s=ubuntu").

---

### Post by Sarai the Geek on 2009-04-30
I don't know a whole lot about your computer specifically but Netbook remix might be a good idea- from what I hear it comes with a lot of drivers and such that make setting up a netbook easier.
If you're looking for speed and simplicity, Xubuntu would be okay but be prepared for a little additional setup time. If you really want to squeeze every last drop of power out of the computer, you could go Damn Small Linux, too.
I suppose a lot of it is aesthetics.

---

### Post by foodle on 2009-04-30
I am running Ubuntu 9.04 UNR on my N120. Almost everything works out of the box.

Issues I'm having:
- brightness control FN keys do not work. Standard NC10 xbacklight workaround works
- sometimes after coming out of suspend, wifi is hosed. No solution yet.

---

### Post by andyghall on 2009-05-01
Quick update: n120 received today.

Installed crunchbang Linux (based on ubuntu, runs openbox).

Looks great, runs super fast, low system load.


Almost everything works out of the box - including some function keys, like suspend, numlock, wireless, audio

Plays YouTube movies, and 720p DivX with no problem.


Only having issues with backlight setting, function keys, and external speakers not shutting off when headphone jack is inserted.
There's plenty of info on fixing these types of faults scattered around the Internet.

At this stage, I'd recommend crunchbang to anyone wanting to run an Ubuntu-based system on their N120.

---

### Post by chadeldridge on 2009-05-05
I also have the N120 ... so far so good with Ubuntu 9.04 although out of the box I do have issues with the following:

WPA2 is not available for the wireless, the madwifi driver does not work at all though

None of the FN options work, I am looking at doing the fixes for the NC10 on this machine to see if that works


Have you had any luck with these features?

---

### Post by foodle on 2009-05-05
The FN brightness keys weren't working, so I used Ubuntu Tweak and xbacklight to remap ctrl+up and ctrl+down to control the brightness. Some of the other FN keys are ok (e.g., mute).

WPA2 has been working ok for me (router is an Apple Airpot Extreme).

---

### Post by fancyl on 2009-05-12
My dad just ordered the N110 online and it's supposed to arrive on later this week. I'm trying to sell him on Linux, specifically Ubuntu Remix. I've used Ubuntu before, so I think I could get things running on the netbook. But I'm afraid these issues will dissuade my dad from using Linux. He doesn't have a lot of patience for computer problems.

Should I try installing Ubuntu Remix on his new N110 or just tell him to stick with Windows?

Does anyone know of a walkthrough or how-to to get everything working properly on the N110?

---

### Post by KnThrak on 2009-06-09
Installing UNR when my N110 arrives in ~2 hours.
I'll post any immediate troubles I find here. Hope it goes well, I really like the slick look of UNR from the pictures. ^_^

---

### Post by ectospasm on 2009-06-12
> **KnThrak said:**
> Installing UNR when my N110 arrives in ~2 hours.
I'll post any immediate troubles I find here. Hope it goes well, I really like the slick look of UNR from the pictures. ^_^

I'm actually ordering an N110 this weekend, and hope to have it next week.  Let me know if you run into any snags or snafus.  All in all the problems seem to be minor (except for maybe the wifi not working after a resume from suspend).

Once I get it I'll post my issues as well.

---

### Post by dds125 on 2009-06-27
Hi, I want to buy the N110. Does Ubuntu work ok on it then? 
Anyone have any experience using KDE on this machine?
thanks
d

---

### Post by ectospasm on 2009-06-27
> **dds125 said:**
> Hi, I want to buy the N110. Does Ubuntu work ok on it then? 
Anyone have any experience using KDE on this machine?
thanks
d

I'm using the Ubunt Netbook Remix on my N110, and it works great!  I haven't tried KDE on it, so I can't comment on how well it works.  The UNR interface is GHOME based, but it's definitely different. I like it because it's simple, and works well with the small screen.  It sems to me that KDE would be too clunky on this machine, but ymmv.

---

### Post by dds125 on 2009-06-28
Thanks..
After trying UNR on my eee I personally prefer Kubuntu.
Is battery life on yours as good as claimed under windows?
I'm after a netbook and at the moment it's between the samsung(nc10 or 110) and the 1000he..
I liked the NC20 but after reading the very long post about it, have decided not to struggle with the issue with the VIA chipset.
Any recommendations welcome...

thanks
d

---

### Post by ectospasm on 2009-06-29
About the only problem I've come across with my N110 (which is not related to UNR at all) is that randomly the machine will not boot.  Power light comes on, HD activity light comes on briefly and goes out, and nothing else, it does not POST.  Simply rebooting it two or three times fixes it.  If the BIOS flashes up (and it's FAST), then it's good to go.  If I get a chance tomorrow, I'll try contacting Samsung about it.

Now, to wipe UNR off and try to fix (er, reinstall) Windows.  I don't know yet if I'll need it for class, so I figured I should struggle now and not then to get it to a working state.  Then, a reinstall of UNR, with backed-up settings.  I'll let you know also if reinstalling Windows without a USB DVD drive makes a difference.

---

### Post by candtalan on 2009-08-12
> **foodle said:**
> I am running Ubuntu 9.04 UNR on my N120. Almost everything works out of the box.
Issues I'm having:
- brightness control FN keys do not work
I have just tried a samsung N110 for a friend and noticed the poor brightness, then later I got into the bios (F2) and could see a brightness setting - it was on 
Auto, and I changed it to 'Manual'

I have not done many checks in the brief time I had but it seemed to me to be much better - please confirm someone?


Also, using easypeasy 1.1 (ubuntu based) I found that I could not seem to get the built in microphone to work with skype. More tests will be done when time allows

---

### Post by barryd3 on 2009-12-28
Hey, I installed ubuntu 9.10 on the n110 and had no trouble! In fact, i'm talking to you on it now! I seen some people talking about some of the buttons not working, like brigtness button but i had no trouble with that either! although the installation of ubuntu on a netbook is somewhat different than the norm. 
     start by downloading ubuntu as a iso from their webpage. 
   *** [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download) ***

     Then we need something else called poweriso. They give a 30 day free trial but we only need it for about 20 mins, so it's a thank ye, love ye, and a see ye later type of job. You can find it here:
    *** [http://download.cnet.com/PowerISO/3000-2646_4-10439118.html](http://download.cnet.com/PowerISO/3000-2646_4-10439118.html)***
    
     Now we need a virtual drive to mount the iso onto. To do this, can ye guess it, yes, we download a virtual drive. You can find it here:
    *** [http://www.slysoft.com/en/download.html](http://www.slysoft.com/en/download.html)   ***.......... look under virtual clone drive and its free.
     download and install all three in windows. After the installation it would probaly be a good idea to reboot the computer. After rebooting, [SIZE=2]**look at the ****bottom right hand corner of screen, and the should be a silver looking cd, right click, and mount the iso which you download from ubuntu from the ubuntu webpage**[/SIZE]. The cd should autorun. If it doesn't go to my computer and the ubuntu disc should be plainly visiable from there..

for the brightness troubled people using the n110. Beside the Ctrl, Fn, hold the Fn and push up or down. works fine for me. if it doesn't work for you, i haven't got a clue.

    hope people find this useful... well it was nice knowing ye, love ye, see ye, and all that bull crap! goodbye!

---

### Post by gillza on 2010-03-13
To fix the brightness issue you have to apply BIOS update from Windows (unfortunately).
I had reinstall barebone winxp just for this purpuse (killed my recovery partition), install the patch and then tried to run ubuntu from usb. Fn + up/down now works.

---

### Post by thomas_toscani on 2010-05-22
I am posting this to potentially help someone who has installed Ubuntu 10.04 (Lucid) on their Samsung NC20 netbook.

I've tried every possible solution that I could find on the net to fix the screen brightness keys and get them working so I could increase the screen brightness.  Nothing worked.

For most or many people, some of the suggestions will work fine.  For those of you who can't get them to work and are stuck with Ubuntu 10.04 on the NC20 with a dimmed-out screen, I have a quick workaround:

When you boot and get to the BIOS password prompt, use the function and up-down array keys to control the brightness there.  The screen brightness will be carried through to Ubuntu.   You might be able to do this at the GRUB prompt.  The point is that the BIOS handles the screen brightness before Ubuntu, so it just works.

I hope this helps.  Nothing else worked for me.  At least now I can adjust the brightness at boot, and have a workable screen.

---

