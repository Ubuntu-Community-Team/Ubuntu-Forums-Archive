---
title: "Lucid Lynx minimal w/ Openbox, Slim, and launcher for old hardware and beginner users"
date: 2010-07-20
forum: Desktop Environments
---

### Post by chrisharrington on 2010-07-20
Hi, I am trying to develop a custom install of Lucid Lynx that has four very specific criteria:


[LIST=1]
[*]Latest kernel (for the latest security, drivers, to run the latest web apps etc.) thus Lucid Lynx
[*]Runs on old hardware. I've given up (for now) on 64MB RAM, so minimum 128MB+ RAM, 10GB storage, 800Mhz+ CPU. So currently starting with the mini.iso. Apps do not have to run fast! Just run. Obviously ;)
[*]Custom configured Desktop and GUI for absolute beginners (as in "what's a mouse?") based on a "not-a-desktop" iPhone GUI idiom (such as Ubuntu Netbook Remix with its netbook-launcher). However this should obviously be scalable so as users grow proficient they can remove the launcher and use a normal desktop.
[*]Good Japanese support (my users are all native Japanese speakers)
[/LIST]
And the purpose of the project is:[INDENT]To bring people in my rural Japanese community out of the stone age vis a vis computer infrastructure and technology without requiring them to replace their existing hardware, when they have it, or buy new hardware when they don't, or purchase software. For those who's hardware is just too old or have never used a PC, I will be using used donated hardware.
[/INDENT]There is, subsequently, one other criteria such that some form of my custom install run on PPC (G4) hardware because I may get my hands on a few used G4 Macbooks, but in that case I may create a separate version because the Macbooks have better specs and fewer package options.

If my only goal was 2 (and disregarding PPC hardware), then there are plenty of great options out there, from Damn Small Linux and Tiny Core on the very low end, to Puppy Linux, all with localized Live distros, and quite recently, the really slick Ubuntu based Mint LXDE. However, these options fail on criteria 3 by being less intuitive the lower you go, so though some of my users have been using Windows (98, ME, 2000 etc., very few on XP) or Mac (usually up to 10.3.9) just barely grasping what they were doing (lack of basic understanding of the file/directory idiom), many, of all ages, have never used a PC, and for such users I think the iPhone idiom is a much more appropriate starting point for their PC learning adventure, sort of an OLPC for grownups approach, and means much less time spent by me teaching them.

Based only on criteria 3, one of the best options is the UNR, especially after the performance boost from dropping the 3D acceleration requirement in 10.04, but unfortunately that runs on Gnome which kills criteria 2 dead on arrival. It is my personal environment of choice, but no go on old hardware.

So I have resorted to rolling my own, basically a scaled down approximation of the base command line install plus some of the LXDE environment.

I am sharing the process here in the hopes that someone more knowledgeable than I about Ubuntu and GNU/Linux in general, and custom installs in particular, might have some pointers. Also, perhaps this might be of use to anyone who has a similar goal.

Other lesser criteria:

[LIST=1]
[*]Users will not need to do much configuration. They will be provided machines pre-configured (email accounts, etc.). So only GUI configuration for GTK theme change or other cosmetics will be needed, or even desired, as I don't want them to click on things accidentally and break everything (which I watch people do all the time on "normal" desktops)
[*]In the same vein, everyone in the area is hooked up on ADSL where the provider gives them a standard modem with a single Lan port, and network config requirements are thus pretty much the same across the board, so that will also be preconfigured. I will be doing a parallel effort to get routers out to everyone so I can set network to DHCP for mobility (in the case of laptops etc.) and uniformity of configs.
[*]Anything complicated config-wise that changes over time I will do by visiting them or remotely by reverse-VNC or perhaps remote login over a VPN.
[/LIST]
My process is to use the mini.iso for 10.04 found here
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

I select the standard command line install choosing the defaults for all questions. Language initially set to English (otherwise the terminal is unreadable), region/time-zone to Japan, otherwise default/yes to everything.

Then I reboot and log in.

