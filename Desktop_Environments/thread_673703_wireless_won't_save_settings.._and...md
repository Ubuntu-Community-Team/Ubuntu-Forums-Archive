---
title: "wireless won't save settings.. and.."
date: 2008-01-20
forum: Desktop Environments
---

### Post by deathguppie on 2008-01-20
hi, 

[COLOR=red][rant] [/COLOR]
[COLOR=DimGray][I]now I've been a long time linux user (since 96) so when I went out and bought an ubuntu based system from Dell I thought, **"hey I'll give Ubuntu a try.... and while I'm at I'll see if I can get used to Gnome"**  (Gnome was just getting started in 96, and KDE was already usable.. you stick with what works for you)

So it's been about 8 months, and I've learned to work around the fact that Gnome has about a third the functionality of KDE.  I've accepted the fact that Gnome takes way longer to start.. and that it is only marginally configurable.   I even learned to appreciate the built in setup utilities for some things under Ubuntu.  

That being said when some of the desktop widgets started disappearing for no apparent reason and then the file browser icons all turned into unreadable files, just before gnome locked up and I had to reboot the system to get it back.. hey you know it still kinda worked, and to tell you the truth I installed KDE under Ubuntu and it had it's own problems.. 

The fact is the system itself seems odd sometimes.. [FONT=Tahoma]why peoples political agenda has become so important that they make the system a wretched pain in the rear to use sometimes is beyond me.[/FONT]  After finally allowing some at least remedially easy way to install an nvidia driver the actual module is so obfuscated that from the system that you literally have to scour the entire system tracking down file after file to understand how they get the damn module loaded into the kernel in the first place.  Well of course one might claim that there would be no need for that, and I would agree except for the fact that if you needed to do some sound work for some video editing you were doing, you might need a realtime kernel, and you might not want to have to edit your xorg.config file every time you boot.  Seeing as there is no nvidia module available in the repositories for the rt-kernel. (all other kernels fail the jack test)  Well of course the sound driver, and the wireless modules were an entirely different pain but at least you could put the modules in a sane place and expect them to load.  Not so with nvidia.. no because it is a proprietary driver someone has decided to punish every ubuntu user who needs it.  I'm not even going to get started with decss.. 

Well thats all well and good.. so here I am with ton's of time vested into this system to try to get it working, and putting up with all of it's little quirks and inconsistencies.. and along comes something that really make me blow steam out my ears.[/I].[/COLOR] :mad:
[COLOR=Red][/rant][COLOR=Black]

Ok, so now the gnome network manager will not automatically set up my wireless card anymore. (it worked for months fine)  A really basic.. 

[/COLOR][/COLOR] [COLOR=Magenta]Ethernet controller: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)

[COLOR=Black]... not such a big deal right?

Right, the driver works fine, everything seems to work fine except for gnome network manager.  The weird thing is that if I boot into one of my unusable kernels that does not have the driver for the card.. then boot back into my regular kernel (generic) then I can reconfigure the network manager that has now lost my wpa passwd and it will work.  I don't know why.. 

Reboot (after a few days when Gnome starts to disintegrate) and I lose my network all over again.

[COLOR=Red][rant_continued][/COLOR]
[COLOR=DimGray]* .. and I really don't think that any one here will be able to help me.  I'm just posting because I've earned it.  I've dealt with more issues with Ubuntu than a newb has using Gentoo!!..  (I've used Gentoo.. I know .. )  Some of these issues are cause simply by the way Ubuntu is put together.. just for political reasons at the cost of the user experience (codecs to be precise), and don't give me that crap about legal issues.. there are plenty of other distro's out there that leave a nice easy path to the needed codecs.  Without whining or penalizing the user.  Hell it is easier to get a dvd playing with Xine in Suse, Mandriva, or Red Hat for that matter... That is without having Gnome screensaver throwing an exception and go into powersaving mode turning the screen black every ten minutes while trying to watch a movie.*[/COLOR]
[COLOR=Red][/rant_continued]


[COLOR=Black]Well, I need to go now, I'm trying to get the system to see 4gigs of ram and now I need to reboot to see if the mem= parameter I put in menu.lst will do the trick, since even thought the kernel .config file shows the needed builtins, it still doesn't seem to see it.  Anyway, I won't have network for a while again as repeat all my steps to get it working as usual.. \\:D/[/COLOR]
[/COLOR] [/COLOR][/COLOR]

---

