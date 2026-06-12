---
title: "Library, Internet Cafes and Kid Proofing Linux"
date: 2009-03-22
forum: Education &amp; Science
---

### Post by Matrix7 on 2009-03-22
Hello all, I am new to the forums here and have a couple of questions I would like to throw out there. Little background first though so you know where I'm coming from.

I am a former Windows (yuck) network administrator of a smallish network (20 PCs and one mac) for about 5 years and am familiar with working on command prompt type stuff, networking, system setting and other mid level "guts work".

I used Linux a little in College (ten years ago or so) - (Red Hat 7) but had dialup at home so I decided until I got high speed I would keep reading up on it but not install. I've had high speed for about a year now and had forgotten about it until I started getting into downloading Podcasts and saw the "[Going Linux]("http://goinglinux.com/")" podcast. I downloaded a couple episodes and fell in love, so I downloaded a few LiveCD's and have been tinkering since then.

An idea that I had (and my questions) is since money is tight all around this may be an opportune time to start introducing some local coffee shops, internet cafes, libraries and schools to Linux as a low cost alternative to the pricey and hardware hungry Windows boxes they have set up for kids to use to do reports and surf the web. Many times they just want something that can do the following:

- Let the kids get online (with some limitations of course)
- Let them write reports and save in Word format (Open Office should do for that)
- "Kid Proof" the station so it would be low maintenance for the staff to maintain
- Usually run on older hardware so they don't have to upgrade all the time
- Not get a bunch of viruses, trojans, spyware, malware, etc on the computer
- Restrict kids from installing a bunch of junk on the system

My thoughts on this after using LiveCD's is what if you converted their current systems into a LiveCD Linux box? Since it is a CD everything would be Read Only, Linux doesn't get viruses (does anybody else have trouble convincing people of that??), it is very minimal in the system requirements, and anything they would more than likely download to install (again Read Only disc) would also not run on Linux.

Okay here is what I would like to know:

- Is anybody doing this already - if so what success/problems should I expect.
- What distro should I use and what packages should I install
- Should I stay with the Live CD idea and somehow disable the CD tray unless you are staff OR do a full install on a small hard drive.
- I am looking to do this to both help bring my community up to speed and maybe to make a little cash on the side. Linux is free so of course no charge for that, but how long would each station take and how much should I charge to set each up?  I am hoping that if these places see they could either keep buying beefier and beefier towers to handle Window's ever ballooning system requirements or pay some guy $25 per seat or something to set up something more suited for their needs that will last longer.  Let me be clear - I am NOT in this for the money, I just want something that will open people up to Open Source.  Also people have a problem w/ "free" it seems.  You tell them free and they think "What's the catch", you tell them a low price and they jump at it.  *shrug*

Just some thoughts - I have heard how well the Linux community LOVES forums and being helpful so here's your chance, go crazy When recommending distros please use ones (if possible) that have Live CD's so I can test hardware and such before I install.

Thanks much in advance.

Matrix7

PS - The Linux distro I have been messing with is the latest from Ubuntu's site if that helps.

---

### Post by hsweet on 2009-03-22
Ever hear about LTSP and or Edubuntu?  Start reading if you haven't!

You need only one decent box for a server which can easily host 20 thin clients.  Thin clients = almost any old junk with an ethernet card that can PXE.  Including donated junk.  

Install software on server, plug into switch, (optionally) rip out old hard drives, disconnect the local cd's hit F12 and you have an instant lab.  You can carry your server around and demo the system almost anywhere.

I run it in my school for 3 yrs now.  

How would you turn this into a business.  It might be a model i'd be interested in at some point.

---

### Post by Matrix7 on 2009-03-22
From the Google results I am guessing LTSP means "Linux Terminal Service Project".  I have done some terminal service stuff in Windows and am happy that Linux (of course) has an Open Source alternative.  What I really wonder is how on Earth people accept paying so much for software in the Windows world when there are free versions available???  It completely baffles me.

