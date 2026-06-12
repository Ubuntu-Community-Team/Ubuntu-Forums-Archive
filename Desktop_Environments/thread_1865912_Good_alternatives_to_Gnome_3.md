---
title: "Good alternatives to Gnome 3?"
date: 2011-10-20
forum: Desktop Environments
---

### Post by super_nerd on 2011-10-20
Hello,

    Today I upgraded my computer to 11.10. Unfortunately, the UI was switched over to damned UNITY(Useless Nuts Interface Terribly Yuck! :mad: :evil: ](*,) ). You may be able to tell by now I don't care for unity! :D

    Anyway, I promptly installed GNOME which is better but I have been using GNOME 2 until today. Unfortunately GNOME 3 lacks the control and ease of customization I loved about GNOME 2 and I am just not as happy with it. :(

    I have tried GNOME shell, and KDE but do not care for either. KDE is very customizable :) but for me it was buggy, messy, bloated, and overwhelming. :(

    Could other UI's be recommended that have the clean, simple feel of gnome and are more customizable like gnome 2? Should I just switch back to gnome 2?

-Thanks

---

### Post by Smilax on 2011-10-20
XFCE rocks

and now nealy every other one has been iphoned it's looking really great.

i feel the same as you  about gnome 3 and unity,

i tried KDE a few years ago and my reaction wasn't good, to say the least.

---

### Post by super_nerd on 2011-10-20
Thanks! I will check it out!

"Iphoned"; that's a good word for it! I wonder why the hell the developers think that Linux users want to downgrade their Desktop interface to be like a smartphone! Makes no sense to me.

---

### Post by Copper Bezel on 2011-10-20
XFCE is a very popular desktop right now, and it's been improved quite a bit in the last year or so. This question is coming up quite a bit as you can imagine, and I tend to suggest KDE first, simply because XFCE is still a relatively lightweight (read: limited) desktop and smaller project in terms of developers, but if KDE isn't your flavor, XFCE might fit the bill, and it is at least going to be more friendly with your familiar GTK-based Gnome apps.

---

### Post by bob-linux-user on 2011-10-20
The Gnome that is available on Ubuntu 11.10 is I find a good alternative to Unity and as far as I can see it looks and feels like classic gnome. The instructions below let you use a panel, get rid of the diabolical overlay scrollbars and put the window controls back at top right.This is what I did:

[SIZE="2"]Install ubuntu 11.10 in normal way
In a terminal type
 sudo apt-get install synaptic
 sudo apt-get remove overlay-scrollbar liboverlay-scrollbar-0.2-0
 sudo apt-get remove overlay-scrollbar liboverlay-scrollbar3-0.2-0
 sudo apt-get install gnome-session-fallback
 sudo apt-get install gconf-editor
 sudo apt-get install gnome-tweak-tool
log out and log back in gnome classic
In a terminal type 
 gksudo gconf-editor
Browse to apps/metacity/general. Double click on button_layout and gconf-editor and set value to  
:minimize,maximize,close
Alt right click on panel at top.
-Set orientation to bottom and size to 36
Alt right click on time and move to extreme right
Alt right click on panel and add
-Main Menu
-Window List
Alt right click on "Applications Places" menu and remove
Alt right click on the "speech bubble" at bottom right and remove
Remove the slim top panel by alt right clicking and deleting
Alt right click on panel and add
-Show desktop icon
On a general area of desktop right click and change the background to what you want ( I chose Jardin Polar)
in a terminal type
 sudo apt-get install ubuntustudio-theme
 sudo apt-get install ubuntustudio-icon-theme
 sudo apt-get install human-theme
 sudo gnome-tweak-tool
 Set Theme:Icon theme to Ubuntu Studio
 Set GTK+ theme to Raleigh
 Set window theme to human[/SIZE]

Does anyone know how I can install and preview themes as was done on 11.04?

---

### Post by ajgreeny on 2011-10-20
> **Copper Bezel said:**
> XFCE is a very popular desktop right now, and it's been improved quite a bit in the last year or so. This question is coming up quite a bit as you can imagine, and I tend to suggest KDE first, simply because XFCE is still a relatively lightweight (read: limited) desktop and smaller project in terms of developers, but if KDE isn't your flavor, XFCE might fit the bill, and it is at least going to be more friendly with your familiar GTK-based Gnome apps.
I would have to say that any of the ubuntu family of desktops environments, other than unity and gnome3 which I just can not get on with at the moment, are great.

My preference is probably XFCE, though LXDE in the form of lubuntu, is now increasing in appeal very strongly.  As long as I can do what I want in configuration and finding applications, I don't care too much about the DE, as all the applications are available from the repos for any and all the DEs.

That, I am afraid, is where unity etc. let me down; I just can't find things quickly enough, nor work out where things are any more, and even when I do find how to do certain things, it takes me longer to get to them or start them.  Horrible!

Have a good long look at both xubuntu and lubuntu and see what takes your fancy.  Both desktops have moved on a fair bit over the last couple of years and are becoming well appointed DEs, in my opinion.

---

### Post by super_nerd on 2011-10-20
> 
The Gnome that is available on Ubuntu 11.10 is I find a good alternative to Unity and as far as I can see it looks and feels like classic gnome. The instructions below let you use a panel, get rid of the diabolical overlay scrollbars and put the window controls back at top right.This is what I did:


Thank you, bob-linux-user! Now that I know how to add stuff to the panels gnome 3 is working somewhat better for me. :) Though I still will try XFCE out of curiousity.

