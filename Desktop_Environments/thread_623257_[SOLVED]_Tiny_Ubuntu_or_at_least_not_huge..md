---
title: "[SOLVED] Tiny Ubuntu or at least not huge."
date: 2007-11-25
forum: Desktop Environments
---

### Post by jludeman on 2007-11-25
This is the start of an attempt to create a tiny ubuntu iso and live cd. I'd appreciate any one reading this to offer help and or criticism 

Background:

In the last few weeks I have installed Ubuntu 7.04, 7.10 and Xubuntu 7.10 on two systems and three different hard drives. All three systems use about 2GB for a clean install. Gnome was slow to boot and slow to get to a usable desktop. I really liked the Gnome desktop after customizing it. In fact I customized it about ten times. Not because I wanted to. There is a bug in Gnome panel that occurs when adding or removing a launcher. It tries to redraw the panel and rewrite the configuration. If the drawing process fails for any reason the old configuration is gone and there is no new one. Bang all gone. The default menus and any user added launchers all gone. I decided I didn't like Gnome that much after all. 

So I tried xfce, fluxbox, openbox, enlightenment and fvwm. Xfce is still pretty slow on Ubuntu or Xubuntu. I did'nt like enlightenment or fvwm. Both fluxbox and openbox were good. Openbox has good fonts right out of the box. It's right click menu is very responsive.
Fluxbox has crappy fonts and no obvious way to fix them. It's right click menu is annoying. Unless you left click on an empty desktop space, it will just hang there in the way.

I decided to follow the directions here. [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) 

I've actually got .5 GB on the older system and 2 GB on the laptop. I still wanted to do a clean install from the command line and try openbox and fluxbox without the GDM and Gnome layers.

Beginning:

The command line install went very smoothly. I can now triple boot to windows or ubuntu on hda or command line on hdb. This system is using 374MB just to get to a command line. Damn Small Linux uses about that much for a working hard drive install with fluxbox and various tools built in. (Browser, editor etc.) DSL can become a full fledged debian install as well using Synaptic. It has so many broken dependencies that it's impossible to use for programming and development. That's why I'm moving to Ubuntu or whatever this hybrid thing I'm attempting to build is called. I'd like to see an ISO image of 200 to 400 MB size that could burn a live CD of this small system.

Bummer number one. I'm hooked to a phone line. Just to do sudo aptitude update is going to take 20 minutes or more. Maybe I can install from the cdrom. Well the article from help.ubuntu.com doesn't tell me anything about it. Time to google for imformation. If I didn't have a second working system how would I do that? Is there a command line browser?

Okay that's pretty simple apt-cdrom add. No wait a minute it's sudo apt-cdrom add. I'm about a half hour into this and I've typed my password way too many times already.

Sudo aptitude install xorg installs many many packages. It also says error in starting battery a whole bunch of times. On reboot startx fails.
This is a desktop - there is no battery - I think? Time to go to the working system and do some more googling.

Half hour later. To make a long story short the battery thing was caused by acpi being turned off in bios. I think it borked the xorg install though. I still can't startx successfully. I tried aptitude purge xorg and that did not help. Error is cannot stat /etc/x11/x.

I'm going to try another clean install after I pound my head against the wall for a while.

On reinstall the installer hung on the program load step twice. No appearant reason. Going back to the partition step and each following step finally cured it.
Basic clean install with xorg and startx is done. Time to login screen on old sytem 40 seconds. This is considerably faster than Ubuntu or Xubuntu. From experience I'm guessing about 20 seconds on the newer sytem.

Installed XDM, fluxbox and  openbox. Boot into x and openbox. Install gedit, thunar, feh, firefox, thunderbird, abiword, gimp and gnumeric. Using a combination of CD and modem time is about 3 hours. Also installing Emelfm, Synaptic and Midnight Commander. Hard drive usage is now 1.1 GB. Time to log in screen is 50 seconds. Time to usable desktop is about 1 second.

Breakdown is 45.6% in /usr/share. Doc is using a big chunk. Gnome icons is using a big chunk. I need to know more to prune this down without breaking the system. 

