---
title: "I'd really like to make the complete switch now"
date: 2008-12-30
forum: General Help
---

### Post by DrTaylor on 2008-12-30
There is one thing - only one! - that is keeping me from just wiping Vista off my hard drive once and for all, and that is TV shows online. I admit it, I am an addict to Fringe and also to Netflix on demand. I recently discovered switching my user agent in Firefox, which works great for everything else, but it's that pesky ActiveX control that's keeping me from accessing my Netflix. Haven't tried any other sites yet - I figure I'll just jump off that bridge when I come to it.

Anyway, there are two things I can think of to do, either of which would solve this problem and get me one step closer to living windows free.

1.Does anyone know if you can install ActiveX in Firefox? Is there a faked-up version that will do it, or a way to make NPAPI look like ActiveX?

or

2.I have had terrible luck with IE in Wine, as well as IE4Linux, but I'm willing to give that another go too, if anyone has any tips. It has basically refused to install every time I've tried.

Thanks!

---

### Post by AlanR8 on 2008-12-30
Another option would be to install Vista or XP inside VirtualBox. That way you can use Linux for everything but still load Microsoft to watch your progs!

---

### Post by dduehning on 2008-12-30
From my limited experience (I've recently made the switch), when I want to view videos, all I've had to install under firefox was the appropriate flash plugin.  There have been a few sites that I needed to install some gstreamer plugins to support quicktime files, but other than that, all of the videos worked just fine for me.  You don't need activex as it's a ms technology for use in IE.  

Now, I'm not a netflix user, so I can't say for sure that it does work; have you tried it yet?  Do you have a machine that you can test on?  Maybe install ubuntu on that box, get the plugins, and check out netflix.  I know that if you don't have the proper plugins, firefox will prompt you to download and install them.

---

### Post by Lazerouth on 2008-12-30
> **DrTaylor said:**
> 
2.I have had terrible luck with IE in Wine, as well as IE4Linux, but I'm willing to give that another go too, if anyone has any tips. It has basically refused to install every time I've tried.

Thanks!

Why not use Firefox?

---

### Post by DrTaylor on 2008-12-30
> **AlanR8 said:**
> Another option would be to install Vista or XP inside VirtualBox. That way you can use Linux for everything but still load Microsoft to watch your progs!
That's one I hadn't considered, actually. The only complication I can see is that RadioShack now sells computers with the installer for the OS directly partitioned onto the drive. Not only does it eat up ten gigs, but I don't have an install disc. Good try though - any idea how to get around that?

> **dduehning said:**
> 
Now, I'm not a netflix user, so I can't say for sure that it does work; have you tried it yet?  Do you have a machine that you can test on?  Maybe install ubuntu on that box, get the plugins, and check out netflix.  I know that if you don't have the proper plugins, firefox will prompt you to download and install them.

Yes, I've tried it. I am currently dual-booting so I can watch tv shows. That's sad. I haven't tried any of the tv station websites, but the netflix thing is a huge stumbling block so I'm not even worrying about that yet. I tried it this morning when I realized switching my User Agent works for the website I need to access for work, and got a completely different message - netflix thought I was in IE without ActiveX, which is progress.

ActiveX is a control, not a plugin, and therein lies the problem, because it only works with IE. As far as I know, there's no way to fake it, although if anyone has any ideas I'd be willing to try. The good news is, it comes with IE so if I can get IE working in Wine I might be all set.

> **Lazerouth said:**
> Why not use Firefox?

Because ActiveX is needed to play it at all, and for ActiveX you need IE, unless you know of a version for Firefox.

---

### Post by AlanR8 on 2008-12-30
> The only complication I can see is that RadioShack now sells computers with the installer for the OS directly partitioned onto the drive. Not only does it eat up ten gigs, but I don't have an install disc. Good try though - any idea how to get around that? 

My wife's Dell and Son's HP, and thinking about it, this Sony laptop were the same. No install disks but a "recovery" partition. When I bought this Sony, Vista stayed on long enough to burn the three, yes THREE DVDs required. They're stored in a safe place.

My install of Kubuntu wiped the entire disk so making the recovery discs was a must.

---

### Post by kokkus on 2008-12-30
Which ActiveX plugins do u need?
I Know you can find some guides on the webtv site [www.scumbox.com](www.scumbox.com) about Sopcast and TVU Player on Linux.

---

### Post by BuudWeizErr on 2008-12-30
I have XP installed in VBox 2.1 and I tried to view Netflix on demand.  Versus a native XP install, the quality was noticeably less.  It worked, but the quality wasn't where it should have been for my connection.

I haven't even started troubleshooting it though, if I tweak some of the video settings I might have luck getting a better signal.

---

### Post by dduehning on 2008-12-30
I don't have time to check it out myself, but here's something worth reading...

[http://www.pcadvisor.co.uk/news/index.cfm?newsid=108137&](http://www.pcadvisor.co.uk/news/index.cfm?newsid=108137&)

---

### Post by masque7 on 2008-12-30
> **DrTaylor said:**
> 2.I have had terrible luck with IE in Wine, as well as IE4Linux, but I'm willing to give that another go too, if anyone has any tips. It has basically refused to install every time I've tried.
[Embedding Internet Explorer in tabs of Mozilla/Firefox: Firefox-Addon -IE Tab](https://addons.mozilla.org/en-US/firefox/addon/1419)

---

### Post by Alvinius on 2008-12-31
ABC does not support linux with their software, I urge people to send them mail. CS and NBc ar no problem.

---

### Post by DrTaylor on 2008-12-31
> **BuudWeizErr said:**
> I have XP installed in VBox 2.1 and I tried to view Netflix on demand.  Versus a native XP install, the quality was noticeably less.  It worked, but the quality wasn't where it should have been for my connection.

I haven't even started troubleshooting it though, if I tweak some of the video settings I might have luck getting a better signal.

But it's great to know that it can work, at least. So far I've heard nothing, nothing at all, from anyone who made it work. Last time I brought this up, I got a flat "no" from everyone who replied.

> **Alvinius said:**
> ABC does not support linux with their software, I urge people to send them mail. CS and NBc ar no problem.
Yeah, well, you see what sending Netflix mail got me - a big donut hole for my troubles. Discovered CBS this morning. Not as good as in Windows, but still works okay. Star Trek Remastered is pretty.

---

### Post by DrTaylor on 2009-01-01
> **kokkus said:**
> Which ActiveX plugins do u need?
I Know you can find some guides on the webtv site [www.scumbox.com](www.scumbox.com) about Sopcast and TVU Player on Linux.

Says right at the bottom that some sites need ActiveX.

---

### Post by DrTaylor on 2009-01-01
> **dduehning said:**
> I don't have time to check it out myself, but here's something worth reading...

[http://www.pcadvisor.co.uk/news/index.cfm?newsid=108137&](http://www.pcadvisor.co.uk/news/index.cfm?newsid=108137&)

It's not exactly in the working stages, is it? Maybe soon, I can only hope.

---

### Post by DrTaylor on 2009-01-01
> **masque7 said:**
> [Embedding Internet Explorer in tabs of Mozilla/Firefox: Firefox-Addon -IE Tab](https://addons.mozilla.org/en-US/firefox/addon/1419)

Says right on there: not available in Linux.

Someone feel like talking me through getting my Vista install off my hard drive? I'm getting sick of dual booting.

---

### Post by kristopher.ives on 2009-01-01
DrTaylor: I'm sorry people aren't being as HELPFUL as usual around here... *jabs* *other* *forum* *members*

Not positive but I think the link to the Google ActiveX "replacement" was about Gears or something, but anyhow I don't think it's compatible with ActiveX but an alternative.

I believe the best route here is to use Ie4linux. The problem with using the VM is that hardware acceleration is usually lost in the guest VM, so if you're watching a movie it will be done using mostly software video rendering, which will be slow. You will likely have better luck if you're using VMWare instead of Virtual Box, because they have video acceleration in some scenarios.

I am willing to bet that you'll have to use winetricks and possibly some DCOM-related stuff to get it to work, but it should work. I will do some tests and get back to you in this thread, DrTaylor.

Cheers,
Kris

---

### Post by DrTaylor on 2009-01-03
IE4 Linux tried and failed on another machine. We couldn't figure out why. Other ideas welcome.

---

### Post by DrTaylor on 2009-01-03
This looks like a possibility:

[http://www.boxee.tv/]("http://www.boxee.tv/")

It's still in alpha testing but people have had success with it. Anyone tried it out?

---

