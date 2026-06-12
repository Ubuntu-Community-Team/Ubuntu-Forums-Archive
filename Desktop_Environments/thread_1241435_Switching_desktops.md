---
title: "Switching desktops"
date: 2009-08-16
forum: Desktop Environments
---

### Post by isee on 2009-08-16
I have installed Edunbuntu, but would like to be able to switch back to just Jaunty.  I was informed that I could do so at the login screen, but there is no option available that I can find.

Am I stuck with Edubuntu?  Other than uninstalling through Synaptic and using a Psychocats link that i was provided in another thread to remove all associated programs?

Can I not choose between Jaunty and Edubuntu when I boot?

What if I want a third choice for desktop, as I am putting UbuntuStudio into my desktop.

What if I wanted Edubuntu, UbuntuStudio, Kubuntu, and Jaunty Jackalope on the same computer.

How can I achevie this?

---

### Post by warreno on 2009-08-16
At the login screen for Edubuntu, is there an "Options" menu? If so, try clicking that and choosing "Select session" (or something similarly named).

You should get a popup that lets you choose what windowing system you want to log in with; then, ideally, you'll be asked if you want to make Gnome the default for all future sessions.

Today I converted a friend's KDE install to Gnome, and that was the way indicated to change windowing systems.

Hope this helps...

---

### Post by isee on 2009-08-16
Yes I get the options menu, select session;

1 Run Xclient script
2 GNOME
3 Server Remote connection
Failsafe Gnome
Failsafe TERMINAL

These are my options.

What can I do?  I would like to explore Edubuntu, but gosh I hate red and my Firefox is different, Red.

At this point it almost seems I need a partition for Jaunty and the rest, but they are just desktop versions, and I should not need a partition.

---

### Post by warreno on 2009-08-16
Select GNOME from that menu. It's the default window manager for Ubuntu, and should let you get back to the desktop you prefer.

---

### Post by isee on 2009-08-16
-"Do you wish to make GNOME the default for future sessions? .......but your default is Xclient script."-   I picked "just for this session".

Seems I cannot get back to just Jaunty

---

### Post by warreno on 2009-08-16
Maybe I'm not understanding something. TTBOMK, Gnome is the standard GUI for Jaunty; selecting it from the "Options" menu should let you get back to it as your standard desktop window manager. You have the option to make it your default ("Use for all future sessions", or something similar), or to use it just for one session.

When you log out from the Gnome environment you'll get the login screen with the "Options" menu again; from that menu you can again choose what session you want. I'm guessing Edubuntu is the Xclient script. You can choose that one, then, and opt to have it for just that session (so you can test Edubuntu), or make it the default (which will switch you back to Edubuntu as the standard).

What I'm not comprehending is what you mean when you speak of "just Jaunty"; to my mind this means Ubuntu with GNOME as its GUI.

---

### Post by XubuRoxMySox on 2009-08-16
This should work. Open a terminal and type

```
sudo apt-get purge edubuntu-desktop
```

That should bring you back to good ol' Ubuntu.

-Robin

---

### Post by warreno on 2009-08-16
But won't that delete Edbuntu? I don't think that's the intention here; I think isee wants to get back to GNOME, but not actually remove Edbuntu. Of course, I could be very wrong.

Hey, isee, have you actually logged in using the GNOME session? Did it do what you wanted?

---

### Post by XubuRoxMySox on 2009-08-16
> **warreno said:**
> But won't that delete Edbuntu? I don't think that's the intention here; I think isee wants to get back to GNOME, but not actually remove Edbuntu. 

*If* the intention is to use Gnome and keep his applications, then simply logout and choose a different Session. If the intention is "go back to just Ubuntu" then purging the edubuntu desktop will help.

I suspect it's the red theme that is the issue, not the desktop environment nor the installed educational packages.

Preferences>Appearance: Choose a new theme.

-Robin

---

### Post by warreno on 2009-08-16
Hmm. You could be right about that. But isee has been fairly clear about his/her intention to install and use other desktop environments to see which work best for his/her usage; that doesn't seem to be on par with the idea of removing environments or even changing themes.