I add the Ubuntu Japanese remix repository here (instructions in Japanese):
[http://www.ubuntulinux.jp/products/JA-Localized](http://www.ubuntulinux.jp/products/JA-Localized)

As I am using an Openbox specific panel/pager "ADeskBar" by [ADcomp]("http://www.ad-comp.be/") at the moment, I also add his private repository:
[http://crunchbanglinux.org/forums/topic/441/little-application-launcher-for-openbox/](http://crunchbanglinux.org/forums/topic/441/little-application-launcher-for-openbox/)
--------------------------------------
EDIT 2010.07.22 ADeskBar will be deprecated because it uses Python and python is too much a memory hog to use as a resident process on a low RAM machine
--------------------------------------


Then apt-get update, apt-get upgrade. A couple of packages are replaced by localized versions from the Japanese remix.

I then install the following packages with apt-get (no command options):

First the basics:
xorg openbox obconf obmenu slim hal adeskbar conky lxappearance lxrandr leafpad galculator pcmanfm abiword gnumeric thunderbird chromium-browser cups gpicview

(Wish there were lighter weight alternatives for email/browser, both the above choices are for best Japanese support. I don't mind if they run a bit slow, and a new user would not likely notice the 'difference' anyway)

Localization:
language-pack-ja language-support-ja ttf-umefont ttf-konatu poppler-data ttf-ipafont ttf-ipamonafont ttf-sazanami-gothic ttf-kochi-gothic ttf-sazanami-mincho ttf-kochi-mincho thunderbird-locale-ja chromium-browser-l10n

------------------------
EDIT 2010.07.22.11:54:
language-support-ja installs the default Ubuntu input manager, "ibus", and associated dependencies, as well as Anthy, the standard Japanese input manager. However, I've decided that anything written in Python is going to have to be purged because Python programs seem to use far more memory than equivalent alternatives written in other languages. Therefore, I've switched to SCIM which is more popular with Japanese users (Ubuntu Japanese Remix installs it over ibus) but not with Chinese users. Comparing memory usage with free in two VMs that are identical except for one uses ibus and the other scim, this appears to clear up 10MB RAM.

command is
sudo apt-get install scim-anthy scim-bridge-client-gtk
then
im-switch -z ja_JP -s scim
anthy and deps already installed with language-support-ja, but I want to remove ibus so I will add breaking down the language-support-ja package and hand installing only what is required.

EDIT:
language-support-ja is a metapackage that forces the installation of language-support-fonts-ja and language-support-input-ja. The latter, language-support-input-ja is another metapackage with just two deps, ibus-anthy and im-switch. We could use im-switch to make sure we set the input method properly, but we do not need ibus-anthy. Language-support-fonts-ja just installs ttf-takao-gothic and ttf-takao-mincho. While not the better Japanese fonts, there may be parts of the system that assume their presence.

EDIT: seems not to be the case, see below. Safe not to have language-support-fonts-ja

So, the resulting localization packages are

language-pack-ja im-switch scim-anthy scim-bridge-client-gtk ttf-umefont ttf-konatu poppler-data ttf-ipafont ttf-ipamonafont ttf-sazanami-gothic ttf-kochi-gothic ttf-sazanami-mincho ttf-kochi-mincho thunderbird-locale-ja chromium-browser-l10n
------------------------


Extras for ease of administration:
lxterminal xfce4-taskmanager hardinfo

Then for looks:
shiki-colors

Also, I add an Openbox port of shiki-colors found here:
[http://jmcknight.deviantart.com/art/Shiki-Colors-for-Openbox-149966599](http://jmcknight.deviantart.com/art/Shiki-Colors-for-Openbox-149966599)

Finally I configure everything to use Shiki-Wise (GTK, Openbox, and icons) much like Mint LXDE, and set system wide font to the IPA series (the best looking antialiased, but technically non free, Japanese font from the Ubuntu Japanese remix.) All appearance settings can be done with obconf and lxappearance but would like to script these.

And then I set locale to LANG="ja_JP.UTF8" in /etc/default/locale

That leaves the launcher. I took a look at lxlauncher as it is lightweight and has few dependencies. However, while it will partially follow the GTK theme, it has, currently, an unchangeable background and no clear roadmap with no clear activity that I can see. So at the moment I am tentatively using another ADcomp creation, ADesk-Launcher. This is also very much a work in progress and lacks an installer, but it is fully GTK themeable and ADcomp himself is helpful.
[http://crunchbanglinux.org/forums/topic/5584/pythongtk-crunchbanglitenotebookremix/](http://crunchbanglinux.org/forums/topic/5584/pythongtk-crunchbanglitenotebookremix/)
--------------------------------------
EDIT 2010.07.22 ADesk-Launcher will be deprecated because it uses Python and python is too much a memory hog to use as a resident process on a low RAM machine
--------------------------------------

In a VM, this gives me a basic system very similar in appearance and operation to the UNR but running in 30-50MB RAM, leaving enough to run one app at a time (email, browser etc.) in reasonable comfort on older gear. However, I am sure there must be some way to tweak memory usage, remove unnecessary bits of Xorg perhaps if there are such, to reduce that footprint.

Things to do:
Ubuntu will quite happily let you launch as many apps as you like using swap until the system crawls to a halt. The concept of memory is typically far beyond the grasp of a new user. Are there any tools/methods to force limit memory use, memory use per app, and the number of apps running concurrently, in a user friendly manner?

#Ideally, and this is a note-to-self, app icons on the panel/launcher would gray out when there was inadequate free RAM to run them.....obviously a project for another day

Printer configuration: in addition to requiring a good, lightweight, non-Gnome printer config app, printers are famously an issue on Linux in Japan. Support for printers in English/European environments may be good, but drivers supporting Japanese are few and tend to require building from source. Bleh.

Music and video: currently no flash. Either install ffmpeg or gstreamer and one of those user scripts to let them watch at least youtube in Chromium, or come up with something else? Also, it would be nice to find a full functioned music manager/player/ripper as in iTunes replacement level (compatible with iPod etc.). Video player is less important as viewing stand alone videos is a less common task for beginners.

Installing in under 128MB RAM. OK, I know that my base system already uses up to 50MB without doing anything, but with some tweaking and maybe a much older or lighter browser, a 64MB desktop should theoretically be possible (thin client? browser/email only?). Don't like to see otherwise operational hardware going to waste, but emphatically do *NOT* want to support legacy operating systems. The real problem is that even the mini.iso for as far back as Ubuntu 8.04 will die while loading preparatory packages into RAM on anything less than 128MB RAM. Any way around that?

At the moment I am doing (almost) all post login actions using a single shell script to keep things sane and repeatable. Ultimately I may like to burn a CD using:
[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)
but only if that will boot in 128MB RAM (or less!).

So in closing, if anyone has questions, suggestions, learned observations, etc. please let me know.

Thanks

---

### Post by tekknokrat on 2010-07-21
Hi,

i like the idea of a minimal environment with a modern kernel and desktop, optimised for old hardware. Just a question. Why not start with the ubuntu-netbook edition and then try to optimise on top of that. I would try to remove most of the gnome stuff, replace the launcher with the upcoming efl part, perhaps replace the filemanager with rox(-filer) or also enlightment file manager. 
For default tools I would go with sylpheed, midori (or other webkit browser), gnumeric, abi office... 
Perhaps you have experience in console and can try to give users easy access to companion commandline tools like w3m, mutt, irssi, etc...

Put some further optimisation in the kernel in case of responsive, a problem I see a lot on older hardware. Also don't forget to add some optimisations to reduce battery power consumption.
Just my 2 cents ;)

---

### Post by chrisharrington on 2010-07-21
Thanks for reading the long post ;)

> **tekknokrat said:**
> 
Why not start with the ubuntu-netbook edition and then try to optimise on top of that.


I don't have the skill to do a subtractive install process yet. I'm concerned there would more likely be unnecessary junk left on the system I wasn't aware of.

> **tekknokrat said:**
> 
I would try to remove most of the gnome stuff, replace the launcher with the upcoming efl part,


Actually the package, netbook-launcher-efl, is available now. apt-get -s install netbook-launcher-efl will give you a list of deps, and it doesn't look all that bad, lots of libs of course but none of the Gnome processes to run in the background eating memory. Seems to use Python though, same as ADesk-Launcher. A python process will eat up 10-20MB easily so I'm actually thinking of replacing the launcher I use now with something else anyway...too bad, Python is such an otherwise accessible language.
I don't know why I wrote off the new efl version the other day, I think I saw more Gnome stuff in there than there really was, and I had this idea that installing it was going to pull the whole Gnome desktop environment in with it...

I certainly don't mind extra libraries on the hard drive. Libraries don't run themselves :)

> **tekknokrat said:**
> 
perhaps replace the filemanager with rox(-filer) or also enlightment file manager. 


I haven't compared the memory and speed performance of pcmanfm with the others. I tried Thunar first as it seems popular with Openbox users. I'll cycle through all of them and end up using the one with the least extra features and best looking GUI from among the low resource options. As I am targeting beginners, extra menus and superfluous commands are just cause for confusion, something for them to click by accident and then call me up about. When they grow out of the simplicity, they can install what ever they like.

> **tekknokrat said:**
> 
For default tools I would go with sylpheed, midori (or other webkit browser), gnumeric, abi office... 


I tried midori and the user interface was just a bit too painful from the beginners eye, the side bar too much of a guts-showing job, not to mention I could not get it (nor Firefox for that matter) to use anti-aliased Japanese fonts properly, which is fatal. It does have to be readable. Chromium, on the other hand, got along with my gtk and openbox font preferences somehow, and I have hopes for near future Chromium html5 video support, which would solve the flash issue (assuming video would even play at its frame rate on a 800Mhz CPU, or I may have to raise the bar there).

More important than snappy performance is that the browser show, with the exception of Flash, every web site the user visits without glitches, and that knocks quite a few of the simpler browsers out of the running from what I have seen so far, but I still need to do a more thorough comparison.

Have not tried slypheed, need to put that on the list of things to do.

> **tekknokrat said:**
> 
Perhaps you have experience in console and can try to give users easy access to companion commandline tools like w3m, mutt, irssi, etc...


Unfortunately console is out of the question. I do much of my work in bash, but I'm actually going to hide it, remove it from panels, menus, etc. from my distro. In the west, most of us grew up learning to touch type on an electric typewriter if we grew up too long ago to learn it on a PC. In Japan, the vast majority of professionals in almost every industry (other than computer obviously) had *never touched a keyboard* as recently as the mid Nineties. Even then, many of those who had touched keyboards used Japanese-only proprietary ones on proprietary single purpose word processing hardware rather than the standard QWERTY keyboards which later took over with the influx of DOS. And the people who used those word processors were trained specialists hired to do only that. People in the office would *hand write* copy for the word processor specialist to type in. Go figure. Reason is that Japanese is made from 50 sounds, each with its own alphabet like character, which is then further converted as required into borrowed Chinese characters. Not very keyboard friendly. Today, the process for typing Japanese is, type the romanization of a Japanese word or phrase, hit the space bar, a menu of possible ways to write that sound in Japanese will pop up, you cycle through till you find what you want, then hit enter to select it, and start typing roman letters again. Obviously you don't have to do that to type shell commands, but the complexity of the former leads to a dislike of keyboards in general. While in the modern office today touch typing has become a basic job requirement in any field, rural Japan has not benefited from that change, and most people still cringe at the word "PC" and stick to writing emails on their cell phones.

So, point being, asking a first time PC user in Japan to *type a command* would be like asking the average Mac user to download and compile source code. In both cases, you are told exactly what to do, but the feeling of intimidation doesn't go away.

My final install lineup will, of course, include a typing game....

> **tekknokrat said:**
> 
Put some further optimisation in the kernel in case of responsive, a problem I see a lot on older hardware. Also don't forget to add some optimisations to reduce battery power consumption.

 
Do you have any links or pointers in that department? I am clueless, but if a custom tweaked kernel is going to lower my footprint significantly than it is worth the investment of time, trial and error.

> **tekknokrat said:**
> 
Just my 2 cents ;)

Thanks very much for the input!

---

### Post by chrisharrington on 2010-07-21
> **chrisharrington said:**
> 
Actually the package, netbook-launcher-efl, is available now. apt-get -s install netbook-launcher-efl will give you a list of deps, and it doesn't look all that bad, lots of libs of course but none of the Gnome processes to run in the background eating memory.

Well, I take that back. That was yesterday. Today when I removed the -s and did apt-get install netbook-launcher-efl I was informed that Firefox would be installed.

Firefox.

As a dependency for the *launcher*.

Needless to say I aborted and added --no-install-recommends

But then that threw out the baby with the bath water (gnome-menus for instance, probably the dependency for reading in the apps in /usr/share/), so I have a "launcher" with nothing in it and no way in the GUI to kill it. Seems like it themes well, appears to use the shiki-wise gtk theme, but not completely sure yet.

I'll try hand adding some dependencies and see what happens.

**Firefox!?** ](*,)

