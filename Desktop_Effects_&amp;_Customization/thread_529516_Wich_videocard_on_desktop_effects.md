---
title: "Wich videocard on desktop effects?"
date: 2007-08-19
forum: Desktop Effects &amp; Customization
---

### Post by backcracker on 2007-08-19
I can't find the section in where there is a list of the best video cards for desktop effects.
I don't know wich one to buy...
(and what are the min. specs for Mobo/Proc?)

---

### Post by orangebase on 2007-08-19
Can't tell you specifically what to get, but stay away from any ATi cards. Pain to set up (with desktop effects), bad driver support.

---

### Post by psyopper on 2007-08-19
I'll second that orangebase...

Get anything Nvidia Geforce 5x or higher, or Intel 900 or higher. I think the best bargain out there is an evga Geforce 6600 256 meg for around $35 at tigerdirect.com.

---

### Post by mysticmatrix on 2007-08-19
Nvidia and Intel are the best thing to go when it comes to linux.

Any Nvidia card above Geforce 2 FX would work with Compiz Fusion.
Any Intel Card above i855 would work too. (This from official site of compiz)

As for ATI, they have a very poor linux support from official drivers. The community is trying to devolop better open source drivers but they are not complete.

BOTTOMLINE: You will easily get compositing on Intel and Nvidia with little efforts and may have to face trouble when trying on an ATI card.

---

### Post by FuturePilot on 2007-08-19
Nvidia or Intel will work great with compositing. Whatever you do **stay away from ATI**

---

### Post by backcracker on 2007-08-19
okay that should be enough info on that one...
now, what about mainboards and processors? what would be the minimum configuration on where my future system would run smooth?
Thanks again!!!

---

### Post by psyopper on 2007-08-19
CF runs nicely if a little laggy with high end effects like transparent cube. It's an Athlon XP 3000+ with 512 meg of PC133. That's right, a 4 year old machine...

Anything you put together now or in the future with "new" pieces will work just dandy.

---

### Post by backcracker on 2007-08-20
will this do:

[http://www.brack.ch/aspx/Shop/lager.aspx?ArtID=59089](http://www.brack.ch/aspx/Shop/lager.aspx?ArtID=59089)

?

---

### Post by Parms on 2007-08-20
Will an ATI Radeon Xpress 200M card work with compiz? Its installed with my laptop so can't really install a new one, unless I pay big money. Or get a new laptop.

I get the following errors...
parms@parms-laptop:~$ compiz --replace -c emerald
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
parms@parms-laptop:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
parms@parms-laptop:~$ 

I can succesfully run compizconfig and can enable and disable things but can't get the last step to work.

Any ideas on the drivers? I just clicked enable driver and it installed some thigns and says it's enabled.

---

### Post by mysticmatrix on 2007-08-20
> **backcracker said:**
> will this do:

[http://www.brack.ch/aspx/Shop/lager.aspx?ArtID=59089](http://www.brack.ch/aspx/Shop/lager.aspx?ArtID=59089)

?

That would be more than enough.

---

### Post by idanool on 2007-08-20
maybe this will help you:
[http://ubuntuforums.org/showthread.php?t=528820](http://ubuntuforums.org/showthread.php?t=528820)

---

### Post by mysticmatrix on 2007-08-20
> **Parms said:**
> Will an ATI Radeon Xpress 200M card work with compiz? Its installed with my laptop so can't really install a new one, unless I pay big money. Or get a new laptop.

I get the following errors...
parms@parms-laptop:~$ compiz --replace -c emerald
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
parms@parms-laptop:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
parms@parms-laptop:~$ 

I can succesfully run compizconfig and can enable and disable things but can't get the last step to work.

Any ideas on the drivers? I just clicked enable driver and it installed some thigns and says it's enabled.

Since you have installed the offical ATI crap, you'll need to enable XGL to run Compiz.
Install XGL with [help of this]("https://help.ubuntu.com/community/CompositeManager/Xgl"), login to a XGL session and then start compiz.

---

### Post by Parms on 2007-08-20
> **mysticmatrix said:**
> Since you have installed the offical ATI crap, you'll need to enable XGL to run Compiz.
Install XGL with [help of this]("https://help.ubuntu.com/community/CompositeManager/Xgl"), login to a XGL session and then start compiz.

OK, I will try that. Also I'm using ENVY right now to re-install the drivers, I wonder if that will work. Just found it in a post somewhere. If it doesn't I'll try the XGL method. I don't even know what XGL is, lol. I'm such a n00b. But at least I'm learning slowly.

Kinda crazy going from windows to linux. Don't know what's more frustrating.. Windows crashing. or trying to get things to work in linux. LOL. 

I know once I get the hang of it I'll enjoy it better than windows. Only reason I use windows anyways is because I know how to do everything.

---

### Post by mysticmatrix on 2007-08-20
Parms, don't be afraid to learn new things. You will probably dedicate less time to learn Ubuntu than you did to learn Windows.

Also, wikipedia is your friend. [http://en.wikipedia.org/wiki/XGL](http://en.wikipedia.org/wiki/XGL)

You ***will need*** XGL over ATI drivers as those crappy drivers don't support a essential component required for Compiz and Beryl.

XGL is not a video driver. It runs atop your ATI crap to help it do cool things.

---

### Post by Parms on 2007-08-20
Ok thanks for the help. I'm not affraid to try to learn new things, it's just very confusing at first and seems like there is a lot to do!!! Which is what I like most about linux. I'm a hands on person and like to dig deep. I'll learn till there is nothing else to learn!! Which will be until I die, lol.

I wish my school was more hands on with linux. Mostly spent my time in that windows crap they call an OS.

---

### Post by backcracker on 2007-08-20
Ok!
Thanks everybody with all the help! I am going to install it over the weekend I guess.

Can't wait!!
Backcracker

---

### Post by mysticmatrix on 2007-08-20
Params posted to me:

I tried the XGL session A.

When I get to the part to logout and login with XGL.. it gives me a grid like looking screen with an X for my mouse pointer.

Hmmm....

Should I try method B, and if I do is there anything I have to undo from method A??

Thanks.
___________


Well you don't have to undo anything. I recently noted that your chipset X200M is not exactly fully supported. If you want to login to regular session, just suggest GNOME from session manager.
Also, did you tried the method for listed under ATI/Intel?
I have an intel chipset, and the initial grid screen passed after few seconds and I got regular session.

TIP: Try posting public, so that other may also get help from it.

---