I have a hunch that the terminology is getting a bit thick. There is, of course, a disconnect between the filesystem (Linux/Ubuntu) and the windowing system or desktop environment (Gnome/KDE/Edbuntu/whatever).

Without a bit of technical background it can be hard for pretty much anyone to understand that the GUI is not the same as the OS. Not the least because both Windows and Mac make it essentially impossible to see that distinction, and even very competent users of those OSen end up at sea initially with Linux.

So when isee says s/he wants to get back to "just Jaunty", I wonder if that means *I want to get back to the windows, system bars and chrome that I had when I first installed Ubuntu*, which might mean, *Get back to Gnome*.

If that's the case, choosing to switch sessions at the login window is probably the way to go, since it will allow isee to install and "hot-swap" different desktop environments at will, once the skill has been acquired. Otherwise, yes, your suggestion to purge Edbuntu is probably the better one.

Absent feedback from isee, of course, all of this is speculation. We don't even know if s/he tried to actually log in under a GNOME session, for instance, nor what the results were.

---

### Post by isee on 2009-08-17
Well, I do remember when Windows was a program rather than an operating system.

It is a little difficult to describe what I am asking.  Kubuntu uses a KDE GUI?  Is that correct?  Edubuntu and Ubuntu (just Jaunty) use a GNOME GUI?

I have UbuntuStudio on my desktop, which uses GNOME also?

I selected a GNOME session on my desktop (just this session) and it loaded Studio.  It gave me a message that XClient script is my default, which if that is what normally loads if I log straight in rather than chose a session, then XClient loads Studio also, so it seems Jaunty is not available on my desktop either.

When I say Jaunty, I mean the environment that I installed when I first changed from Windows.

Hope thats a little more clear.

Thanks!

---

### Post by warreno on 2009-08-17
OK, sorry that the terminology wasn't clear. The way it used to be with Linux was you installed the base operating system, and it was all command line. Looked a little like DOS used to. You could then choose to install a GUI atop that. (Or not, as you wished.) Linux, including Ubuntu, is still basically the same. You can see the CLI -- command-line interface -- yourself any time by hitting CTRL-ALT-F1. (Press CTRl-ALT-F7 to get back to your GUI.)

The CLI isn't as pretty as the GUI, but it excites nerds to know it's available. ;)

Short answer is that, yes, different distributions of Ubuntu use different windowing systems. Kubuntu, as you say, uses KDE for its front end. Plain vanilla Ubuntu (which includes Jaunty) uses GDE (or Gnome) instead.

Now if I'm understanding correctly, when you chose GNOME you didn't get the original install you expected; you ended up with UbuntuStudio, yes?

And when you select the Xclient script instead, you still get UbuntuStudio? Or do you end up in Edubuntu?

---

### Post by warreno on 2009-08-17
Oh, wait a second. Does UbuntuStudio's look and feel bug you? It might just be a question of opening a terminal session (Applications -> Accessories -> Terminal) and typing in

```
metacity --replace
```

That's assuming (1) you've logged in under the GNOME session; and (2) UbutnuStudio is essentially GNOME with a different window manager. Metacity is the one you see in the basic Ubuntu Jaunty install.

---

### Post by warreno on 2009-08-17
You know what, I checked into both Edubuntu and StudioUbuntu to see what they use for desktop managers, and as near as I can tell they both use GNOME as well.

I suspect **dixiedancer** had it right when she was discussing themes. My apologies if that's been the case all along; the fix should be easy.

Go ahead and log in as you normally do on that machine, right-click the desktop and select ""Change desktop background". A window should open. Select the "Theme" tab and click the one called "Human". If everything goes back to the way you wanted it, that's all it was.

---

### Post by isee on 2009-08-17
Ahhhh...   Thanks so much.  Switching to Human returned my computer to Jaunty.  I don't know about having Edubuntu and Studio together, as I have them on separate computers, but I see the theme that is Studio in the available themes in the Edubuntu version, which makes them just themes with software packages, rather than a different environment like Kubuntu.

