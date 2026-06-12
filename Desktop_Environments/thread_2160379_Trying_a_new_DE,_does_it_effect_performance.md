---
title: "Trying a new DE, does it effect performance?"
date: 2013-07-06
forum: Desktop Environments
---

### Post by RadicaX on 2013-07-06
So scrolling around the forums and such, I seen people talking about installing new DEs over ones on their variant of Ubuntu.

Like say someone installing Cinnamon on Xubuntu. This sounds like a neat thing to do. But how does it effect performance? For example, if I had Unity or a KDE Desktop Environment. Would installing LXDE allow me to have those benefits of it? (Like Low resource use, Lower Ram usage, etc.) Or is the session just a candy coating over it really. And still going to be bloated like KDE? I find that interesting, and it might be useful to go and try other DEs out rather than a whole new OS every time you want to try it out. 

Thank you in advance.

---

### Post by BreezyBrooke on 2013-07-06
All desktops in Linux have different performance ratings due to the diversity of programming and tastes. Some are really fast, while others very slow. The Default Unity on Ubuntu is about middle ground.

The fastest are probably JWM (Joe's Window Manager) and Openbox. Both are incredibly simple and fast in design because they don't use 3d acceleration. JWM being like Windows 95 and Openbox like Windows 3.1. 

Next up would be desktops like E17 and LXDE. They are a little heavier but still lightning fast. E17 has a built in compositor that gives it effects, but the performance impact is ziltch. LXDE is essentially Openbox with a desktop panel, it has no effects, but they can be added using standalone compositors like xcompmgr. 

Then there are desktops like Gnome-Shell and Unity. They are heavy, but move at a good speed. They have complex effects enabled and require a good graphics card. 

Finally there is Cinnamon and KDE. They are the heaviest and have a significant impact on performance. They use lots of effects and the like, but are the most Windows like. You should only use these if you have a good PC. 

There are far more destops out there, but these are the popular ones.

---

### Post by RadicaX on 2013-07-06
That is interesting, thank you for the quick reply. So really, you can have 3-5 different ones if you wanted, but the one you are using is what effects your performance if I am understanding right? Really, out of the ones I have tried, I have liked Xfce the most, it is a nice middle ground. But maybe one day I will be in a KDE mood, or an Openbox type mood. Thank you for your speedy reply.

---

### Post by SuperFreak on 2013-07-06
[http://askubuntu.com/questions/181370/how-heavy-on-resources-is-cinnamon-desktop-environment]("http://askubuntu.com/questions/181370/how-heavy-on-resources-is-cinnamon-desktop-environment")
Certainly not definitive but looks like Unity and Cinnamon DE are about the same
Also,I certainly don't think Cinnamon is much like Windows or at least not much like Win 8


To answer your question, I don't think adding additional DEs will affect performance as you log on to each separately.I have Gnome, Unity and Cinnamon. Adding additional DEs may add more packages and will use up more Hard Drive space though

---

### Post by BreezyBrooke on 2013-07-06
@SuperFreak

Well on my PC, Cinnamon runs like doo-doo while Unity flies. In fact, I GL benchmarked the two using glmark2 and found that running Unity gave me a score of 1019 while Cinnamon game me a score of 509. Practically halved. As for Cinnamon being like Windows, I was refering to it's Windows XP/7 like appearance.

@Radiax

Yes, you can run more than one desktop and yes your performance varies by desktop and not the applications. As for XFCE, I forgot to put it in the post up there. :redface: Anyways, XFCE is considered lightweight and is fast, has good effects that don't slow too much. So it's in between E17 and Gnome-Shell in terms of performance. But general rule of thumb, don't install too many desktops, especially if they are radically different. they could clash in config files and have each others installed apps listed as with their own. Like KDE and Gnome. Cluttred and confusing.

---

### Post by Roasted on 2013-07-06
> **BreezyBrooke said:**
> 
Finally there is Cinnamon and KDE. They are the heaviest and have a significant impact on performance. They use lots of effects and the like, but are the most Windows like. You should only use these if you have a good PC. 


Not to interject, but have you used KDE 4.10 yet? I'm not exactly a KDE fan (love the project, but the countless rough edges keep me on Gnome), but KDE 4.10 was the only thing that did NOT run like trash on my single core Atom nettop. KDE 4.10 absolutely surpasses Unity in performance, hands down.

Earlier versions of KDE, yeah, they got the fattest pig award. Anymore Unity seems to be reigning king in that regard, even though it's gotten better performance wise in recent releases.

---

### Post by RadicaX on 2013-07-06
I see, thank you all for the input on it. Seeing as I have 40-50 gigs left of free room, that would not be to much an issue on filling it up. I could not see having to many on my machine though. I like light-weight normally because they are so zippy. But really, I think my family would just perfer something with a bar on the bottom of the screen. rather than the top. So You said KDE 4.10 was pretty light weight though? Am going to look into that. So here is another question, lets say I have 2 DEs. Very much alike, with many of the same packages, does this cause problems? Will that slow boot times down, or make programs slower to open? Like if I did download Cinnamon, and Gnome, since they both have so much of the same stuff, will they have trouble seeing it then?

Thank you all for your help in this matter. It is really cool Linux can do this at all.

---

### Post by buzzingrobot on 2013-07-07
Different software has different resource requirements. A desktop environment, even the simplest, is a collection of many pieces of software. 

The capabilities of your hardware are the most important factors in performance.  

DE's with reputations as "light" typically do require less memory. However, you need to verify that on your system because memory use varies depending on things like the amount of memory that's available and how you've configured things.  E.g., KDE's default configuration has many effects and capabilities enabled.  If they are disabled, memory use decreases considerably.  XFCE's reputation as "light" may or may not have merit these days.

Using less memory doesn't necessarily equate with running faster.

When you install different DE's, bear in mind that it's often difficult to uninstall them cleanly.  Many dependency links are created and an "apt-get remove ..." may want to remove some core software.

---

### Post by SuperFreak on 2013-07-07
> **buzzingrobot said:**
> Different software has different resource requirements. A desktop environment, even the simplest, is a collection of many pieces of software. 

The capabilities of your hardware are the most important factors in performance.  

DE's with reputations as "light" typically do require less memory. However, you need to verify that on your system because memory use varies depending on things like the amount of memory that's available and how you've configured things.  E.g., KDE's default configuration has many effects and capabilities enabled.  If they are disabled, memory use decreases considerably.  XFCE's reputation as "light" may or may not have merit these days.

Using less memory doesn't necessarily equate with running faster.

When you install different DE's, bear in mind that it's often difficult to uninstall them cleanly.  Many dependency links are created and an "apt-get remove ..." may want to remove some core software.


+1

---

### Post by Peripheral Visionary on 2013-07-07
[Here]("http://forums.linuxmint.com/viewtopic.php?t=54945&f=90#p314893") is the best "layman's language" summary of the subject I've ever read.  It's a little old now because it doesn't include some newcomers to the party but it's in plain and simple newbie-friendly language.

---

### Post by vasa1 on 2013-07-07
> **buzzingrobot said:**
> ....  XFCE's reputation as "light" may or may not have merit these days.
...
Would you elaborate on that? Did you mean Xubuntu or Xfce, *per se*? In either case, what, according to you, has changed for the worse (in terms of lightness)?

---

### Post by buzzingrobot on 2013-07-07
> **vasa1 said:**
> Would you elaborate on that? Did you mean Xubuntu or Xfce, *per se*? In either case, what, according to you, has changed for the worse (in terms of lightness)?


Nothing more than that I've seen some comparisons showing XFCE looking better in resource use and some comparisons showing XFCE not looking better in resource use.  Hence, the "may or may not..."

Comparisons like that always need to be extrapolated because none of us run on exactly the same hardware/software used to make the comparisons, and at that point it all becomes pretty relative.

Personally, unless someone is running on extremely limited hardware, I think we make a bit of a fetish about resource use. I'll trade memory for speed any day.

---

### Post by Peripheral Visionary on 2013-07-07
Xfce *as a desktop environment* is not much "heavier" or slower than the ultralight LXDE desktop.  But Xubuntu may be "heavier" or slower than it's younger sibling **because of the installed applications and default settings**, _NOT_ because there's that much difference in performance /resource demand between the two DEs.  The difference between Kubuntu and Ubuntu, for example, is much *more* than the difference between the KDE and Unity desktop environments.

---

### Post by RadicaX on 2013-07-07
I see. That is pretty cool to know. I found in that link given, it was a pretty good idea to just have a windows manager, really, that could be the way to go on older machines. 

My Machine is somewhat old. It is a Campaq Presario SR5250NX model. A gig of ram, duel core processor it would seem. (Intel.) about 2.6 GHz. And some intel graphics card. It was pretty cheap when I got it. And have used this computer exclusively for several years now. From the OSes I have tried, I found Ubuntu 11.10 to be fine really. Xubuntu to be slightly faster. But Puppy Linux seemingly the fastest. I have tried slackware too, expecting it to be somewhat fast, but not quite so. It was slower than Xubuntu. Really, I like speed, and anything that does not make my computer to work overly hard. Xubuntu so far has been a nice medium for looks, and speed. 

Might I ask, how many of you change or add a DE to use to your Linux of Choice? What would be your motive for it, rather than just using a Linux of a different flavor. (Like why not just go with Xubuntu if you use Ubuntu and want XFCE?)

---

### Post by Peripheral Visionary on 2013-07-07
> **RadicaX said:**
> 
My Machine is somewhat old. It is a Campaq Presario SR5250NX model. A gig of ram, duel core processor it would seem. (Intel.) about 2.6 GHz. And some intel graphics card. It was pretty cheap when I got it.


My computer is half of that and runs Xubuntu 12.04 LTS faster and prettier than it did WindowsXP when it was brand new!  If you want the latest bleeding-edge stuff - and are willing to pay a little cost, perhaps, in stability, use the latest version.

But your larger question boils down to this:

> **RadicaX said:**
> 
Might I ask, how many of you change or add a DE to use to your Linux of Choice? What would be your motive for it, rather than just using a Linux of a different flavor. (Like why not just go with Xubuntu if you use Ubuntu and want XFCE?) 

If you want to try [COLOR=#000080]**L**[/COLOR]ubuntu, open Synaptic Package Manager and install the [COLOR=#000080]**lubuntu-desktop**[/COLOR] metapackage.
But if you want to try [COLOR=#000080]just the LXDE *desktop environment*[/COLOR], install only[COLOR=#000080] **LXDE**[/COLOR] and it's dependencies.

To try [COLOR=#0000ff]**X**[/COLOR]ubuntu, install [COLOR=#0000ff]**xubuntu-desktop**[/COLOR].  To try [COLOR=#0000ff]just the Xfce environment[/COLOR] *without all the preconfigurations and applications of Xubuntu*, install only [COLOR=#0000ff]**Xfce**[/COLOR].

To try [COLOR=#008080]**K**[/COLOR]ubuntu, install [COLOR=#008080]**kubuntu-desktop**[/COLOR] from Synaptic.  Or to try [COLOR=#008080]*just the KDE environment*[/COLOR] without all the kubuntu settings and configurations and default applications, choose [COLOR=#008080]**KDE**[/COLOR].

See the difference?

Log out of your current session after installing one you want to try, then log back in choosing your new **session**: Xfce *or* Xubuntu,  KDE *or* Kubuntu, LXDE *or* Lubuntu.  If you have plenty of room on your HDD you can try them all without downloading and installing separate LiveCDs!  Simply choose the session you want to explore!

Ultra-mega-fast blazing speed with sufficient cool desktop eye candy for me, was **minimal ubuntu with Xfce** (*not xubuntu-desktop, just the Xfce desktop environment*) installed.  Then I choose my favorite applications (the native Xfce ones work best in Xfce of course, but they're all pretty much interchangable anyway) and **Xfce-goodies** to make it pretty.

It was faster than Xubuntu, but only because Xubuntu uses some very cool settings and configurations and default applications that make it wonderful and intuitive.  While I was able to get slightly "more speed" using only Xfce instead of Xubuntu-desktop, I've decided that the Xubuntu team really does know what they're doing and have chosen a near-perfect balance in their defaults.  It's so much easier for me to "trim down" Xubuntu than to build my own from scratch.  It was fun trying it and I learned a lot, but it was too frustrating and time consuming.  Humbled, I bowed down low and paid homage to the amazing Xubuntu team for their wisdom in choosing those default settings and applications so well that Xubuntu works right out of the box and needs only a few minor changes to suit me perfectly.  Like different wallpaper, panel applets, and a different icon set.  Not much more than that.

The beauty of Linux is that it can be whatever you wish it to be!  The beauty of Ubuntu is the imagination and inginuity of the teams who develop those wonderful configurations, settings, and choices of default applications.

---

### Post by RadicaX on 2013-07-07
I see. That makes sense. So when you download an environment, you get a core set of it, just the DE. But you can opt to download a set that is per-configured like lubuntu to try. Having just the DE might be nice if you can work with it, and spend time in it. But if you want a full desktop like experience, without as much work, you can just download the one of the buntus or something. 

This is my last question then. Part of why I like Ubuntu and its derivatives of Linux, is the updates are easy to do. A click of the button, and it tends to handle it. Now Canonical is not handling all of the different DEs, but would my update-manager look for updates for those DEs. (Even if you have to change the configuration a bit?) Sorta like it does for Google Chrome, or FireFox applications? If that were the case, I might just opt for the one with the longest security support and just fiddle slap some other DE on it. 

Thank you all for your input on this. Really, I have had all my questions answered, and then some!

---

### Post by SuperFreak on 2013-07-07
I am not sure of other DEs but cinnamon DE is updated through Update Manager

---

### Post by RadicaX on 2013-07-08
Well, that answered all my questions. Thank you!

---

### Post by Hylas de Niall on 2013-07-08
Thank you for a great thread :)

I've been reading all the questions and answers with great interest, and *it's answered a fair few questions of my own* without me having to ask them!
[SIZE=1]I just wish there was an official Openbox spin of Ubuntu so that i didn't have to jump hoops to get a nice #! (Crunchbang) style Ubu (i tried Madbox, but that wasn't as easy to reconfigure as #! is :(  ).[/SIZE]

Anyhoo, thanks again, and if all your questions have been answered please mark the thread as 'solved'.

Cheers!

---

### Post by RadicaX on 2013-07-08
Indeed. it was something I had searched for, but could not find all of the answers about. Sometimes starting a thread really helps others find the answers too. Glad you had some of your questions answered too.

Oddly, when I go to thread tools, it does not allow me to pick solved? This seems to have happen to me a few times when making threads now. Why is there no solved option?

---

### Post by Peripheral Visionary on 2013-07-08
Ubuntu updates everything that needs updating - everything that is installed.  But you can choose "only security updates" and "only long-term-support versions" if you're one of those paranoid people like me who needs absolute stability.

Your summation is very well put, RadicaX:

> So when you download an environment, you get a  core set of it, just the DE. But you can opt to download a set that is  per-configured like lubuntu to try. Having just the DE might be nice if  you can work with it, and spend time in it. But if you want a full  desktop like experience, without as much work, you can just download the  one of the buntus or something. 

That's it in a nutshell!  

**The wonderful teams of people who put together these different 'buntus, and the wonderful users who *test* these mixtures to see how they work and uncover any bugs and issues are my heroes!**  I have only one computer and it absolutely has to work reliably!  Otherwise - and if I had the time to spare - I would be a tester too, and do my part to help make the 'buntus the awesome things they are.

This thread was fun!

Be sure to mark it [SOLVED]("http://ubuntuforums.org/showthread.php?t=2121377").

> Go to the first post in your thread. Click on "Edit Post". Now click on  the orange "Go Advanced" button. In the advanced editor change the  prefix to "SOLVED". Now click on the orange "Save Changes" button.  If you don't see the button, manually edit the Subject line and just type the word SOLVED into the title when you edit the first post.

---

### Post by Hylas de Niall on 2013-07-08
Edit the first post, click the 'Go advanced' button and you can change the thread title there. ;)

---

### Post by RadicaX on 2013-07-08
Thank you and duly noted! This thread is now marked solved.

---

