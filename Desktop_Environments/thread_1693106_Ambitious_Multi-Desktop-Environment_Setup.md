---
title: "Ambitious Multi-Desktop-Environment Setup"
date: 2011-02-22
forum: Desktop Environments
---

### Post by Dark Owl on 2011-02-22
Hello people, do you like a challenge? I wonder if I could ask for your advice. 

(I apologise in advance if I should have posted this elsewhere).


  I&#8217;m completely new to Linux (so please keep jargon in your replies to a minimum), although I am currently researching the best options for a duel-boot setup with Windows. My main reason for wanting to try Linux is to get a feel for the different user interfaces that have been designed for desktop PCs. However, to keep bloat to a minimum, I only really want to install one Linux operating system, which I hope can be customised to demonstrate many different user interfaces.


  My plan is this (please correct me if I get any descriptions about features or technologies confused!):
[COLOR=White],[/COLOR]
              
[LIST=1]
[*]I shall await the first stable release of Ubuntu 11 and install it as my Linux distribution of choice. This should allow me to experience the Unity interface and the Compiz Fusion effects right out of the box.
[COLOR=White],[/COLOR]
[*]Ubuntu 10 had a &#8216;Sessions&#8217; menu on the login screen which would allow the user to log into the desktop with varying interfaces. I use this word loosely, because I do not know how customisable a &#8216;Session&#8217; is. In other words, might I assume that I can create sessions with specific desktop environments, themes, and/or start-up applications? Anyway, I hope that this &#8216;Sessions&#8217; feature exists similarly in Ubuntu 11.
[COLOR=White],[/COLOR]
[*]I then hope to install a KDE 4.6 desktop environment as a separate &#8216;session&#8217;, in much the same way as I know is possible in Ubuntu 10.
[COLOR=White],[/COLOR]
[*]I then hope to somehow install the Gnome 3 Shell interface as a third session.
[COLOR=White],[/COLOR]
[*]As a fourth session, I would like to prepare a desktop that looks similar to Gnome 2, which may be a direct install, or possibly a stripped-down version of Gnome 3,... although I don&#8217;t know if either is possible.
[COLOR=White],[/COLOR]
[*]Next I would like to create a session to mimic Mac OS X using Mac4Lin and other similar applications. I do not know what interface could be used as the basis of this &#8211; but I know people have had success on Ubuntu 10&#8217;s default environment.
[COLOR=White],[/COLOR]
[*]Finally, and this need not be a &#8216;session&#8217; per se, I would like to install the menu from Linux Mint (possibly in the Gnome 2 session).
[COLOR=White],[/COLOR]
[/LIST]
  Now then, only my question remains: How might I achieve this setup? Or more to the point: is this setup actually possible? (I can quiz you all about the installation details later if necessary).


  Many thanks!

---

### Post by dabl on 2011-02-22
While it is possible to install every DE supported by *buntu, if your only goal is to evaluate them and then select the one you like, doing the full installation seems like a waste of space and time.  Just make a Live CD of each, and run that on your computer, and do your evaluation that way.  Then you only have to install the one you like.  You'll make 4 Live CDs:

Ubuntu/Unity
Kubuntu
Ubuntu/Gnome
Xubuntu

Pick the one you like, and you're ready to install it.

---

### Post by malspa on 2011-02-22
Everybody's got their own approach. Mine was to keep Windows on a separate computer. As it turned out, I quit using Windows and gave that computer away. On my Linux computer, I have several distros installed. In most of those distros, I have two or three different desktop environments and/or window managers installed. Each time I boot up, I log into a different distro, and I usually don't log into the same DE or WM twice in a row.

This gives me a feel for different distros, different DEs/WMs, and also I feel like it has helped me learn a lot about Linux, just by comparing different things.

Not saying that I'm recommending this approach, just that it fits me. Maybe I just have a strange idea of "fun." I also feel that multi-booting all Linux is a lot easier than having Windows in the set-up. Just seems like things went a lot better for me once I decided to take Windows out of my multi-boot set-up and keep it on its own machine.

---

### Post by Copper Bezel on 2011-02-22
> While it is possible to install every DE supported by *buntu, if your only goal is to evaluate them and then select the one you like, doing the full installation seems like a waste of space and time. Just make a Live CD of each, and run that on your computer, and do your evaluation that way. Then you only have to install the one you like. You'll make 4 Live CDs:

He wants to play with some of these other installable options that a live CD wouldn't support, though. And Unity, Gnome Shell, and a standard Gnome desktop with Mac4Lin's tweaks wouldn't cause any conflicts so long as they were in separate user profiles, because they're all running on the same Gnome.

---

### Post by __Sun__ on 2011-02-23
I have done something similar to what you wish to achieve. Though, your aim goes beyond what I have done.

On my ubuntu (I am using the stable 10.4 Long Term Support release), I initially used what came with the setup. Then I decided to make the GUI similar to that of a Macintosh OS and installed Mac4lin which worked rather well.
I then tried the fast but graphically dull XFCE interface which, from my experience, was indeed quite fast.
Finally, I installed KDE which I am currently using. It is slower than the default GNOME and XFCE interfaces but the quality of software is better.

And indeed, I can choose at startup which session I wish to log into, GNOME, XFCE or KDE.
Mac4Lin is a theme and can be changed after startup.

There were some clashes betwixt GNOME's manager and XFCE's manager. So, from my experience, it would not be wise to install both at once.

I did not face any further problems and am rather please with my current KDE setup.

Simply type following command once you reach the stage where you are about to install KDE.

```

root@dhcppc1:~# apt-get install kubuntu-desktop koffice

```

The rest is easy too, except for installing Mac4Lin where you may have to read the entire documentation and install other pieces of software to complement it.

Best of luck.

---

### Post by Dark Owl on 2011-02-23
Thanks for your replies, although I'm not sure I've made my aims  absolutely clear. I am not interested in Live CDs or multi-booting  numerous different distributions of Linux, and it is also quite  important for me to have my desired Linux setup in a multi-boot with  Windows.

@Copper Bezel, you mentioned about having different  'profiles' for different Gnome variants. Is this the same as 'Sessions',  or might I assume that 'Sessions' allows the choice of desktop  environment (eg. Gnome or KDE), whilst 'profiles' allows the interface  to be customised? In this regard, is a 'profile' similar to a 'User  Account' in Windows?

If my assumption is correct then, and to extend upon @Copper Bezel's list, I desire:
A Gnome session with 5 profiles: 

[LIST]
[*]Unity,
[*]Gnome Shell,
[*]a standard Gnome desktop,
[*]a standard Gnome desktop with Mac4Lin's tweaks (and other Mac-like tools),
[*]a standard Gnome desktop with the Linux Mint menu 
(and other Linux Mint interface features if possible).
[/LIST]
and a standard KDE session.

However, do we know if Ubuntu 11 will feature 'Sessions' similarly to in Ubuntu 10?

Also,  (and I'm not too concerned about the technicalities just yet), are you  sure that there will be a way to get the 'standard Gnome desktop' on  Ubuntu 11 (which I understand is being built around Gnome 3)?

(As  an aside, am I correct to assume that a 'standard Gnome desktop' is  your description for the interface included as default in Ubuntu 10?)

@Sun, what is meant by GNOME's 'manager'? I also take it that KDE and Gnome sit peacefully side by side on your setup, right?

Ultimately,  I would simply like to know if such a setup will be possible. I  appreciate that definite answers cannot be given just yet  because several of the features I wish to implement are not yet stable  and/or ready for general release. But as more information surfaces,  please keep me informed - I am aiming to have the time to prepare and  experience this setup in July.

Many thanks!

---

