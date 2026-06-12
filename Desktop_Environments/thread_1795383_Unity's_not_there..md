---
title: "Unity's not there."
date: 2011-07-02
forum: Desktop Environments
---

### Post by MG&amp;TL on 2011-07-02
Just to start off- I'm NOT a Unity hater, and I don't mind progress. :o

When I upgraded from 10.10 to 11.04, it came up with the standard error message 'you do not have the hardware to run unity' when I logged in to 'Ubuntu'

Obviously, I needed to add the hardware drivers, so I used an 'experimental 3d' one rather than the proprietary Nvidia ones, as the Nvidia ones have repeatedly mucked up my system in various ways on install. Anyway, I rebooted and logged back in to 'Ubuntu' (not Ubuntu classic), only to find it either was, or was pretending to be GNOME. (I.e standard Applications, places, System along the top, no launcher on the side.) No error message appeared. Ubuntu classic was exactly the same, although you would expect that to be.

My computer, as far as I'm aware, is 3d capable, and will also run Unity 2d without fault. Is it something I've done wrong, a problem with the release, or (I think most likely) just the 'experimental' driver playing up?

If it's the driver I will just have to file a bug report and 'like it or lump it' until the nice guys at Canonical/Nouveau wherever sort it out.

Have attached screenshot of 'experimental driver'

---

### Post by Frogs Hair on 2011-07-02
I agree that it is most likely that the experimental driver is not capable of running unity 3d on your system . Do a bug report or add to an existing one because the developers want feedback for that driver.

---

### Post by coffeecat on 2011-07-02
One piece of information you haven't given us is exactly which nvidia card you have. Since Jockey is recommending you the 173 version of the proprietary driver, then you probably have an older card - pre GeForce 8000 series I would guess.

I have read that some GeForce 7*** and 5*** have been problematic in 11.04, but I cannot remember the details. You might find it useful to do a forum search for your particular GPU. What is it, by the way?

---

### Post by wildmanne39 on 2011-07-02
> **MG&TL said:**
> Just to start off- I'm NOT a Unity hater, and I don't mind progress. :o

When I upgraded from 10.10 to 11.04, it came up with the standard error message 'you do not have the hardware to run unity' when I logged in to 'Ubuntu'

Obviously, I needed to add the hardware drivers, so I used an 'experimental 3d' one rather than the proprietary Nvidia ones, as the Nvidia ones have repeatedly mucked up my system in various ways on install. Anyway, I rebooted and logged back in to 'Ubuntu' (not Ubuntu classic), only to find it either was, or was pretending to be GNOME. (I.e standard Applications, places, System along the top, no launcher on the side.) No error message appeared. Ubuntu classic was exactly the same, although you would expect that to be.

My computer, as far as I'm aware, is 3d capable, and will also run Unity 2d without fault. Is it something I've done wrong, a problem with the release, or (I think most likely) just the 'experimental' driver playing up?

If it's the driver I will just have to file a bug report and 'like it or lump it' until the nice guys at Canonical/Nouveau wherever sort it out.

Have attached screenshot of 'experimental driver'
Hi, I know for me the 173 driver is the only one that works with my nvidia card in natty, I even have the cube with many effects and it is flawless. I tried other drivers and it just caused problems. My card the the 6150.

---

### Post by Geezanansa on 2011-07-02
Hi folks

I to have had exact same probs as MG&TL .. after ironing out  others... not moaning cos this a great way to get familiar with new os  and i am really enjoying ubuntu 11.04

I have however managed to get unity working again. (previously unity was  working fine on my sytem then had probs booting due to xorg  misconfiguration then after successfully booting unity no work- exact  same as MG&TL).

To help clarify what i did is first confirm that the crt monitor in the  system i am using is conected to my onboard gpu which is a nvidia  geforce 6100 and it is being driven by the recommended experimental  driver.(not 173.)

Restart system

Hold shift key after post screen to load grub

select recovery installed version

Once at the recovery menu choose the failsafex option>choose reconfigure  xorg>select cancel to get to restartx option and go booting normally  to your new unity desktop.

Easy peezy:smile:

---

### Post by Geezanansa on 2011-07-02
well it aint that easy cos i just went to additional drivers and that tells me the recommended is installed (not 173.) but is not in use!!!!!
What ever happens when i do the recovery thing explained in last post it gets unity working but it aint booting using installed driver??????mmm

---

### Post by wildmanne39 on 2011-07-02
> **Geezanansa said:**
> well it aint that easy cos i just went to additional drivers and that tells me the recommended is installed (not 173.) but is not in use!!!!!
What ever happens when i do the recovery thing explained in last post it gets unity working but it aint booting using installed driver??????mmmHi, it saying that it is not in use is just a bug if you activated it and you see the green light plus you can get to the unity desktop then it is in use.

---

### Post by Geezanansa on 2011-07-02
Good to know wildmanne39 thx.:popcorn:  hope it helps MG&TL too:D

Look forward to the updates:wink:

---

### Post by MG&amp;TL on 2011-07-03
Thanks a lot guys. Great response :)

