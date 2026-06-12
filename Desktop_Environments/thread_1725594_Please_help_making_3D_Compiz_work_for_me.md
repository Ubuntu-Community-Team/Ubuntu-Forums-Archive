---
title: "Please help making 3D/ Compiz work for me"
date: 2011-04-09
forum: Desktop Environments
---

### Post by ClientAlive on 2011-04-09
Hello,

I apologize if this has been addressed elsewhere. I've been searching this forum but can't find a very close match to my situation and graphics card (especially being that this is 2011 and I'm running the current version of Ubuntu). I've also looked on the Internet but have been largely unsuccessful so far.

I'm running Ubuntu 11.04 on an HP ze2000 laptop. My graphics card is an ATI Technologies Inc Radeon XPRESS 200M 5955 (PCI E). I'm just now beginning to learn how Compiz works; and, when I attempted to follow something in their wiki:  [http://wiki.compiz.org/FAQ](http://wiki.compiz.org/FAQ)  (heading: How do I use the desktop cube?") I discovered that it is currently being rendered like a flat sheet (2D?).

I followed the instructions given about going into Compiiz Configuration Settings Manager and setting Horixontal Virtual Size to **4**. This gave me a total of 8 desktop environments but was/ is still rendered flat. As a further examination I also set Vertical Virtual size to 4 giving me a total of 16 desktop environments but still flat. It is currently set back to 2 x 2 for a total of 4 desktop environments.

I'm very, very fresh to all of this so I'm sorry if I sound kinda dumb here - but I assume that what this means is that hardware acceleration is not currently working on my graphics card.

Under this assumption I did a couple other things to try and discover more about where things sit with this system. (1) I went into software center and checked my installed applications for "fglrx" but the only thing listed seemed to be the additional drivers app. And I ran "fglrxinfo" in terminal but was given the response command not found. I got this idea from here:  [http://sidrit.wordpress.com/2008/08/10/enabling-desktop-effects-for-ati-radeon-xpress-200m-on-ubuntu-hardy-heron/](http://sidrit.wordpress.com/2008/08/10/enabling-desktop-effects-for-ati-radeon-xpress-200m-on-ubuntu-hardy-heron/)  (2) I launced additional drivers (which searches for drivers automatically when you launch it) but there is only one restricted drive listed - which I am using/ activated - and it has to do with a "software modem".

I'm not sure if I have this diagnosis correct, if it is the only issue, or even where to begin. All I really know is that it sure would be cool to get some of the functionality of Compiz working on this machine. At least then I could experiment and try the things I'm learning about Compiz as I learn them to see first hand how things work.

Sorry if this was a bit long. I just wanted to be sure and list everything I had tried and what's going on in detail. Thought it might be useful.

Can anyone please help?

Thanks.

Jake
:D

--------------------

PS: I was looking here:  [http://en.wikipedia.org/wiki/Radeon](http://en.wikipedia.org/wiki/Radeon)  to try and figure out what "generation" my graphics card is but the terminology doesn't seem to line up with the information/ identification I have for it so far.

--------------------

OMG!! It that my graphics card listed there in the blacklist!  [http://wiki.compiz.org/Hardware/Blacklist](http://wiki.compiz.org/Hardware/Blacklist)  [URL="http://wiki.compiz.org/Hardware/Blacklist"]:frown:
[/URL]

---

### Post by ClientAlive on 2011-04-10
Bump

---

### Post by Enigmapond on 2011-04-11
It may just be a simple thing. Open Preferences/Appearances/Visual effect and check the bottom box to enable the effects. Also if you haven't already done so, install simple-ccsm.

---

### Post by ClientAlive on 2011-04-11
I'm running 11.04 (Natty Narwhal). My desktop environment is not the same as yours but I can go into Applications > Appearance (which I did). I've looked for this box to check before and not found it. In fact, there is no "Visual Effects" available here. I've seen pictures before of the appearances app from earlier versions; and, in them, there is a fourth tab for that which I do not have.

The pictures below show my Appearance app opened and what it is like right now.

Picture one = first tab to far left

Picture two = window I get when clicking "Customize" button under that first tab

Picture three = second or middle tab

Picture four = third or last tab

Could I be going into the wrong thing - since my desktop (and, hence, navigation) is different?

Oh, by the way, I have ccsm and I would prefer that challenge of something more advance and then grow into it (unless this will be impossible for some other reason).

Also, I looked under "System Settings" also but didn't see anything in there to do with appearance. Only "monitors" which is under the hardware category.

Thanks

Jake

---

### Post by Enigmapond on 2011-04-11
Just another Natty  thing that doesn't thrill me at all. The only other thing is to install simple-ccsm and that will show in your Preferences tab when installed. It;s just a small Compiz manager that you can enable/disable effects and adjust the Cube... Sorry I can't be of more help. Just another reason I'm staying with Lucid until it dies. Maybe they will fix it prior to release.

Cheers!

```
sudo apt-get install simple-ccsm
```

---

### Post by Yellow Pasque on 2011-04-11
Think of your chip as an integrated X300. ATI dropped support for legacy cards in Catalyst/fglrx years ago, so that's why you don't see it in Hardware Drivers.

Post your /var/log/Xorg.0.log

---

### Post by ClientAlive on 2011-04-11
Ok. I understand. I guess I didn't really explain what I was thinking/ wondering . . .

If I already have ccsm and I install simple-ccsm is that going to replace ccsm for what I end up using to work with Compiz? The thing is, if I can, I do ultimately want to use ccsm, not simple-ccsm.

Perhaps I don't understand the differences between the two well enough to make an informed decision like that; but, seeing the word "simple" in simple-ccsm causes me to assume it does not have all the features of ccsm.

So, ok, simple-ccsm is fine - if I have no other option. I would rather have something than nothing. It's just that I'm shooting for the full-blown effect.

Can anyone please clarify/ give more detail on what I'm facing here with this ccsm/ simple-ccsm thing - and - whether there is a way to end up being able to use ccsm, under the circumstances? If so, what additional steps might I be facing if I were to install simple-ccsm in order to try and get my situation resolved?

I should describe something in more detail also. I thought I mentioned this in a previous post in this thread but I guess was wrong.

What I mean to convey by the following information is of a troubleshooting nature. In other words - something that may help to determine if Compiz is being used on the system and what that might mean for me. Perhaps this is irrelevant since Natty uses Compiz as the window manager by design - I don't know.

So - I have the magnifying glass working that is available through ccsm or enabled through it. When I first enabled it I actually set the fast keys for it to something else (something I chose) and it worked fine. I then went back in later and restored the fast keys for it to the default (windows key+m) and it still works fine.

Thanks so much.

Jake

---

### Post by ClientAlive on 2011-04-15
Not solved; but, since no-one seems to think it matters . . .

whatever.

---

### Post by ClientAlive on 2011-04-16
Hi,

I'm pretty sure Compiz is enabled/ running on my machine but I can't get 3D effects. Someone said something about clicking a box in Appearance for enabling it but I'm running 11.04 and I don't have a Visual Effects tab in Appearance. I also heard something about simple-ccsm but want to use ccsm if I can find a way to make it work for me (make 3D work for me while still using it).

My graphics card is an ATI Radeon 200M.

Does anyone have any ideas?

Thanks
Jake

---

### Post by cottfcfan on 2011-04-16
Not too sure with you using a beta.
Try installing fusion-icon, then right click it in the panel, and make sure compiz is selected as the window manager, then reload, and see if your effects come back.

---

### Post by PCaddicted on 2011-04-16
You would better be greedy,like me,and minimize special effects to increase performance.

---

### Post by Blasphemist on 2011-04-16
You can install ccsm from the software center.

---

### Post by ClientAlive on 2011-04-16
Oh wow!! I think I just made a big bubu. When I went to google the fusion icon to learn a bit about it I came arross the Compiz Arch Wiki: [https://wiki.archlinux.org/index.php/Compiz](https://wiki.archlinux.org/index.php/Compiz)  ; and, in the course of reading that had opened ccsm and was making sure a couple basic plugins were enabled. Well, under "Effects," I saw something called "3D Windows," I thought this might help my cause. When I went into that page and checked the box to enable it I was presented with, if I remember correctly, two succeeding messages: the first said something about desktop cube having a feature/ doing a feature that was done by Desktop Wall that gave you Large Desktop and I was given a choice to disable Desktop wall or Disable/ not enable Desktop Cube. I clicked to enable the Desktop cube (I was moving forward with this). Next a message was given something like Desktop Wall had something in it like Unity Plugin and the option to disable it or not. I did. Now I don't have the top bar across my windows where you can close or minimize the windwo or where menu items appear and I don't have the (start bar?) on the left to open any apps. Also I can not open the terminal by using ctrl+alt+t but I can get a virtual terminal window with ctrl+alt+F1 and can close it with F7.

I'm sorry about the poor description of events above but I am trying to do this from memory - without the ability to open ccsm again. When I clicked that last thing and all this happened I was given an error message that said compiz had crashed or something to that effect. I don't know what to do! I'm afraid to restart the computer (even though I can not do it through the gui I know the command for it and could run it in the vritual terminal). So I'm afraid to restart because I don't understand how that would improve my situation and I can't open ccsm to change things back.

I hope someone can please help soon. I'm stuck!
------------------------------------------------------------

PS: I'm running Ubuntu 11.04

Thanks

---

### Post by Blasphemist on 2011-04-16
You can run ccsm from the terminal and correct your settings. I use desktop wall and have the unity plugin enabled. I saw something that mentioned a bug with desktop cube and the unity plugin but that may have been fixed.

---

### Post by ClientAlive on 2011-04-16
I screwed something up in a setting for Compiz through ccsm and now I'm really stuck! I have another thread where I had started out asking how to do something with Compiz and just spent a chunck of time describing the issue there.

This is the link to it:  [http://ubuntuforums.org/showthread.php?p=10684044&posted=1#post10684044](http://ubuntuforums.org/showthread.php?p=10684044&posted=1#post10684044)

If anyone here can help please, please do. My current situation is I don't have the top bar across my windows where you have buttons to close or minimize or resize windows, don't have the took bar on the left to open or close apps, ccsm is no longer open (so I can't go in there and try to put things back), and I can't open a terminal using ctrl+alt+t. I can open a virtual terminal with ctrl+alt+Fi and can close it with ctrl+alt+F7.

For a more complete description of the events that led to this please see my psst at the link above. It isn't the best description since I had to do it from memory but it's the best I could do right now.

Please help. Don't know what to do and I'm stuck.

Thanks
Jake
 PS: I'm running Ubuntu 11.04

---

### Post by ClientAlive on 2011-04-16
> **Blasphemist said:**
> You can run ccsm from the terminal and  correct your settings. I use desktop wall and have the unity plugin  enabled. I saw something that mentioned a bug with desktop cube and the  unity plugin but that may have been fixed.



Sir - I don't know how. I'm just barely, barely learning command line. I only know a few commands and nothing like that. If whatever I ran in the terminal didn't solve my problem I'm afraid I wouldn't even be able to communicate on this forum about this. I can't access apps through gui and I don't know how to launch my browser any other way. I'm fortunate enough that this browser window was open behind ccsm when it crashed. That's the only reason I'm able to access this forum and communicate with you all right now.

Thanks

---

### Post by nitstorm on 2011-04-16
I had a similar problem earlier, so i had to remove compiz from my system. [This is the link to the specific post]("http://ubuntuforums.org/showpost.php?p=8304582&postcount=15") that solved the issue i had and [this is the whole thread]("http://ubuntuforums.org/showthread.php?t=1324475")

---

### Post by ClientAlive on 2011-04-16
Sir - I'm running Ubuntu 11.04 which uses Compiz as the window manager. Unity Desktop and Compiz window manager. If I removed it altogether wouldn't I be left without a window manager entirely?

Thanks

---

### Post by nitstorm on 2011-04-16
Oops, don't know about that.... sorry if i misled you... My bad.

But you could always install compiz back again right? Better get some true expert's opinion before toying around though, just thought i'd post coz i had a similar issue earlier...

---

### Post by ClientAlive on 2011-04-16
It's ok. Thanks for your help.

I think what I need is the code to run,m to lauch ccsm from the terminal (or in my case the virtual terminal window). I think that if I could get ccsm open again I might be able to undo what has been done and get back to where I started at least.

Thanks

---

### Post by stinkeye on 2011-04-16
This when run in terminal will set compiz back to default settings
```
gconftool-2 --recursive-unset /apps/compiz
```
This works for Maverick and I'm assuming it's the same in Natty.

---

### Post by Blasphemist on 2011-04-16
I'm no expert in this either but try this. Just run ccsm from the command prompt. You don't even need sudo. That works for me but my system isn't in the state yours is. Please post whether that works and if not we can try xserver restart.

---

### Post by Blasphemist on 2011-04-16
thanks stinkeye, that sounds like good solution for him

---

### Post by cottfcfan on 2011-04-16
If you disable compiz using the fusion-icon & select Metacity as your window manager you should get your gui back.

---

### Post by ClientAlive on 2011-04-16
> **stinkeye said:**
> This when run in terminal will set compiz back to default settings
```
gconftool-2 --recursive-unset /apps/compiz
```This works for Maverick and I'm assuming it's the same in Natty.

I ran that code; and, as far as I can tell, it executed fine. What happened in terminal is there was no error message or anything it just gave me a new fresh line (for me it is: clientalive@clientalive . . . $). The situation 'appears' to be the same as I described before but (I may need to restart for the new/ default settings to take effect?)

I'm worried about restarting without knowing for sure that the default settings have been restored because I'm afraid I wouldn't even be able to communicate on this forum about  this. I can't access apps through gui and I don't know how to launch my  browser any other way. I'm fortunate enough that this browser window was  open behind ccsm when it crashed. That's the only reason I'm able to  access this forum and communicate with you all right now.

As a backup in this situation it would _also_ be nice to know how to launce Mozilla Firefox (newest/ most up to date) from the terminal - just in case. Specifically, I don't mean to use Firefox in the terminal I mean to actually launch the gui application so if I had to I could at least get back here.

Thanks

---

### Post by Blasphemist on 2011-04-16
Again given you system condition no guarantee this will work for you but just typing firefox at the command line will launch it for me. Same as for ccsm.

---

### Post by ClientAlive on 2011-04-16
ok, well, its something - for now. I could try that if I had to.

Thanks Jim.

Jake

---

### Post by Blasphemist on 2011-04-16
And by the way, if you have a live cd in the worst case you can boot from it and get back to the forums but I don't know if you have one. It seems like you do.

---

### Post by ClientAlive on 2011-04-16
I just tried launching firefox from the terminal like you said Jim but got an error message. My intention was, rather than just sit here staring at this thing, to go ahead and restart with the hope that, that code I ran had restored compiz to the default settings. I didn't want to do this without proving to myself that I could launch firefox if I had to though. As it is I don't have a way to do that.

Jake

---

### Post by ClientAlive on 2011-04-16
Don't have the fusion icon installed, can't launch apps so can't launch synaptic or software store. Someone gave me a code to reset compiz back to the default settings through the terminal.

```
gconftool-2 --recursive-unset /apps/compiz
```

I ran it but nothing changed. I think I may need to restart for the settings to take effect but, again, am worried about being able to access this forum after that if things don't work out.

By the way - compiz _is_ the window manager for the unity desktop (Ubuntu 11.04).

Thanks
Jake

---

### Post by Blasphemist on 2011-04-16
I see this is the thread you've used most recently and am curious. Looked like you were going to reboot. Did that not go so well? What is your condition now?

I've blown up my unity so will be researching ccsm and DE stuff myself but will watch for your posts.

---

### Post by overdrank on 2011-04-16
Threads merged. :)

---

### Post by ClientAlive on 2011-04-16
> **Blasphemist said:**
> I see this is the thread you've used most  recently and am curious. Looked like you were going to reboot. Did that  not go so well? What is your condition now?

I've blown up my unity so will be researching ccsm and DE stuff myself but will watch for your posts.


Managed to contact someone at a local computer shop. They had me try a few things but ultimately didn't make a difference. I went ahead and took the risk of rebooting - hoping all would be well after having run that command I was given to reset the default compiz configuration. That left me with firefox no longer open/ running and none the better. Currently running live from cd to communicate here.

While I did get some good hints from the error messages I saw while attempting to fix things through the terminal (codes suggested to me by the guy at that computer shop) I've ultimately decided to just re-install Ubuntu. I'm gonna just pave over the whole damn thing I guess. It's a lesson learned.

When I do this re-install though I want to do it the right way this time (with regard to partitions). I'm going to go ahead and start a new thread about that in the appropriate forum though.

Blasphemist, thanks so much for all your help. Sorry it took me so long to get back - issues with this infernal thing, you know. If this partition thing is something you think you may be able to guide me with can you please pm me. I'd like to begin this reinstall as soon as possible.

In a nutshell: I have heard that putting some things on their own partitions can be very wise. As I recall/ understand it - it is good to have your home folder on it's own partition and the rest of the o/s on the other? This would leave one with a total of 3 partitions? The one with your home folder on it, the swap file, and the rest? Or is it that there is yet another element that should have its own partition? Such as user accounts or settings? This is where I'm at with it though and would like to do it right this time (first install I think everything was just lumped into one partition). Any help would be appreciated.

Thanks
Jake
:)

---

### Post by Larkspur on 2011-04-16
> **ClientAlive said:**
>  In a nutshell: I have heard that putting some things on their own partitions can be very wise. As I recall/ understand it - it is good to have your home folder on it's own partition and the rest of the o/s on the other? This would leave one with a total of 3 partitions? The one with your home folder on it, the swap file, and the rest? Or is it that there is yet another element that should have its own partition? Such as user accounts or settings? This is where I'm at with it though and would like to do it right this time (first install I think everything was just lumped into one partition). Any help would be appreciated.

Thanks
Jake
:)

 Your user accounts and settings are in /home anyway.  As far as I know, the thinking behind a home partition is that you can keep your settings when you reinstall without having to bother tweaking your system again, or you can use it with other types of distros.  There may be other reasons (I'm no expert).

---

### Post by ClientAlive on 2011-04-16
Thanks Larkspur. I found some information on the internet here:  [http://www.easy-ubuntu-linux.com/ubuntu-installation-606-7.html](http://www.easy-ubuntu-linux.com/ubuntu-installation-606-7.html)  As best I can tell this is the right way to do it. Now I'm trying to figure out how to allocate the space for each part.

I have a hard drive that is basically 30 gig

They show a buffer or 1 mb at the end of ea partition (for a total of 3 @ 3 mb total)

I'm pretty sure I should use 1024 mb (1 gig) for my swap file since my RAM is equal to that amount. I am wondering if I shouldn't increase that amount a little though. I may want to run some pretty big apps at some time in the future or many apps open at once (when multi-tasking things).

For "/" (root) I'm a little confused since (I think) this is where apps are stored. Im trying to be mindful of the future (wanting to install additional apps maybe or updates needing space). I'll be installing Ubuntu 11.04 beta which tells you at installation you should have at least 2.6 gig of free hd space available. I can round that to 3 and double it - but I'm not sure that will be large enough to have much in the way of apps. I wish I had an idea of the average size of an app but I'm sure that varies quite a bit. So, hypothetically, lets say I allocated 9 gig for that part. 9 + 1 + 10 Igig) - not counting buffer space - ok.

That would leave roughly 20 gig for the home part.

I don't know. Maybe I'll look around at the size of some of my "must have" apps and add up the space, maybe double that (if I can).

What do you think?

Anyone?

What would you do with a 30 gig drive? How would you do it?

Thanks
Jake

---

### Post by Blasphemist on 2011-04-16
Hi again! This is a link to the ubuntu documentation on partitioning and it has helpful instruction but it really doesn't answer your question. My answer is that with a drive that small you should just have swap in addition to the file system. I'd just make the file system partition leaving enough for a swap 1.5 GB since you have 1 GB memory. The reasoning is if you try to decide now how much for home and anything else you could end up with one partition full and wasted space in another. Some would say not to even have a swap unless you will be using suspend.

[https://help.ubuntu.com/10.10/hardware/C/disks.html#partitioning-device](https://help.ubuntu.com/10.10/hardware/C/disks.html#partitioning-device)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by ClientAlive on 2011-04-16
> **Blasphemist said:**
> I'd  just make the file system partition leaving enough for a swap 1.5 GB  since you have 1 GB memory. The reasoning is if you try to decide now  how much for home and anything else you could end up with one partition  full and wasted space in another. Some would say not to even have a swap  unless you will be using suspend.

[https://help.ubuntu.com/10.10/hardware/C/disks.html#partitioning-device](https://help.ubuntu.com/10.10/hardware/C/disks.html#partitioning-device)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)


Thanks for the links. 1.5 on swap does sound best. I get the thing about wasting space. The more pieces you cut your drive into the more you have that concern. I  guess it's possible to resize a partition later if I had to but don't know what the limitations of that are. Thought I'd try and make a good guess in the beginning. I'm noticing that most of the apps for Linux are not very large though. Might not take much space to have a pretty good playground (apps).

Thanks
Jake
---------------------------------------------------------------------------------------
I got it brothers. I'm just going to take an educated guess. I want to give a good dose of space for apps so I'm erring in that direction. I probably will end up with a little more unused space because of it but I'm good with that.

I think I'll . . .

Part 1   root   7 gig

Part 2   home   21.5 gig

Part 3   swap   1.5 gig + extra above the 30 gig total size (it's about 1/10th of a gig over 30)

Buffers 3 @ 3 mb total

I'm gonna go to work here then and see what I can come up with.

Thanks again.
Jake
:)

---

### Post by ClientAlive on 2011-04-16
Just thought I'd take a chance and see if I catch you here Blasphemist.

One last thing I need to find out and I can go ahead proper with this thing.

So, of course, I'm installing Ubuntu 11.04 beta and partitioning into 3 parts. One for root, one for home, and one for swap.
 
In the partitioning utility available during installation (at the  beginning of installation actually) there is a drop down box for  selecting the mount point of the partition. I'm good on the first two  but am not sure what to select for swap. I'm searching on the Internet  too but am not seeing what I need right off.

Basically what has me confused is that every option looks like the first part of an absolute path. Every one contains slashes and none are just named intuitively. Again, I got root and home figured out just need to know what swap is.

If anyone knows and can help I would sure appreciate it.

Thanks
Jake
:smile:
 		                   		  		  		 		 			 				__________________

---

### Post by Blasphemist on 2011-04-17
I am just now seeing this. Yes, early in the install you get prompted about allocating space. You'll choose "Specify partitions manually" when the other options are to erase and use the entire disc and install alongside other OS's. Just make sure at allocate space you use the manual option.

This page has instructions and screenshots for what you want to know that are a part of Herman's description of setting up dual boot. Just look for the allocate space detail.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by ClientAlive on 2011-04-17
> **ClientAlive said:**
> Stayed up until nearly 4 am working on this  thing. Found the place to set that part (partition) for swap. It turns  out that the selection for swap is not made in the field for mount point  but in the field for file system type. Mine is set to ext4 by default.  When you look in the drop down menu for that field there is a list of  many options and one of them is swap. I don't think that is a precise  quote of how it is titled but it will say swap in the title. So, in the  end, it turns out I had been looking in the wrong field.

Fortunately, Ubuntu 11.04 (and probably other releases of Ubuntu also  but I wouldn't know that from experience) warns you with a dialog box  when you try to proceed without having designated a swap. Once I learned  about that warning/ fail safe I proceeded to select and try almost  every option available in the mount point field - beginning with no  mount point, of course, as suggested by Imarmisa and ronparent and  proceeding through all the other ones that looked like they might apply.  (Of course, my limited knowledge I'm sure caused me to try selections  someone else would know better than to try). When I discovered none of  those were correct (because of the warning/ dialog box) I was pretty  much stumped - for a minute.

The thing is, I was told the file system type is something you never  ever mess with. I don't recall where I got that idea from but that's  what I had believed. That foolish thinking is what kept me from looking  in that field for so long. After I sat there for a few minutes and  thought about it I finally just kinda shook my head and though, "well,  lets give it a try and see what's in there." Sure enough, there was the  place to set it for swap.

So, ultimately, It was set for swap in the file system type field and  the mount point field was left as none. It doesn't actually say "none,"  it doesn't say anything for that selection, it's just blank (in Ubuntu  anyway).

I did not manage to make a part (partition) for the boot loader and I'm  hoping this will be ok. I can only assume the reason for doing something  like that is when you are going to want to run more than one distro on  the same computer? This is just a guess though. So I have root and home  and swap. Hopefully that will a more merciful set up for me in the  future if things go really really wrong like they did yesterday  afternoon.

Yesterday: my first experience screwing Linux up something fierce. Oh  how I how I messed this thing up! Broke it all to hell. Funny, didn't  seem like that would happen at the time I did it. :smile: Lol. Oh well, it's a learning experience. It's all a learning experience.

Hedge, you're the greatest brother. I love you mannn . . .   :smile:

Jake
-----------------------------------------

One last thing . . . 

I ran into a situation with the math I'd done for the size of the  partitions. This seems like an easy thing for a newbie to overlook (like  myself). I had gone off the total disk size that was given at the  beginning of install, before you go into the partition tool and that  figure is not a precise figure. When I got to the third (and for me,  final) partition I discovered the available space for it was much less  than I had anticipated and had to do some checking in my math to,  ultimately, figure out where I had gone wrong. Where (for me) the total  size of my disk had been listed as 40 gig at the beginning of install  (before going into the partitioning tool) it was actually only 40007 mb  (roughly 39.06 gig). That, more precise figure, was/ is given once you  start that partitioning tool.

[http://ubuntuforums.org/showthread.php?t=1731249](http://ubuntuforums.org/showthread.php?t=1731249)

Thanks Blasphemist. Your aw-sum brother.

Jake

---