Screenshots follow. I'm using feh for the background manager. As you can see the fonts are not all that great in Openbox. I'm guessing that when it was on top of Gnome it inherited the fonts better than fluxbox did.

Just to be fair I did a re-install of Xubuntu on the slow system. Time to install < 1 hour. Boot to login 57 seconds. Login to useable desktop is an additional 7 seconds. Hard drive usage is 1.2 GB. If I trim out the unused fonts it would be less. 

Help please:
I don't want acpi at all. Not in bios - not in bootup.
I don't use the restricted drivers at all. Quite a bit of time is used in boot to deal with them.
What is safe to trim from Xubuntu?
Would it be smarter to start from the command line and work up to a usable system?

That's it for this episode. More later.

---

### Post by jludeman on 2007-11-25
The first post was written before Thanksgiving. I've been using Openbox on top of Xubuntu since then. My time to a usable screen is about 41 seconds. For comparison the Ubuntu installation could take up to 1 minute 15 seconds. I've definitely decided on openbox as the windows manager.

I'm using a lot of gnome stuff including gnome-panel. I learned from the web how to back up gnome-panel settings. I don't load it until after openbox is up. I don't have it open that much either. Clicking the quit button on the panel closes the panel. Openbox stays open. The right click menu in openbox has a menu item for gnome-panel when I need it.

My next step is a command line install with just the stuff I use. I'll report on the results in a few days.

---

### Post by benerivo on 2007-11-25
Good stuff. I've subscribed to this thread. Have you seen [this]("http://psychocats.net/ubuntu/minimal#barebones") attempt at a minimal install?

---

