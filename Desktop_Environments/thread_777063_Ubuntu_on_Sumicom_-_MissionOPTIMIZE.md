---
title: "Ubuntu on Sumicom - Mission:OPTIMIZE"
date: 2008-05-01
forum: Desktop Environments
---

### Post by r0b0h0b0 on 2008-05-01
Hello ubuntugurus!

I have installed 8.04 server on a Sumicom S620, but because I need to develop a (Java) GUI app for a client, I had to install the desktop as well. I did a **sudo apt-get install ubuntu-desktop**, which (of course) worked well.

However, this desktop comes with a billion bells and whistles which I will never use (on this particular machine). All I need are the very basics (like admin stuff) and no more - if there's anything extra I need, I'll install it later. As you may or may not know, the Sumicom is a little industrial computer and it has limited resources, so a full-featured desktop is really putting unnecessary strain on it. I don't want to manually uninstall packages because I'm going to have identical setups on a number of similar machines and I don't want to waste so much time.

I want Ubuntu as an OS, but I need a super light, stable, nice-ish GUI desktop.

Secondly, I do need both Apache and MySQL to run on startup (as is the default), but I don't want PHP (et al) to init. In fact, since you are the Ubuntu Guru's, I'm going to ask you for any advice you may provide as to how I can go about to really optimize my setup, so that the machine starts and loads only the absolute necessary.

What do you suggest I get? (Keep in mind that I am relatively new to Linux and please also tell me how/where to get it, and how to install it)

How do I uninstall the desktop I have now? Is it even necessary? I have an 80GB HDD so I suppose I may as well leave it on and just use it when I need it?

Thanks in advance

---

### Post by r0b0h0b0 on 2008-05-04
Hello people

I googled Xubuntu to death and it is still more than what I want. I keep ending up at these forums when looking for help, so, on I go...

Xubuntu is almost perfect, and I'll be going with it, but there are still far too many bells and whistles. I need a much lighter GUI, without most of the pre-installed applications. I think I have 2 options: 

2) Manually remove packages after installation
1) Manually edit the initial installation instructions

Option 2 is the easy (albeit dreary) way out. I /can/ sit and clickety click and uninstall everything I don't need, but it doesn't make sense to do it that way if I can somehow /not/ install them in the first place. Esp. considering I'll be repeating this process for at least 4 computers.

The drawback of option 1 is that I must be very sure of what it is that I am *not* installing...and frankly, I'm not.

I need help and/or advice with this, as I am a noob. Please!

---

### Post by r0b0h0b0 on 2008-05-06
OK, this is now officially no longer a 'thread in a forum'. It's a blog. Why no replies? The mind boggles.

Anyhoo, I've now installed Xubuntu (Alternate CD) as CLI only, then I did a **sudo apt-get install xorg kde-core kdm**. I'm getting closer to a very light OS with minimal bells-and-whistles. The setup I have at the moment is certainly a lot sleeker than the standard Ubuntu install, yet it retains many of the benefits of Ubuntu.

Although, due to time constraints, I'm going to settle for the way things are now, I'm still on a mission to find the most useful minimalistic install (with GUI). As time goes on I'll keep adding to this 'blog' so that perhaps it may serve someone well in the future.

---

### Post by moopere on 2008-05-06
> **r0b0h0b0 said:**
> OK, this is now officially no longer a 'thread in a forum'. It's a blog. Why no replies? The mind boggles.

Its been an interest of mine for years, but honestly, its hard work and so many compromises end up being made that you have wonder at the end what you've really achieved.

Something is definitely going wrong in Pc land in my view though.  Window95 (you gotta love it) was a helluva system considering the minimal system specs you needed to run it.  I've had it up on 386 systems with 2MB of ram.  With an early Pentium and 8MB the sky seemed to be the limit.  Everything you expect in a modern system and it was really fast!  Even NT4, once you upped the RAM a tad more was an extremely light system.  A pentium 200 and 32-64MB RAM was far more than the minimum requirement.

Yet years later here we are with mind bogglingly powerful machines and gigabytes of RAM yet our last generation PC's (1Ghz P3's for instance) struggle to run operating systems let alone applications.  Folks will immediately come back to me citing functionality increases, but goodness me, whilst functionality and usability has definitely gone up they are not improving at the same rate at the hardware 'gobble'.  Even if I was to agree that functionality has doubled (which I doubt) the machine spec given away for that gain is a power of magnitude and some more!

Even Windows XP appears 'light' these days.  Sheesh!

Cheers,
Craig

---

### Post by prshah on 2008-05-06
> **r0b0h0b0 said:**
> 
Anyhoo, I've now installed Xubuntu (Alternate CD) as CLI only, then I did a **sudo apt-get install xorg kde-core kdm**. I'm getting closer to a very light OS with minimal bells-and-whistles. 

Everything I've read so far suggests that you'd be better off using Arch; I have never used it, but I understand that it starts with a rather bare-bones type system, to which you can add-on what you need.

Caveat: I have no experience with Arch except looking at screenshots and reading forum posts.

---

### Post by r0b0h0b0 on 2008-05-08
w00t! Replies! Hey guys, thanks ;)

There appear to be many, many "light" versions and distros. Every now and again I come across yet another...xubuntu, fluxbuntu, arch, DSL, featherlinux, and so on. Each one has its own idiosyncrasies, strengths and weaknesses (duh). If I am learning anything from this endeavour, it's that I know jack squat about linux...not that I ever thought or claimed anything else, but it's really driving home the point. Oh, curse that damned M$ and its OSes that have turned me into a lazy user! 

I really am enjoying this. I get giddy at the thought of having to do stuff in the CL, and I'm even considering buying some geek apparel - like that t-shirt I saw this scrawny kid in once that read "got root". I compiled my first driver yesterday (OK, so I had a step-by-step list), which made me so excited that I even told my wife. If you knew her you would know what an absurd thing that was to do :)

---