I have just installed LXDE on my laptop, which gives quite a few options at the login under Sessions, and of course more questions, as it seems LXDE uses KDE.

So Edubuntu and Studio are just Jaunty themes with additional software installs, can't really switch between as they are the same thing, except with a customized Login splash screen.

Thanks again!

---

### Post by isee on 2009-08-17
The Ctrl-Alt F1 and F7 are pretty cool.

---

### Post by isee on 2009-08-17
Oh.. and Edubuntu is basically available in LXDE, and I know why now.  Thanks!

---

### Post by XubuRoxMySox on 2009-08-18
> **isee said:**
> Ahhhh...   Thanks so much.  Switching to Human returned my computer to Jaunty. 

Sweet! I'm glad we could help. I'm still a newbie (just started in March) and my Ubuntu experience has been so trouble-free that I haven't got much experience at fixing broken stuff yet... but it feels great to help someone else!

> 
I have just installed LXDE on my laptop, which gives quite a few options at the login under Sessions, and of course more questions, as it seems LXDE uses KDE.


LOL, I guess it does kinda sorta *look* that way, but LXDE is completely independent and does not "use" KDE or Gnome. But a fresh install of LXDE "looks like KDE" because of the default blue desktop and icons. You can change that, by the way... I added my way-kewl dark/emo/dance wallpapers to *usr/share/lxde/wallpaper*, and with a right-click on the desktop I can change them at will. Icons can be put either in the task bar or on the desktop with a few mouse clicks. Elegant simplicity. I love it.

Anywayz, KDE is hyoooge, and pulls in whole libraries of stuff that it depends on. Gnome the same way. Xfce pulls in quite a few as well. LXDE needs *very* few. It's quite independent, and so lightweight that it is often "accused" of not even being a true desktop environment at all.

Enjoy! And as a newbie myself I'm always delighted (and often surprised) to help someone!

-Robin

---

### Post by warreno on 2009-08-18
> **isee said:**
> Ahhhh...   Thanks so much.  Switching to Human returned my computer to Jaunty.

That was all **dixiedancer**. I'm glad you were able to get it worked out, though. Enjoy!

---

### Post by isee on 2009-08-18
Well, as far as my laptop is concerned, I ran the Edubuntu install, then changed themes, which made it basically Ubuntu Jaunty again, so ran the purge edubuntu-desktop command, to see what would happen.

Basically nothing.  I checked synaptic and a lot of Edubuntu packages were still installed, no big deal, but Edubuntu Desktop was not.  So I re-engaged Edubuntu Desktop through Synaptic.  Then to be sure I ran apt-get install edubuntu-desktop, which told me, as I expected, that the current Edubuntu Desktop was already installed.  There was no change to my computer, no difference wether I have the Edubuntu desktop installed or not, as it's not like I can choose it

What is the issue here I think is that Edubuntu is billed as a version the same as Kubuntu and Xubuntu, which it clearly is not.  I cannot change between Ubuntu and Edubuntu, or UbuntuStudio and Ubuntu as I have on my desktop, but I can change to KDE or Xfce or LXDE.

I guess my confusion is I have Linux, I have Ubuntu, and either GNOME, KDE, ect as my desktop.

If I had Linux Mint, would I still have GNOME, KDE, etc?  Like Linux and GNOME, but Mint rather than Ubuntu?  Is that the way it works?

I used to have MSDOS and Windows, a long time ago, so it is the third layer that is confusing me.

---

### Post by SushiR on 2009-08-19
> **isee said:**
> What is the issue here I think is that Edubuntu is billed as a version the same as Kubuntu and Xubuntu, which it clearly is not.  I cannot change between Ubuntu and Edubuntu, or UbuntuStudio and Ubuntu as I have on my desktop, but I can change to KDE or Xfce or LXDE.

I guess my confusion is I have Linux, I have Ubuntu, and either GNOME, KDE, ect as my desktop.

