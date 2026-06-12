---
title: "Many Issues with KDE 4.x"
date: 2008-09-03
forum: Desktop Environments
---

### Post by jimbo99 on 2008-09-03
I have the latest KDE 4.x as of this morning when updates were pushed out.  Over the past few months I've periodically looked at KDE to see if it is a solid product.  I've seen many things I do like and many that I just can't stand and even more where I'm in the middle (could give or take on them).

When I started with KDE it was my opinion they were shooting themselves in the foot by delivering something (even in alpha/beta) that was as bad as it was.  Yes, with the latest it has seriously improved but honestly I have to wonder in which direction.  What I mean is that there are improvements but in many ways there were so many problems that were so visible that should have focused on those.  It appears they have not.  An example of this is the K menu.  When you bring it up there are a ton of missing icons. Really, this is something that we work on day in and day out why would they not put representative icons in place?  Another example would be when I download files via FF I tell it to save them to the desktop yet they are not there.  Yet another is when I traverse folders many times they have this generic ? icon.  What's up with that?  If folders have icons and this folder is the same as all the others shouldnt' they all have the same icons?

Another difficulty is in finding my the volumes representing my other drives.  I have several drives in this machine and I certainly would love to easily access those with the click of a mouse.  It took forever to discover that I could see them in the dolphin file manager under this little tiny icon to the left of the name of the folder I was in.  There has to be better more representative way to display the fact that I have more volumes.

I list a few more.

By now they should have put the Up button in Dolphin.

The little + symbol associated with each folder which is supposed to represent "select item" appears to do nothing at all.

The Desktop even though I have 3.25 gigs of RAM and an Athlon X2 6000+ with dual 8800gt 512mb video cards appears very choppy.

System monitor indicates I only have 1.1 gigs of RAM.  As I stated above I have 3.25gigs.

System monitor indicates at times that I have X% of CPU usage yet when I have the list set to display all and sorted by CPU utilization it is often wrong.  I can total the numbers up and they are always less than the total consumption that system monitors indicates is being used.  For instance it was showing 63% CPU usage but when I view the tasks sorted by CPU usage it totaled 13%.

When I grab a window to drag around (Ubuntu 8.10 with latest updates running compiz). When I grab a window it can sit for a couple seconds before responding and when I move the mouse, the window will show a delayed movement and a jump.

The trashcan applet constantly tells me I have 55 items and provides me with the option to empty the trash.  The problem is that it never resolves itself to 0 items.

With just 2 desktops if I hold down the button to switch desktops it will spin the desktops at a fast rate and then crash asking me of all things (and I find it laughable) to report that to KDE.

When I indicated that I wanted more than 2 desktops (4 total instead) it wouldn't update.  It still only provides 2.

Lots of dialog boxes aren't sized properly and lots of check boxes are so improperly sized that a residual dots from wrap or sizing are displayed too.

There are far too many others to list here.  I am just wondering where these guys are in their thought process.  Are they aware that it is the visual aspect that we see first and that access to our folders, icons, and files is extremely important?

---

### Post by ursus262 on 2008-09-04
I'm not sure if KDE 4.1 is much good anyway. It's not very stable and I find that I've lost control of many of my laptop's audio controls, like the volumee buttons, etc. Very buggy in my opinion. I'm not even sure if I have KDE 4.1.1, although there was a major upgrade yesterday on my adept package manager, so I guess something has happened.

It looks stunning, but it's a right pain to use! And every time I start up and shut down, I hear this ridiculous piano flourish at full volume. Any idea of how to get rid of that?

4.1 is great, but I reckon more work needs to be done before I am entirely convinced.

---

### Post by kenono on 2008-09-04
I'm sorry to hear that you haven't had a good experience with KDE 4, I'm new to it myself and haven't been having very many issues at all.

> By now they should have put the Up button in Dolphin.

I agree it should be there by default, but it can be done by editing the toolbar settings.

> The trashcan applet constantly tells me I have 55 items and provides me with the option to empty the trash. The problem is that it never resolves itself to 0 items.

This is one issue I've been having too, it resolves itself if I empty the trash from the trash window in Dolphin but not if I do it directly from the widget. As a result, I've stopped using that widget.

I'm sorry I can't really help with the rest of your problems but I hope you figure them out. :)

---

### Post by adibudeen on 2008-09-06
I also hope that you are able to resolve your problems, as they seem to mostly be problems unique to your system.  I have KDE 4.1.1 running on three machines in my house (including an EeePC), and I haven't experienced any of those problems.  There are no icon issues at all.

> Another example would be when I download files via FF I tell it to save them to the desktop yet they are not there. 

KDE 4 uses a different philosophy for the "desktop".  Gone are the days of piling scattered files all over the desktop.  This is something someone like me welcomes, as I always preferred an organized desktop with only a few, if any icons.  If, however, you prefer to have the piles, fullscreen folderview will be implemented to allow you to have a more traditional desktop.