---

### Post by chrisharrington on 2010-07-21
Adding gnome-menus will get netbook-launcher-efl running properly.

*However*

I made the mistake of installing lxpanel from LXDE at the same time, as it was said to have few dependencies and written in C (so lighter perhaps than ADeskBar) as well as Synaptic.

One of those three apps installed at least 2 Gnome related processes which *remain on the system and run automatically* even after all three of the above packages are removed. This is precisely the gnome stuff I wanted to get rid of. 

Namely,

gvfsd gconfd-2 

Correction: gvfsd is installed already by my default set of packages, but not gconfd-2

Why do these run if nothing uses it??

EDIT: looks like maybe ibus used gvfsd?

I will have to go back and do step by step to see which package or packages pull these in.

---

### Post by chrisharrington on 2010-07-21
> **chrisharrington said:**
> 
apt-get install netbook-launcher-efl I was informed that Firefox would be installed.


Netbook-launcher-efl has a plugin to add web bookmarks to the favorites category in the launcher, called webfav. This plugin only works with Firefox. So it is webfav that pulls in Firefox. A bit like the cart pulling the horse, but then this launcher was written very specifically for Ubuntu & Gnome, so an understandable assumption I guess.

> **chrisharrington said:**
> 
 Seems like it themes well, appears to use the shiki-wise gtk theme, but not completely sure yet.


