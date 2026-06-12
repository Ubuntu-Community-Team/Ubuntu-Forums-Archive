---
title: "whats up with 5.04?"
date: 2005-04-18
forum: Desktop Environments
---

### Post by nonrefundablelifetime on 2005-04-18
Great! The previous distro worked fine, now I can't install anything. What happened to the "install" feature? I've just wasted a day trying to install Real Player..for God's sake if at ain't broke don't fix it.

---

### Post by bored2k on 2005-04-18
[QUOTE=nonrefundablelifetime]Great! The previous distro worked fine, now I can't install anything. What happened to the "install" feature? I've just wasted a day trying to install Real Player..for God's sake if at ain't broke don't fix it.[/QUOTE]
 Can you be more explicit ? A day installing realplayer? what is up with downloading the .bin and running [sh filename.bin] it as root ?

What's wrong with Synaptic Package Manager ? What are you doing to install software? What extensions are you trying to install with? What previous distro?

---

### Post by nonrefundablelifetime on 2005-04-19
Ok 
I don't know how to use synaptic manager (i've tried and tried)
the previous version I installed "warty warthog" had a function whereby
you could scroll down a box and click "install" when selecting an app to install..
this worked perfectly
in this new release. this option doesn't seem to be available.
i have no idea how to do what i want to do..it ain't intuitive like the old vers.
i don't think i'm mentally challenged at all, it appears that the installation process has been obfuscated in a way that i don't understand anymore
if you can explain it to me i would appreciate it.

---

### Post by shakin on 2005-04-19
There is an add/remove programs dialog if you run System Tools -- Add/Remove Programs.

Is that what you're looking for?

---

### Post by yanik on 2005-04-19
nonrefundablelifetime

The add/remove thing is just for the provided apps.  You should use synaptic for installing software, but some people find plain apt-get just easier.  Are you familiar with apt-get?

In a terminal window, 

sudo apt-get update  # is to update the package database
sudo apt-cache search somepackage # to search, of course
sudo apt-cache show somepackage # to see info on a package
sudo apt-get install somepackage # to install a package
sudo apt-get remove somepackage # to remove a package
sudo apt-get dist-upgrade # to upgrade the entire distro to the latest available.

As a former debian user, synaptic seems more confusing than helpfull, I prefer apt-get

---