> 
As long as I can do what I want in configuration and finding applications, I don't care too much about the DE, as all the applications are available from the repos for any and all the DEs.


This is exactly how I feel. Nicely put ajgreeny.

I just enjoyed the functionality of gnome 2. Shiny is nice but functionality is necessary. I'll update after I play around with XFCE enough to form an opinion.

Thanks everyone :)

---

### Post by super_nerd on 2011-10-20
I am really liking XFCE so far! So I am going to mark this thread as solved.

Within 5 minutes of using xubuntu I had my DE set up nearly ideally for me, and my workflow feels uninhibited once again!

I recommend anyone having the same problem as myself who might happen to read this to try out xcfe.

Thanks again to everyone who helped with their suggestions!

:)

Hopefully the unity people wil get their heads screwed on straight sometime! I guess some people like it though.

Cheers!

---

### Post by merlinus on 2011-10-20
Does installing xfce (as opposed to xubuntu-desktop) bring in all sorts of applications such as abiword, or just the desktop, menus, etc.?

---

### Post by super_nerd on 2011-10-20
> **merlinus said:**
> Does installing xfce (as opposed to xubuntu-desktop) bring in all sorts of applications such as abiword, or just the desktop, menus, etc.?

I don't know. I just used the xubuntu-desktop package but it did install a few applications including abi-word. For me it wasn't that bad though; I didn't get nearly as much extra junk as when I tried Kubuntu.

---

### Post by Smilax on 2011-10-20
> **super_nerd said:**
> 
Within 5 minutes of using xubuntu I had my DE set up nearly ideally for me, and my workflow feels uninhibited once again!


yip, that's pretty much how things went for me to

---

### Post by djahma on 2011-10-21
I totally agree with how this thread is going!
Was on gnome2.x for 2 years in row and with the new ubuntu 11.10 had to try different DEs. 
Unity mindset is aimed at stupid people...tried gnome3 and felt so disappointed it was built in the same spirit. Didn't try KDE because of words of bugs, so had a go at Lubuntu. That was nice but I felt too limited, LXDE is really lightweight. Eventually tried XFCE and man,
Xfce is wicked!
Xubuntu will install a limited amount of its own software. After that you take possession of a sharp, responsive environment, that hasn't failed on me once since I made the move 3 days ago. It's also greatly customizable out of the box: _you can create your own panels exactly the way you want them _XFCE themes are great looking _you can tailor to your desires the navigation and flow in your desktop.
XFCE is also fairly lightweight so you can easily add compiz without noticing the hit, on most modern machines at least.
So yeah, I'm a happy new Xfce convert\\:D/

---

### Post by LewisTM on 2011-10-21
I agree that XFCE is the way to go.

It might be a bit more plain and limited but then simply throw in cairo-dock. It is infinitely customizable and powerful but still manages to get out of the way when you just want to work.

And it plays nice with XFCE. I replaced the static bottom Xubuntu dock with it and it rocks!

Cheers!

---

### Post by nethero on 2011-10-21
IMO the best alternative to Gnome 3 is Gnome 2.  It was awesome!  It's what made me want to use Ubuntu in the first place.  I tried other distros that used KDE and XFCE but I never liked them.  The moment I installed Hardy Heron I was hooked on Gnome.

