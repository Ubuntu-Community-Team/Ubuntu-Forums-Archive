---
title: "Best way to stable system?"
date: 2005-05-16
forum: Desktop Environments
---

### Post by vicks on 2005-05-16
What method gives the most stable system: 1. kubuntu or 2. ubuntu+kde?  What is your experience?

---

### Post by philipacamaniac on 2005-05-16
Kubuntu uses the same package source, and is thus the same, as Ubuntu. The difference is that GNOME and any dependencies are not included, and KDE and some default settings are included instead.

If you install KDE in Ubuntu, you get the exact same setup, minus the Kubuntu default settings (which is a package itself). The default settings package only affects styles and a few setting tweaks. Won't affect performance or stability.

In other words, Kubuntu and Ubuntu+KDE are the same. From what I understand, anyway.

---

### Post by jeremy on 2005-05-17
I have tried it both ways, and in my case a fresh kubuntu install has proved to be more stable. Also my USB camera and scanner both worked immediately, in ubuntu/gnome they didn't work.

---

### Post by thecrimsonking on 2005-05-17
Installing Kubuntu = unstable system
Kubuntu + updates = unstable system
Kubuntu + updates + gnome = stable system
Ubuntu + apt-get KDE = stable system

I don't get it.

---

### Post by maruchan on 2005-05-17
> Installing Kubuntu = unstable system
Kubuntu + updates = unstable system

I think much of this is rumor. My system has been perfectly stable in these cases, and I think people who are calling it "unstable" are just new to Linux in general. At least, that's been my experience on IRC and in the forums.

Hope that helps.

---

### Post by thecrimsonking on 2005-05-17
My observations were from my personal experiences with Kubuntu and Ubuntu.
Kubuntu just isnt stable without also installing gnome.

And no, I am not new to linux.

---

### Post by Firetech on 2005-05-17
I think the best way is to install Ubuntu first and then kubuntu-desktop and kubuntu-default-settings. That way, I think you get past the kdelibs-data update bug which deletes all of your kde-settings.

---

### Post by DerekInGermany on 2005-05-17
I also tried the Kubuntu way first.(Installed numurous times) and always had problems.
Then I installed Ubuntu then added KDE and I couldn't be happier.  Best Linux distro IMHO.

Derek

---

### Post by Terracotta on 2005-05-17
If you first do a server install and then kubuntu-desktop you have the same result as first gnome and then KDE. There must be something wrong with the kubuntu-cd, in my case it was just nvidia-driver stuff :-).

Since the first time I installed kubuntu I did however notice a slight improvement every time I did it (which is about euhm :s 3 times  ](*,) ).
(for example: kynaptics open, which it did not, in the first install, some setup changes...) Yeah the folks of kubuntu are working hard :-).

---

### Post by thecrimsonking on 2005-05-17
I have installed K/Ubuntu on 3 different pc's with completely different configs.   With a total of 12 installs.

It just doesn't matter how much tweaking or updating I do, until gnome is installed i have an unstable system.

No there is nothing wrong with my Kubuntu cd.  

Kubuntu just does NOT work right without gnome installed.  That's my story and I am sticking to it.

And, I still don't get it.

---

### Post by ludi on 2005-05-17
Please, merge both distributions in just one.
More Cd's (3 at least), this turn our lives much more simple (dial up users).
I'm using KDE but I grabbed the Ubuntu (just to take a look at the new gnome version).

---

### Post by mknapp23 on 2005-05-18
[QUOTE=thecrimsonking]My observations were from my personal experiences with Kubuntu and Ubuntu.
Kubuntu just isnt stable without also installing gnome.

And no, I am not new to linux.[/QUOTE]

I installed kubuntu clean and it was as stable as a rock until I installed Gnome..then I got totally screwed up, had to re-install, now everything fine again.



--Baffle a Democrat with common sense--

---