### Post by nonrefundablelifetime on 2005-04-19
Simply stated, I would like to be able to "install" like i could do before in warthog...
i don't seem to be able to do that anymore
correct me if i'm wrong but wasn't that an option with that package?
i am not a linux user, BUT i tried the warthog distro and for the first time i found a linux package that made sense. 
it was very easy to install stuff because there was an "install" option in the package
it actually said "install" as an option in a window.... maybe this new version is better, but as far as i'm concerned it's a step backwards because i can't use it anymore..i don't have the time to figure out how to install programs like real player which should be a part of firefox or something like it anyway (but that's another issue), that will actually play these files...
if you want to convert people to linux, it needs to be more user friendly 
as i said warthog worked fine for me, but this new one doesn't make sense.. apt get synaptic manager or whatever..what happened to INSTALL?

---

### Post by ttp on 2005-04-19
Are you saying that you can't find "Synaptic Package Manager"?

System -> Administration -> Synaptic Package Manager

[http://ubuntuguide.org/#synaptic](http://ubuntuguide.org/#synaptic)

---

### Post by nonrefundablelifetime on 2005-04-20
jesus...

---

### Post by mike998 on 2005-04-20
[QUOTE=nonrefundablelifetime]jesus...[/QUOTE]

Have you TRIED Synaptic?
Try checking out the bottom left of Synaptic, there are four buttons, and perhaps they will give you the view you want to see.
To get an option to "Install" a package, right click on it, and select "Install".

We understand your frustration, but perhaps you could post a few screencaps if you feel you are having difficulty getting your point across?

---

### Post by dermotti on 2005-04-20
Serious dude, open synaptic, find the program you want to install, click the little box next to the app, and hit install. 

I undersand yer a newb, but this is beyond simple!

---

### Post by nonrefundablelifetime on 2005-04-20
SYNAPTIC MANAGER

ok i have my app sitting in the left column of SM. how to i get it to install?
ie, how do i get it into a place where it will install?
there appears to be no way to obtain a tree view of where anything is stored in any of these directories
there are plenty of packages for me to install, but i can't get the one i downloaded from real.com into any directory that the other stuff is in. i don't even know where any of it lives.
there doesn't seem to be any option for me to install this file RealPlayer10Gold.bin from where it is in the place that it's now sitting which is the left hand column of SM
what am i doing incorrectly? does this file need to be made executable and if so, how?
thanks.

---

### Post by QCompson on 2005-04-20
From the realplayer website:

Installation Instructions

- Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window.

- Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.

- When you launch the player for the first time, a set-up assistant will take you through configuring your player.

- Enjoy your RealPlayer10 for Linux!

---

### Post by nonrefundablelifetime on 2005-04-20
gee thanks for that . how did you figure out that i was incapable of reading and understanding english?

---

### Post by QCompson on 2005-04-20
just a guess...

---

### Post by Gary Powers on 2005-04-20
I fear this ole' boy is just beyond help!  He doesn't seem to want to hear anything that you guys are saying.

It sounds like he may have found a tarball with an installation package in it and successfully installed like that.  I seem to recall having used something like that.

Gary

---

### Post by nonrefundablelifetime on 2005-04-20
pardon me i was wrong, apparently apart from me, there seems to be nobody else out there who can read or understand english..

it is entertaining though...

---

### Post by deadlands on 2005-04-20
[QUOTE=nonrefundablelifetime]pardon me[COLOR=Red],[/COLOR] I was wrong[COLOR=DarkRed].[/COLOR] Apparently[COLOR=DarkRed],[/COLOR] there seems to be no [COLOR=DarkRed]one[/COLOR] else out there who can read or understand English, apart from me.
[/QUOTE]

Sorry, had to correct your English. You'll notice the correct placement of punctuation and grammatical corrections.

</grammar police>

I think the problem here is that you didn't really explain exactly what the problem is, so people will have to make some assumptions in order to help you. What exactly do you mean in this statement:
> the previous version I installed "warty warthog" had a function whereby
you could scroll down a box and click "install" when selecting an app to install.

Are you talking an "install" selection if you right-click on a Deb package? See, this is very vague and really doesn't help us understand where the issue is. 

Anyway, there is no one way to install software in linux, it all depends on how the software is packaged. Sometimes you get a Deb package, which you can just use dpkg, sometimes there's install scripts that you have to run in a shell, sometimes you get installers, and sometimes you have to compile from source. I agree that's not intuative if you come from Windows or Mac, but it's not very hard to get the hang of.

---

### Post by nonrefundablelifetime on 2005-04-20
"Anyway, there is no one way to install software in linux"

and therein lies the problem.


but I think i explained myself very comprehensively a couple of posts ago, which no one has responded to yet.

---

### Post by deadlands on 2005-04-20
[QUOTE=nonrefundablelifetime]"Anyway, there is no one way to install software in linux"

and therein lies the problem.[/quote]

That's not a problem with Ubuntu or Linux. In fact, I don't think it's a problem, it's a choice. I prefer Debian packaging over RPM, I'm glad I get that choice. To me, having more than one to do something is part of the beauty of open-source.


> but I think i explained myself very comprehensively a couple of posts ago, which no one has responded to yet.

Which post? "a couple of posts ago" is a little vague. But from what I read every one of your posts have been responded to.

---

### Post by Boomgawd on 2005-04-20
Hey nonrefundablelifetime, 

sounds to me like you should install windows.

Boom

---

### Post by crane on 2005-04-20
[QUOTE=nonrefundablelifetime]"Anyway, there is no one way to install software in linux"

and therein lies the problem.


but I think i explained myself very comprehensively a couple of posts ago, which no one has responded to yet.[/QUOTE]


I have read this thread and I am now confused!! ](*,) 

Installing software in linux in easy, granted it is a little more diificult that windows but thats because everyone is an admin in windows. LOL

If your having problems installing a program just be more specific about the problem, the type of file (sh, bin, deb), and the error your getting if any, This really seems to be turning into your own lnux bashing thread. In which case you will run off any one capable of helping you.

Just my 2 cents.

 Also, I'm not real familiar with sYnaptic because I just use apt! But will be glad to help if I can figure out the question.

---

### Post by dewey on 2005-04-21
$sudo apt-get install PACKAGENAMEHERE

Sure is difficult.  You're not listening to what people are telling you, there are step-by-step instructions for installing common things at [www.ubuntuguide.org](www.ubuntuguide.org)

Linux has become very user friendly in the past few years, you just have to you know, do something.

---

### Post by nonrefundablelifetime on 2005-04-21
that's gonna get a lot of converts. (the windows crack) although installing windows apps is a breeze compared to this mess i have to say

as to my post, it's the one regarding Synaptic Manager, which nobody has yet addressed, i live in hope that somebody will respond to it...foolish though that hope may be, although maybe they have by now..it's getting a bit busy down here maureen..

anyway let this not be a flame session. i actually like Ubuntu a lot and want to get it to work...i'll try some of these ideas put forth here and see what happens.

---

### Post by codejunkie on 2005-04-21
open up Synaptic Manager click the search button type realplayer rightclick on it and choose Mark for installation then click Apply. realplayer is now installed if you don't have the Synaptic Manager listed in the menu press alt+F2 and type gksudo synaptic
that should work unless your using kde as your desktop then type kdesu kynaptic that should do it.

---

### Post by sijp on 2005-04-21
perhaps the problem is that it is too easy, no one can explain it :) .

