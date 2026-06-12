---
title: "Ubuntu 18 aesthetics"
date: 2020-07-24
forum: Desktop Environments
---

### Post by heatopher2 on 2020-07-24
Hi, I've just upgraded from 16 to 18 (maybe on the way to 20 soon enough if I can't get things fixed - let's see). I really needed to do it, because I was having a lot of trouble with the sound on this laptop, and those problems do seem (touch wood) to have been sorted out. But let's give it a few more days to see if that's true. However, there are a few things that I really don't like about the desktop, and wondering whether I should just jump straight to #20. As the title suggests, aesthetics are important for me. Please advise, based on the following:

 I can't for the life of me understand why they took away the automatic possibility to have the horizontal-vertical workspace grid, which is absolutely one of my favourite things about using Linux (from way way back when I first used UNIX at university). So I installed the Unity desktop and got my grid back. But unfortunately I've lost another favourite feature - the Variety wallpaper changer. To be precise, I haven't exactly lost it. It's sitting there on the top bar, but I've got no wallpaper at all right now - just a black background. It appears still to be working. I can view the history of images that it's been using, and it still appears to be downloading new images from these online repositories that it uses (which is why I really like this app). But the preferences tab doesn't open when I click on it. I don't have any idea where to go from here.

When I restarted in 18 for the first time I had the current Variety wallpaper, but no sign of the tray icon. The wallpaper was still there after installing the Unity desktop, but still no icon. The icon did finally turn up after a couple of restarts, while doing some other attempted tweaks. I wanted to change the login screen to display the Variety wallpaper, and to get rid of that Ubuntu drum sound, which I don't particularly want to hear every single time I log in. The thing which appears to have knocked the wallpaper out was when I tried following instructions about changing the wallpaper. I think that it *might* have been [this one]("https://askubuntu.com/questions/1102151/lightdm-is-not-changing-background-on-ubuntu-18-04"), but to be honest I don't exactly remember, as I was reading different threads at the same time, and getting myself confused. Now that I've read some of the small print on that thread, I can see that they precisely don't want people setting their own wallpaper on the login screen because of security issues. Fair enough, but I need to know how to get Variety working again (and would still like to get rid of the drum roll, if someone can tell me how to do that). I went to the Appearance tab in settings, but that's not even changing to any of the preloaded Ubuntu wallpapers.

The other thing that is bugging me a bit is the state of Cairo Dock, which again is a very aesthetically pleasing little application, with its "better-than-mac" animation effects. But it's problematic now. Some icons don't display properly in the dock (Gnome Tweaks and dconf-editor are two examples), and the shortcuts to the file manager don't work (I uninstalled nautilus and nemo is currently default). I don't know if that's something wrong with Cairo Dock or maybe something that Ubuntu 18 has knocked out. Well, I suppose it's the same thing, isn't it? 8-[