At any rate, you simply have to add a folderview plasmoid to your desktop that will display the desktop folder.  Then you will see your downloaded files.  If you still don't see them, there is something else wrong with your filesystem setup.

> By now they should have put the Up button in Dolphin.

This is something that is really just your personal preference.  By default, Dolphin comes in a very simplified configuration.  Since they provide you with the means to easily add the up button, why complain?

> When I indicated that I wanted more than 2 desktops (4 total instead) it wouldn't update. It still only provides 2.

You indicated that you are using compiz, and that is probably where the problem lies.  This does not exist with kwin.  Compiz uses a different (gnome-like) method of representing virtual desktops than what KDE uses.  This problem exists in KDE 3 as well, but there have been hacks that fix it.  I'm sure those hacks will appear in KDE 4 as well.  Since compiz is basically an add-on to desktop environments, IMO the fix should come from the compiz developers, not the KDE ones.

> The Desktop even though I have 3.25 gigs of RAM and an Athlon X2 6000+ with dual 8800gt 512mb video cards appears very choppy.

I'm assuming that 8800gt means that it's an Nvidia card.  If so, the problems with the nvidia drivers have been well documented, and some workarounds do exist.  This is something that Nvidia needed to fix with their drivers, and from what I've heard, the newest beta drivers have solved the problems.

Having stated what I mentioned above, it is important to know that each system setup is  unique, and it is impossible for developers to know every anomaly that will occur with every system.  As I mentioned, I have three very different systems all running KDE4 and have experienced none of your problems.  I therefore recommend submitting bug reports to the appropriate places.  Although your problems may have to do with your specific hardware, you might not be the only one, and a few people will benefit from any solutions that result from your help.

I wish I could be of more assistance to you.  The important thing to remember about KDE 4 is that it does take a different approach to using a desktop.  It takes getting used to, and some people simply won't like it.  Free software has always been about choice, and that is why we have different desktop environments to choose.

---

### Post by awakatanka on 2008-09-06
Thrash can problem i have also, i empty it by going in thrash with dolphin and delete the files. Also nvidia give some problems here but not as much as some have. + symbol is working here no problems with it. 

Are those problems still there if you don't use compiz? maybe compiz gives you some of the problems

---

### Post by dentharg on 2008-09-06
I took an update to 4.1.1a today. Everything now depends on MySQL server? Why the hell?

---

### Post by pbhj on 2008-09-06
> **adibudeen said:**
> KDE 4 uses a different philosophy for the "desktop".  Gone are the days of piling scattered files all over the desktop.  [...] At any rate, you simply have to add a folderview plasmoid to your desktop that will display the desktop folder.  Then you will see your downloaded files.  If you still don't see them, there is something else wrong with your filesystem setup.