This is probably wrong, in retrospect it looked more like the standard color scheme for Ubuntu 10.04.

---

### Post by mister_p_1998 on 2010-07-22
Have you had a look at Peppermint OS as a base? it runs passably on my P3 500.

---

### Post by chrisharrington on 2010-07-22
> **mister_p_1998 said:**
> Have you had a look at Peppermint OS as a base? it runs passably on my P3 500.

This is a distro I had never heard of, thanks. Looks like it is a customization of Linux Mint, not sure what version. I did take a very close look at Mint 9 LXDE, which is of course Ubuntu with some nice custom packages like their software updater etc.

If I were targeting experienced PC users with older hardware, I would seriously consider just using Mint 9 LXDE, as it beats hands down any other 'lite' Ubuntu based distro such as Xubuntu or Lubuntu in my opinion, much more polished and complete.

However, I'm really basically trying to create a kind of OLPC for grown ups who can't type, so I need something far more minimalist, and as I said above, I'd rather start from scratch and build up then start with a complete desktop and tear down.

---

### Post by proxess on 2010-07-22
Epiphany with extensions does HTML5 youtube...

Yesterday I installed on a Celeron 366 128MB RAM: Ubuntu Mini, LXDM (I couldn't get XDM to work), OpenBox, tint2, WICD, Epiphany, Leafpad and Gnome-Games (for Mahjongg) it it works quite nicely.

---

### Post by tekknokrat on 2010-07-22
Just downloading Peppermint Ice for tryout with an old toshiba satellite...
I suspect the "Peppermint One" version running nice when I read Firefox.
Are there any further Firefox optimisations?  

At all I see a lot of new interesting stuff here, e.g. LXDE was completely passed by. I was good with Arch Linux on this machine and XFCE but it looked way to sparse and I was hooked in by UNR, on my shiny new eeepc ;) 