I guess that I have two questions here. Firstly, does anyone here know if these two applications mentioned here are still being developed/maintained/supported? I have my doubts in both cases. If the answer is "no", what programs are there around which do the same kind of job? Secondly, given the aesthetic stuff that I've just moaned about, would it be better or worse for me just to skip this Ubuntu version and go straight to the latest one? I still don't fully understand how these shells/environments (Unity, Gnome, KDE, etc) all interact with each other, and to what extent you can have one working alongside the other (hence I've currently got both the Gnome and Unity Tweak Tools and don't know how much they conflict with each other. I suppose that there's a bit of version history involved in all this, eh? Is it that Unity is the original Ubuntu, and Gnome comes from other Linux distributions??? Of course I don't want to load the system up with too much clutter, speaking of which I'll stop there and avoiding cluttering this forum with any more than this.

TIA

---

### Post by heatopher2 on 2020-07-24
Quick update: while writing that post I was playing around with the Variety image history, and for some reason (no idea how!!) I've now got a picture of a grumpy looking Napoleon after the Battle of Waterloo as my desktop background. That's an improvement on the black background, but I would like some, aaaaaah, "Variety" \\:D/

Time to get some sun! Hope to get some ideas later!

---

### Post by CatKiller on 2020-07-24
> **heatopher2 said:**
>  I suppose that there's a bit of version history involved in all this, eh? Is it that Unity is the original Ubuntu, and Gnome comes from other Linux distributions???

In The Beginning (2004) Ubuntu used Gnome 2, and Ubuntu releases were synchronised with Gnome releases. Some time later, when netbooks were a thing, Ubuntu made an environment for those, called the Ubuntu Netbook Remix. Then, around the time that Gnome was switching to Gnome 3 (which was fairly painful) Ubuntu wanted to make an Ubuntu Phone. They wanted to have one interface that unified the desktop, UNR, and phone interfaces, which they called Unity. It had some bits of Gnome, some bits of Compiz, and some bits that they wrote themselves. After a number of years the Ubuntu Phone hadn't happened, and they couldn't afford to keep it going (they also had to drop staff), and netbooks had evaporated, so they dropped Unity and went back to Gnome. They've tried to make Gnome behave similarly to Unity as much as they can.

I didn't really like Unity and I don't use Gnome any more, so I can't really help with your adjustments between them, but that's the history.

---

### Post by ActionParsnip on 2020-07-24
[https://github.com/Cairo-Dock](https://github.com/Cairo-Dock)
Updated fairly recently. I'd say it's maintained.

Plank is a decent dock. I've used it in the path but then divorced myself from the "Mac look" and went total minimalist :)

---

### Post by heatopher2 on 2020-07-24
> **CatKiller said:**
> They've tried to make Gnome behave similarly to Unity as much as they can.

Hmmmm, it's not that I'm in love with the Unity look overall. It's pretty clunky, to say the least, and of course Gnome looks much more slick. But I just really like being able to make a nice big grid (six by six!!) to have different windows on. Surely it must be possible to integrate that with Gnome?

I also couldn't understand why Emacs had been uninstalled by the upgrade?!?!? Do people not use it any more?
 
> **CatKiller said:**
> I didn't really like Unity and I don't use Gnome any more, so I can't really help with your adjustments between them, but that's the history.

Sure, thanks for the overview anyway. It just all ends up being a bit confusing having these different environments going at the same time. You don't know what affects what. I'd happily do without Unity if I could only have the grid on Gnome, but that just doesn't appear to be possible at all. It seems strange that they can't include that. Oh well, hopefully someone else will have suggestions about these tweaks, and especially about the wallpaper thing, pleeeeeeease. I just restarted and I've got the black background again ](*,) I might try logging on with the Gnome desktop later, to see what the wallpaper situation is there :|

---

### Post by heatopher2 on 2020-07-24
> **ActionParsnip said:**
> [https://github.com/Cairo-Dock](https://github.com/Cairo-Dock)
Updated fairly recently. I'd say it's maintained.

Yes, it looks more or less OK. More than OK. It's very nice and I love it. But some icons inexplicably turn into question marks:

[ATTACH=CONFIG]286532[/ATTACH]

Well, maybe I'll try writing to the developer(s).

> **ActionParsnip said:**
> Plank is a decent dock. I've used it in the path but then divorced myself from the "Mac look" and went total minimalist :)

OK, thanks. I'll have a look at it later. And maybe the minimalism is something that I should think about myself!

---

### Post by heatopher2 on 2020-07-26
Hello, no advice about wallpaper? I've been through all the settings (Settings, Gnome Tweaks, Unity Tweaks, dconf-editor) and can't understand it at all. As I said before (I think) Variety seems to be running as usual, but no way to interact with the preferences. I've set one of the stock  Ubuntu wallpapers as background while all this is going on, but that doesn't work and I still get the black background. I've tried uninstalling and reinstalling Variety, and that didn't work. So what is going on? If I go into dconf editor I see this:

The current Variety wallpaper set as wallpaper. 
[ATTACH=CONFIG]286552[/ATTACH]

I tell it to use the default wallpaper (stock Ubuntu):
[ATTACH=CONFIG]286551[/ATTACH]

I don't actually get that wallpaper in the background as a result, and then within a few seconds, this happens :?
[ATTACH=CONFIG]286550[/ATTACH] 
The Variety wallpaper pops back up. So presumably Variety is still in control of something, without actually giving me what I want.

As far as I can tell, this is only happening on the Unity desktop. On the Gnome ones I have a wallpaper, whether Variety or stock Ubuntu (stock Ubuntu since I changed that setting).

Aaaaaaaaah! Can someone tell me if this will all go away if I skip Ubuntu 18 and just go straight to #20? Or is there some alternative to the Unity Desktop within Gnome? To be honest, another not amazing thing about Gnome is that none of the usual tray icons (Dropbox, Skype, Variety of course, et al) don't show in the top bar. Why??? That's just bad design, surely?

---

### Post by CatKiller on 2020-07-26
Not being very customisable is a deliberate choice by the Gnome devs that came in with Gnome 3. If you can't get the behaviour that you want out of Gnome and its extensions you could give another desktop environment a try. KDE is what I prefer, which is very customisable, or Cinnamon/Mate might suit you since they were initially forks of Gnome 2. As far as I know, Gnome didn't get any more customisable between 18.04 and 20.04.

---

### Post by heatopher2 on 2020-07-26
Well, in the meantime, in case anyone is interested.... I have now managed to get the Workspace Matrix plugin working in Gnome (I'm pretty sure that I tried it before, but maybe had missed some step - who knows?)

And that means that I do now have the current Variety wallpaper showing on the desktop (hurrah for that minor victory), but still no control over the changes because the dropdown icon isn't there on the top bar. The same goes for the Dropbox and Skype icons which were there before. If anyone can help me to sort that out, I might be finished here! I shall do a little searching in the meantime.

What is for sure is that I'll be ditching the Unity Desktop :???::???: It seems to be pretty dysfunctional.

---

### Post by heatopher2 on 2020-07-26
> **CatKiller said:**
> Not being very customisable is a deliberate choice by the Gnome devs that came in with Gnome 3. If you can't get the behaviour that you want out of Gnome and its extensions you could give another desktop environment a try. KDE is what I prefer, which is very customisable, or Cinnamon/Mate might suit you since they were initially forks of Gnome 2. As far as I know, Gnome didn't get any more customisable between 18.04 and 20.04.

Right, that is what I guessed, and I definitely am going to give Mint and KDE Neon a USB test run on the desktop, before deciding which one to install. You were one of the people who responded to my post about dual-booting with Windows (and thanks again for that).

But I think I'm kind of stuck with Ubuntu on this laptop, which came preinstalled with it. Dell set it to "never" upgrade, simply because they didn't want to support later versions of Ubuntu (it took me ages to find that information, and of course I got no answers from the Dell Forum). It's quite disgraceful actually, because I had a serious issue with the sound, which appears to have been sorted by upgrading to 18. But so many problems with the desktop, still not fully resolved :???: (Dropbox, Skype and of course Variety app indicators completely missing)

---

### Post by heatopher2 on 2020-07-26
Right, I've managed to get the top bar app indicators working (including Variety), thanks to the Gnome extension poetically named &#8216;KStatusNotifierItem/AppIndicator Support&#8217; . Thankfully it works for me, and I now have Dropbox, Skype and even Variety visible. Unfortunately I still can't open my Variety preferences (while I can for Dropbox and others, so who knows why that is....) but if it's just inherited the preferences that I had before, and nothing is going to change, I will live with that for now (anyway, I assume that you can edit variety.conf in the .config folder). 

And now it's time for a break from all this. Thanks very much to those of you who tried to help. I know that it's hard to help when everyone is by definition trying to do their own thing. I think that the overview is very important sometimes for people who are coming from a background outside computer science, as it can all be very intimidating at first trying to understand what the differences between all these distros are. Which is why Ubuntu serves a great purpose as a first stopping point for new people. I just think that I'm ready now to try something else.

---

### Post by heatopher2 on 2020-07-26
Oh, and by the way, someone on another forum told me that the issue of some icons not showing properly in Cairo Dock is not unknown, and the quick and dirty solution is just to find the relevant 48px icon in /usr/share/icons, copy it to a folder called Cairo Icons (or whatever you want to call it) and configure Cairo Dock to use that icon. I haven't sorted out the file manager shortcut thing yet, but again I'll park that one for now.

---

### Post by CatKiller on 2020-07-26
> **heatopher2 said:**
> But I think I'm kind of stuck with Ubuntu on this laptop, which came preinstalled with it. Dell set it to "never" upgrade, simply because they didn't want to support later versions of Ubuntu

I've got a Dell that came with Ubuntu. It was no trouble putting a different version on there. I went Cinnamon first and then KDE. 

There's no secret sauce: they have their own repositories for any last minute tweaks they might need for that specific software, which they then upstream: having the software available not only through Dell benefits everyone, and Dell not having to maintain it themselves benefits them. If a new LTS comes out during the lifecycle of a particular model then new sales (after a testing period) get imaged with the new LTS, but I think you're right that they don't produce new images for old sales. That doesn't matter, though, because they've upstreamed all their changes. You can just upgrade through the upstream project.

---

### Post by heatopher2 on 2020-07-26
Aaaaaaah, OK. This one is XPS 13 9360 (I think). I bought it from a friend, and the warranty was long gone, so I can say that I am free to experiment at least. Well, maybe I can just ask for a little advice, then. The partitions look like this:

[ATTACH=CONFIG]286554[/ATTACH]

If I were to experiment with a different distro, would I need to leave those two green ones at the beginning? EFI is, I presume, to do with the UEFI stuff that you guys were telling me about my dual-boot machine? (I don't know why there is that unallocated 1MB, by the way)

---

### Post by CatKiller on 2020-07-26
I have no idea what's in the second one but, yes, the first one is the EFI System Partition, where your bootloaders live. I don't know why we end up with 1 MiB unallocated bits, either, except that I think it's to do with having things aligned on a particular boundary.

This is already a dual boot with Windows on another drive, IIRC? That makes things trickier, but not necessarily impossible. Ideally you'd have one ESP with bootloaders for all your OSes and the actual OS installs on whichever drive(s) make sense for them. It was to get into that state from where you'd got to that I was recommending fresh installs of both, I think. That's probably still the sensible option, only installing Windows in UEFI mode followed by whichever 20.04 flavour you end up preferring.

In principle you could shrink your existing partitions down, have that third bootloader somewhere (sharing the ESP with your Ubuntu install, perhaps, bearing in mind the installer bug/feature/whatever that puts the bootloader on the first drive it finds rather than where you're installing to), and install to your newly unallocated space. But you don't have a lot of room to work with.

So what I'd suggest is playing around with some 20.04 images (or new images of a different distro if you prefer), either on USB thumb drives or in VMs, to pick the one flavour that you want. Then install Windows in UEFI mode (since Windows tramples all over everything if you install it second) then install your preferred flavour of Ubuntu (or other distro) in UEFI mode. You've got a fairly hefty amount of data stored as "stuff," so you'll want to make sure that's backed up somewhere before you start fiddling, just in case. Plus whatever you wanted to keep from the Windows side.

---

### Post by heatopher2 on 2020-07-26
Ah, no, this isn't the dual boot PC, sorry. I'm going back to that soon. This is the laptop, and no intention of trying to make it dual boot. I don't need that complexity, and prefer to have space for my "stuff" :D I'm OK with having a Windows VM on this one. Getting used to it. 

I think that the second small partition is a recovery partition, but to be honest the fella that I bought it from has not been incredibly informative (can't blame him too much - he's got a new-born baby to take care of) and I'm mostly working it out by myself, with the help of good folks like yourself.

At the risk of asking a question to which I may possibly not understand  the answer, could I ask why you chose KDE over Cinnamon in the end?

---

### Post by CatKiller on 2020-07-26
> **heatopher2 said:**
> At the risk of asking a question to which I may possibly not understand  the answer, could I ask why you chose KDE over Cinnamon in the end?

Essentially, I just liked it more. 

Cinnamon (at the time I installed it) had better high-DPI support than Gnome (I'd been using my own smooshed together Gnome/Compiz setup on the desktop) so I installed that on my high-DPI laptop when I got it. I'd used KDE briefly when it was KDE 4, but didn't like it: the introduction of KDE 4 was *rough*. Cinnamon was fine, and I used that for maybe a few years.

By the time I built a new desktop, the Gnome devs had irritated me a bit more, so I wanted something else on the new desktop. I tried Kubuntu and really liked it - none of the problems I'd had with KDE 4, and I had the wobbly windows and desktop cube that I was used to from Compiz. After a couple of weeks I realised that I was just really enjoying using KDE Plasma and switched my laptop to that, too. 

The feeling that I got was that the KDE devs were putting all their effort into making their desktop *better*, for all their users, whereas with Gnome the devs were mostly trying to realise their vision regardless of what their users wanted, and the Cinnamon devs were mostly trying to correct for the Gnome devs' attitudes. 

For me KDE is now just the right balance between helpful and getting out of the way. I don't see myself using anything else unless something really fundamental changes. You, of course, might really hate it :) Best to try it out for a bit and see how you get on.

---

### Post by uninvolved on 2020-07-27
> **CatKiller said:**
> I don't know why we end up with 1 MiB unallocated bits, either, except that I think it's to do with having things aligned on a particular boundary.

It's where they store stuff like the descriptor, master file tables, logs, and stuff like that. So, the space isn't available for you.

That's my understanding.

---

### Post by heatopher2 on 2020-07-27
> **CatKiller said:**
> Essentially, I just liked it more. 

Cinnamon (at the time I installed it) had better high-DPI support than Gnome (I'd been using my own smooshed together Gnome/Compiz setup on the desktop) so I installed that on my high-DPI laptop when I got it. I'd used KDE briefly when it was KDE 4, but didn't like it: the introduction of KDE 4 was *rough*. Cinnamon was fine, and I used that for maybe a few years.

By the time I built a new desktop, the Gnome devs had irritated me a bit more, so I wanted something else on the new desktop. I tried Kubuntu and really liked it - none of the problems I'd had with KDE 4, and I had the wobbly windows and desktop cube that I was used to from Compiz. After a couple of weeks I realised that I was just really enjoying using KDE Plasma and switched my laptop to that, too. 

The feeling that I got was that the KDE devs were putting all their effort into making their desktop *better*, for all their users, whereas with Gnome the devs were mostly trying to realise their vision regardless of what their users wanted, and the Cinnamon devs were mostly trying to correct for the Gnome devs' attitudes. 

For me KDE is now just the right balance between helpful and getting out of the way. I don't see myself using anything else unless something really fundamental changes. You, of course, might really hate it :) Best to try it out for a bit and see how you get on.

Well, as predicted, I didn't understand absolutely everything you said there, but that's fine, and I suppose I probably will understand one of these days. The desktop cube sounds interesting, anyway.

So, yes, thanks again for a really nice overview. I'm going to have to get a move on with deciding which distro to install on the PC, but I'll keep having a look at whichever one I don't install. Well, of course I can always install a virtual machine.

Really appreciate all that help!!!

---

### Post by CatKiller on 2020-07-27
> **heatopher2 said:**
> Well, as predicted, I didn't understand absolutely everything you said there, but that's fine, and I suppose I probably will understand one of these days. The desktop cube sounds interesting, anyway.

Compiz was one of the first window managers to use the GPU rather than the CPU to draw windows. A composited desktop, in the parlance. Most of them can do it now, but they couldn't ~2005. That's why it was picked for the Ubuntu Phone: mobile chips (particularly then) had weak CPUs and underutilised GPUs.

Its introduction led to all kinds of exuberance - I miss windows going up in flames when closed, but that one was apparently too scruffy to keep when the code went through a rewrite. You can probably still find lots of *very* enthusiastic videos from the time showing it off.

Mapping the different workspaces to the faces of a cube (or the polyhedron of your choice) is a more concrete (less abstract) way of keeping track of them. Wobbly windows are a quick sanity check for problematic performance. I'd really miss them if they weren't available. Plus, they're ineffably cool to your internal nine-year-old.

---

### Post by heatopher2 on 2020-07-27
Learning fast!!! Yes, it's the inner child in me that likes the workspace grid. I think I did try to get the cube going now that I remember back, but I couldn't get my head around it. I'll try again soon.

By the way, last word on Cairo Dock - the folder shortcuts still weren't working. I found a  post on this very forum from a while back. Solution (worked for me at  least):

Close Cairo Dock and run  this:

```
sudo apt-get install cairo-dock-gnome-integration-plug-in
```

---

