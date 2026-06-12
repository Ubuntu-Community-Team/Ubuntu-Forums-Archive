---
title: "Uninstall KDE4"
date: 2008-10-30
forum: Desktop Environments
---

### Post by trogdor282 on 2008-10-30
I didn't realize how terrible KDE4 is until I upgraded to Intrepid. What's the easiest way to go back to 3.5? Do I have to reinstall Hardy?

---

### Post by Asraniel on 2008-10-30
Yes.
Kubuntu 8.04 will be supported for another year, and kde 3.5 is more than enough.

Kubuntu 9.04 will use kde 4.2, which is way better than kde 4.1, and has all the features missed from kde 3.5

By the way, could you just give a small list of what the things are you don't like about kde 4?

---

### Post by trogdor282 on 2008-10-30
Basically I there are menu and confing items missing. EVERYWHERE. I should be able to unlock a panel and grab it by the corner to resize it. Just like taskbars have done for over 9000 years. I don't want to have to learn some overcomplicated panel editor ********, I JUST WANNA DRAG THE DAMN CORNER! Why are all my desktop icons in a box now? I right click to send them back to the regular way, OOPS no option to do that. Fine, then at least make them smaller OOPS no option to do that. I drag the kicker from one panel to the other OOPS won't do that. I want a 4x8 grid of quicklaunch buttons OOPS only one row.

Who cares if it's fancy looking when nothing works? They should have started with functionality and added shiny.

---

### Post by Kalinda on 2008-10-30
> **Asraniel said:**
> Kubuntu 9.04 will use kde 4.2, which is way better than kde 4.1, and has all the features missed from kde 3.5
Will it really? ALL of them? That's a pretty tall order considering how much is missing.

I still like KDE 4, though, but it isn't yet ready for me to use it.

---

### Post by grotto on 2008-10-31
There is a multi-row quick laucher plasmoid on [KDE-look]("http://www.kde-look.org/content/show.php/QuickLauncher+Applet?content=78061"). I'm not sure if it is exactly what you need, however.

---

### Post by GreatBunzinni on 2008-10-31
> **Asraniel said:**
> Yes.
Kubuntu 8.04 will be supported for another year, and kde 3.5 is more than enough.
That's great but it's nonetheless a bit irrelevant as it isn't possible to get KDE 3 along with all the good stuff that comes with the 8.10 release.
> **Asraniel said:**
> 
Kubuntu 9.04 will use kde 4.2, which is way better than kde 4.1, and has all the features missed from kde 3.5
Wasn't that said about KDE 4.1?

> **Asraniel said:**
> 
By the way, could you just give a small list of what the things are you don't like about kde 4?

It isn't possible to config the panels to auto-hide, KDE app borders are huge and it appears that isn't configurable, there are UI responsiveness issues and there are still artefact issues, specially with popup menus and the system tray.

Granted, I welcome window transparency with open arms. Nonetheless, I don't know if that trade-off is good or bad.

---