@chrisharrington:
Sorry, did not have the ultimative guide to kernel optimisations but perhaps [http://kernel-seeds.org/](http://kernel-seeds.org/) helps you to get started.

---

### Post by chrisharrington on 2010-07-22
> **proxess said:**
> Epiphany with extensions does HTML5 youtube...


Then I definitely have to try it. I'd been ignoring it because of its having Gnome in its description...

> **proxess said:**
> 
Yesterday I installed on a Celeron 366 128MB RAM: Ubuntu Mini, LXDM (I couldn't get XDM to work), OpenBox, tint2, WICD, Epiphany, Leafpad and Gnome-Games (for Mahjongg) it it works quite nicely.


I downloaded and compiled the latest version of tint2 (has some nice extra features not working in the version in the repositories). Yes, this is light weight, customizable, and slick. Now I just need a launcher.

> **tekknokrat said:**
> 
At all I see a lot of new interesting stuff here, e.g. LXDE was completely passed by.


I tried LXDE too over a mini.iso install, and that gave me hints for auxiliary apps to use (image viewer etc.).

> **tekknokrat said:**
> 
@chrisharrington:
Sorry, did not have the ultimative guide to kernel optimisations but perhaps [http://kernel-seeds.org/](http://kernel-seeds.org/) helps you to get started.

Looks like a good place to start, thanks!


EDIT:

OK, tried epiphany-browser.

Fonts are a problem, same as firefox, so I would need to find a way to get the system to use the nice Japanese fonts instead of the ugly ones.

Memory/process comparison
Epipany-browser 34MB (default Debian page shown)
 -following install and run along with it
gnome-keyring-daemon 1MB
gconfd-2 1MB
gvfsd-metadata .82MB
gvfs-gdu-volume-monitor .41MB
gvfs-afc-volume-monitor .38MB
gvfs-gphoto2-volume-monitor .36MB
Total use 37.97MB RAM of which 3.97MB stays in memory (all the g~ stuff) after closing the browser.

Chromium-browser (showing google.com)
chromium-browser 23MB
chromium-browser --type=renderer... 17MB
chromium-browser 9MB (another process?)
Total use 49MB RAM, none of which stays in memory after closing.

On the one hand, I like epiphany-browsers buttons to make the font bigger and smaller, great for beginners, older users etc., and that it saves RAM over chrome when first launched. I have a real problem with it launching other processes that nothing else uses without cleaning up after itself. Anybody know a way to stop that?

EDIT2:

OK, I went and uninstall gvfs
sudo apt-get remove gvfs
epiphany-browser can live without it as can most everything else (perhaps need to use a different file manager that uses something else for hot plugging etc.)
Then I tried removing gconf2 and lost a bunch of stuff that made me say "huh?" such as all Ubuntu Japanese language support packages (!?) and, drum roll please, the whole shiki-colors theme pack. Even though I just want the gtk theme, the package installs metacity stuff and Gnome stuff and therefore depends on gconf2, as does the whole epiphany-browser. So I apt-get remove 'd  anyway and did

sudo apt-get install epiphany-browser --no-install-recommends

Much leaner, but it still wants gconf2

<RANT>
I don't need or want gconf2, it is for having config changes be reflected instantly across Gnome apps. Not needed. Perhaps I should investigate compiling epiphany-browser from source and somehow get it to not depend on gconf2? I can config by hand I really don't care about real time cross app changes, so I don't want that daemon running. [Seems I am not the only one annoyed by gconf2 dependency by an app]("http://brainstorm.ubuntu.com/idea/23338/"). And, oh I don't know, with, now that I've looked at it, Ephiphany being the lightest weight, best beginner GUI browser but requiring gnome specific daemons to eat memory seems a bit counter productive.
</RANT>

Any ideas?

(BTW, oddly enough, with scim-anthy installed and configured and the system wide locale set to "ja_JP.UTF8", the loss of Ubuntu Japanese support packages is has no noticeable effect.....)

EDIT:
OK, perhaps its time for a reality check....now I'm starting to look into compiling Epiphany from source or even, no, yes, Linux from Scratch.......

---

### Post by Harii on 2011-02-02
as for an lite launcher = wbar
it is limited but real lite for old hardware.

you might want to use puppy linux - one of the ubuntu ones?

---

### Post by EarlsFurniture on 2011-05-19
Check out Woof.  After you create your ultimate spin, you can "woof" it into a puplet.  Then it will run in RAM like a regular Puppy Linux but be based on your custom Ubuntu remix.  This should solve your memory requirements, and may even get you under 64MB if you are careful. (standard Puppy runs at 39MB fresh)

Also, look into xPud.  It seems to already have a GUI possibly along the lines of what you are looking for.  Though I don't know how good their Japanese support is. (the developers are Chinese it seems) They also have their own package system, but from the looks of it, it shouldn't be too difficult to convert a .deb to an .opt package they use.  Unfortunately, they don't use the latest kernel, so they fail #1 for sure, but there is promise there, and it might be possible to recompile the newest kernel into their .iso, though I haven't tried that yet myself.  Installation isn't straight forward, but it isn't hard either.  It is simply a matter of booting the .iso from Grub.  Having persistent storage is another issue I haven't figured out yet, but I haven't really had the time to try either.  When I saw your #3, it was xPud that immediately came to mind.  I hope to use it for similar situations that you are addressing when I have the time to tackle the rough edges of it.  FYI, standard xPud comes in at a respectable 45MB of RAM on first boot.

Edit - I just noticed on their site they do custom versions. (for a fee I'm sure) But they also have a new system called mkxpud that takes an existing system, installed apps and all, and creates an xPud .iso out of it.  So perhaps this is the gem you are looking for.  They do assume Ubuntu 9.10, but it might work on a newer version, I don't know.  It seems to me in theory, you could create your custom Ubuntu, disregarding the DE (maybe using LXDE if that's what you intend as a fallback) and then using mkxpud to create your .iso.  It will run in ram, boot from grub, AND give you the iPhone like GUI you are looking for.  As for Japanese support, I suspect handling that initially before mkxpud while you are customizing the Ubuntu system, the language support would carry over and not be altered.

Caveat - xPud relies heavily on Gecko for the GUI.  Yep.  I'm not sure if there is a way to get it to use Webkit or not.  You may have to ask the developers.  Though I think you could let it use Gecko for the GUI, and then only have Chromium or Midori installed as the actual browser app the user will see.

Best of luck.

---