No, KDE4 (which I'm using now on 2 boxen) doesn't use a desktop; it has a large application launcher, like a quicklaunch bar but not as useful, a largely non-functional widgets (plasmoids, bleurgh!). You don't have to "pile scattered files" on it to find it useful. For me it's always been a holding place allowing me to finish a task before deciding exactly where to file stuff, or to remove a download altogether if it was only needed transiently. KDE4's desktop-like interface is useless to me as it stands.

Folderview is just a poor replacement for having a file manager open in the background.

---

### Post by randcoop on 2008-09-06
What's remarkable to me at this point is that there are still defenders of KDE 4.xx.  It's been an abysmal failure from start to finish.  To begin with, it was introduced prematurely, so buggy as to be unusable by any but the most hardened of computer geeks.

After that launch, the story was repeatedly told about how the developers knew that it wasn't ready for prime time and they just wanted more testers.  Wait until version 4.1 and all will be wonderful.  

Instead, 4.1 has brought more of the same.  

KDE developers have decided to appeal to a small audience of users, people who want all sorts of eye candy, even if that means relinquishing ease of use and functionality.  

The current version of 4.1.1 still doesn't permit keyboard shortcuts to work properly.  Everything is mouse driven.  And the customization process of making the panel look the way you want it to is still lacking.

These are just the tip of the iceberg.  Konqueror still has major problems and even the migration from Kmail in 3.5.xx to 4.xx is so difficult as to be impractical again for all but the most savvy of users.

After using KDE for years, I recently switched to Xubuntu.  Still I long for the days when developers actually tried to broaden the base of users instead of shrinking it.  But KDE is an object lesson in how not to do that.

---

### Post by TheUbGuy on 2008-09-06
> **ursus262 said:**
> I'm not sure if KDE 4.1 is much good anyway. It's not very stable and I find that I've lost control of many of my laptop's audio controls, like the volumee buttons, etc. Very buggy in my opinion. I'm not even sure if I have KDE 4.1.1, although there was a major upgrade yesterday on my adept package manager, so I guess something has happened.

It looks stunning, but it's a right pain to use! And every time I start up and shut down, I hear this ridiculous piano flourish at full volume. Any idea of how to get rid of that?

4.1 is great, but I reckon more work needs to be done before I am entirely convinced.

KDE 4.1 has great potential. Many users have had no problems with it, while just as many seem to always have problems. Although it is an improvement over 4.0x, it is still unstable. If you run it, just be prepared to deal with whatever glitches may arise.

---

### Post by awakatanka on 2008-09-07
> **randcoop said:**
>  
The current version of 4.1.1 still doesn't permit keyboard shortcuts to work properly.  Everything is mouse driven.  And the customization process of making the panel look the way you want it to is still lacking. know problem that is being worked on, sometimes it takes a bit longer to solve it. If you know better then try to do it.


If its not ready stay on kde 3.5.10 you are not forced to use kde4. Seems to me you want to use bleeding edge but don't want to deal with the short comings if you use bleeding edge. Mostly people complain about something that is worked on already.

---

### Post by Sain on 2008-09-07
I've always preferred KDE over Gnome, but now I'm on Gnome, and don't think of coming back to KDE anytime soon...

KDE4 has potential, but it's barely half finished product! I've waited for 4.1 to use it (as advised from KDE team) but it didn't do. There are lots of improvements, but it's still slow and buggy beyond forgiveness. Desktop environment is part of a base of operating system and it HAS to be stable...

That said, I don't think 4.2 will be much better. I think I'll try it again in a year or two.

---

### Post by randcoop on 2008-09-07
> know problem that is being worked on, sometimes it takes a bit longer to solve it. If you know better then try to do it.

I've heard this rather odd kind of response before.  I am a computer user, not developer.  I don't pretend to know how to make KDE work; the developers do pretend to know.  When my car breaks down, I expect the mechanic to be able to fix it, not tell me that if I'm unhappy with the amount or quality of his work, I should fix it myself.

> If its not ready stay on kde 3.5.10 you are not forced to use kde4. Seems to me you want to use bleeding edge but don't want to deal with the short comings if you use bleeding edge. Mostly people complain about something that is worked on already.

If KDE 4 is to be considered bleeding edge, then someone should mention this to the developers of the system.  THEY don't call it bleeding edge.  They actually seem to believe that it is ready for use by computer users like myself.  I don't use bleeding edge systems.  The problems arise when expectations are created.  Don't announce that a system is ready for prime time and then tell users that it's really bleeding edge software after they've downloaded it.

---

### Post by awakatanka on 2008-09-07
> **randcoop said:**
> I've heard this rather odd kind of response before.  I am a computer user, not developer.  I don't pretend to know how to make KDE work; the developers do pretend to know.  When my car breaks down, I expect the mechanic to be able to fix it, not tell me that if I'm unhappy with the amount or quality of his work, I should fix it myself. If you unhappy about a future that you are missing in the car you can't demand that company to put it in because you need it. You can pay some to do it for you our you do it. And kde 4 isn't broken for many users but it sure lacks some option they are working on, and if that is an option you need you can stick to kde 3.5 that worked for you till it is there.  You telling someone to fix you're car without giving something in return. And sure i did the same in the past but now i realize that i demand someone to fix something while he has x numbers of the same sort of questions where he is working on. If it isn't there yet it will be in later our they have a good reason not to put it in.



> If KDE 4 is to be considered bleeding edge, then someone should mention this to the developers of the system.  THEY don't call it bleeding edge.  They actually seem to believe that it is ready for use by computer users like myself.  I don't use bleeding edge systems.  The problems arise when expectations are created.  Don't announce that a system is ready for prime time and then tell users that it's really bleeding edge software after they've downloaded it.If its new then it is bleeding edge, and sometimes they need to reinvent because in the old version it work but was hacked around to get it to work. Now they want it to work with clean code and that can take a bit longer then you want. Make a choose, make something and keep it beta with a few people testing and bug reports are small and that makes progress also slower, our release it because most function work but lacks some options and lots of people start using it and bug reports coming in fast and that make the progress also faster. The last thing they did and warned people also on many other sites and blogs.

---

### Post by ursus262 on 2008-09-07
There is no doubt that KDE 4.x is innovative insofar as it will take Linux into the web 2.0 and Windows 7 era.  However, at the moment, their hands are tied with current hardware standards and this can't make things easy for them.

I think the issue here is one of communication, because any new piece of software, when implemented, will show up inadequacies and bugs; that's the nature of the beast I'm afraid. However, it would have been better all round if the developers had made it clearer that this is a development project in the first place.  Of course, people have a choice, which is one of the advantages of Linux, but that depends on clear information to people who may not be quite as computer savvy as the developers who created the software in the first place.

---

### Post by Sain on 2008-09-07
> **ursus262 said:**
> There is no doubt that KDE 4.x is innovative insofar as it will take Linux into the web 2.0 and Windows 7 era.  However, at the moment, their hands are tied with current hardware standards and this can't make things easy for them.


So what are you saying, that KDE4 is beyond today's hardware?

They need to work on BUGS. Plain and simple!

---

### Post by ursus262 on 2008-09-07
What I am saying is that the demands of 4.1 are probably too much for many of today's pcs and it will probably come into its own as hardware and technology develops over the coming months.  My laptop, for example, cannot run Vista properly because of the intense graphics, even though it was installed as default from new.

Yes, there are bugs too, and useability problems that will, I am sure, be resolved in the near future - but it's much more than that.

---

### Post by tpls on 2008-09-07
[http://palkki.oulu.fi/~takkintu/upload/bugitus.png](http://palkki.oulu.fi/~takkintu/upload/bugitus.png)

I've installed kde4 and the result was quite interesting. How can I get rid off those chessboxes? Althought, resolution is ok for my lcd but kde-box is too small. I've installed nvidia tv-out with two separate screens on xorg.conf. Thanks for help in advance.

---

### Post by Sain on 2008-09-07
> **ursus262 said:**
> What I am saying is that the demands of 4.1 are probably too much for many of today's pcs and it will probably come into its own as hardware and technology develops over the coming months.  My laptop, for example, cannot run Vista properly because of the intense graphics, even though it was installed as default from new.


I have 3-year-old Pentium 4. That's not "today's PC", but KDE 4 should *fly* on this configuration. Vista does. 

If KDE 4 doesn't work like it suppose to on "today's PCs" it simply means that it's not optimized, and that is wasting resources. And that's a bug. Besides KDE 4 should be even less memory intensive than KDE 3, due to optimized Qt libraries.

---

### Post by randcoop on 2008-09-07
To talk about KDE as though it is an entirely new system is simply wrong.  When Vista came out, after numerous delays, the big criticism was that it still wasn't ready.  It's the same with KDE.  Once you've created a large user base, like KDE has, it's wrong to decide to come out with a new version of your software that doesn't work for many or even most of that user base.

KDE didn't have to introduce 4.0 prematurely; the developers chose to do that because they wanted to take advantage of a large user base of "testers."  To entice people to download and install this so-called beta version (although they didn't use the word beta and it actually was more like alpha), they promised that development would be fast and furious and that version 4.1 would be fabulous...the real final release.  

But that hasn't happened and now everyone's saying maybe it will happen in version 4.2.  

I know perfectly well what my options are.  I've been using Linux for a very long time and have changed distros and desktops and window managers many times.  My problem with KDE 4.xx isn't a problem with the idea of having to change.  It's a problem of the way the development has proceeded and the abuse I believe the users of the system have had to endure.

---

### Post by QCompson on 2008-09-07
> **randcoop said:**
> It's a problem of the way the development has proceeded and the abuse I believe the users of the system have had to endure.
I tend to agree.  I wouldn't go so far as to call it abuse, but the KDE developers have certainly tested the patience of a lot of their userbase.  4.0 was pretty much unusable for day to day work; 4.1 is better, but still isn't there yet IMO.  I can't get over the fact that basic keyboard shortcuts aren't working at this point in the release cycle.  

The developers have become very testy and defensive after all of the criticism they have weathered.  That's understandable, but some of their responses (including a couple very cranky posts by developers claiming that KDE doesn't need or care about users) and decisions have left a really bad taste in my mouth.  I really think they've made a horrible mess of the transition from KDE 3 to 4.