I updated to 11.10 not realizing that Gnome 3.2 would be so bad.  I tried and I tried for the last few days to tweak it to my liking but all the usual features available in Gnome 2 that allowed me to customize my desktop were either broken or missing in Gnome 3.  I think Gnome 3 is too much into its infancy as a Desktop environment to be usable right now.

I tried using XFCE and LXDE for a while but I found myself missing Gnome 2.  I'm not sure where to go from here.  I don't want to leave Ubuntu so I've been thinking I may just use Lucid Lynx which (hopefully) still uses Gnome 2 and hope that by the time Canonical no longer supports it that Gnome 3 will have matured to the point it is usable.  I guess I could also use Debian which still uses Gnome 2, but how much longer will Gnome 2 be around?  I keep hoping Gnome 2 will continue to be supported, it was a great desktop environment and I will use it for as long as I can.

---

### Post by Smilax on 2011-10-21
looks like XFCE could be the winner in this gnome3/unity super brawl

---

### Post by merlinus on 2011-10-21
LinuxMint will be supporting both gnome 2 and 3 in their distributions, including the upcoming version 12.  It is based on ubuntu, so the differences are slight.

Have a look at their website -- linuxmint.com

You can also download a live cd.

---

### Post by lethalfang on 2011-10-21
I have officially given up on Gnome. Buh'bye. 
I'm using Xubuntu now. I like the Xfce desktop much better. I really wanted that multiple workspace thingie that I couldn't find in Unity. I want my Application Menu visible and easily accessible at all times. 
The Xfce experience very much duplicates Gnome2.

---

### Post by Sonador on 2011-10-21
XFCE indeed, those days is xfce 4.8 really mature desktop environment (except menu editing). And if you are feeling sad giving gnome bye bye, you can keep nautilus as file and desktop(file/background) manager. It works fine for me and it gives an impression of the favourite gnome2.

I'm happy that many users run away from gnome3 and choose xfce, it might be a good guarantee for further development.

---

### Post by lethalfang on 2011-10-22
Only question I have so far is that I still haven't figured out the equivalent of the "gnome-open" command in Xfce.

---

### Post by JacobVengeance on 2011-10-22
I have only used xfce on an old inspiron 8000, I didn't like it at the time. I might check it out eventually. Whats your opinion on things like E17?

---

### Post by Flotter on 2011-10-22
Anybody using AfterStep?  I installed it the usual way - apt-get install afterstep gut I don't get the option to log into it from the session manager (gdm, I think, though I *DID* install kubuntu-desktop as well)  I've been using Fluxbox for years, but I have a few problems with it lately in the newest version. I've used AfterStep before and kinda liked it...

---

### Post by jdorenbush on 2011-10-22
I've been using Ubuntu since 8.04 "Hardy Heron" and 11.10 is the first Ubuntu release that I'm displeased with, so much so that I downgraded back to 11.04. The previous Ubuntu desktop environment worked perfectly and users were comfortable with how it functioned, but the release of 11.10 forced users to change how they interact with their desktop environment.

Based on what people are saying in this thread, I guess I should be checking out XFCE.

---

### Post by plasmafusion on 2011-10-22
i'd go for lxde. tried them all...even icewm and enlightenment...and i find it gives the best balance of performance and looks.

---

### Post by vinayg18 on 2011-10-23
Going by the comments here, I've decided to install xubuntu-desktop and give XFCE a shot. I think I've been spoilt by the omniscient search (Search for a song, hit enter and have Banshee play it etc) provided by GNOME 3 and Unity, though.

ETA: It's up and running. So far, so good. I set up Synapse to quick-launch apps/files. XFCE seems a lot like GNOME 2.

---

### Post by Copper Bezel on 2011-10-23
Synapse and Zeitgeist are bloody amazing. Unity's implementation comes close, but I like Synapse's more efficient keyboard navigation.

> **lethalfang said:**
> Only question I have so far is that I still haven't figured out the equivalent of the "gnome-open" command in Xfce.

You actually want to use xdg-open, which will pass off to the appropriate service, including gnome-open under Gnome and exo-open in XFCE.

---

### Post by Nevyn on 2011-10-23
Read the thread and decided to try xfce. Installed the xfce-desktop (and all dependencies) without problems. But when I try and choose 'Xfce' or 'xubuntu-desktop' during login, I still reach the Unity desktop. Feels related to the thread even though it's solved, but how do you go about to actually use the desktop environment?

