---
title: "Pro/Engineer Linux experiences?"
date: 2007-01-12
forum: Education &amp; Science
---

### Post by arsenix on 2007-01-12
Is there anyone else running Pro/e in ubuntu?  Remarkably the installer ran great after I worked out the dependancies (i never got it running right under gentoo)... and it fires up... BUT... i seem to get random freezing up when running it.  

  When I say freeze up I mean X stops responding to mouse clicks and keyboard input, but the clock still runs and I can switch to a VT or kill X if I want...

  Anyone else see this problem?  Or have other experiences with it?  It seems to run great up until the freeze up... faster than under windows in fact.  There seems to be little info about running it under Linux on the net.  If you do run it I also suggest you contact PTC and tell them since they are planning on dropping linux support in wildfire 4.0 due to "slow adoption". 


James

---

### Post by damormino on 2007-03-08
We have 10 seats of Pro/E Wildfire 3.0 - all of which are running on Linux.  We are using CentOS (similar to Redhat Enterprise.)  We have not had any notable problems relating to freezes or lock-ups.  I don't believe we have tried using Ubuntu, although this is my preferred distribution at home.  I don't see any reason why it wouldn't work.  Perhaps we can try this in the coming weeks.

We are pressuring PTC *not[* to drop support for Linux in Wildfire 4.0.  If you are on maintenance with PTC, please contact them and tell them you will not pay for maintenance if they drop support for Linux.  They should respond the this pressure.

---

### Post by arsenix on 2007-03-08
I actually found the solution to this problem.  The issue was that Pro/E was losing contact with my license server during a user interface operation (like dragging a panel or clicking a menu) and for some reason this was freezing my whole UI.  Improving the reliability of my license server connection, and an upgrade to a newer release of Wildfire eliminated the issue.  In general, Pro/e works great under linux!  I have contacted ptc to urge them to continue support for linux, but I'm not sure it is looking too good.  

  If anyone else uses pro/e under linux please contact them and encourage them to continue supporting it!

James

---

### Post by jamov on 2007-06-09
I had testing ProE on OpenSuse but have recently switch to Ubuntu.  I've had a good experience with it as well.

Here is a note I just logged with PTC.

"I am writing to log my dissatisfaction with PTC's recent decision to drop support for the Linux OS.  Specifically the reason for it, "slow adoption", irritates me as a large part of the reason for us not switching to Linux across the board was PTC's lack of support for all products/features on the Linux platform. I had confidence that PTC would get everything working with future releases and thus continued to approve the maintenance payments to PTC.  I will now start looking for an alternative product."

I may try and put a petition on the web.   I will provide a link here if/when I do.

---

### Post by daschmidty on 2007-06-10
This news is particularly depressing to me as a mechanical engineering student who was looking forward to a bright future of pro/e+linux in the workplace....

---

### Post by hengehog on 2007-07-25
I've just tried out WildFire 3 (on Win XP) & really like the new ProE.
Last time I had a look at it was the original WildFire back in about 2002 & have to say that I've been a pretty devout SolidWorks user since then.
BUT the new ProE WF3 is damn good. I'd say better (& easier to use, quicker, more powerful etc) than any other CAD program I've used before (incl. NX4, Catia V5, Inventor 10).
I contacted the PTC office in the UK after trying WF3 as we are looking for a new CAD program, & I specifically asked about LInux support.
Have to say that it doesn't look good.
BUT, all I really want to do is get away from Windows, so I asked about Solaris support (Been also running Nexenta / OpenSolaris).
As yet I have'nt received any reply, but according to the PTC site, Solaris will still be supported.
As the latest version of Solaris JDS is linux based, could this not be used on a linux desktop?
It must be pretty similar I would have thought, as nVidia supply Linux, Solaris & BSD drivers in the same package.
However, I will be getting back in touch with PTC to complain about the Linux support being removed for such a good program.

Hope someone has some luck,

Russ

---

### Post by slade on 2007-08-03
> **daschmidty said:**
> This news is particularly depressing to me as a mechanical engineering student who was looking forward to a bright future of pro/e+linux in the workplace....

same here :/  I use wildfire 3 (on windows...) at work every day, and was looking forward to the possibility of linux.  pro/e is a large part of the reason i'll be keeping vista around on my laptop.

---

### Post by fred23195 on 2007-08-22
Hello,

I am a PTC wildifre 3's great user too, and I have installed a XP license under Ubuntu using Wine, but I am surprised that it's really too slow ?!
there are some little other troubles but nothing that can prevent running.

my hardware: core2duo E6600 + 2G ram + Nvidia 8500GT 512M !
screen: 24" 1920x1200 resolution

when I use wildfire and I make some simple visual translation or rotation, the CPU comes with more than 50% of uses ! and it views slowly some little assembly.
I have changed my graphic card, because at the begining, I had an integrated intel gma950, and I thought that it was the limitation. but it has changed nothing in the performance.

I come from France, I have asked a french provider what was going on with wildfire 4.0 support on linux, but they are not concerned at all about that.
so, I asked them to provide me with a free linux wildfire 3.0 license: I am waiting...

fred

---

### Post by slade on 2007-08-22
> **fred23195 said:**
> Hello,

I am a PTC wildifre 3's great user too, and I have installed a XP license under Ubuntu using Wine, but I am surprised that it's really too slow ?!
there are some little other troubles but nothing that can prevent running.

my hardware: core2duo E6600 + 2G ram + Nvidia 8500GT 512M !
screen: 24" 1920x1200 resolution

when I use wildfire and I make some simple visual translation or rotation, the CPU comes with more than 50% of uses ! and it views slowly some little assembly.
I have changed my graphic card, because at the begining, I had an integrated intel gma950, and I thought that it was the limitation. but it has changed nothing in the performance.

I come from France, I have asked a french provider what was going on with wildfire 4.0 support on linux, but they are not concerned at all about that.
so, I asked them to provide me with a free linux wildfire 3.0 license: I am waiting...

fred
you're trying to run a graphics and ram intensive program in wine, of course it's not going to perform well.  also if you're using large assemblies, i hope you have a lot of swap.

did you pay for a full windows version, and support?  if so they will give you the linux CD free, if not, good luck.  let us know how it goes.

---

### Post by fred23195 on 2007-08-23
I've installed the 3.0 trial version under ubuntu to make some tests, because I own an old wildfire 2.0 license without maintenance / support (got after a dismissal).
and now, I wonder which software I'll buy (solidwork, inventor, wildfire...) for my new own company.

does the linux version work well under ubuntu and is it simple to install ? (following James troubles,at the begining of this post)
what are the innovation of the 4.0 version, coming next year ?

and about wine:
why do some big windows games run well under wine, and not cad software ?
will Cedega be better than wine for this ?
(my swap is 2G large like my ram.)

---

### Post by fb2007 on 2008-02-14
> **arsenix said:**
> Is there anyone else running Pro/e in ubuntu?  Remarkably the installer ran great after I worked out the dependancies (i never got it running right under gentoo)... and it fires up... BUT... i seem to get random freezing up when running it.  

  When I say freeze up I mean X stops responding to mouse clicks and keyboard input, but the clock still runs and I can switch to a VT or kill X if I want...

  Anyone else see this problem?  Or have other experiences with it?  It seems to run great up until the freeze up... faster than under windows in fact.  There seems to be little info about running it under Linux on the net.  If you do run it I also suggest you contact PTC and tell them since they are planning on dropping linux support in wildfire 4.0 due to "slow adoption". 


James

I'm also trying to install pro/e wildfire 3 to ubuntu (7.10 32-bit), but i can't get installer to work! Is there any possibility that you would write a little howto for installing pro/e on ubuntu?

Any help would be very appriciated!


thanks luka

---

### Post by arsenix on 2008-02-14
I have since fixed these issues.  It was related to the license server.  When Pro/E lost contact with the license server during a mouse drag it would grab the mouse and keyboard and freeze until it either got a license or timed out (a long time).  Making my connection to the license server more reliable fixed it.  It runs quite well.

   Getting it installed I believe was as simple as installing a few things their installer script calls.  I think it uses ZSH?  (been a while since I installed my memory is foggy on it now).  If you look through their .sh install file I think you'll be able to figure out which programs you'll need to install.  Once these dependencies were out of the way the install runs flawless.  Although I do remember that I had trouble with the "Web Installer" and had to use the full download.

   Sadly PTC is dropping support for Pro/E in wildfire4.  Too bad but irrelevant for me since my company is dropping paying for Pro/E anyways in favor of better programs.  IMHO Pro/e is one of the worst CAD packages out there and PTC the company has pretty bad service and support.(not to mention their annoying and aggressive salespeople)  I wish Catia or Solidworks would come out for linux.  Catia already runs on other unix's so it would be the most likely of the two.


James

---

### Post by cb951303 on 2008-05-18
did pro/e stopped linux support with wildfire 4.0?

---

### Post by StampU on 2008-06-10
Does anyone know if Wildfire 4 will install/run on OpenSolaris?  Or better yet, does anyone have Wildfire 4 running successfully on Ubuntu Hardy? How about Hardy 64 bit?  Thanks

---

### Post by pjgl2 on 2008-07-18
I can say we have had excellent experiences with ProE under Linux. We have >150 workstations using it here. We have also issued a large number >1500 liv e CD's with proE on which means that officially sanctioned users can work anywhere in the world with a common installation, provided they can see our license server.

 It has been a great success, it is a real shame that is not going to be supported any more

---

### Post by fhansson on 2008-10-14
> **cb951303 said:**
> did pro/e stopped linux support with wildfire 4.0?

Yes, Pro/Engineer Wildfire 3.0 is the last version supported in Linux. No more versions will be available. I think this is very sad and also a big let down for Linux. I am interesting in CAD and mechanical engineering but I also like Linux. Combining these two looked very good but sad enough Windows is what every company uses so no one was interesting of buying the license.

---

### Post by vlke on 2009-07-22
Since this is almost year old ( I just switched to Ubuntu only few months ago) ... has anything changed as far as the support for ProE in linux?

---

### Post by salariua on 2009-07-22
> 
Since this is almost year old ( I just switched to Ubuntu only few months ago) ... has anything changed as far as the support for ProE in linux?


No.... nothing has changed. V3 is still running but 4 or 5 are not supported. 

I wonder if the Solaris version will work in Nexenta or in StormOS.

This is really sad especially since, from my experience proe was running better on linux than on windows.

---

### Post by dfu80 on 2009-08-11
Hello,

How could you make ProE W3 working under Ubuntu?
I installed but whe I tried to run it I get this:
**setenv: Too many arguments**
and after 2 minutes: **setenv: Too many arguments**.

I saw some post with people with the same problem, but I didn't get the solution.

Can you help me please?
I am quite new on Linux :S

Thanks in advance.

Dfu

---

### Post by dfu80 on 2009-08-11
Sorry it was a mistake before. 
After 2 minutes **WARNING: Name Server is shutting down due to timeout reached.**
is what I can read on the terminal.

Any help would be very appreciated.

---