I'm using a GeForce FX 5200. (there you go CC).  I'm reluctant to try installing the recommended 173 driver, as previously it has necessitated booting from recovery mode, or a reinstall :( , or just hasn't worked. Thanks for input though wildmanne.

This particular driver is the first one that will run 3d. Weirdly, it isn't there in 10.04/10.10. (Note that I burnt my last cd as 10.04, then ran out of cds, so I'm waiting for some more to arrive so I don't have to go from 10.04 to 11.04 every time I muck up or something dies)

Ok, Geezanasa. Will try that. Do I have to do that every time I want unity, or just the once? Thanks for going to the effort of finding that out for me. Will post the results.

Thanks everyone.

---

### Post by wildmanne39 on 2011-07-03
Hi, you are both welcome, I have been using nvidia card for the last five years, and they are one of the best supported, it just takes a little work sometimes. I have written a guide for setting up the cube and effects in natty, if you are interested this is the link.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

---

### Post by MG&amp;TL on 2011-07-03
Sorry, Geezanasa, recovery mode doesn't work. ](*,)

Boot GRUB, select recovery mode (the background is purple, which is unusual, usually I find it's black.) the computer hums for a bit and spits out some MS-DOS/terminal type black text white background rubbish. That's normal. It then boots to a blank(although lit) screen, and doesn't do anything else. Eventually my CPU light turns itself off, so I guess it thinks it's loaded.

Should I post the commands for recovery mode?

Is this a separate bug or the same one affecting GRUB too?:(

I have used recovery mode before, btw. I don't THINK it's me pressing the wrong button.

---

### Post by wildmanne39 on 2011-07-03
> **MG&TL said:**
> Sorry, Geezanasa, recovery mode doesn't work. ](*,)

Boot GRUB, select recovery mode (the background is purple, which is unusual, usually I find it's black.) the computer hums for a bit and spits out some MS-DOS/terminal type black text white background rubbish. That's normal. It then boots to a blank(although lit) screen, and doesn't do anything else. Eventually my CPU light turns itself off, so I guess it thinks it's loaded.

Should I post the commands for recovery mode?

Is this a separate bug or the same one affecting GRUB too?:(

I have used recovery mode before, btw. I don't THINK it's me pressing the wrong button.
Hi, here is a link that deals with setting boot parameters.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by MG&amp;TL on 2011-07-03
That's interesting. The thing that's designed to fix crashes...crashes.:) Once again, I've broken something!

---

### Post by MG&amp;TL on 2011-07-03
Thanks, wildmanne. Don't know what I'd do without Ubuntu Forums. Still be stuck in some hole deep in GRUB. Actually probably still in Windows. :D

---

### Post by MG&amp;TL on 2011-07-03
Sorry wildmanne...which bit of his tutorial were you suggesting I followed? I enabled modeset (it didn't work, but it made my mouse go 'blinky' and it pulled up an error on the ubuntu loading screen before the login screen. Something about "phy0" "failed to allocate device" and "invalid RT chipset" ? What does this mean, and how do I fix? The mouse is still blinky, even though I've undone the modeset change, updated GRUB, and rebooted.

Thanks for all the help. :D

(Sorry, this thread's been claimed by Mr.Fred Drift, hasn't it?)

EDIT: mouse has stopped the blink now. Error messages have disappeared too.

---

### Post by Geezanansa on 2011-07-03
After following wildemanne39's link to try cube after restarting froze at ubuntu splash...
tried alt+sysreq+r/e/i/s/u/b and tried to get to recovery console on booting but no recovery option kept trying to load to desktop i think dunno cos it froze on ubuntu splash too.  So now I cannot boot into os:( at all off hdd.

I am now using the live cd to boot from (make up a 11.04 live cd as quick as pos MG&TL) might stop ya reinstalling.  I am sure no need for that.  Same probs would possibly resurface anyway!

I was working with unity desk top when I last posted I aint now:(

Recovery options were available after choosing revovery version on hdd they aint now:(

I did think i was getting to grips of what is happening i dont now:(

I try nomodeset after restarting without live cd

I love a challenge :guitar:
Bring it on....

Where there is the will there is a way:P

---

### Post by createdcreature on 2011-07-03
Unity is absolute rubbish.

---

### Post by Geezanansa on 2011-07-03
> Thanks, wildmanne. Don't know what I'd do without Ubuntu Forums. Still  be stuck in some hole deep in GRUB. Actually probably still in Windows. :grin::lolflag:

That if grub loaded.......   

I just again tried to load grub to try nomodeset again but grub said it was loading but didnt went to ubuntu splash and froze started doing its thing all i can see is the ubuntu logo and a progress bar with white indicators turning red as everything loads then all indicators stay red and hdd stops everything freezes.
The only way i can get natty to load is from live cd and there aint no unity.

I tried nomodeset yesterday and the grub version in natty dont recognise the command but works in lucid apparently the only tutorials for nomodeset i can find are for lucid and older....

> Unity is absolute rubbish that your  opinion.  Fair enough. Here is mine You are talking rubbish.  I think unity has huge devolpment potential touch screen applications perhaps i aint no developer; but i think unity is nice to use when it is working and somebody posted asking for help to get it working.  Are you helping Robert Moyse?

Please dont post answer it is a rhetorical question.

---

### Post by Geezanansa on 2011-07-03
Are you using 64bit or 32bit version of natty MG&TL?

I am using 64bit currently but am finding myself going round in circles fixing/broken/fixed again oops broken again
Noticed recommended indicator for 32bit natty download website so am now gonna try making up a usb with 32 bit version n try that

Allso found i was not holding shift for long enough for grub to load......:oops:

Tried nomodeset = no joy

LiveCD dont need nomodeset so installed kernels probably dont either it defo no worky for me.

---

### Post by MG&amp;TL on 2011-07-03
Right...I shall hold off fiddling any further until I have a live CD. CDs come Tuesday, therefore I shall continue then...Incidentally, how do you recover an OS using a live CD? :confused:

What I usually do is do a system wipe and a clean install, then re-upgrade to 11.04.  That's fine as long as I don't have any important files, but I'm starting to program seriously now, and it's becoming less of an option everytime I muck it up to have a clean system.:mad:

Had that 'red buttons then freeze' thing before, don't know what I did though. Wasn't mucking around with grub then though, was still trying to work out what 'terminal' did :biggrin:. Good times...

I love a challenge, too. I'm probably out of my depth when the time comes to make my own instructions(rather than follow or adapt someone else's) at the moment, though. :(

Oh, and Moyse, telling people that the developer's hard work isn't a good thing is a good way to get you shouted at, as demonstrated here by my helpful acquaintance Geezanasa. If I were you, I wouldn't mention it here. Try the community cafe or somewhere instead.

---

### Post by MG&amp;TL on 2011-07-03
32-bit. Considering the amount of hassle I had with 32, I thought 64 was suicidal.

Done that myself....:oops: There's a particularly good interval you can get where it shows 'GRUB loading' so you take your hand off, then it just stays like that. Power button is the only way round that one...:D

Nomodeset didn't work for me, either. Interesting flickery mouse pointer, though.

---

### Post by MG&amp;TL on 2011-07-03
How come you know so much about this, anyway?

I know we're not supposed to take reference from bean-count, but you are the same as me, but you seem to understand stuff. :confused:

---

### Post by MG&amp;TL on 2011-07-03
Would 'recovery mode' do it, under the start menu? I shall go look-see
EDIT: No, it doesn't.

---

### Post by Geezanansa on 2011-07-03
> 32-bit. Considering the amount of hassle I had with 32, I thought 64 was suicidal.ROFL

I am a new ubuntu user like you only started using earlier this year.
Once you have a bootable cd or usb ( just go ubuntu.com>downloads all info there.) just boot from the device with the iso you just burned on.

Once you start booting from cd or usb (usb quicker) you will get the purple screen with a couple of icons at bottom of screen if you press and hold shift you will get different installation choices you could do what i have done just this afternoon and use the option that keeps all your currently installed apps in the installed kernels you are using currently or you could try without installing just to see that everything loads to desktop
okay.

All my browser settings documents etc are all there in now my downgraded 32bit installation. Handy for  my forum bookmarks!  I do have unity desktop but no docky and still checking out what is what allso get out of range window for most of the boot process just let my system go on as hdd led kept flashing indicating something is happening eventually log in screen appears...

Just been sharing what i have been learning over last couple of days trying to iron out the creases.

This is now the limit of my knowledge and really do hope for you and i both that the resolution to this is not far off.  I get feeling answer staring me in face, cant see the trees from the forest!


ATB MG&TL

---

### Post by MG&amp;TL on 2011-07-03
<blink, blink. Sort of getting you.>  Have been doing physics homework, it's scrambled my brain. :shock:

Get all the stuff about the live cd, will try that next time something dies...

Have you filed a bug report? If you confirm it, I think it gets dealt with faster. :D I put mine here:

[https://bugs.launchpad.net/ubuntu/+bug/805192](https://bugs.launchpad.net/ubuntu/+bug/805192)

Haven't got anywhere with unity or Recovery mode, will try the rest of the options for grub in that link wildmanne gave us.

Yeah, I hope something gets done, too. (Hint, hint, development guys! :)) I'll leave this thread open in case somebody else can sort us newbies out!

I guess it's a waiting game now. Install unity 2d and make do with that. I don't suppose there's somewhere where people suggest particular features they'd like for Ocelot? 

Non-related question: The 'friend' feature on this forum-what does it actually do? And is it a 'facebook' friend, whom you know vaguely over the web, or somebody you actually know in real life?

Thanks, everyone, particularly Geezanansa and wildmanne39. Even Robert Moyles did his thing ;)

---

### Post by MG&amp;TL on 2011-07-03
Installed unity 2d, now 'Ubuntu' shows as Unity 2d, rather than GNOME. I guess it looks for the most similiar fallback option.

---

### Post by wildmanne39 on 2011-07-03
Hi, that link for nomodset, what you are suppose to do is try one option at a time like noacpi,nolapic, because with a many different systems out there, there is no way to know what one option will work for any single person, you just have to try them all on that page one at a time, one of them will most likely work. I did not intend for you to try to set up the cube until you have all your problems fixed and unity was working good, I have tried that guide several times and I have not had any problem setting up the cube and effects with it. I will check back in on this thread in a little while.

---

### Post by Geezanansa on 2011-07-04
Just to update on the progress I have made = stable fully working desktop environment with full agp effects so all i did MG&TL is a reinstallation of 32bit version replacing the 64bit version previously installed i chose the option that kept installed packages and my home folder.  It really was as easy as making a live usb and booted to that device on start up.  (different machines have dfferent hot key to bring up your boot order menu this will allow you to choose which device you want to boot from or you could press f2 to enter bios setup and change first boot device to the one you want but you would probably need to change this again after you finished updating/installing and want to boot from your hdd. ayndwk)

Once booted from live version just follow the instructions and select the options you want/need.

Thx MG&TL for the reporting bug advice i havent familiarised myself with that process/site yet but did register at another ubuntu support site but didnt post cos spent ages looking/searching.   A real eye opener at the array of career opportunuties n avenues...  you stick in and make sure you get your qualifications behind ya


Thx wildemanne39  for feedback i have to admit that i was not following the instructions to the tee due to ignorance but i am not scared to have a go n practice makes perfect. So what i posted earlier about nomodeset not working in natty is inaccurate.Live n Learn.  I still have some graphics probs on booting but once login screen appears graphics visuals are the best they have been for me since i updated to natty. This is after changing from 64bit to 32bit version.

---

### Post by Geezanansa on 2011-07-04
:p
> Non-related question: The 'friend' feature on this forum-what does it  actually do? And is it a 'facebook' friend, whom you know vaguely over  the web, or somebody you actually know in real life?  You can only add members of this forum site to your contact/friend list.  For private messaging.

---

### Post by Geezanansa on 2011-07-04
Hi again 

Thx wildemanne39 managed to follow your very detailed tutorial on the cube.  Cube is working on my system now and it is a brilliant tool.

When following the cube tutorial i had to install ccsm which is normaly part of the default process...part of my architecture downgrade/change? possibly
I dunno but possible compiz config conflict causing graphics probs?
MG&TL you could try uninstalling/reinstalling all compiz packages if you can still get to your desktop, defo [SIZE=3]_**research first**_[/SIZE], sure to be a tutorial!!

Thx folks

---

### Post by MG&amp;TL on 2011-07-04
> **wildmanne39 said:**
>  I did not intend for you to try to set up the cube until you have all your problems fixed and unity was working good, 

I haven't tried to set up the cube, although it does look awesome. Never actually seen compiz work in real life...:(

Right, very hot here...I do not agree with heat and I think that I've dropped a few IQ points...:roll: Never mind, but can I re-iterate what you suggest doing? 

1. Re-install 11.04, but keep documents and settings by pressing shift on live cd boot.

2. Go through nomodeset options one-by-one, looking for what? Recovery mode working? Or am I not meant to do anything with recovery mode anymore? 

Cds came today, so I should be able to do this tonight (London-Lisbon time).

Thanks for all the interest and support, guys. This is exceptional, even for Ubuntu Forums :)

---

### Post by MG&amp;TL on 2011-07-04
That's odd...at the end of the quiet splash line there's something-'vt_handoff=7' -but it doesn't show up in /etc/defaults/grub. :confused:

And how do I tell the difference between unity 2d and 3d? They seem pretty similiar...

Also, sometimes, usually when  I've fiddled with one of the grub commands the boot before, grub loads like so:

GRUB loading...
_

whereas most of the time, it's something else entirely, it gives me some specs about my machine, then says:

keyboard failure-
GRUB loading.

I still have my keyboard though.

---

### Post by wildmanne39 on 2011-07-04
> 1. Re-install 11.04, but keep documents and settings by pressing shift on live cd boot. Hi, you can keep your documents by not partitioning your home folder and choosing to put your home on the partition when you reinstall, but if you do not have much to loose or can put what you want to keep on a external drive or usb drive I would do it that way, just reinstalling over the old system, can cause conflict,for sure when changing from 32 bit to 64 bit and vice versa.
> 2. Go through nomodeset options one-by-one, looking for what? Recovery mode working? Or am I not meant to do anything with recovery mode anymore? 
if you are going to reinstall then do not try nomodeset unless you still have problems booting.

---

### Post by wildmanne39 on 2011-07-04
> **Geezanansa said:**
> Hi again 

Thx wildemanne39 managed to follow your very detailed tutorial on the cube.  Cube is working on my system now and it is a brilliant tool.

When following the cube tutorial i had to install ccsm which is normaly part of the default process...part of my architecture downgrade/change? possibly
I dunno but possible compiz config conflict causing graphics probs?
MG&TL you could try uninstalling/reinstalling all compiz packages if you can still get to your desktop, defo [SIZE=3]_**research first**_[/SIZE], sure to be a tutorial!!

Thx folksHi,no ccsm is not installed by default, you have to install it. What graphics problem are you having?

---

### Post by MG&amp;TL on 2011-07-05
Cds came today, so I've burnt an 11.04 cd (which will soon be outdated...sigh:( )

Anyway, I did a full reinstall, and I've left it to do its thing, tell you how it gets on tommorow afternoon. Education does get in the way of things, doesn't it?

---

### Post by Geezanansa on 2011-07-05
> Hi,no ccsm is not installed by default, you have to install it.I stand corrected... I aint often right but is wrong again.... see mg&tl beans do count! :oops:my terminology/advice not up to scratch....

Just caught up on thread i have had time consuming steep learning  curve.  I been round cycle of fixing , breaking then fixing and then  breaking then fixing and then breaking then fixing and then.....

wildemannes recommendation in his post > but if you do not have  much to loose or can put what you want to keep on a external drive or  usb drive I would do it that way:guitar:

I have went through the cycle of getting unity working and then probs  slowly develop from right click menus/shortcuts missing wierd random  stuff then out of range warning box when booting... this is the start of  having to load grub or meta+sysreq+R/E/I/S/U/B or which version to boot  from grub screen then eventually being unable to get to log in or  desktop. 
I havent had much success through the use of the recovery console  command prompt or the grub command prompt or configuring an xorg config  file for the system simply due to lack of code familiarity.  The probs i  am sure you will come across ie unity launch bar and menu bars stop  working you should still be able to select help from any open  application try out some keyboard shortcuts if aint familiar with them  allready they handy for getting to log out restart etc without hitting  power button to force reset/shutdown ( meta+sysreq+R/E/I/S/U/B)

Just a personal opinion but as i have been adding hardware devices i  have been having probs with system ultimately unity being most adversely  I have found that if you open a gnome terminal and tell gnome to reset  unity by```
unity --reset
```Youll be able to see what probs there is and was with unity anything detected not quite right should get fixed.

My machine is now running 32bit Natty and i appear to have a much more  usable machine the cube and all the effects are a joy to behold....when  they working

 unity --reset(ctrl+alt+t to open terminal or install another  application launcher(like docky)so you could open terminal that way)

cough hmm this has helped me on at least one occasion and going by forum  searches ie plenty of similar probs graphics / keyboard system  usability in general it will come in handy. as a new user of ubuntu i am  not yet confident in typing code.  still have that thought of what it  gonna do? can it blow up ?waiting on a bang n puff of smoke! every time i press enter

> 
 Education does get in the way of things, doesn't it? Ubuntu usage is an education....have to admit its been a while formally  but i am sure no matter how long you on the planet it still great when     well i didnt know that? how do i do that? 

All these glitches are a great way to familiarise ourselves with our new os hope you enjoy as much as i


The onboard gpu i am using for my crt monitor is of smilar spec as yours  mg&tl and since fitting a xfx 6800gt 256mb ddr3 dual dvi pci-e card  connected to an old analogue tv(no tv licence.LOL) my unity  (s-video  connector if you wonderin.)  so now i have boot probs with cft monitor  it dont boot at all when that monitor is  forced by bios  settings.    From after the grub loading cursor out of range appears and gets  stuck...so change bios to let pci-e output be used as default .  Get  wierd and wonderful black and whitr sychedelic blocky stuck shapes as  the outline of text silhouetted. DOES BOOT TO LOG IN SCREEN then lovely launch bar and loads of differnt effects on n desktop and the list of applications is endless...  I post new thread for this as i got  unity working disabled it to get cube going....then....

no boot =no good
 grub gnome 

knowledge is power

---

### Post by noloader on 2011-07-05
> **MG&TL said:**
> **Unity's not there.**
Count your blessings.

---

### Post by wildmanne39 on 2011-07-06
> **Geezanansa said:**
> I stand corrected... I aint often right but is wrong again.... see mg&tl beans do count! :oops:my terminology/advice not up to scratch....

Just caught up on thread i have had time consuming steep learning  curve.  I been round cycle of fixing , breaking then fixing and then  breaking then fixing and then breaking then fixing and then.....

wildemannes recommendation in his post :guitar:

I have went through the cycle of getting unity working and then probs  slowly develop from right click menus/shortcuts missing wierd random  stuff then out of range warning box when booting... this is the start of  having to load grub or meta+sysreq+R/E/I/S/U/B or which version to boot  from grub screen then eventually being unable to get to log in or  desktop. 
I havent had much success through the use of the recovery console  command prompt or the grub command prompt or configuring an xorg config  file for the system simply due to lack of code familiarity.  The probs i  am sure you will come across ie unity launch bar and menu bars stop  working you should still be able to select help from any open  application try out some keyboard shortcuts if aint familiar with them  allready they handy for getting to log out restart etc without hitting  power button to force reset/shutdown ( meta+sysreq+R/E/I/S/U/B)

Just a personal opinion but as i have been adding hardware devices i  have been having probs with system ultimately unity being most adversely  I have found that if you open a gnome terminal and tell gnome to reset  unity by```
unity --reset
```Youll be able to see what probs there is and was with unity anything detected not quite right should get fixed.

My machine is now running 32bit Natty and i appear to have a much more  usable machine the cube and all the effects are a joy to behold....when  they working

 unity --reset(ctrl+alt+t to open terminal or install another  application launcher(like docky)so you could open terminal that way)

cough hmm this has helped me on at least one occasion and going by forum  searches ie plenty of similar probs graphics / keyboard system  usability in general it will come in handy. as a new user of ubuntu i am  not yet confident in typing code.  still have that thought of what it  gonna do? can it blow up ?waiting on a bang n puff of smoke! every time i press enter

Ubuntu usage is an education....have to admit its been a while formally  but i am sure no matter how long you on the planet it still great when     well i didnt know that? how do i do that? 

All these glitches are a great way to familiarise ourselves with our new os hope you enjoy as much as i


The onboard gpu i am using for my crt monitor is of smilar spec as yours  mg&tl and since fitting a xfx 6800gt 256mb ddr3 dual dvi pci-e card  connected to an old analogue tv(no tv licence.LOL) my unity  (s-video  connector if you wonderin.)  so now i have boot probs with cft monitor  it dont boot at all when that monitor is  forced by bios  settings.    From after the grub loading cursor out of range appears and gets  stuck...so change bios to let pci-e output be used as default .  Get  wierd and wonderful black and whitr sychedelic blocky stuck shapes as  the outline of text silhouetted. DOES BOOT TO LOG IN SCREEN then lovely launch bar and loads of differnt effects on n desktop and the list of applications is endless...  I post new thread for this as i got  unity working disabled it to get cube going....then....

no boot =no good
 grub gnome 

knowledge is powerHi, here is how to fix the out of range problem if it is just at boot time.
```
gksudo gedit /etc/default/grub
```
and change this line:

#GRUB_GFXMODE=640x480

to this:

GRUB_GFXMODE=640x480

Then save and exit the document.


Then do:
Code:
```
sudo update-grub
```I had this problem also, and the 640x480 you can set to 800x600 and it will look much better then the one that is default.

---

### Post by MG&amp;TL on 2011-07-06
Ummm...right. Will try "Unity --reset" Then see what happens and let the bugs loose. :)

Geezanansa:
"waiting on a bang n puff of smoke! every time i press enter"


I'm slightly more comfortable with terminal than you, geezanansa, but you have other skills beyond my comprehension...as for wildmanne...:P

For easy terminal course, try here:

[http://linuxcommand.org/lts0020.php]("http://linuxcommand.org/lts0020.php")

It's really quite good and very useful for following tutorials: less 'okay, lets paste it in slowly and see what happens' more, 'oh, right, he's doing thaaaaat. Never thought of that.' Can recommend it.

---

### Post by Geezanansa on 2011-07-06
> Hi, here is how to fix the out of range problem if it is just at boot time.
     Code:
     gksudo gedit /etc/default/grub 
and change this line:

#GRUB_GFXMODE=640x480

to this:

GRUB_GFXMODE=640x480

Then save and exit the document.


Then do:
Code:
     Code:
     sudo update-grub 
I had this problem also, and the 640x480 you can set to 800x600 and it will look much better then the one that is default.

I can not remember what idid exactly and cant find thread with info to clarify what i did but ultimately i reinstalled and updated plymouth and as part of which i got to edit the boot screen parameters

my grub  ile reads like
 # The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1024x768-24
 ]ie the command line is already uncommented


it means i get a nice purple screen( just pure plain purple) on booting now no black and white so possible plymouth bug? as i aint getting the usual red and white progress bar with ubuntu logo..

Once logged in to ubuntu session no unity log out then log in to ubuntu classic and unity working....?????..

log out and back in unity no work on any session.


On these forums i found these links [HTML]http://ubuntu4beginners.blogspot.com/search/label/Unity[/HTML][HTML]
http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html[/HTML]Have found these helpful for getting unity working but after a few start ups /restarts start getting random bugs like menus and launchers not working or disappearing completely ...

is it compiz or unity or hardware or ....

Slowly getting through the process of elimination


the more i learn the less i understand

Still think answer staring us  in face.


MG&TL mentioned a problem with unity starting as simple keyboard session/ keyboard probs ie unity installed and activated but not working
 I too have had this and cant remember exactly what i did to see this/then fix  . think it was using command line to check what version of unity installed if installed

Another valuable point i think wildemanne39 mentioned is do nott have the simple ccsm installed.
Well hope posting will help others to help us 
Thanks in advance

---

### Post by wildmanne39 on 2011-07-06
> **Geezanansa said:**
> I can not remember what idid exactly and cant find thread with info to clarify what i did but ultimately i reinstalled and updated plymouth and as part of which i got to edit the boot screen parameters

my grub  ile reads like
 # The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1024x768-24
 ]ie the command line is already uncommented


it means i get a nice purple screen( just pure plain purple) on booting now no black and white so possible plymouth bug? as i aint getting the usual red and white progress bar with ubuntu logo..

Once logged in to ubuntu session no unity log out then log in to ubuntu classic and unity working....?????..

log out and back in unity no work on any session.


On these forums i found these links [HTML]http://ubuntu4beginners.blogspot.com/search/label/Unity[/HTML][HTML]
http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html[/HTML]Have found these helpful for getting unity working but after a few start ups /restarts start getting random bugs like menus and launchers not working or disappearing completely ...

is it compiz or unity or hardware or ....

Slowly getting through the process of elimination


the more i learn the less i understand

Still think answer staring us  in face.


MG&TL mentioned a problem with unity starting as simple keyboard session/ keyboard probs ie unity installed and activated but not working
 I too have had this and cant remember exactly what i did to see this/then fix  . think it was using command line to check what version of unity installed if installed

Another valuable point i think wildemanne39 mentioned is do nott have the simple ccsm installed.
Well hope posting will help others to help us 
Thanks in advanceHi, I think you should change this GRUB_GFXMODE=1024x768-24
to this GRUB_GFXMODE=1024x768, mine would not show the screen properly with the 24 at the end, I hope that helps.

---

### Post by Geezanansa on 2011-07-06
thx again wildemanne39
with regard to getting unity fired up
here is what happens when i try to reset compiz and unity with my current/most recent settings

```
user@user-desktop:~$ gconftool-2 --recursive-unset /apps/compiz-1
user@user-desktop:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: glXCreateContext failed
Compiz (bailer) - Info: Ensuring a shell for your session
user@user-desktop:~$ Cannot register the panel shell: there is already one running.
```

note how i allready in unity profile do had to swith to metacity mode>try again in classic session?


with reference to your last post about booting/missing plymouth prob wildemanne39 I will try dropping the-24 as advised
 it denotes 24bit right?

okay just updated grub file by doing this 

```
user@user-desktop:~$ gksudo gedit /etc/default/grub

(gedit:2346): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2346): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.KUZHYV': No such file or directory

(gedit:2346): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2346): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.IA22XV': No such file or directory

(gedit:2346): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
user@user-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```Thought i would post BEFORE reboot......

:lolflag:

---

### Post by Geezanansa on 2011-07-06
Just logged in to unity desktop with the launcher down left side of screen instead of classic menu bar style desktop.  YIPPEEEE:popcorn:
   My machine went through the post screens then a purple screen  until  log in screen appears. The purple did fit my screen better that time  round though wildmanne39.!!!

I started a new thread "[B]Unity, Cube and multiple monitors HELP" trying to describe better what probs i am having specificly.  Still no replies yet ....

any  advice on how to configure system with one monitor connected to pci-e  card s-video out and one monitor connected to i/o shield/onboaed?

Have been posting last few posts on system using analogue tv connect to a xfx gf6800gt 256mb ddr3 PCI-E card

I have to go into bios settings and change setting for which graphics to use as default to PCI-E

I can then get to system desktop.. 

If  itry to boot from crt monitor connected to i/o shield/onboard  after changing the bios settings to select onboard graphics as default -save and reboot-get post  screens then out of range window and plymouth never appears nor does  log in screen or anything else no input devices so hard power  down/reset.


What i am trying to do is achieve the set up i  had on my  old system(currently building one i am using) so that i can  switch screens one for gaming/surfing and one for anything i feel like  

in theory/practice  i know can do but with the current hardware config still determining....

live n learn[/B]

---

### Post by Geezanansa on 2011-07-06
After rebooting to ubuntu desktop without unity launchpad logged out and logged in to classic session with unity launch pad so logged out and logged back to ubuntu session and had unity launchpad.
Then started getting cube and special effects folloeing [HTML]http://amazingubuntucube.blogspot.com/[/HTML]
when restarting after activating cube etc same process again to get unity launchpad in ubuntu session
so after days of circles at the end of the article @ [HTML] http://amazingubuntucube.blogspot.com/[/HTML] it clearly says
> [SIZE=4]There are many other effects and  settings that you can experiment with, I recommend changing them one at a  time that way if  you have an undesirable outcome you will know what to  change back.  Also if you change something that messes up unity just  logout and back in and that should fix your problem, assuming you did  not deactivate the unity plugin.

**Warning do not deactivate the unity plugin after setting up the cube and effects.**[/SIZE]

So as i have been adding hardware devices etc could this at any point deactivate unity(or put unity to simple keyboard mode)?

How to restart unity from simple keyboard to higher status?

---

### Post by wildmanne39 on 2011-07-06
Hi, the only thing that would miss up unity is to install a new graphics card or possibly a new graphics driver, other then opening ccsm and unchecking unity plugin. I do not know why you have to log into classic then out and then it will let you log in to unity. Open dash by hitting alt+f2 this is in unity and type in login and it will open the login screen settings,then at the bottom of that window it will have a grayed out window that says select as default session see if that is ubuntu and not ubuntu classic, you will have to put in your password to change it if it needs to be changed.

---

### Post by Geezanansa on 2011-07-07
Just updating when i stert machine from cold get to log in screen and log into ubuntu session and get  menu bar/task bar etc load ie classic screen.
I now log out and log straight back into ubuntu session and get launch pad etc ie unity working....
If after booting and logging in to ubuntu get no launchpad etc then log out i do still get launchpad etc in classic session too...
so i tried alt+f2 and searched/typed login but login did not load
searched apps found login selected it and it then launched..
my default session is definitely ubuntu

Two days/sessions in a row with effects and unity still activated.....

Progress is being made!!!

---

### Post by wildmanne39 on 2011-07-07
> **Geezanansa said:**
> Just updating when i stert machine from cold get to log in screen and log into ubuntu session and get  menu bar/task bar etc load ie classic screen.
I now log out and log straight back into ubuntu session and get launch pad etc ie unity working....
If after booting and logging in to ubuntu get no launchpad etc then log out i do still get launchpad etc in classic session too...
so i tried alt+f2 and searched/typed login but login did not load
searched apps found login selected it and it then launched..
my default session is definitely ubuntu

Two days/sessions in a row with effects and unity still activated.....

Progress is being made!!!Hi, yes there is progress, but I have no idea why you have to log in that way to get unity, but I am going to research the problem.

---

### Post by MG&amp;TL on 2011-07-07
Sorry everyone-got distracted learning how to use a terminal properly, writing shell scripts, writing patches for ubuntu and such. A little better prepared now I think. However, I now have a LOT of catching up to do with you guys though...:D

Now know what unity3d looks like, I stuck a live cd in my mum's laptop.

"The more I know the less I understand" -So true, but it's better than the windows 'cotton-wool' approach, isn't it?

P.S. (not relevant at all, but not worth starting a new thread for)
(On a different pc)If you dual-boot windows 7 and ubuntu, be very careful re-partitioning things. Got myself 'burnt' today, booted to 'grub: no such partition' 
grub rescue>
It seems the way around this is to re-install ubuntu alongside windows, and then it works fine. Scary though.

---

### Post by MG&amp;TL on 2011-07-11
<Posting from non-buggy laptop>

Is it normal for unity --reset to run for quarter of an hour, and counting? Because it is.

On the plus side, a shadow now appears behind the windows, everything's still sort of operational,the launcher's there, you can launch progs from there, but it's blank.

On the not-so-good side, it spewed a lot of stuff abosut Xquery trees, like your posts, but then it started saying things like **failed, d_bus failure, X_Bio and that. (Sorry, can't be too specific, the terminal's still running and the screen keeps blinking. Did you guys get this before you fixed it?

(Just realised this thread has had nearly 1,000 views :o . Therefore, after this has all been fixed, is it worth writing a how-to, or is it too obscure for that? Just a thought, and I'm happy to write it providing someone experienced in such matters, like wildmanne or an admin, gave me the go-ahead.)

---

### Post by MG&amp;TL on 2011-07-11
Terminal is STILL going, after half an hour, although the screen has stopped blinking, so I can post the output. I'm assuming it's hung. :(

WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing mousepoll options...done
Initializing vpswitch options...done
Initializing animation options...done
Initializing snap options...done
Initializing expo options...done
Initializing move options...done
Initializing place options...done
Initializing grid options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing ezoom options...done
Initializing workarounds options...done
Initializing staticswitcher options...done
Initializing resize options...done
Initializing fade options...done
Initializing unitymtgrabhandles options...done
Initializing scale options...done
Initializing session options...done
** (<unknown>:1556): DEBUG: Unity accessibility initialization
** (<unknown>:1556): DEBUG: Shows on edge: 1

Screen geometry changed:
  Monitor 0(primary)
   0x0x1280x1024

unity-panel-service: no process found
** (<unknown>:1556): DEBUG: PanelController:: Added Panel for Monitor 0
Initializing unityshell options...done
** (<unknown>:1556): DEBUG: MaximizeIfBigEnough: Gnome-terminal window size doesn't fit
Starting unity-window-decorator
** (<unknown>:1556): DEBUG: PlaceEntry: Applications
** (<unknown>:1556): DEBUG: PlaceEntry: Commands
** (<unknown>:1556): DEBUG: PlaceEntry: Files & Folders
** (<unknown>:1556): DEBUG: /com/canonical/unity/applicationsplace
** (<unknown>:1556): DEBUG: /com/canonical/unity/filesplace
** (<unknown>:1556): DEBUG: Setting to primary screen rect: x=0 y=0 w=1280 h=1024
** (<unknown>:1556): DEBUG: Acquired the name com.canonical.Unity.Launcher on the session bus


(<unknown>:1556): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (<unknown>:1556): DEBUG: IndicatorAdded: libapplication.so
** (<unknown>:1556): DEBUG: IndicatorAdded: libsoundmenu.so
** (<unknown>:1556): DEBUG: IndicatorAdded: libmessaging.so
** (<unknown>:1556): DEBUG: IndicatorAdded: libdatetime.so
** (<unknown>:1556): DEBUG: IndicatorAdded: libme.so
** (<unknown>:1556): DEBUG: IndicatorAdded: libsession.so
Setting Update "run_command_terminal_key"
Setting Update "fullscreen_visual_bell"
** (<unknown>:1556): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:1556): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:1556): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:1556): DEBUG: TrayChild Rejected: update-notifier update-notifier Update-notifier
** (<unknown>:1556): DEBUG: Connected to proxy

(<unknown>:1556): dee-WARNING **: Transaction from com.canonical.Unity.FilesPlace.SectionsModel is in the past. Ignoring transaction.

(<unknown>:1556): dee-WARNING **: Transaction from com.canonical.Unity.FilesPlace.GroupsModel is in the past. Ignoring transaction.

(<unknown>:1556): dee-WARNING **: Transaction from com.canonical.Unity.FilesPlace.GlobalGroupsModel is in the past. Ignoring transaction.
** (<unknown>:1556): DEBUG: Connected to proxy
** (<unknown>:1556): DEBUG: Connected to proxy

(<unknown>:1556): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:1556): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:1556): GLib-GIO-CRITICAL **: g_bus_own_name: assertion `g_dbus_is_name (name) && !g_dbus_is_unique_name (name)' failed

(<unknown>:1556): GLib-GIO-CRITICAL **: g_bus_watch_name: assertion `g_dbus_is_name (name)' failed

(<unknown>:1556): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed

(<unknown>:1556): GLib-GIO-CRITICAL **: g_dbus_connection_register_object: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed
** (<unknown>:1556): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate

(firefox-bin:1668): LIBDBUSMENU-GTK-CRITICAL **: dbusmenu_menuitem_property_set_shortcut: assertion `gtk_accelerator_valid(key, modifier)' failed
:confused:

Anybody have a clue?

EDIT: Nope, it's not hung, it's just spat out some more giberish. Yay. Will post update when volume of gibberish is a reasonable quantity.

---

### Post by wildmanne39 on 2011-07-11
Hi, usually letting it run three minutes is long enough then you need to restart, and everything is fixed but you are having an issue that is a little different. Also have a look at this link, he had the same issues but I believe he never got it right without reinstalling.
[http://ubuntuforums.org/showthread.php?t=1797332&highlight=window+borders](http://ubuntuforums.org/showthread.php?t=1797332&highlight=window+borders)

---