### Post by jludeman on 2007-11-25
Thanks 
I shaved another five seconds off boot time by installing Slim. (simple login manager) Unfortunately it broke something. See my post here.
[http://ubuntuforums.org/showthread.php?p=3838900#post3838900](http://ubuntuforums.org/showthread.php?p=3838900#post3838900)

I checked out your link. To say that openbox is slightly faster than  xfce does not do it justice. Even apps run faster. In xfce there is a noticeable lag between clicking on firefox and seeing anything. In openbox it's just there. Now.

That article is in the domain of what I'm trying to do. I'd like to see a live cd that people could try the light system on to see if they like it. Something small enough to download the ISO over a phone line if you're patient.

By the way there is a comman line browser called lynx.

---

### Post by jjalocha on 2007-11-25
Maybe you could take a look at the [fluxbuntu]("http://www.fluxbuntu.org") project? They are creating a minimal *buntu distro around Fluxbox. I didn't have the time yet to install their 7.10 release candidate, but community comments are very good, so far.

---

### Post by urukrama on 2007-11-26
If you want to use xfce and openbox, try doing a command line install and adding xfce4 to it, not xubuntu-desktop. I find it uses less resources, and it doesnt' come with a whole string of applications you might never need or use (Abiword, Thunderbird, etc.)

Also, if you want help configuring Openbox, follow the link in my signature. It leads to a fairly comprehensive guide in configuring Openbox. 

For panels, gnome-panel might not be the best option, unless you really want/need one of the applets of the gnome panel. Try fbpanel or lxpanel, for example, they are much lighter (there are more panel options in the above mentioned guide).

To clean up space on your harddisk, use one of the following:

[LIST]**sudo aptitude autoclean or sudo aptitude clean**: from the man pages:
>  **clean**  Removes  all  previously  downloaded .deb files from the package
              cache directory (usually /var/cache/apt/archives).

       **autoclean**
              Removes any cached packages which can no longer  be  downloaded.
              This  allows  you to prevent a cache from growing out of control
              over time without completely emptying it.

[/LIST]
[LIST]Install **localepurge**: during the installation you have to mention which locale (language, etc.) files you want to keep. Whenever you install something through apt/aptitude/synaptic, localepurge will remove all the language packages you don't want. From the man pages:
>  localepurge is a small script to recover disk space wasted for unneeded
       locale files and localized man pages. It will be automagically  invoked
       by  dpkg  upon  completion  of  any apt installation run.  
[/LIST]
[LIST]**Debfoster**:  debfoster maintains a list of installed packages that were explicitly
     requested rather than installed as a dependency.  Arguments are entirely
     optional, debfoster can be invoked per se after each run of dpkg and/or
     apt-get.

     If a new package is encountered or if debfoster notices that a package
     that used to be a dependency is now an orphan, it will ask you what to do
     with it.  If you decide to keep it, debfoster will just take note and
     continue.  If you decide that this package is not interesting enough it
     will be removed as soon as debfoster is done asking questions.  If your
     choices cause other packages to become orphaned more questions will
     ensue.
[/LIST]
[LIST]**Deborphan**: deborphan  finds  packages that have no packages depending on them. The     default operation is to search only within the libs  and  oldlibs  sections to hunt down unused libraries. (if you prefer a graphical user interface, you can easily create a filter in Synaptic for orphaned packages if deborphan is installed).
[/LIST]

I hope this helps.

---

### Post by jludeman on 2007-11-26
Thanks for your help. I tried most of the panels and did not like them. With gnome panel not loaded until after openbox it does not cost much in terms of speed or memory use. I can turn it on and off at will so I can use openbox by itself.

I haven't tried lxpanel. I'll take a look at it. Mostly I just want a clean desktop. I actually liked fbpanel but could not figure out how to turn it on and off from a terminal.

I'm working on trimming a command line install now. It's going to take some time and research.

---

### Post by maybeway36 on 2007-11-26
I like IceWM for something like this.

---

### Post by urukrama on 2007-11-26
> **jludeman said:**
> I haven't tried lxpanel. I'll take a look at it. Mostly I just want a clean desktop. I actually liked fbpanel but could not figure out how to turn it on and off from a terminal.

I quite like fbpanel too, because it is easily configurable. If you want to easily turn of a panel, or any other application for that matter, you can just use the command "killall *name of the application*" I have entries in my Openbox menu to turn conky, panels, skippy and xcompmgr off. Very practical.

---

### Post by Griff on 2007-11-26
> **jjalocha said:**
> Maybe you could take a look at the [fluxbuntu]("http://www.fluxbuntu.org") project? They are creating a minimal *buntu distro around Fluxbox. I didn't have the time yet to install their 7.10 release candidate, but community comments are very good, so far.
I'm running the latest RC of fluxbuntu and it's excellent.  If your only fluxbox experience is with the fluxbox package in the ubuntu repos the difference is going to be night and day.  It's a very fast, efficient system.  After it boots up it idles at about 70MB.  Gnome and KDE were usable on my system (4 year old laptop), but fluxbuntu absolutely flies.  I'd recommend a look.

---

### Post by jludeman on 2007-11-26
I appreciate any and all help and suggestons. However this is a personal project. I'm going to include any applications that I need or want. In the end I may just prove to myself that Xubuntu is a decent starting point for an openbox system. Or not.

Next Steps:

One - Basic System:
I'm using aptitude from local debs to save time. I know I could use dpkg -i *.deb but that does not resolve dependencies.
I copy the /var/cache/apt/archives folder to my home directory. 
From a terminal 
cd /home/username/archives.
find . -name "*.deb" > override 
dpkg-scanpackages . override > Packages

Now add a line to /etc/apt/sources.list
deb file:/home/username/archives ./
I can use apt-get, aptitude or synaptic on the local debs. Saves a ton of time.
Here are the contents of my /etc/apt/sources.list.
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
deb file:/home/jim/archives ./

Command line install with nothing but xorg, slim, midnight commander, openbox openbox-themes and obconf.
total hard drive space 494 MB
/usr/lib/ 134.4 MB
/usr/lib/dri 34.9 MB
/usr/lib/python2.5 18.5MB
/usr/lib/xorg 13.1
/usr/lib/perl 10.3

/usr/share 127.1

Actually I think I can just leave this alone. It's not that big.

Two - Needed Apps - stage one:

Firefox and Thunderbird.

Installing Firefox adds a ton of libraries and other stuff.
total hard drive space 683.6
/usr/lib 199.4
/usr/share 223.1 MB

Three - Needed Apps - stage two:

Gnome panel, nautilus and gedit. sudo aptitude install gnome-panel gets nautilus as well.
total hard drive space 962.3 MB

Okay I might be able to live with this. This is a much cleaner install than Xubuntu. I'm going to drop back to step one and try to clean up as I go. At step three I'm going to fork. Fork one is gnome based. Fork two is lightweight panels. I need to find a good tabbed editor and a decent replacement for nautilus. Maybe a third fork for some KDE apps?

To urukrama:  I'll be using deborphan and localepurge on my next step. Thanks for the tip on killall. I'll be using that on the lightweight fork. That's pretty slick having an avatar for an avatar.

---

### Post by urukrama on 2007-11-26
> **jludeman said:**
> I need to find a good tabbed editor and a decent replacement for nautilus. Maybe a third fork for some KDE apps?

I'm not sure about the tabbed editor (I use mousepad and have no real needs for tabs so never looked for a light text editor with it), but instead of Nautilus I strongly recommend Thunar. It is a lot faster, and has some good features: restore from trash, custom actions, etc.

> **jludeman said:**
> That's pretty slick having an avatar for an avatar.

Thank you. ;)