If I had Linux Mint, would I still have GNOME, KDE, etc?  Like Linux and GNOME, but Mint rather than Ubuntu?  Is that the way it works?

I used to have MSDOS and Windows, a long time ago, so it is the third layer that is confusing me.

I'll try to put it simple:

1.) You've installed an operating system. It'a a linux operating system.

2.) You've chosen a distribution. In your case, it's UBUNTU. It could be as well Opensuse, Mandriva, Fedora or whatever.

3.) There are different RELEASES of your (or any) operating system. Yours is Ubuntu JAUNTY (release number 9.04 - 9 for the last digit of the year, 04 for the month it was released). The one released before was called INTREPID (8.10). The releases differ in what software versions are installed. Newer releases have newer software versions, often with improvements for hardware and features in general.

4.) There are different - let's call it - SPINOFFS from Ubuntu, that are EDUBUNTU (aimed at educational use), UBUNTU STUDIO (multimedia production), KUBUNTU (uses KDE as desktop environment), XUBUNTU (uses XFCE desktop environment, aimed to be used on older hardware) or plain UBUNTU (uses GNOME).

Under the hood the spinoffs of one version (here: Jaunty) are more or less the same but have a different bunch of software atop. And you can install that special software bundle in addition to your installed spinoff. If you installed plain Ubuntu (with Gnome), but want the benefits of KDE (which is default at Kubuntu), you just can install "kubuntu-desktop"...and there you are. At login, you can chose which one you want to login. Easy, isn't it?n It's all just software that can be added and removed.

The reason for different spinoffs are plain simple: Somebody who likes KDE but want the benefits of Ubuntu (as distribution) can rather install Kubuntu than installing Ubuntu, then adding KDE and removing Gnome.

I hope you have a better understanding of it now.

Cheers, Sushi

---

### Post by isee on 2009-08-19
Well I am getting closer to understanding, and no disrespect meant, but even you are considering Edubuntu and Ubuntu Studio as spinoffs like Kubuntu and Xubuntu, which is misleading because I can chose Kubuntu KDE, Xubuntu Xfce, and even LXDE which I've heard may become Lubuntu, but GNOME is the other option.

There is no difference then, between Edubuntu, UbuntuStudio, and Ubuntu (Hardy, Intrepid, Jaunty), as they are all just GNOME and you can't choose between, and from what I can tell you can't really get rid of them once installed.

I guess I don't understand the difference between Distros then, the mythical second layer.

I am gaining an understanding of desktops, know my OS is GNU/Linux.

Does RedHat or Mint run KDE or Xfce?  Whats the difference if Linux is my OS, GNOME is my desktop environment, what Distro I have?

Sorry, thats a lot of questions, but I switched to Linux to gain full control of my computer.

---

### Post by XubuRoxMySox on 2009-08-19
> **isee said:**
> ... no disrespect meant, but even you are considering Edubuntu and Ubuntu Studio as spinoffs like Kubuntu and Xubuntu, which is misleading because I can chose Kubuntu KDE, Xubuntu Xfce, and even LXDE which I've heard may become Lubuntu, but GNOME is the other option.

You can turn your "plain vanilla" Ubuntu into Kubuntu with one command:

```
sudo apt-get install kubuntu-desktop
```

Don't like it and want to change it back? Open a terminal and type

```
apt-get purge kubuntu-desktop
```

Same with Xfce (Xubuntu). These metapackages do more than just add the KDE or Xfce dektop environments, but several of their applications as well. Lubuntu will be a notable exception, though, since LXDE has so few dependencies. And they are looking to use only lightweight applications. So far there is no "lubuntu-desktop" metapackage to install.

You can add LXDE to Ubuntu and then remove the Gnome desktop

```
sudo apt-get install lxde
```
```
sudo apt-get purge ubuntu-desktop
```

but you'll still retain many Gnome packages and applications. That's actually a good thing while you're still a newbie, because you can try stuff out and see what works for you. Some day you can build your own customized Ubuntu with only the stuff you want and none of the stuff you don't.