---

### Post by TitanKing on 2011-10-24
I am an old Linux user, I mean almost a decade of Linux under my belt. Red Hat was my first, then Mandrake and then I started using Ubuntu from one of the very first releases. I really think it was good up and until Unity. Being an open source developer myself I realise that sometimes you have to shed out some baggage for something new. But when you realise the damage being done is too big you have to revert and just focus on what's important. In fact, I had to realize this disillusion recently.

Unity is not easier, in fact, old people find it harder to use if not impossible. My father is using Ubuntu (the one for human beings) and he loves it, there will be no way in hell he will ever be able to use Unity it seems. So I guess, for me it is backing down to Xfce, a Desktop for Human Beings, simplicity and without interfering, some people actually need to get work done and does not play music or browse Face Book all day.

I am really sad about Ubuntu Unity and Gnome 3, I respect what they are trying to do, but I think they are failing in the execution. It feels like Ubuntu has shown me the door and invited yappie users from a new neighbourhood. Ubuntu does not want to be my friend anymore, at least his wife is happy to be my friend, come here Xubuntu while your husband is too busy entertaining his new friends, lets get down to business ;)

---

### Post by lethalfang on 2011-10-24
> **Copper Bezel said:**
> Synapse and Zeitgeist are bloody amazing. Unity's implementation comes close, but I like Synapse's more efficient keyboard navigation.



You actually want to use xdg-open, which will pass off to the appropriate service, including gnome-open under Gnome and exo-open in XFCE.

Cool.

---

### Post by Nezing on 2011-10-24
Plasmafusion:
**"i'd go for lxde. tried them all...even icewm and enlightenment...and i find it gives the best balance of performance and looks".**

Totally agree with you.Tried Gnome,KDE,XFCE,Fluxbox,X1,Open GEU.And have now installed LXDE,Totally stable (for me).

---

### Post by jmate24 on 2011-10-24
LXDE is cool and fast i really like it works great and very light.

---

### Post by bob-linux-user on 2011-10-24
In reply to my own post #5 on this thread I must make it clear that all I did was put together what I had learnt from googling and that none of it is my original work.

---

### Post by Marzata on 2011-10-25
Being with Ubuntu (Gnome) since the beginning. Until this October of 2011. Moved all machines to Xubuntu 11.10 and felt in love with Xfce. ...    

> **TitanKing said:**
>  ... come here Xubuntu while your husband is too busy entertaining his new friends, lets get down to business ;)

---

### Post by hollowhead on 2011-10-25
thanks bob-linux-user I will try this, like so many people I've been horrified by unity.  I want my old look back with avant at the bottom, compiz switching between destops and a proper menu system etc.  I'm not even sure what apps are installed.  Here's an example of the stupidity of it.  I can see no way to add applets to the toolbar at the top but as it upgraded it upgraded these that I used previously....

---

### Post by kd4dii on 2011-10-25
Hi
     Another unity hater here.  I installed 11.1 on another partition on my box and tried the changes posted above by bob-linux-user and got a lot of the abilities of the old gnome back.  Thanks bob-linux-user you da man!


Bob

---

### Post by bob-linux-user on 2011-10-25
If ubuntu is any harder to configure than this next time, then I will be off to Mint, or I may try Xubuntu again, although I find it is not as easy to customize or as good looking as gnome 2.xx

Although it not hard wired into anybody's dna, the old (and in my view better) method of pressing a symbol and having some sort of cascading menu pop up as per Windows 95 has almost become as much of a "natural law" as the qwerty keyboard. (Although there are minor variations on qwerty across the globe)

---

### Post by Barbie845 on 2011-10-25
I've been using Ubuntu off and on since it's very early days.. What's strange to me with this Desktop Environment controversy is it took Ubuntu years to get Gnome virtually bug free, and make it almost an exclusively point and clink GUI. AKA it was very user friendly..

And soon as they got that done they trash it for Unity and Gnome 3.. Neither which are 'point and click friendly'.. I loaded 11.10 a few days ago and I haven't had to do so much Terminal work since the early days of Ubuntu.

---

### Post by nethero on 2011-10-25
> **merlinus said:**
> LinuxMint will be supporting both gnome 2 and 3 in their distributions, including the upcoming version 12.  It is based on ubuntu, so the differences are slight.

Have a look at their website -- linuxmint.com

You can also download a live cd.