### Post by lakcaj on 2005-05-18
As my first post, I would also like to pipe in how I would prefer that ubuntu and kubuntu merged into a single distro.  All that would be needed during the install process is "would you like gnome or KDE?".  The fact that there are currently two different distributions for the sake of two different desktops is silly.  Add to that the confusion expressed in this thread about the various ways to get to the same end, sometimes with differing results, again points towards a consolidation of efforts into a single distro with the _choice_ of KDE or gnome.

Well, that's my 0.02.


Thanks,


lakcaj

---

### Post by brenx on 2005-05-18
Ubuntu (server install) + apt-get install kubuntu-desktop worked fine 4 me.

---

### Post by philipacamaniac on 2005-05-18
[QUOTE=lakcaj]As my first post, I would also like to pipe in how I would prefer that ubuntu and kubuntu merged into a single distro.  All that would be needed during the install process is "would you like gnome or KDE?".  The fact that there are currently two different distributions for the sake of two different desktops is silly.  Add to that the confusion expressed in this thread about the various ways to get to the same end, sometimes with differing results, again points towards a consolidation of efforts into a single distro with the _choice_ of KDE or gnome.[/QUOTE]

Good idea.

However, the problem lies with the fact that if Canonical started shipping CDs with Gnome and KDE, and calling Ubuntu, they would then have to create an entirely different documentation set for KDE. (I understand that Kubuntu folks are working on  that). Then they would also have to provide official support for KDE (they include KDE in MAIN, but I don't believe official support is provided.)

Also, if you notice other distro's that include both (or used to), they always have at least 2 installation discs, because GNOME and KDE plus GNU/Linux won't fit on to one CD. I'm actually more supportive of the separate disc idea, like it is now, but they shouldn't be treated as 2 different distributions.

There is hope, I think, because the Kubuntu developers are involved with the Ubuntu process now. Jonathan Riddell (who should be paid by Canonical, I think) was at Ubuntu Down Under, and all of the planning sessions for Breezy included bits and pieces of KDE.

Ideally, you will get the same exact setup if you install kubuntu-desktop on Ubuntu or install Kubuntu. Likewise, you'll get the same exact setup if you install ubuntu-desktop on Kubuntu or install Ubuntu. Personally, I think that is exactly how it is right now, but some people apparently disagree.


Phil

---

### Post by Segovia on 2005-05-18
[QUOTE=thecrimsonking]Kubuntu just does NOT work right without gnome installed.  That's my story and I am sticking to it.

And, I still don't get it.[/QUOTE]
I don't get it either, but my experience also matches your claims.

---

### Post by philipacamaniac on 2005-05-18
[QUOTE=Segovia]I don't get it either, but my experience also matches your claims.[/QUOTE]

Perhaps you can elaborate? Is there a specific example of an application not working in KDE (Kubuntu) until you install GNOME?

---

### Post by thecrimsonking on 2005-05-18
[QUOTE=philipacamaniac]Perhaps you can elaborate? Is there a specific example of an application not working in KDE (Kubuntu) until you install GNOME?[/QUOTE]

In my case it is not apps as much as general system weirdness.

Menus would hang forever, konqueror would crash often, my taskbar would randomly rearrage itself.

Specifically I couldn't add ksysguard or weather report to my taskbar.  Also, many symlinks would break and shortcuts would just stop working.

Even weirder, kaffeine would never start.

After I installed gnome (and NOTHING else - no, not even kde updates) all these problems went away.

Yes, I downloaded a new kubuntu .iso, yes the md5 checked out.

---

### Post by philipacamaniac on 2005-05-18
[QUOTE=thecrimsonking]In my case it is not apps as much as general system weirdness.

Menus would hang forever, konqueror would crash often, my taskbar would randomly rearrage itself.

Specifically I couldn't add ksysguard or weather report to my taskbar.  Also, many symlinks would break and shortcuts would just stop working.

Even weirder, kaffeine would never start.

After I installed gnome (and NOTHING else - no, not even kde updates) all these problems went away.

Yes, I downloaded a new kubuntu .iso, yes the md5 checked out.[/QUOTE]

Well, that's no good - I'm glad my Kubuntu installation didn't turn out that way! :) Like I said previously, I installed from the Kubuntu CD with no problems (except for a Kaffeine CPU issue, which shows up regardless of installation method, and was easily  fixed with a new package). My Kubuntu is as stable as a rock.

---

### Post by maspro on 2005-05-20
I would also like to add my two cents:

Although I'm a KDE fan myself, it's my conclusion that Kubuntu isn't as stable as running Ubuntu all by itself. 

An example:

- playing divx movies in mplayer under Ubuntu works just fine, but in Kubuntu movies are really choppy. (I have both Gnome and KDE, so I'm not talking about separate installs)

- When running a KDE session and starting appz it frequently happens that I click an icon and then see a small icon jumping around, but then nothing happens, the program doesn't start, I get no error and re-clicking the icon doesn't help, sometimes a reboot solves the problem, only to repeat itself later on with an other program. 

- Gnome appears to be faster, while KDE sometimes reacts real sluggish. 

- Also some KDE specfic appz sometimes crash, such as Konqueror and Kaffeine.

So for the time being I'm going to stick with Gnome and only install some KDE appz, but not the KDE desktop itself. Gnome seems much more stable to me at the moment.

---

### Post by phantom on 2005-05-20
[QUOTE=maruchan]I think much of this is rumor. My system has been perfectly stable in these cases, and I think people who are calling it "unstable" are just new to Linux in general. At least, that's been my experience on IRC and in the forums.

Hope that helps.[/QUOTE]
 good info, I was wondering the same thing. I downloaded both the cd's to make sure.

I'm installing tommorow morning :D

---

### Post by maspro on 2005-05-20
[QUOTE=maruchan]I think much of this is rumor. My system has been perfectly stable in these cases, and I think people who are calling it "unstable" are just new to Linux in general. At least, that's been my experience on IRC and in the forums.

Hope that helps.[/QUOTE]
I find this argument a bit strange, if I install Kubuntu or Ubuntu+KDE and after doing nothing special or system critical, just playing some movies, running some appz and browsing around and during those things the system makes an unstable impression this in my opinion is wrong. A system should behave, look and feel stable regardless of who is using the computer, newcomer of not.

If there are however user-errors, in other words that it is the user his own fault, then that's a whole other story of course.  ;-)

---

### Post by Antonio Ricardo Correia on 2005-05-20
I tried to install Kubuntu with the instal CD several times. After rebooting it would crash everytime with a grey screen and a frozen mouse pointer. Apart from the bug of deleting /etc/kderc it would also refuse to update kdlibs4 saying it couldn't replace the file because it was needed by kdenetwork. Whatever I tried resulted in a frozen system after reboot.
I then installed Ubuntu, did the packages upgrade in synaptic and finally installed kde-desktop. Since then everything runs ok without a glitch and the the system is rock stable.
I'm not a novice either in Unix or Linux and in my humble opinion it's better to install it that way. Perhaps Kubuntu will install ok with different hardware, mine and a lot more as I can see don't.

PS - Going the way around (installing Kubuntu and then adding gnome) doesn't do the trick, I tried it. So I think that there is something else to it than just needing gnome to work ok.

Best regards,
Antonio

---

### Post by abhaysahai on 2005-06-03
I Tried installing ubuntu-desktop and on top of it installed kubuntu-desktop. Ofcource I had configured to use KDM instead of GDM. The system (X11) used to freeze very frequently. Uninstalling ubuntu-desktop, GDM etc did not help. I tried various updates -- no go. 
As I had only ubuntu install CD, so I choose the option suggested in this thread and installed Ubuntu server.  apt-get install kubuntu-desktop did the trick for me. 

Now all my media, USB device work properly and thanks god no more X11 freeze. 

Regards,
Abhay

---

### Post by Antonio Ricardo Correia on 2005-06-03
[QUOTE=Antonio Ricardo Correia]I tried to install Kubuntu with the instal CD several times. After rebooting it would crash everytime with a grey screen and a frozen mouse pointer. Apart from the bug of deleting /etc/kderc it would also refuse to update kdlibs4 saying it couldn't replace the file because it was needed by kdenetwork. Whatever I tried resulted in a frozen system after reboot.
I then installed Ubuntu, did the packages upgrade in synaptic and finally installed kde-desktop. Since then everything runs ok without a glitch and the the system is rock stable.
I'm not a novice either in Unix or Linux and in my humble opinion it's better to install it that way. Perhaps Kubuntu will install ok with different hardware, mine and a lot more as I can see don't.

PS - Going the way around (installing Kubuntu and then adding gnome) doesn't do the trick, I tried it. So I think that there is something else to it than just needing gnome to work ok.[/QUOTE]

I am glad it did work for you. I've read a lot about it not only in the English forum but also in the French one (though I am portuguese).
I've seen people installing Kubuntu directly and that have no problems but the large majority does have them, me included until I installed Ubuntu and evolved from that to Kubuntu. I also tried what you mention in your post script, going the way around, and like in your case it didn't work.
That said, I am not a Linux expert, it's my system of choice and having lived with Mandrake/Mandriva for a long time I did do the jump into Kubuntu for two main reasons. First, I don't like the way Mandrake deals with users that don't pay an heafty subscription in order to have access to software that is widely available for Debian based distributions. Second, the Limited edition 2005 destroyed my 10.1 instalation to such a degree that I had to re-install everything from scratch.
Now and though I still have Mandrake installed in one of the partitions I'm using Kubuntu every single day. I go to Mandrake when I try to figure out some of the config files (hardware related) that work well and I'm trying to fix Kubuntu shortcomings. Some things puzzle me, because for instance creating an /etc/modprobe.conf in order to make Kubuntu recognize my TV card destroyed all /dev audio related devices. Doing a MAKEDEV not only didn't solve the problem but also put the system in such a state that I had to re-install everything...
If I could have a word for a wish list, I really would like Kubuntu/Ubuntu to have the same kind of install Mandrake has, giving us the possibility of choosing our hardware during the installation procedure. I'm yet to get my webcam to work, what it does as a charm under Mandrake. No matter what I try with gnomemeeing I can't get an image.
I've also tried everything in order to install the smp kernels and it crashes the system every single time. The smp kernels allways worked with my pentium under Mandrake I wonder what's wrong with the ones under Ubuntu. ](*,) 

Best regards,
Antonio

---

### Post by jagguars on 2005-06-04
so no problems with kubuntu till now. the synaptic pakage manager is a pain in the ass and at k3b a pakage is missing but that are minor errors for me.

about the speed of kde i can't say anything, with my 2.6 GHz it works fast.

to the installation i want to mention that i prefer the DVD versions. i don't like to change the CD's if i install just one program, or operating systems or anything.  [-X  the combination of a live cd and the install cd on one dvd was great idea. 

mfg josef grohs

---

### Post by Takis on 2005-06-04
Firstly, about distributing both Gnome and KDE together - no no no no no! That's what Debian does, it ASKS you what you'd prefer as your desktop manager, and then never actually gets it working on its own.  ](*,)  ](*,)  ](*,) 

[QUOTE=maspro]
- When running a KDE session and starting appz it frequently happens that I click an icon and then see a small icon jumping around, but then nothing happens, the program doesn't start, I get no error and re-clicking the icon doesn't help, sometimes a reboot solves the problem, only to repeat itself later on with an other program. [/quote]
The application has crashed. The bouncing icon is simply a thing KDE does to show you that, yes, you clicked the button. It's actually faking feedback for 30 seconds (you can change this setting in Control Center->Appearance and Themes->Launch Feedback).

I dunno duders, I installed off a Kubuntu DVD and nothing's gone wrong with my system that I didn't cause myself.

---

### Post by johnprgr on 2005-06-07
Is it possible that installing ubuntu and then kde works because when installing kde that way it pulls in the updated kde packages with no other kde stuff in the way?  Just a theory.  As an additional point of interest, I used to use Mandriva and very often also had problems any time the package containing the kderc file was updated.  So I wouldn't necessarily blame kubuntu for 100% of the difficulty.

---

