---
title: "Halo 2?"
date: 2007-05-02
forum: Gaming &amp; Leisure
---

### Post by Entity` on 2007-05-02
Is there any way to get Halo 2 Vista running under linux?  I'm not going to spend $200 on an operating system that hardly works with any of my hardware.  If there is a way can someone show me?

---

### Post by hikaricore on 2007-05-02
Given that the original Halo doesn't run under wine and the original demo just barely runs.

It's pretty safe to say you won't be able to run Halo 2 under linux anytime soon.

---

### Post by Entity` on 2007-05-02
....*sobs*

---

### Post by specv on 2007-05-02
> **hikaricore said:**
> Given that the original Halo doesn't run under wine and the original demo just barely runs.

It's pretty safe to say you won't be able to run Halo 2 under linux anytime soon.
or ever. By the time it might be possible halo 3 vista will be out

---

### Post by justin whitaker on 2007-05-02
> **specv said:**
> or ever. By the time it might be possible halo 3 vista will be out

Yeah, I'm not holding my breath on this one. I might actually break down and get the console. :( :)

---

### Post by lordhebe on 2007-05-02
> **hikaricore said:**
> Given that the original Halo doesn't run under wine

Some people have been able to get it working. [http://appdb.winehq.org/appview.php?iVersionId=2720]("http://appdb.winehq.org/appview.php?iVersionId=2720")

---

### Post by donkyhotay on 2007-05-02
Forget it, most games aren't compatible because the programmers they're too lazy to worry about linux compatibility. Microsoft however DOES worry about linux (just look at the forums and you'll see that games are the #1 reason for not leaving windows) and I believe they intentionally write they're software to be as incompatible with non-windows systems as they can. Look at all the big name MS games including halo, AoE(123), freelancer, etc. and you'll see that except for AoE3 all of them are listed as bronze-garbage with maybe a silver here or there.

---

### Post by justin whitaker on 2007-05-03
> **donkyhotay said:**
> Forget it, most games aren't compatible because the programmers they're too lazy to worry about linux compatibility. Microsoft however DOES worry about linux (just look at the forums and you'll see that games are the #1 reason for not leaving windows) and I believe they intentionally write they're software to be as incompatible with non-windows systems as they can. Look at all the big name MS games including halo, AoE(123), freelancer, etc. and you'll see that except for AoE3 all of them are listed as bronze-garbage with maybe a silver here or there.

I wouldn't say they are LAZY...that makes it sound like game developers don't care, and some do, like Epic, Bioware, Id, etc.

The fact is, DirectX makes it easy to develop for two platforms: the Xbox, and the PC, without complete rewrites. Considering it takes $10+ million to develop a commercial game title, where do you think game developers are going to concentrate their efforts? Using DirectX becomes a 2 for 1 deal. 

Now, Microsoft, they have no reason to make their code accessible to other OSes...and why should they? Bad for business, according to the rules that MSFT plays by....of course, we have seen that open/social/community development  can get you there faster and cheaper, but Microsoft is like GM: clinging to old ideas and old glory.

---

### Post by davin on 2007-05-03
Halo on linux ?? what is your configuration ??:(

---

### Post by Sindwiller on 2007-05-03
> The fact is, DirectX makes it easy to develop for two platforms: the Xbox, and the PC, without complete rewrites

The other fact is, OpenGL makes it easy to develop for more than two platforms: Windows, Linux, OS X, FreeBSD, PS3, Wii and any other (older) console which used OpenGL respectively OpenGL ES. Your argument doesn't make sense. ;)

---

### Post by bastiegast on 2007-05-03
> **Sindwiller said:**
> The other fact is, OpenGL makes it easy to develop for more than two platforms: Windows, Linux, OS X, FreeBSD, PS3, Wii and any other (older) console which used OpenGL respectively OpenGL ES. Your argument doesn't make sense. ;)

I'm no developer and neither are you probably. Your right, OpenGL is compatible with lots more systems than DirectX. But your forgetting one thing, that DirectX is a complete toolkit, including Direct3D DirectSound DirectInput DirectWhatever, whereas OpenGL is just graphics. So porting DX games is much easier between it's two platforms (which include the most used gaming OS Windows and maybe not market leading but still a fair 30 percent game console)

---

### Post by hikaricore on 2007-05-03
*yawn*

---

### Post by DoktorSeven on 2007-05-03
> **bastiegast said:**
> I'm no developer and neither are you probably. Your right, OpenGL is compatible with lots more systems than DirectX. But your forgetting one thing, that DirectX is a complete toolkit, including Direct3D DirectSound DirectInput DirectWhatever, whereas OpenGL is just graphics. So porting DX games is much easier between it's two platforms (which include the most used gaming OS Windows and maybe not market leading but still a fair 30 percent game console)

Well, this is why you use other open-source libraries, like SDL.  Granted, SDL on Windows uses DX to do its stuff, but you still get the benefit of cross-platform development by avoiding a solution that only works in Windows and the XBox.

SDL+OpenGL+OpenAL seems to be a good choice.

---

### Post by Mblackwell on 2007-05-03
I think/wonder if the people that Halo didn't work for didn't have appropriate video hardware. One guy even lists his hardware and it's.... very poor to say the least.

Which I think is one of the things I notice most is that Linux users will try to run x newer game (from the last few years) and wonder why it doesn't work or runs extremely slow, but then they list their hardware and they have a Geforce 4 MX.

It's gotta stop! If you want to play games upgrade your video hardware!

I realize the operating system is made to be compact and use as little horsepower as it can get away with which is why everything runs great even on slow machines, but game applications are not so nice. They want to use any resource they can and as much of it as they can get and they want it ten seconds ago because what they need to get all of those fancy graphics on screen ;). And if you don't have the video hardware it just won't fly.

---

### Post by Sindwiller on 2007-05-04
> I'm no developer and neither are you probably

You're right. I'm just a crappy dumb game artist, who uses to complain alot :) 

>  But your forgetting one thing, that DirectX is a complete toolkit, including Direct3D DirectSound DirectInput DirectWhatever, whereas OpenGL is just graphics. So porting DX games is much easier between it's two platforms (which include the most used gaming OS Windows and maybe not market leading but still a fair 30 percent game console)

Like DoktorSeven stated, there are libraries and packages who deliver sound, network and input features. Like SDL, OpenAL or others. Most of them are ported to almost everywhere.

---

### Post by Acglaphotis on 2007-05-04
But wont halo 2 vista be written in dx10? [This project]("http://alkyproject.blogspot.com/") could be the answer for linux gamers out there.

-Acgla

---

### Post by bastiegast on 2007-05-04
Wine is starting initial DX10 support this summer.

---

### Post by pay on 2007-05-04
> **bastiegast said:**
> Wine is starting initial DX10 support this summer.I wonder if Cedega will have DirecX 10 support by then....

---

### Post by pay on 2007-05-04
> **Acglaphotis said:**
> But wont halo 2 vista be written in dx10? [This project]("http://alkyproject.blogspot.com/") could be the answer for linux gamers out there.

-AcglaHas anyone actually seen any proof that alky works? Apparently they can get an openGL game based on doom3 engine (Prey) which runs perfectly under wine... It doesn't seem that impresive considering that you have to pay for it. $50 for one demo... no thanks... even if it works...

---

### Post by Sindwiller on 2007-05-04
> Apparently they can get an openGL game based on doom3 engine (Prey) which runs perfectly under wine...

That's pretty much obsolete I guess, as Doom3, Quake4 and Prey are ported to Linux? :?

---

### Post by lordhebe on 2007-05-04
> **Sindwiller said:**
> That's pretty much obsolete I guess, as Doom3, Quake4 and Prey are ported to Linux? :?

Prey isn't but Prey runs perfectly under both cedega and wine, so again, obsolete.

---

### Post by Entity` on 2007-05-04
> **Acglaphotis said:**
> But wont halo 2 vista be written in dx10? [This project]("http://alkyproject.blogspot.com/") could be the answer for linux gamers out there.

-Acgla

Hmmm... this project looks pretty promising.  And by the way, don't consoles use a embedded version of linux too.  Granted, its heavily modified; but its still linux.  If someone somehow got that linux versoin off of an xbox and ripped it apart, don't you think we would find some simalarity between standard linux and that one?

---

### Post by stchman on 2007-05-04
Gaming is the only reason I ever boot into Windows anymore.  EVERYTHING else I use Ubuntu for.  I hear Cedega is really good for gaming under Linux.

---

### Post by ThenonS on 2007-05-06
same here. I t would be great for wine to get a bit of DX10 going :D

---

### Post by Enverex on 2007-05-06
> **hikaricore said:**
> Given that the original Halo doesn't run under wine and the original demo just barely runs.

It's pretty safe to say you won't be able to run Halo 2 under linux anytime soon.

> **specv said:**
> or ever. By the time it might be possible halo 3 vista will be out

These aren't true. Just because something is new it doesn't mean it wont work and just because something is old it doesn't mean it will work, it purely depends on what has been implemented.

For example STALKER works rather well for something so new, but Interstate '76 which is from back in 96 or so doesn't work at all. It's all the luck of the draw at the moment with devs working on whatever parts they get time to work on.

And yeah, stay away from Alky. They appear every year, promise something amazing, gladly accept lots of money then disappear again till the next time the cycle restarts.

---

### Post by Entity` on 2007-05-06
Thanks for shedding some light upon the shady dealings of alky.  I never heard of it anyway, so that doesn't help the issue at hand here.

---