So does this mean someone from Linux Mint will continue to fix bugs in Gnome 2?  Or will they simply offer the option to install Gnome 3 or Gnome 2 in their releases?

---

### Post by Copper Bezel on 2011-10-25
See [_this release_]("http://www.h-online.com/open/news/item/Linux-Mint-developers-make-GNOME-3-edition-plans-1362441.html"). They're moving to Gnome 3, but they're delaying the move while they customize their Gnome 3 experience through a set of extensions. Until it's ready, they're using Gnome 2.

---

### Post by hollowhead on 2011-10-26
I'm happier having made the changes that bob-linux-user outlined but still unhappy about themes I cannot use all parts of my old themes presumably I can install new gtk+ themes which dominate the look and feel.  Does anyone know if avant and compiz will work with this?   Lastly whilst xscreensaver is fully installed I cannot find it in the menu system......

---

### Post by kd4dii on 2011-10-26
Hi
     About the screen saver I saw the below in another post and tried it, it works ok but has a different set of screen savers.  I installed electric sheep but it doesn't show in it.
 
Code:
sudo apt-get remove gnome-screensaver


sudo apt-get install xscreensaver xscreensaver-gl-extra xscreensaver-data-extra


After installing, go to ‘Control –> Startup Applications’

 

screensaver_oneiric_2

 

Then click ‘Add’ and type the entry below:

Name: xscreensaver

Command: xscreensaver –nosplash

xscreensaver -nosplash



Hope this helps you.

Bob

---

### Post by Marzata on 2011-10-26
Other possibility is to use Openbox or Fluxbox. See: [http://openbox.org/wiki/Openbox:Screenshots](http://openbox.org/wiki/Openbox:Screenshots)

---

### Post by WinRiddance on 2011-11-01
> **jdorenbush said:**
> I've been using Ubuntu since 8.04 "Hardy Heron" and 11.10 is the first Ubuntu release that I'm displeased with, so much so that I downgraded back to 11.04. The previous Ubuntu desktop environment worked perfectly and users were comfortable with how it functioned, but the release of 11.10 forced users to change how they interact with their desktop environment.

Based on what people are saying in this thread, I guess I should be checking out XFCE.

I think you're confusing 11.10 and 11.04 with 10.10 aren't you?
11.04 was the first Ubuntu to use Unity by default and it was also the version that drove thousands of people to switch to Mint, Debian, or Ubuntu with the XFCE desktop environment. Ubuntu 11.10 just made it a little more confusing - or helpful - depending which way you look at it, by including Gnome3. So unless I'm missing something, the "good Ubuntu version" that you're talking about reverting to would have to be version 10.10 right?
.

---

### Post by WinRiddance on 2011-11-01
> **TitanKing said:**
> 
Unity is not easier, in fact, old people find it harder to use if not impossible. My father is using Ubuntu (the one for human beings) and he loves it, there will be no way in hell he will ever be able to use Unity it seems. So I guess, for me it is backing down to Xfce, a Desktop for Human Beings, simplicity and without interfering, some people actually need to get work done and does not play music or browse Face Book all day.

I am really sad about Ubuntu Unity and Gnome 3, I respect what they are trying to do, but I think they are failing in the execution. It feels like Ubuntu has shown me the door and invited yappie users from a new neighbourhood.;)

I couldn't agree with you more ... you hit the nail on the head. :D
I've played around with different Linux versions for years too, but it wasn't until I tried Ubuntu about 3 years or so ago that I decided to make the complete switch from Windoze to Linux. Not dual-booting or with wine or a VM either, just straight up Ubuntu. What thrilled me to the max was the ability to perform professionally & privately ... on a desktop that met my "visual & interactive demands" 100% without having to learn a bunch of command line functions. Unity and Gnome3 took that away from me. I tried a couple of weeks but I just couldn't live without my own personal demand from what I expected my desktop to do for and with me. I hate that cell phone ipad look, I really do.

My phone is my phone, period. I really try hard not to "yack my life away" with thousands of useless apps or ridiculous time consuming functions, and my computer is my computer, performing the kind of work on a large 22" screen for which I'd never be able to use a phone anyway. So yeah, it seems to me that Unity and Gnome3 are catering more to those who have oodles of time on their hands to waste with pretty nonsense, as opposed to being designed for those of us who'd like to produce work in our own highly customized, comfortable environment which is what Linux/Ubuntu used to be all about ... FREEDOM ... and not just "partial" freedom.

