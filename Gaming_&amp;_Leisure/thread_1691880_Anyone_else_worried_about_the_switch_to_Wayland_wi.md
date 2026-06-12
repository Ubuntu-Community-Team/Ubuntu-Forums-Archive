---
title: "Anyone else worried about the switch to Wayland with proprietary drivers?"
date: 2011-02-20
forum: Gaming &amp; Leisure
---

### Post by Dlambert on 2011-02-20
I for one am worried about the future switch of Ubuntu from x to Wayland, because Wayland is not x-server, which my graphics card driver is for. Am I the only one?

:confused:

---

### Post by sakuramboo on 2011-02-20
Gnome is a desktop environment. Wayland is a display server. Wayland is replacing X11, not Gnome. Meanwhile, Unity is a modification to Gnome. Gnome will still be offered for hardware not meeting the requirements for Unity.

But, more to the point. Yes. It looks like that for the time being, a wrapper will be made to allow for proprietary drivers to be used on top of Wayland, since Nvidia and ATI drivers only support X11. Canonical did say that the open source drivers will support Wayland right out of the box, but I want the best frame rate that I can get, so I might just be replacing Wayland with X11 when 11.04 comes out.

EDIT: I talked about this a little more a while back.

[http://ubuntuforums.org/showthread.php?t=1619557](http://ubuntuforums.org/showthread.php?t=1619557)

---

### Post by bud986 on 2011-02-21
I don't hav any highhopes for the opensource drivers from what I have seen they seem to be waybehind the prioratary drivers. Anyway I might a good thing to switch from x11 to wayland but I think it's going to be a bumpyride.

---

### Post by Dlambert on 2011-02-21
> **sakuramboo said:**
> Gnome is a desktop environment. Wayland is a display server. Wayland is replacing X11, not Gnome. Meanwhile, Unity is a modification to Gnome. Gnome will still be offered for hardware not meeting the requirements for Unity.

But, more to the point. Yes. It looks like that for the time being, a wrapper will be made to allow for proprietary drivers to be used on top of Wayland, since Nvidia and ATI drivers only support X11. Canonical did say that the open source drivers will support Wayland right out of the box, but I want the best frame rate that I can get, so I might just be replacing Wayland with X11 when 11.04 comes out.

EDIT: I talked about this a little more a while back.

[http://ubuntuforums.org/showthread.php?t=1619557](http://ubuntuforums.org/showthread.php?t=1619557)

Wow, cant believe i put gnome. Sorry i mean x11. Wow

---

### Post by Ctrl-Alt-F1 on 2011-02-22
I'm going to avoid versions/distros that rely on Wayland until there is proprietary support for it.  Having said that, I think it's good that someone is evolving the display server.

---

### Post by Perfect Storm on 2011-02-22
> **Ctrl-Alt-F1 said:**
> I'm going to avoid versions/distros that rely on Wayland until there is proprietary support for it.  Having said that, I think it's good that someone is evolving the display server.

This. Though I may a dual boot on Ubuntu.
It's time to switch away from the ancient X.

---

### Post by BigSilly on 2011-02-22
I didn't realise Wayland was something to be frightened of as an Nvidia user. I also thought that Mark Shuttleworth had said that is was a while away yet from full implementation. I mean, I'm aware Unity is coming in Natty, but Wayland I believe is a way off. I'm sure if it's better than X, then Nvidia will want to continue their work with Linux and the proprietary driver.

---

### Post by Dlambert on 2011-02-22
> **BigSilly said:**
> I didn't realise Wayland was something to be frightened of as an Nvidia user. I also thought that Mark Shuttleworth had said that is was a while away yet from full implementation. I mean, I'm aware Unity is coming in Natty, but Wayland I believe is a way off. I'm sure if it's better than X, then Nvidia will want to continue their work with Linux and the proprietary driver.

Nvidia has no plans to support Wayland.

---

### Post by BigSilly on 2011-02-23
Not right now, but as far as I can gather, Wayland is about four years away from general use. Things change.

Put it this way, I have no plans to use Windows 8, but it might be different when it comes out! :D

---

### Post by Dlambert on 2011-02-23
Nvidia has already stated NO support.

---

### Post by BigSilly on 2011-02-23
Well, OK, if you insist this is irreversible. ;)

Either way, it's a way off, and if Nvidia won't support it, then it's up to Canonical to. And if they don't, well by the time it comes in I'll probably have switched to whatever *is* working for Linux. I only buy hardware that works effectively in Linux personally. It's what prompted me to buy Nvidia in the first place. If it's slowly heading towards ATI, then that's where I'll go.

I'm not fretting about it, and I don't think anyone should.

---

### Post by cascade9 on 2011-02-23
I've got problems with wayland. MIT licence, and a current intel employee started the project (see the last bit of this post). Its interesting that the distros that have even talked about wayland much are ubuntu, fedora and..meego (intel/nokia)  

> **sakuramboo said:**
>  Canonical did say that the open source drivers will support Wayland right out of the box, but I want the best frame rate that I can get, so I might just be replacing Wayland with X11 when 11.04 comes out.

AFAIK the nouveau drivers will have at least some problems with wayland currently No idea on how the ATI open source drivers would go.

If 11.04 has wayland as anything more than an optional install, I'd be suprised. I think that even a unity/gnome style 'pick what you want' would be going way to far with wayland for the next year at least (and probably far futher than that) 

> **Dlambert said:**
> Nvidia has already stated NO support.

nVidia might say that now, but who knows where things could go. Mind you, for nVidia to come out and say they are supporting wayland would probably involve linux gaining a lot of market share, and for the majority of distros to be heading toward wayland. Or apple using wayland (ya never know...). Or nVidia to be so blasted out of the market that they would write some drivers for wayland in the hope of just keeping some of its market share. 

nVidia is harding for major trouble IMO. Intel wont licence nvidia to make iX  chipsets, AMD doesnt really want nvidia doing AMD chipsets (not that they will stop them....but nvidia hasnt made a new AMD chipset for years now). 

Intel video is everywhere, killing off the low end of the GPU market that nvidia needs to survive, and AMD is going to move to GPUs on CPUs like intel has. (BTW, intel basicly used its power in the CPU and chipset market to break into the video market, after the they proved they couldn't compete with Matrox, 3DFX, nVidia, ATI, or even S3 in the standalone video card market) 

Bumpgate hurt them badly as well.....nvidia should be scared.

---

### Post by thatguruguy on 2011-02-23
> **Dlambert said:**
> Nvidia has already stated NO support.

No, they stated that they have no plans to support wayland.  That's different from stating that they will not support it.

For instance, I have no plans to punch you in the face.  That doesn't mean that I won't, if the proper occasion arises.

---

### Post by Dlambert on 2011-02-24
> **thatguruguy said:**
> No, they stated that they have no plans to support wayland.  That's different from stating that they will not support it.

For instance, I have no plans to punch you in the face.  That doesn't mean that I won't, if the proper occasion arises.

Made my day. :)

---

### Post by mbidewel on 2011-02-25
Color me very worried.  If done improperly, such a move could spell doom for desktop Linux and relegate it to an embedded and server OS.  A return to the wild west of "Will my graphics work?"  is just not an option.  At best the Shuttleworth announcement was premature because at the time only Intel cards worked with Wayland.  ATi has been added, but...

This issue has me considering a Mac for my next computer.

---

### Post by BigSilly on 2011-02-25
But it's not an issue...

:confused:

---

### Post by Dlambert on 2011-02-25
Im currently using the Unity beta, and lets just say it breaks WINE gaming, it causing the games to distort (COMPIZ). And unless you can shut 3d effects off in11.04, im installing Gnome 3.

---

### Post by Ctrl-Alt-F1 on 2011-02-25
> **Dlambert said:**
> Im currently using the Unity beta, and lets just say it breaks WINE gaming, it causing the games to distort (COMPIZ). And unless you can shut 3d effects off in11.04, im installing Gnome 3.

One of my biggest annoyances in Linux.  I have to turn off compositing if I want to play some games/watch some flash videos decently.  I don't know whether it's x11, compiz or what but it needs to be fixed.  It's awful.

---

### Post by Dlambert on 2011-02-25
> **Ctrl-Alt-F1 said:**
> One of my biggest annoyances in Linux.  I have to turn off compositing if I want to play some games/watch some flash videos decently.  I don't know whether it's x11, compiz or what but it needs to be fixed.  It's awful.


Yea, and the game ran fine in Gnome. :confused::confused:

---

### Post by del_diablo on 2011-02-25
> **Dlambert said:**
> Nvidia has no plans to support Wayland.

I think this is a good position to hold.
Until Wayland gets a proper userbase, or the server is finally being done written, it should not be worth the effort of supporting it.
The noveau project and the radeon project already got a lot covered, so for the people who want to help develop it, nothing is stopping them.
It is a bit like new "techology", until you can actually purchase items in a store that uses it, it is more or less worthless R'n D that just wants publicity.
The radeon project starting gaining moment around xmas last year didn't it? They are still in a position where only the 1xxx cards are properly usable, the driver is still ages from being done, the skeleton is unfinished, and the developers argue.
I think the same of Wayland: Until it is actually finished, leave it be.

---

### Post by beew on 2011-02-28
Yes, I am worried. This is a much more drastic change than Unity. Frankly I don't really think keeping the gnome panel or not is such a big deal.

We are just on the verge of getting graphic cards working out of the box. I was reading old forum posts and tutorials on installing Nvidia cards and it was a painful process just a few years ago and now it just works.I am looking forward to more progress in that direction. This switch may set things back.

The Nvidia card is working beautifully in my laptop. I am all for innovation but perhaps they should make a special version with Wayland just for testing instead of switching before they ensure that there is proper support from graphic cards manufacturers. 

The open source drivers (I am speaking of Nouveau) has gone a long way but don't kid yourself, while they work nicely with composting and desktop 3d they don't support features like vdpau, which is one of the best things coming to Linux. Video playback with Nouveau is hit and miss with a lot of flickering and not to mention using a lot more cpu.

How long is Wayland off? Is it going to be in 11.10 as default? Will there be an option to stay with X? I want an idea about the timeline.

---

### Post by wog on 2011-02-28
Based on what I've read, I really doubt Wayland will be in 11.10. Maybe a couple of versions after that.

---

### Post by BigSilly on 2011-03-01
Mark Shuttleworth himself intimated it could be four years before we see anything solid of Wayland in Ubuntu.

I don't know what everyone is getting so apocalyptic about. There's no doom or gloom with this at all imho. Who knows were Nvidia or Ubuntu or Linux in general will be in a few years time?

---

### Post by rajeev1204 on 2011-03-01
Wayland is far far away from being the least bit usable.The OP probably read some FUD on some site.Or wikipedia.

I vote for closure of this thread.It has no place in gaming and leisure at this point in time.Except spreading more FUD.

Or moving it to cafe or such.

---

### Post by Dlambert on 2011-03-02
Im fine with it being closed or moved, i didn't know where to put it. And it does involve gaming, because without driver support gaming cannot happen.

---

### Post by cascade9 on 2011-03-05
> **BigSilly said:**
> Mark Shuttleworth himself intimated it could be four years before we see anything solid of Wayland in Ubuntu.

I don't know what everyone is getting so apocalyptic about. There's no doom or gloom with this at all imho. Who knows were Nvidia or Ubuntu or Linux in general will be in a few years time?

No, that is not what shuttleworth said. Here is what he actually said- 

> Timeframes are difficult. I&#8217;m sure we could deliver *something* in six months, but I think a year is more realistic for the first images that will be widely useful in our community. I&#8217;d love to be proven conservative on that :-) but I suspect it&#8217;s more likely to err the other way. It might take four or more years to really move the ecosystem. 

[http://www.markshuttleworth.com/archives/551](http://www.markshuttleworth.com/archives/551)

You can ask him what was meant by 'move the ecosystem', but I dont think that he meant 'move ubuntu to wayland' there. 

Still, 1 year until 'the 1st images will be widely useful' makes me think that you will get wayland in 11.10, and it could well end up beign defualt, or even the only option well before the 4 year timeframe is up. Or it could end up like windicators.....

---

### Post by MasterNetra on 2011-03-05
> **Dlambert said:**
> Im currently using the Unity beta, and lets just say it breaks WINE gaming, it causing the games to distort (COMPIZ). And unless you can shut 3d effects off in11.04, im installing Gnome 3.

Well it is still in development, who knows it might not at 11.04, its still too early to judge. Besides Unity is NOT wayland and is off topic at this point.

I look forward to wayland. And as I understand it though, while wayland will be in 11.04 repos, x will still be what runs it by default. And I would imagine it would be the case for 11.10 as well. Wayland isn't replacing anything for now.

---