### Post by slakkie on 2008-10-31
You might want to have a look here: [http://ubuntuforums.org/showthread.php?t=963695](http://ubuntuforums.org/showthread.php?t=963695)

---

### Post by GreatBunzinni on 2008-10-31
> **slakkie said:**
> You might want to have a look here: [http://ubuntuforums.org/showthread.php?t=963695](http://ubuntuforums.org/showthread.php?t=963695)

Installing random packages from a random repository set up by a random user isn't exactly the wisest thing to do. I do believe that whoever built the packages and made them available in order to sidestep Kubuntu's silly and unexplainable decision to bet it all on KDE4 should get an award. Nonetheless, there is this matter of trust which in this case is non-existent.

---

### Post by dentaku65 on 2008-11-01
> **GreatBunzinni said:**
> Installing random packages from a random repository set up by a random user isn't exactly the wisest thing to do. I do believe that whoever built the packages and made them available in order to sidestep Kubuntu's silly and unexplainable decision to bet it all on KDE4 should get an award. Nonetheless, there is this matter of trust which in this case is non-existent.

Well, you must say in "your opinion" is not-existent trust, to be correct. I did that HowTo, if you have read all the steps you can realize:
[LIST=1]
[*]you have Ubuntu (Gnome) Intrepid official
[*]you have KDE 3 external repos
[*]you have KDE 4 ppa repos
[/LIST]
Tomorrow, if you wish, you can remove both kde 3 and kde 4 and install official kubuntu packages simply doing
```
sudo aptitude kubuntu-desktop

```
Is not random of something, is a community effort besides the official line (not against).
Have you other reasons to say that is silly and not wise to do it?

---

### Post by francis_ba on 2008-11-01
[IMG]http://tinyurl.com/rerunner/[/IMG]
GOT IT UNINSTALLED, LOVE UBUNTU!!!

---

### Post by sdd231163 on 2008-11-01
One reason for using linux was to have choice in things like desktops. Kubuntu has removed my desktop of choice without warning me. 

I liked having both KDE 3 and 4 - 3 for work and 4 to experiment - all I want is the right to choose and not have it forced on me Microsoft style.

---

### Post by slakkie on 2008-11-01
> **dentaku65 said:**
> Well, you must say in "your opinion" is not-existent trust, to be correct. I did that HowTo, if you have read all the steps you can realize:
[LIST=1]
[*]you have Ubuntu (Gnome) Intrepid official
[*]you have KDE 3 external repos
[*]you have KDE 4 ppa repos
[/LIST]
Tomorrow, if you wish, you can remove both kde 3 and kde 4 and install official kubuntu packages simply doing
```
sudo aptitude kubuntu-desktop

```
Is not random of something, is a community effort besides the official line (not against).
Have you other reasons to say that is silly and not wise to do it?


What are ppa repo's? 

Eitherway, it would be nice if those packages make it into the official repository, since KDE 4 is more experimental DE and KDE 3 is a mature DE.

I have no problem installing custom packages as I needed to do this in previous versions of Ubuntu for software which was not available from the official repositories.

If you don't want random packages from a random guy from a random repository, you can always download KDE3 sources, install checkinstall and build KDE yourself. Checkinstall will install/create a .deb and you can then remove/add KDE 3 to your liking, just like with any other package you have installed.

---

### Post by dentaku65 on 2008-11-01
> **slakkie said:**
> What are ppa repo's? 

Eitherway, it would be nice if those packages make it into the official repository, since KDE 4 is more experimental DE and KDE 3 is a mature DE.

I have no problem installing custom packages as I needed to do this in previous versions of Ubuntu for software which was not available from the official repositories.

If you don't want random packages from a random guy from a random repository, you can always download KDE3 sources, install checkinstall and build KDE yourself. Checkinstall will install/create a .deb and you can then remove/add KDE 3 to your liking, just like with any other package you have installed.

I supposed that the kde3 integration on official Kubuntu Intrepid is not easily possible, and in any case this decision it depends by the team of Kubuntu itself.

The kde3 packages from Madscientist159 repository as been tested by me among other users of Kubuntu and they working fine under Intrepid. At least at the moment :)

The ppa repositories stands for Personal Packages Archives
[http://news.launchpad.net/cool-new-stuff/personal-package-archives](http://news.launchpad.net/cool-new-stuff/personal-package-archives)

I agree completely with you about external repos in case they provide applications/updates that the official ones do not provide.

---

### Post by barna on 2008-11-01
I completely agree with the first post in this thread: KDE4 is extremely annoying, unusable, and unstable, and it just doesn't work. What you get on the other side, is a very fancy look, which I always hated, because it takes resources off from really useful development. To give a few examples:
- I used to have Ctrl+Alt+O to open a terminal. I went to the keyboard shortcut settings, and I have set it up like this. It did not work, if I press either Ctrl+Alt+T (the default), or Ctrl+Alt+O, nothing happens
- I resized the panel, I don't like the default huge size. I logged in/out, and voila, my panel is again big (although not as big as initially)
- Alt+F2 starts the 'Run command' dialog. I typed in firefox, pressed Enter, and got the error message 'Run command crashed with ....'
- I have set up Ctrl+Alt+Right to change one desktop to the right. It works, but it takes a surprisingly long time.
- I started adept, and selected 'synaptic' for installation. Adept crashed (it detected probably that a concurrent application is being selected? :-) I don't know if this is a kde4 issue.

On my notebook the last usable ubuntu version was 7.10 (8.04 had a buggy driver for the atheros wireless card, which made the notebook hang with 100% cpu usage - this driver was not updated, or at least for a very long time not, so I switched back to 7.10)

I think KDE has reached the point, where it exceeds even MS Windows in useless fancy-looking things, for the price of being unstable. I used KDE because it had many integrated things - cd burner, kpdf, etc etc. I would switch now to either gnome or xfce. Does anybody have experience with these two?

---

### Post by mooha on 2008-11-01
Let's take an example: 
> The PCLinuxOS development team has announced the availability of the first public beta release of PCLinuxOS 2009: "The Ripper Gang is pleased to announce the first public beta ISO release of what will ultimately become PCLinuxOS 2009. This beta ISO features kernel 2.6.26.6, KDE 3.5.10, OpenOffice.org 2.4.1, Firefox 3.0.3, Thunderbird 2.0.0.14, FrostWire, KTorrent, Amarok, Flash, Java JRE, Compiz Fusion 3D and much more. **[SIZE="4"]We decided to use KDE 3.5.10 as our default desktop as we could not achieve a similar functionality from KDE 4.[/SIZE]** We will however offer KDE 4 as an alternative desktop environment available from the repository once we stabilize it. We request that only our more experienced PCLinuxOS users test this beta release and report any issues with it in the forum provided specially for it."

So this is what I think "in my opinion" is the problem:
If the cutting edge software is number one before Usability and Stability in Ubuntu, you get those forum threads over and over.

Personally I'm a Gnome lover, but I always have to install both Gnome and KDE, because sometimes you find an easy way to do things in both cases KDE / Gnome, sometimes you find an application that you think is the best for you in Gnome that dosent exist in KDE at all and some times is the other way back, Exp: I found Kaffeine a video/DVB better application  then any other video applications I tried so far.

If you wanna get a rid of KDE just go to Synapic seach for "KDE" select to un-install whatever you want in your result then apply.

KDE4.1 as a default for 8.10 is a mistake in my opinion.

I'm just hoping that every missing application will be completed on the next release.

Another thing: BRAVO to every one that is contributing and helping in Free Software in general.

Keep up the good work

---

### Post by ronocdh on 2008-11-01
> **dentaku65 said:**
> Well, you must say in "your opinion" is not-existent trust, to be correct. I did that HowTo, if you have read all the steps you can realize:
[LIST=1]
[*]you have Ubuntu (Gnome) Intrepid official
[*]you have KDE 3 external repos
[*]you have KDE 4 ppa repos
[/LIST]
Tomorrow, if you wish, you can remove both kde 3 and kde 4 and install official kubuntu packages simply doing
```
sudo aptitude kubuntu-desktop

```
Is not random of something, is a community effort besides the official line (not against).
Have you other reasons to say that is silly and not wise to do it?
For anyone newbies reading this, the code should be:```
sudo aptitude **install** kubuntu-desktop
```Please keep in mind that in 8.10, this will install KDE 4.1!

---

### Post by slakkie on 2008-11-01
> **dentaku65 said:**
> I supposed that the kde3 integration on official Kubuntu Intrepid is not easily possible, and in any case this decision it depends by the team of Kubuntu itself.


I think they wanted more eye-candy :) A mistake iyam, I think they should have leave the choice up to the user in this case.

> 
The kde3 packages from Madscientist159 repository as been tested by me among other users of Kubuntu and they working fine under Intrepid. At least at the moment :)

The ppa repositories stands for Personal Packages Archives
[http://news.launchpad.net/cool-new-stuff/personal-package-archives](http://news.launchpad.net/cool-new-stuff/personal-package-archives)


Ahh, I knew about non-official user repo's on launchpad, but I guess the name didn't stick.. :) Thanks for the reminder!

---