here is a small demonstration:

[[IMG]http://img260.echo.cx/img260/4318/step16dp.th.jpg[/IMG]](http://img260.echo.cx/my.php?image=step16dp.jpg)
I chose something I want to install.
[[IMG]http://img260.echo.cx/img260/2638/step25kn.th.jpg[/IMG]](http://img260.echo.cx/my.php?image=step25kn.jpg)
I right click it and then choose install
then I hit the Apply button on the toolbar.
this dialog will apear;
[[IMG]http://img260.echo.cx/img260/9260/step32qj.th.jpg[/IMG]](http://img260.echo.cx/my.php?image=step32qj.jpg)
clicking Apply will start the download and the installation right afterwards (all automatically)
[[IMG]http://img260.echo.cx/img260/7581/step47tm.th.jpg[/IMG]](http://img260.echo.cx/my.php?image=step47tm.jpg)
and voila;

because you have not yet installed stuff the right way you still cannot compare between the two native methods.

---

### Post by codejunkie on 2005-04-21
hey **sijp** i know this is off the subject but what theme are you using i really like that window border..?

---

### Post by sijp on 2005-04-21
[QUOTE=codejunkie]hey **sijp** i know this is off the subject but what theme are you using i really like that window border..?[/QUOTE]
 hey, thanks :)

its from gnome-look, it is called fly. it comes with a GTK theme but I didn't like the way my panels looked with it.
[here is a link](http://www.gnome-look.org/content/show.php?content=23191)

---

### Post by codejunkie on 2005-04-21
cool thanks **sijp** im gonna check it out right now, oh yea thanks again.

---

### Post by nonrefundablelifetime on 2005-04-21
thanks everyone for your input

i still haven't got this installed...btw i got it done first time with the previous distro"warthog"
if these forums are to improve the product then consider that 5.04 is harder to use (for me anyway) than the "warthog" model

the guy with the link to ubuntuguide.org had the best solution , it's all up there
i'm getting closer actually installing real player though i can install real alternative with about 3 clicks in windows, so go figure.
this thing is way too time consuming and esoteric at the moment. that's the reason windows is so popular. you shouldn't have to go through this rigmarole to install a simple app

more work needs to be done to make this acceptable to the masses, but maybe that's not what some people want to happen. i would be glad to stop using windows, it's unpleasant in a lot of ways, but i don't have the time to do things that require this amount of admin to do simple tasks.

i might add that if you look though all these posts, you'll get a plethora of solutiuons to this simple problem. i don't wanna type anything. all i want to do is click on something and have it install. petulant i know but i would like to save time.

also i'd LOVE to know where everything lives in this system, then i might be able to find things, relocate them etc..that's a big problem which needs to be addressed.

---

### Post by NaplesBill on 2005-04-21
[QUOTE=nonrefundablelifetime]thanks everyone for your input

i still haven't got this installed...btw i got it done first time with the previous distro"warthog"
if these forums are to improve the product then consider that 5.04 is harder to use (for me anyway) than the "warthog" model

the guy with the link to ubuntuguide.org had the best solution , it's all up there
i'm getting closer actually installing real player though i can install real alternative with about 3 clicks in windows, so go figure.
this thing is way too time consuming and esoteric at the moment. that's the reason windows is so popular. you shouldn't have to go through this rigmarole to install a simple app

more work needs to be done to make this acceptable to the masses, but maybe that's not what some people want to happen. i would be glad to stop using windows, it's unpleasant in a lot of ways, but i don't have the time to do things that require this amount of admin to do simple tasks.[/QUOTE]

I can see where you're coming from.  I was able to install realplayer10 just by following the real website instructions.  I should tell you that I changed to the root password with the user manager and ran all the commands using the "root terminal" under applications.  I also changed the install directory to /etc/RealPlayer(or whatever it suggested for its program folder name).

---

### Post by compmodder26 on 2005-04-21
I am a complete linux noob, but I was able to get realplayer installed on the first try with hoary.  Synaptic is the easiest tool to use IMHO.  I think it's far easier than using any windows installer.

---

### Post by nonrefundablelifetime on 2005-04-21
well it doesn't work for me

---

### Post by QCompson on 2005-04-21
I smell a troll.

---

### Post by nonrefundablelifetime on 2005-04-21
for god's sake grow up

---

### Post by compmodder26 on 2005-04-21
You're bringing it on yourself.  I've spent the past two weeks exploring these forums and I have only noticed nice and helpful individuals.  That was until this thread.  But what I believe caused them to turn on you is the fact that you didn't listen to their advice.  They've been giving you the answers but yet you still say they haven't answered your question.  As far as I can see, you question has been answered.

Now you are bashing linux simply because the "Install" button is missing from Synaptic.  Now I've never used "Warty" before so I don't know how synaptic was laid out.  But I'm sure the developers changed it for a good reason.  I'm sure when Microsoft releases Longhorn, it will have changes to some of it's programs as well.  That's just the nature of upgrades.  As far as I'm concerned, the changes that they did make to synaptic are great.

---

### Post by nonrefundablelifetime on 2005-04-21
i fail to see how personal insults can be helpful

i'm trying to explain that there might be some issues with this thing
(unless you believe it's totally perfect)

if it degenerates into infantile name calling there's nowhere to go i'm afraid

---

### Post by Leif on 2005-04-21
The reason realplayer cannot be installed via the extremely easy to use apt-get method is that they do not allow redistribution of their software. This is the reason why you cannot just click and install it. If you are upset by this, please contact realnetworks and express your feelings. Given that they refuse to have their software handled natively by debian-based distros, the instructions you were given are as easy as things are going to get.

---

### Post by nonrefundablelifetime on 2005-04-21
well if the people who put this o/s together considered the fact that a large percentage of streaming media uses the real or windows format  and considered including something that would play it without the need to download this horrible program this problem wouldn't exist. 

if somebody can come up with the freeware app "real alternative" for windows which plays real and windows media and isn't a product of real networks or microsoft  (which i don't like either btw)
surely a linux genius can make something similar and/or have it included with an o/s that they expect people to use in a realistic manner.. (no pun intended)


before you jump on your high horse read and understand the thread here which is titled "what's up with 5.04?" from the beginning. real player installed perfectly as described by all the helpful people here with the PREVIOUS DISTRO... i had a problem with the LATEST ONE 5.04.  sorry, that's the problem i had, and i still have it.

if the purpose of this forum is to attack people because you think they're too dumb to figure out something you understand perfectly, there's not much hope for this  tribe.

is this not a forum to improve linux? if it's so great and perfect, why even have a forum in the first place?

---

### Post by codejunkie on 2005-04-21
well post some screen shots and error reports of your problems and we will help you we can't see your computer so we don't know what is wrong if you could do this it would be possible to fix this issue.

as for your view on windows yes windows has great way of installing software a couple of clicks and your on your way, but the problem is it only take one click to kill windows  no matter how easy the software install is if the os behind it sucks the apps suck.
that being said it isn't hard to install software in linux its just different you have 
have a choice. and you only have one choice in windows, and the problem with that is no control. stuff is installed in so many locations you could never completely remove it. but thats just my view on windows.

---

### Post by Gary Powers on 2005-04-21
[QUOTE=nonrefundablelifetime]Great! The previous distro worked fine, now I can't install anything. What happened to the "install" feature? I've just wasted a day trying to install Real Player..for God's sake if at ain't broke don't fix it.[/QUOTE]

Going back to his initial premise ... that with the transition from Warty to Hoary, something has changed with regard to program installations ... I am not aware of any changes at all.  Anyone else?

Gary

---

### Post by Mike Douglas on 2005-04-22
wow, STFU nonrefundablelifetime. Seriously, there are people trying to help you but you provide no information are just act like an ass. There was never anyway for Synaptic to "install" from RPM in Warty, so either this guy has no idea what he is talking about, or is trolling. I seem to think a little of both.

---

### Post by sanjeevdas on 2005-04-22
Why don't you post some screenshots of what you are trying to do? You do know how to take a screenshot, right?

---

### Post by nautilus on 2005-04-22
who cares...

since when was the mission to get guys like this using ubuntu, and wasting our time responding to his banter on the forums about how to install a driver for his new monitor in Ubuntu Redhat 9.0?

i, personally, wish this sort of person would stay with their familiar platform.  i'll stay with mine.  i don't care what you use, i don't want people using linux, or 'converting', or 'porting', or comparing, or making equivalents, i just want to lend a hand, get my work done, play some games, and surf some porn.

...what was my point...

i dunno, but yeah, if you aren't a troll, you either have to start paying us to deal with you, or actually start embracing the support (and showing a sliver of appreciation), because otherwise you just look stupid and/or like a jerk.

i know this from first-hand experience, too...

---

### Post by mike998 on 2005-04-22
[QUOTE=nautilus]who cares...

since when was the mission to get guys like this using ubuntu, and wasting our time responding to his banter on the forums about how to install a driver for his new monitor in Ubuntu Redhat 9.0?

i, personally, wish this sort of person would stay with their familiar platform.  i'll stay with mine.  i don't care what you use, i don't want people using linux, or 'converting', or 'porting', or comparing, or making equivalents, i just want to lend a hand, get my work done, play some games, and surf some porn.

...what was my point...

i dunno, but yeah, if you aren't a troll, you either have to start paying us to deal with you, or actually start embracing the support (and showing a sliver of appreciation), because otherwise you just look stupid and/or like a jerk.

i know this from first-hand experience, too...[/QUOTE]


There's a couple of posts stating that this guy should go back to windows.  My opinion is that Linux is for some people, and not for others.  Linux being what it is, it's an operating system in a state of constant flux.  If you aren't happy with change, then go to another operating system.

Every attempt in this thread to help this guy has been rebutted.  There has even been a post with PICTURES as a step by step guide to what we *think* is this guy's problem.

I think what we have here, is a troll.  Plain and simple.

---

### Post by pelago on 2005-04-22
I'm just intrigued by what he might have been doing in Warty Warthog that was so different to what he's trying now?

By the way, the Windows apps Real Alternative (and it's companion, QuickTime Alternative) are just repackages of the DLLs from those two packages, installed in such a way that Windows can play back media in those formats without needing the large proprietary apps installed. So they aren't really a third-party reimplementation of the formats, which is what the original poster seems to think.

---

### Post by nautilus on 2005-04-22
right.. or he's an idiot.

---

### Post by nonrefundablelifetime on 2005-04-22
There you go with the name calling.

Nice people indeed! Look I don't care anymore.

I appreciate everyone's help. I don't appreciate being called a troll. I think it's disgusting behavior from a forum based on a system the philosphy of which goes out of it's way to appear is so caring and sharing. 
That being said, I will still use Ubuntu, but I'll figure it out myself. I'll leave the real trolls in this forum to be nasty to each other. I don't need it thanks.

BTW nautilus, I know you'd really like to look like that, but you're way too mean. 

"personally, wish this sort of person would stay with their familiar platform".

Do you now?  That's progressive thought.

---

### Post by dataw0lf on 2005-04-22
Apparently you all want to act like children.  Thus, like children you shall be treated.  This thread is now officially closed, until I can speak with my fellow moderators and determine exactly what the hell the problem is here.

---