---

### Post by Sain on 2008-09-08
I really like the fact that KDE developers had guts to start from scratch to make the base for desktop environment that doesn't drag the same old code from years ago. 

But 4.1 is still unstable for daily usage and it will take about 4.3 to truly replace 3.5.x And that sucks. Gnome seems like the better option now, although Gnome looks the same to me for years.

---

### Post by QCompson on 2008-09-08
> **Sain said:**
> I really like the fact that KDE developers had guts to start from scratch to make the base for desktop environment that doesn't drag the same old code from years ago.
It was a bold endeavor, and I give them credit for that.  In my opinion they just got their priorities out of whack.  They needed a more competent project manager to better guide the direction of KDE4.

Start out on a whole new code base, have it all in qt4, great.  But have a simple but bug-free taskbar and make sure basic keyboard shortcuts work before you start working on clock and calculator widgets for the desktop and wobbly window animations.  Make sure the basics are in place before you start going wild with the eye candy.

---

### Post by awakatanka on 2008-09-08
> **QCompson said:**
> It was a bold endeavor, and I give them credit for that.  In my opinion they just got their priorities out of whack.  They needed a more competent project manager to better guide the direction of KDE4.

Start out on a whole new code base, have it all in qt4, great.  But have a simple but bug-free taskbar and make sure basic keyboard shortcuts work before you start working on clock and calculator widgets for the desktop and wobbly window animations.  Make sure the basics are in place before you start going wild with the eye candy.Those are thing that are important for some users, others need different things. Who decide what is more important? you, me? They are working on it so they decide what is more important with the manpower they have. And if some people work on widget/plasmoid that doesn't mean they can work on other parts. You don't let a car painter make a motor for a car.  There will always be users unhappy with decision made by others, you can't simple make everyone happy at once but slowly you can try to make them happy if its possible and fits in the picture they see of kde4.