Okay - checking out Edubuntu and it looks VERY much like what I was looking for (and even quite a few things I had not thought of).  This would be something I can pop on a small hard drive and dual boot into for my kids to use (I have a three and a half year old and a 15 month old).  They see daddy onthe computer all the time so of course they are showing a lot of interest already (heaven help me).  Thanks for the tip on this one!

It has been a while since I have used Terminal Services, but how would the speed in browsing the web and the use of the programs be as compared to setting up actual clients on each machine?  I was also considering each of the boxes to have one USB plug accessible in the front for if kids wanted to type up reports, make a presentation or save a picture they did in Gimp to a jump drive (if they had one of course).  

As far as the business part goes this was just an idea I had and am not really sure how people would be to "something different than Windows".  For some reason people have it in their thick skulls that anything other than Windows is sub par *rolls eyes*.  I would say the first step of doing something like this is to practice with some old machines at your home until you have the steps on setting up the server and clients down pat.  Nothing is more embarrassing than getting to a client's place, running into a problem an having to say "It worked before!".  Then probably get some info and stats together for a Windows vs. Linux comparison and just hit the hot button topics that will get their attention: no viruses, will run on old hardware, free upgrades, no viruses, no viruses, no viruses, etc. :-)  Probably also find some information on Linux' credibility because the first thing you are more than likely going to run into is "Linux?  I've never heard of it.  We use Windows." immediately followed by "Free???  How can software be free?  It must not be that good."  Not all of this stuff will be out loud mind you but it will be thought.

Get something eye catching together and I think the kicker will be doing a side by side comparison to: web browsing, paint program, educational programs.  Then have system requirements listed below that with prices spelled out for them (this would be your price to the client not your cost - always keep that in mind) and a grand total.  I seriously feel that if libraries, schools, coffee houses and cyber cafes (to name a few) see a side-by-side comparison like this as well as the benefits it would be hard for them NOT to consider this option, especially when you tell them that you can more than likely use their existing hardware (make sure to have a LiveCD handy during the demo to show them firsthand if necessary).

Again, please don't think that I am trying to make money off of free stuff but I worked as a Support Technician for numerous businesses and home users for years and saw that people honestly assume that if they have a computer they have to accept all this negative stuff and pay for it to be fixed (buggy OS, Blue Screen of Death, viruses, malware, spyware, PC slowing down after time and paying hundreds of dollars to fix any of these problems!).  Having done that for  while I just think this would be a much easier solution for many of them.

Any feedback would be appreciated on this and I thank the posts made so far.  I have some experience putting together marketing material, so once I get some of that put together I will post what I have to see what you all think.  If it is something you feel you would like to start up in the spirit of Open Source I will post all my information for others to use as well in their area.

---

### Post by ugm6hr on 2009-03-22
Making money from installing and supporting open source is positively recommended; it is how the commercial side of open source works.  If you feel guilty, you are free to donate to any worthy projects in either time or currency.

LTSP is indeed a good system for schools - lots of examples internationally:
[http://opensourceschools.org.uk/current-use-schools.html](http://opensourceschools.org.uk/current-use-schools.html)

Additionally, LiveCD systems that run from RAM have been used in schools too.  Something like PuppyLinux.

Of course, LTSP does require the server, which may be a hardware expense most schools would only consider during upgrade cycles.

---

### Post by hsweet on 2009-03-22
LTSP is generally very efficient. With a fast server with sufficient memory and a decent network (at least 100mb/sec ethernet, switches, not hubs) the system is very responsive. + secure + very easy to maintain and upgrade.  We keep an old pentiumII with 64 meg ram around for a client to show off.   

As you have seen, getting other people to believe that this magic is free and better than Windows is the harder part.

Definitly start small to learn before you bring it out in the world.

good luck

---

### Post by bulletdragon on 2011-05-30
Deep analysis but I'm not totally agree with you. There are some doubt due to the fact, I will tell you later ;)

---