---

### Post by rosschilen on 2007-11-26
Are you able to use the ubuntu gui configuration dialogs if you installed the server edition and openbox?  Mainly I like the network selection gui (connect to wired/wirless networks).  This could be avoided if I knew the command line equivalent of the network selection gui.

---

### Post by kerry_s on 2007-11-26
" JWM " the speed of fluxbox or openbox, the look of icewm.

base install
apt-get install xserver-xorg-video-vesa xorg synaptic jwm
as your regular user " startx "

tip:
if you select your vid driver, xorg won't install all of them.
use " rungetty " to auto log in
simple script in the bash profile will auto startx
debian is better for size, ubuntu ties to much together.
(check the commands, i'm going off memory)

---

### Post by jludeman on 2007-11-27
rosschilen - Yes I use wifi-radar right now but I could use the gnome applets.

kerry_s - I switched between fluxbox and jwm when I tried out Damn Small Linux. Both have advantages but I'm really liking openbox right now.

My new session manager is startx. I wish I had more information on removing excess hardware especially restricted drivers. They use up a lot of time at boot and I don't use them. All other hardware drivers also eat up a big chunk of boot time.

Any web links that you could help me out with?

I might end up going with debian. I ran into a lot of bugs during my install. None of them were lethal but a quick search of the web showed me that some of them have been around since April and still are not solved. One bug was alive in Feisty and was released in Gutsy. Pretty minor unless you use Firehol then it becomes a pain to fix.

I still think it would be a good thing to have a very small very fast live cd for Ubuntu. I broke my grub last night and could not boot any of the three systems on this computer.

I grabbed Damn Small Linux live cd and within minutes was on line searching for fixes. The Ubuntu live cd was right there next to it but in the time it takes for it to boot and be ready I was already almost done.

I mean I had to use Dillo to browse and Beaver to edit but it worked. The whole live cd is only 50MB. Sometimes if it's a typo or a missing file you can fix problems from the live cd.

---

### Post by jludeman on 2007-11-27
I did a clean install from the command line. I hit escape at the cd gui prompt and typed in the following.
cli acpi=off hw-detect /start-pcmia=off
Acpi is still causing me headaches. It never worked right on this machine. It never caused problems because I disabled it in bios. Gutsy has a fit no matter what I do. Yes I tried acpi off in grub menu. Still does not work right.

I ended up with a command line system that uses 362.6 MB

Next Steps:

My new x display manager is - bash login - startx

Command line install with nothing but xorg, midnight commander, emelfm, feh, openbox openbox-themes and obconf.
total hard drive space 496 MB

Two - Needed Apps - stage one:
I don't see an alternative to Firefox. It's huge in terms of memory usage and disk space. Once we commit to that we've pretty much lost our tiny footprint. Use the email program of your choice. I like Thunderbird.

Firefox and Thunderbird.

Installing Firefox adds a ton of libraries and other stuff.

Three - Needed Apps - stage two:

Gnome Fork:
Gnome panel, nautilus and gedit. sudo aptitude install gnome-panel gets nautilus as well.
total hard drive space 908.5 MB This includes emelfm, midnight commander, thunar, rox-filer and feh.

I can definitely live with this. This is a much cleaner install than Xubuntu. 

Lightweight Fork:
You can put any or all of the lightweight window managers and panels on the hard drive at less space cost than the gnome fork.
Find a window manager you like and learn it. I'm sticking with openbox.
Use the Xubuntu apps to keep it light.

KDE Fork:

You can add your favorite KDE apps to any of the above at very little extra hard drive cost.

Conclusions:

The folks at Ubuntu did a very nice job with their alternate install disks. Start from a command line install and customize as you go. By the time you get what you want you'll know the system pretty well. You'll end up with a lean mean fast machine. 

For a little heavier and slower experience without the hassle I'd go with Xubuntu.

If you want really lightweight I'd go with the fluxbuntu project. I don't see a real need for anything but Ubuntu/Xubuntu alternate install and fluxbuntu right now.

After thoughts:

I'm sticking with openbox and the gnome under layer. Openbox has one big problem. The xml config needs to be modular. Then you could make and break files without breaking everything. The documentation is very bad. Other than that I love it.

Time to start thinking about a remastered live cd.

My experience with Ubuntu people is pretty positive. They seem to be a little lean on the heavy technical types. These are hard times for techs in the US. No jobs left. If you flip burgers twelve hours a day maybe you can't hang out on the forums.

---

### Post by urukrama on 2007-11-28
> **jludeman said:**
> The documentation is very bad. Other than that I love it.

I find the Openbox [documentation]("http://icculus.org/openbox/index.php/Help:Contents") quite good, actually. I've learned a lot from it and recommend every openbox user to have a look at it.

---

### Post by jludeman on 2007-11-28
Just some observations.

I took honors technical writing in college. I learned four basic things.

1. Target your audience 
2. Re-target your audience - ie graduate engineers dumb it down to sophomore pre-engineering - high school grad assume middle school comprehension
3. Break it into chunks and use white space and images a lot.
4. Tell them what you are going to say, say it and then tell what you just said.

In the fourteen years since college this has proved very useful not only in writing but in meetings, informal conversations and training users. You really can't go wrong assuming that your audience is dumb as a stump. 

Here's a couple of examples:
1. Medicine bottle
open - arrow pointing counter clockwise 
close - arrow pointing clockwise

I doubt that the engineer who designed the container is insulted by this simplicity. Nor is the scientist who designed the contents.

2. There is an excellent article on building a live cd here. [http://www.linuxjournal.com/article/7246](http://www.linuxjournal.com/article/7246)

Read the text and then look at the pie chart. Unless you are pretty savvy about this topic the pie chart conveys a lot more information in a lot less space. Focus is increased by the use of white space around the graphic.
Even text can be improved by using boxes and white space.

The forums here can provide a useful place for new users to learn. It can also provide a learning platform for experienced users to learn to communicate their knowledge. 

I can't really give openbox documentation very much praise - sorry - I just can't.

I found some more links on live cds that may prove helpful.
[http://souptonuts.sourceforge.net/cdrom.htm](http://souptonuts.sourceforge.net/cdrom.htm)
[http://www.debian-administration.org/articles/125](http://www.debian-administration.org/articles/125)
[http://lichota.net/%7Ekrzysiek/projects/kubuntu/dapper-livecd-optimization/](http://lichota.net/%7Ekrzysiek/projects/kubuntu/dapper-livecd-optimization/)
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

I think I'll try to use the last one and try to build a minimal iso of 500MB or less that will boot a live cd.

Openbox seems to suite my work style. I'm more productive using it. I'm a multi-tasker by nature.
Here's a screen shot taken as I write this sentence. Another cleaner shot follows.
Peace

---

### Post by jludeman on 2007-11-28
Oops no screen shots. Next try follows.
That's lxpanel at the top. There's a 16 pixel margin on the right for the mouse menus.

---