---

### Post by Sain on 2008-09-08
Look, the "old" KDE 3.5 didn't even have widgets and compositing effects for window manager... It relied on external programs for that. So they could easily postpone things like compositing support, and make the core things function properly.

They should organize better, and release KDE4 when it was ready or cut some optimistic features... Now we have a desktop environment based on new technology, with huge potential, that crashes randomly and has non-functional keyboard shortcuts

---

### Post by ursus262 on 2008-09-08
> **Sain said:**
> I have 3-year-old Pentium 4. That's not "today's PC", but KDE 4 should *fly* on this configuration. Vista does. 

If KDE 4 doesn't work like it suppose to on "today's PCs" it simply means that it's not optimized, and that is wasting resources. And that's a bug. Besides KDE 4 should be even less memory intensive than KDE 3, due to optimized Qt libraries.

Well, I stand by my previous comments, because I am speaking from my experiences of using Vista (which, let's be honest, is pretty dreadful) on a laptop which I bought from new less than two years ago.  You used the auxilliary verb 'should' in your comment above.  Should.... should...should...!  It should, at least, provide some decent level of functionality as a fully-fledged piece of software - but it doesn't!  Likewise, it should be a stable release, but it's not.  Which brings me back to my central point: had they actually released it for what it is - as an alpha - then there wouldn't have been a problem.  It's about clarity and respect for the users of their creations.  Nothing more and nothing less.

---

### Post by randcoop on 2008-09-08
The defense of the KDE developers on this thread reflects a fundamental misunderstanding (IMO) of the issue that critics are making.  There's no doubt that KDE developers have limited assets (especially time) and that developing an entirely new system manager is a difficult enterprise even for a for-profit enterprise like Microsoft.  But that simply isn't the point.

The point is that that KDE developers ought not to have introduced KDE 4 until it was ready.  And the standard for knowing when it is ready is that it can be used by the legion of faithful and committed KDE users.  Those users...who aren't developers, programmers, specialists, contributors or anything else related to the development process...who are simply users of computers...have every reason to expect that a mature system like KDE will be fit for their use when a new version is introduced.  It wasn't.  And it isn't.

As has repeatedly been pointed out here, the lack of keyboard shortcuts is one simple and obvious example of just how weak this introduction was.  I actually visited the KDE IRC on at least three occasions after 4.0 and 4.0.1 and 4.0.2 came out and asked about the simply invocation of the menu using alt-F1.  This isn't an extraordinary thing.  It's a keyboard shortcut that has been used by KDE from the very beginning.  And expecting a keyboard shortcut to launch the menu is not asking for bleeding edge performance.  I am aware of no system that doesn't have one.

Except, now, KDE.

They botched this thing terribly.  

The only hope is that someone will right the ship.  But if defenders keep claiming that users don't matter, then the ship won't be righted.  Let's hope that doesn't happen.

---

### Post by awakatanka on 2008-09-08
> **randcoop said:**
> 
The only hope is that someone will right the ship.  But if defenders keep claiming that users don't matter, then the ship won't be righted.  Let's hope that doesn't happen.The passenger that try to right the ship will also not work. Someone is the captain and he decide what to do. 

I life without shortcuts and lots of users do the same, people need to say it is **not ready for me** and not kde4 isn't ready because it doesn't do .........

but lets end this because it isn't going anywhere. But the good news is finally gnome is ready because nautilus  has tabs now, those stupid dev people finally have listen to the users :lolflag:

---

### Post by Coplen on 2008-09-09
> **randcoop said:**
> 

As has repeatedly been pointed out here, the lack of keyboard shortcuts is one simple and obvious example of just how weak this introduction was.  I actually visited the KDE IRC on at least three occasions after 4.0 and 4.0.1 and 4.0.2 came out and asked about the simply invocation of the menu using alt-F1.  This isn't an extraordinary thing.  It's a keyboard shortcut that has been used by KDE from the very beginning.  And expecting a keyboard shortcut to launch the menu is not asking for bleeding edge performance.  I am aware of no system that doesn't have one.

Except, now, KDE.

*shrugs* I never knew about that shortcut until you mentioned it and it works fine on my end. :confused:

Maybe you're a little too upset to be speaking rationally about KDE 4. Ok, it doesn't do what you think it should. And that's fine. But ranting on a forum about it isn't helping matters any. I've seen a lot of improvement from 4.0 to 4.1.1. Sometimes these things take time.

---

### Post by randcoop on 2008-09-10
> Maybe you're a little too upset to be speaking rationally about KDE 4. 

Please let me know what you mean by "rationally."  Since I consider myself completely rational, I wonder if you mean to say: "maybe you're not willing to agree with me so I will condescend to you by suggesting that you're irrational, rather than discuss the subject with you intelligently."

> I never knew about that shortcut until you mentioned it and it works fine on my end.

I assure you that you are the very small exception if the alt-F1 key invokes your menu in KDE 4.xx.  The developers know that it doesn't work for almost everyone else and have promised to correct it.  The fact that you didn't know about the shortcut, or that it doesn't matter to you, misses the point entirely.  It matters to many, many people.  That is the point.  Dismissing the interests of others is in keeping with a seeming condescension in tone.  Your use of "shrugs" is another example.  Put it all together: the insult, the indifference, and the lack of interest in other people's concerns, and the question comes up: why bother to respond to what you consider a rant about something that doesn't matter to you from people you don't care about?

The issues about KDE 4.xx are important to many other people.  Their lack of importance to you doesn't reduce that in any way.  And the fact that it is improving over time doesn't answer the problem of having been introduced too early and still not addressing core issues of importance.

---

### Post by ffi on 2008-09-10
I too was very disappointed by by 4.0.0-4.0.x because of the many missing features and many bugs but the kde devs said 4.1 would solve this, so I installed the beta and reported bugs/missing features...oh boy did I get flamed in the kde bugzilla for expressing my wont for some common desktop  features, how dare I ask... the devs had thought long and hard about making these decisions and I had to understand kde4 was very very different and I had to learn and read the manual....

But me as a user, having used computers for over 28 years, really don't want to learn. I have used many desktop enviroments and kde4 was the first one I just didn't get (well okay kde4 and windows3.11).

Really a shame because under the hood kde4 really is impressive and it runs faster even than xfce...I am still hoping the devs (mainly aseigo) will come to their senses and realise people just want their desktop back and that lack of configurability, hiding options and advanced functions don't make a program easier to use but harder...

btw I am writing this from kde4.1.1 on mandriva 2009.0 it looks nice and runs quite smooth even with nvidia and I am trying not to get to irritated when a feature is missing but I do miss many...

---

### Post by awakatanka on 2008-09-10
> **ffi said:**
> 
btw I am writing this from kde4.1.1 on mandriva 2009.0 it looks nice and runs quite smooth even with nvidia and I am trying not to get to irritated when a feature is missing but I do miss many...Name a few please, and what kind of configuration option they hide? Just wanna know so i can learn some new things i have not seen before and make my life also easier.

---

### Post by ffi on 2008-09-10
-where is the device tab in konqueror?
-I wat to get rid of the annoying twirl in the top right and in the panel, right clicking shows no option to do that
-I want to get rid of those annoying toolboxes around plasmoids, a simple right click will do
-desktop background does not support xml files (to play animation like kde3 and gnome in mdv, kde4 background is static)
-right click, drag, move drop for panel
-no thumbnail view in fileselector (how to find that one foto from 100's, do like you do in gnome, open konqueror-> right click to select.....)
-no kmilo, osd or hotkeys (you have to manually assign to kmix and that doesnt even work when you have multiple cards because it binds to one specific card, used to work in kde3)
-no files on the desktop (normally I keep 1 or 2 on the desktop I am working with but know I have folderview, which shows a container, text, a bar, and the annoying popup of tools instead of and on top of the 1 or 2 files)

and there are a couple more but these spring to mind just now....

---

### Post by awakatanka on 2008-09-10
> **ffi said:**
> 
-I wat to get rid of the annoying twirl in the top right and in the panel, right clicking shows no option to do that
-I want to get rid of those annoying toolboxes around plasmoids, a simple right click will do
-right click, drag, move drop for panel
-no thumbnail view in fileselector (how to find that one foto from 100's, do like you do in gnome, open konqueror-> right click to select.....)
-no files on the desktop (normally I keep 1 or 2 on the desktop I am working with but know I have folderview, which shows a container, text, a bar, and the annoying popup of tools instead of and on top of the 1 or 2 files)

and there are a couple more but these spring to mind just now....I answer some because the others i don't know
 The twirl will be gone if you lock widgets if you right click on desktop. The top right wil stay because it has also another function. But forgot what function but you can read it on one of the blogs of a kde dev.

Right click desktop lock widgets and the toolbox is gone. CTRL-L if you use keybord shortcuts.

Right click panel > panel settings, now you can do what you want with the panel like before only a little different then you did in kde 3

Thumbnail view is something they working on i read somewhere, alt-f11 works in svn to show thumbnail

The old "desktop" will be there also only a bit different it will be a full screen container if i read it right on aaron his blog. But dunno why you have problems with folderview plasmoid because it more powerfull then old desktop.

The rest i dunno because i never needed it but will try it on kde3.5 to get a impression what it do.

thxs for the info

---

### Post by ffi on 2008-09-10
> **jimbo99 said:**
> The trashcan applet constantly tells me I have 55 items and provides me with the option to empty the trash. The problem is that it never resolves itself to 0 items.

This could be a permissions problem, when you worked as root/sudo and then trashed some files, go to a console and do:

sudo rm -rf ~/.local/share/Trash/files/.*
sudo rm -rf ~/.local/share/Trash/info/.*

empty the trash again and it should hopefully be empty

---

### Post by ffi on 2008-09-10
> **awakatanka said:**
> Right click desktop lock widgets and the toolbox is gone. CTRL-L if you use keybord shortcuts.

But I don't want to lock them I want to move them around....

> But forgot what function but you can read it on one of the blogs of a kde dev.

So basicly it's useless, for me it's useless and I want it gone, it annoys me taking up the space...

> Right click panel > panel settings, now you can do what you want with the panel like before only a little different then you did in kde 3

I know, now because of those bugreports and the flames, it's just way more complicated that it needs to be and not intuitive at all.

>  But dunno why you have problems with folderview plasmoid because it more powerfull then old desktop.

It makes my desktop way more messier than it used to be. It's cool as an addition, it could be a really powerful and useful addition but it's not a replacement for files on the desktop, like the kde-devs want it to be.

---

### Post by awakatanka on 2008-09-10
> **ffi said:**
> But I don't want to lock them I want to move them around....



So basicly it's useless, for me it's useless and I want it gone, it annoys me taking up the space...



I know, now because of those bugreports and the flames, it's just way more complicated that it needs to be and not intuitive at all.



It makes my desktop way more messier than it used to be. It's cool as an addition, it could be a really powerful and useful addition but it's not a replacement for files on the desktop, like the kde-devs want it to be.and x numbers of users want something else then the other user. if you do not like the way it works then i pitty you, sticking to the old and do not dare to change anything because people may get confused.  Looks more you are not willing to learn something different and everything needs to be like you want, you probably also never change the look of your house because it may confuse you and you can't find things anymore.

---

### Post by ffi on 2008-09-10
The point is that in kde3 all this was configurable, the power to decide was mine, now the kde-devs took away that power and I have to live with their choices, like osx users, vista users and gnome users. Not a good thing....

---

### Post by awakatanka on 2008-09-10
> **ffi said:**
> The point is that in kde3 all this was configurable, the power to decide was mine, now the kde-devs took away that power and I have to live with their choices, like osx users, vista users and gnome users. Not a good thing....
kde3 didn't had plasmoid, and still it is configurable but not like you want it to be (like kde3). It even gives more option then kde3, so that is a non argument.

How would i see all maps of my usb hdd on my desktop in kde3? i needed to make shortcut of all those maps. How could i shrink and make widget bigger in kde3 ( and even rotate them). How could i make the kicker panel shrink and grow till a point i decided? realy there more option you had and not less.

---

### Post by HTML-insane on 2008-09-10
"Panel configuration is more complicated" is just rubbish. You've got all options presented to you and it's not difficult to find what you want, compared to KDE 3 where you had that annoying configuration window with different tabs. I would loose it somewhere in my sea of windows, I would spend ages looking for the thing I wanted to change, I couldn't see any of my other windows while I was doing it... for me, the new configuration tool was a life-saver.

I don't understand what's so complicated about it. Three buttons, paragraph-like alignment, arrows for max- and min-width, click-drag to change the size or position... come on, what's so complex about that?

If you don't like the borders of icons and prefer right-clicking, then no-one's stopping you from right-clicking. Right-click away! Borders don't stop you from right-clicking somehow, do they?

The toolbox in the top right takes up too much room. Right. If it was 600x800 pixels on its own, I might understand... but it's not. It's just a little, mostly transparent icon, no bigger then 15 square pixels. If it were like KDE 4.0, you had a hotspot in that corner and the menu wouldn't go away, then I would understand - but it isn't. It doesn't do anything unless you explicitly tell it to with a click.

Since I started using KDE 4.1, I've been much faster with my work. I can say that honestly. ¬_¬

---

### Post by randcoop on 2008-09-10
If the idea behind KDE 4 was to replace KDE 3 with a different way of doing things, and in the process to remove the user's control of his desktop, and to impose the will of developers on users, then it is indeed successful.

Why can't the naysayers understand that adding features while removing user control is a negative?  Why can't they understand that no one objects to new things, only to the new things not being subject to user control?

The icon for widgets in the upper right corner is not, in and of itself, a bad thing.  If you like it, keep it.  Use it.  Stare at it.  Whatever.  But why not try to understand that a well designed desktop would allow people who don't like it, don't want to use it, don't want to stare at it...it would allow those people to remove it.

KDE 4 has taken away choice.  The question is why?  And how can that be a good thing?  And why, just because you like something, do you want to stop me from not liking it?

It's like keyboard shortcuts.  Having them available hurts no one.  Why in the world would anyone object to me using keyboard shortcuts?  Why, just because you don't like keyboard shortcuts, would you want to stop me from using them?  

A great desktop will place user control as a high priority.  KDE 4.xx isn't that desktop.

---

### Post by ffi on 2008-09-10
> **randcoop said:**
> KDE 4 has taken away choice.  The question is why?  And how can that be a good thing?  And why, just because you like something, do you want to stop me from not liking it?

It's like keyboard shortcuts.  Having them available hurts no one.  Why in the world would anyone object to me using keyboard shortcuts?  Why, just because you don't like keyboard shortcuts, would you want to stop me from using them?  

The obvious answer would be: It makes the Creator(tm) mad and brings its wrath down upon us all, convert now or be doomed for all eternity!

---

### Post by awakatanka on 2008-09-10
> **randcoop said:**
> If the idea behind KDE 4 was to replace KDE 3 with a different way of doing things, and in the process to remove the user's control of his desktop, and to impose the will of developers on users, then it is indeed successful.

Why can't the naysayers understand that adding features while removing user control is a negative?  Why can't they understand that no one objects to new things, only to the new things not being subject to user control?

The icon for widgets in the upper right corner is not, in and of itself, a bad thing.  If you like it, keep it.  Use it.  Stare at it.  Whatever.  But why not try to understand that a well designed desktop would allow people who don't like it, don't want to use it, don't want to stare at it...it would allow those people to remove it.

KDE 4 has taken away choice.  The question is why?  And how can that be a good thing?  And why, just because you like something, do you want to stop me from not liking it?

It's like keyboard shortcuts.  Having them available hurts no one.  Why in the world would anyone object to me using keyboard shortcuts?  Why, just because you don't like keyboard shortcuts, would you want to stop me from using them?  

A great desktop will place user control as a high priority.  KDE 4.xx isn't that desktop.I can not see what chooses the have taken away, there a few still not there but from what i read it is coming. But for some like you not fast enough.  The most thing i read about complains are things that are coming our all ready done. And mostly it are the same negative people that cry the most about a little thing that is coming. People that have old habbits that and don't want to change our learn something in anotherway. You are having more control over your desktop then ever but your not willing to learn something different then your old habbit. Your turning it around its not kde4 that haves a problem its you who doesn't want to see it gives you more control. On kubuntu forum there is a link from the switch from kde2 to kde3, maybe you understand that its going faster then ever the changes and updates.

---

### Post by ffi on 2008-09-10
I have used a lot of desktops: Amiga1.3 and 3.9; Irix; OsX; GNOME2; WIndows 3.11,95,98,ME,XP and Vista; KDE3; XFCE4.4 and 4.2; E16&17; ICEWM and maybe a few others but KDE4 and windows3.11 were the only ones I ever needed a manual for to get...

---

### Post by awakatanka on 2008-09-11
> **ffi said:**
> I have used a lot of desktops: Amiga1.3 and 3.9; Irix; OsX; GNOME2; WIndows 3.11,95,98,ME,XP and Vista; KDE3; XFCE4.4 and 4.2; E16&17; ICEWM and maybe a few others but KDE4 and windows3.11 were the only ones I ever needed a manual for to get...

Funny you din't have any problems with switching from 3.11 to 95 and to xp. All microsoft pruduct but totaly different then the version before. Where all config option are on a different place then before. And you complain about a little difference in kde4 where it is almost the same as before but you have to do it a bit different. And ofcource what you all have used have on the same place the config options. And you complain about little differences

---

### Post by randcoop on 2008-09-13
It's clear to me that awakatanka will never understand what those of us who are criticizing KDE 4 are saying. To some extent, there may be a language problem (I think English is not his or her native tongue).

It's more likely, though, that he or she doesn't want to understand.  While those of us unhappy with KDE 4.x offer specific criticisms, he or she responds with either insults or with comments that suggest that if we don't like it, then there's something wrong with us.  It's a classic rhetorical tactic, this avoidance of the actual points being made, but it doesn't make for much of an intelligent discussion.

I will therefore leave this as my last post.  There's no point in having a discussion with someone who doesn't want to have one.

KDE 4.xx is a major disappointment.  I hope that the KDE developers will try to open their minds and listen to the many many criticisms that have been made in many forums on the internet.  If they do, I'm confident that these people can ultimately produce a very satisfying and productive work environment for the end users.

---

### Post by ffi on 2008-09-13
> **awakatanka said:**
> And ofcource what you all have used have on the same place the config options. And you complain about little differences

I am not complaining about the differences I am complaining about the lack of features and configurability present in kde3 but not kde4.

(I have found another major irritating lack of feature present is desktops since god knows when but not kde4.1.1, right click desktop->new (doc, text, etc))

---