> There is no difference then, between Edubuntu, UbuntuStudio, and Ubuntu (Hardy, Intrepid, Jaunty), as they are all just GNOME and you can't choose between, and from what I can tell you can't really get rid of them once installed.

Gnome is the *default* (because it's awesome), but you can add and remove *any* desktop environment you wish in *any* 'buntu variant.

> 
I am gaining an understanding of desktops, know my OS is GNU/Linux.

Does RedHat or Mint run KDE or Xfce?  Whats the difference if Linux is my OS, GNOME is my desktop environment, what Distro I have?

A "distro" may have a *default* desktop environment (Ubuntu, Mint, many more) but most do not limit you to that. Because most of the different desktop environments pull in dependencies and whole libraries of stuff to run, **developers choose (usually) one default** to include on their CD. Otherwise the CD would be huge and take forever to download. For the most part the other desktop environments are best used by getting the customized "variant" or "edition" for *that* distro (Xubuntu, Kubuntu, Mint KDE, Mint Xfce, PCLXDE, Phoenix (PCLinuxOS's Xfce edition, many more).

So you have **Linux**. Linux has many different **distributions** (like Ubuntu). Distributions can have many different **variants** or **editions** which may default to a particular **destop environment** (KDE, Gnome, Xfce, LXDE, Enlightenment, etc).

The beauty of Linux is that it can be just about anything you want it to be! 

Have fun,
Robin

---

### Post by nu2ubntu on 2010-07-28
Hi,
I accidentally downloaded the Edubuntu theme without knowing it (just thought it was a package of applications). Next time I start up the theme is all different and I lost my desktop background.

Not having it saved in anywhere obvious, does anyone know how I can recover that .jpg/image file?
Thanks

---

### Post by tom4jean on 2010-09-18
I know this thread is a little old but I just had to respond.
Gnome is a desktop environment that runs on Linux.
GNOME, KDE, XFCE,LXDE,  etc... are all different desktop environments that run on Linux.
They are open source environments maintained SEPARATELY from Ubuntu and available and used by virtually all Linux distributions. 
They all have there own websites, so do a search and take a look.

Edubuntu is NOT a desktop environment. It is a set of educational software and different artwork including log-in screens, backgounds, etc.. that run within the GNOME desktop environment that is used by Ubuntu.
That is why you can not switch from Ubuntu to Edubuntu, 
They are both using the GNOME desktop environment. By installing Edubuntu you have simply modified it.
Edubuntu just adds software and artwork.

To remove edubuntu after adding it to Ubuntu you have to remove not only the edubuntu package but all the extra stuff too.
After uninstalling the Edubuntu package from the software center uninstall the turtle programing environment from the software center and it will remove all the extra software with it.
Then go to the synaptic package manager and uninstall edubuntu-artwork that includes the artwork and log in screens.
Unfortunately you have to remove each separately.
(At least I have not found a way to remove them together)

Finally, I would recommend to really learn about how Linux works to install and use Arch-Linux.
You will have to install the base system and then any one or more desktop environments and software to make a complete system.
BUT, You  will learn more by installing and using arch then by reading any books on Linux.

---

### Post by Yavatar on 2010-10-28
Instead of shipping LiveCDs they should ship 128gb pocket drives with the different distros on them. Then you can just have one source to play with all the variants and distros (or at least a good chunk of them). ;)

I installed Edbuntu and was expecting something like Kubuntu. I didn't realize it was more of a package. The odd thing though is that my application title bars are still the default dark gray/black color and windows controls are still on the left (and look the same). I'm not sure if any of those items was suppose to change. I also didn't have a problem with my desktop being changed (although the tree background was there previous to login).

My taskbars (panel bars? not sure the correct term) changed to a light gray, my desktop icons changed, and so did the icons in what would the system tray area in Windows. Don't know what the default Edbuntu appearance is suppose to look like (will have to look it up). From what I saw, Edbuntu completely changed the look but on mine it only did a partial change it appears. I'm not using anything custom aside from my background.

---