For seniors I believe that Unity and Gnome3 are too confusing too. If my dad sees more than 4 or 5 symbols on the screen, especially if stuff just starts sliding/moving/appearing on its own without definitive personal "point 'n' click" involvement, he gets totally confused and frustrated. So again, Unity & Gnome3 may look and perform flashy, but they don't provide the freedom anymore that some of us want - and others need. I ended up switching to Debian, and about 3 months ago I switched to Mint which I really really love. Their forum is annoying though (IMO). Without an eventual fork to Gnome2, I guess I'll be switching to the XFCE environment as well. Gotta have those panels ... :D
.

---

### Post by WinRiddance on 2011-11-01
> **Copper Bezel said:**
> See [_this release_]("http://www.h-online.com/open/news/item/Linux-Mint-developers-make-GNOME-3-edition-plans-1362441.html"). They're moving to Gnome 3, but they're delaying the move while they customize their Gnome 3 experience through a set of extensions. Until it's ready, they're using Gnome 2.

Based on reading the contents of the above link, especially considering words like "starting out from scratch" makes it seem to me as though that's what Mint has in mind for Gnome ... to evolve from Gnome2 to something that takes all of the good out of Gnome3 while still providing users the means to enjoy everything about the customised desktop environment that they were previously used to. Ultimately, that's really the heart of most of the complaints, the fact that people can no longer quickly and intuitively have their desktop set up completely to their liking. It's the thing about both, Unity & Gnome3 that I never understood ...

Why take away the infamous "Linux Freedom" to easily do what you want your desktop to do? I find it hard to believe that that couldn't be accomplished with use of disabling some functions followed by providing the ability to use panels and other options as before? Like many others, that's what I resented, now being forced by Linux/Ubuntu (the human linux) into something that before only Windoze or Mac had the gumption to do ... one of the reasons why many people switched to Linux in the first place. Ah well ...
.

---

### Post by jdorenbush on 2011-11-01
> **WinRiddance said:**
> I think you're confusing 11.10 and 11.04 with 10.10 aren't you?
11.04 was the first Ubuntu to use Unity by default and it was also the version that drove thousands of people to switch to Mint, Debian, or Ubuntu with the XFCE desktop environment. Ubuntu 11.10 just made it a little more confusing - or helpful - depending which way you look at it, by including Gnome3. So unless I'm missing something, the "good Ubuntu version" that you're talking about reverting to would have to be version 10.10 right?
.

No, I meant 11.04, but I see your point. The reason I said 11.04 is because there is still the option to login with classic GNOME desktop.

---

### Post by Leebo on 2011-11-01
Well from the sounds of things I am fortunate enough to still be using Maverick and have yet ventured into this obscure land of Unity/Gnome 3. From the screenshots and other media that have seen, my initial thought of smartphone appearance was what bothered me about the new interface. Has anyone seen photos of the new Windows 8 metrofication? It looks as disturbing and childish as the Unity interface in my opinion. The "smartphone" interface is definitely not my interface of choice, heh , I still do not own a smartphone because I refuse to pay the addition $30 for a data plan and don't get me started on tablets....buy a laptop! 

I do wish for my computer to remain my computer and my phone to remain my phone. That is one thing i do like about Ubuntu and other flavors of linux; you still have the option to choose which WM you wish to use. From what I have read about the new Win 8 they may not be including the option to revert to the classic XP or 7 interface and users may be stuck with the new interface.

---

### Post by Atomic-Fanboy on 2011-11-01
This isn't an ideal solution, but have you tried installing the package 'gnome-session-fallback'?

---

### Post by bob-linux-user on 2011-11-03
Yes i have tried the fallback session. See my post #5.

---

### Post by Marzata on 2011-11-03
What about Mate Desktop Environment, which is a Gnome 2 fork, see: 

[http://ubuntuforums.org/showthread.php?t=1858282]("http://ubuntuforums.org/showthread.php?t=1858282")

but I already moved to Xubuntu (Xfce) and I do not want to look back.

---

### Post by bob-linux-user on 2012-04-04
Update (see my post 5) 
The 12.04 Gnome Fallback is much better than the old one. You can retheme it as well. When used in conjunction with the MWbuttons application to put the buttons back to the right, it seems as good as Gnome 2.

---

### Post by roffisserver on 2012-04-04
I hate Unity too! I would suggest getting LXDE. It is very lightweight but better then Unity!

---

