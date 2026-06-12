---
title: "My Time With Fedora 8"
date: 2007-11-17
forum: Fedora/RedHat and derivatives
---

### Post by Arthur Archnix on 2007-11-17
Well, I think I may be back for good. I used Fedora 8 for almost two weeks, and there was an awful lot that I liked about it. Ultimately though, I couldn't get past Fedora's package management system, which made tweaking my system more difficult than on Debian based systems. I also had font troubles (sidenote: If I had to compliment Gutsy Developers on just one thing, beautiful font rendering. No tweaking necessary), that were solveable, in theory.

What does Fedora have going for it right now?

1. Great default theme. I didn't even change it. Nice wallpaper. Icons. The default theme's colours are changeable. Just a great, great job. Kudos to the artwork team over there, you've set the bar high for the hardy crew.

2. The music mixer, pulse audio. One thing I miss in ubuntu from Vista is the ability to set sound volume individually per application. Fedora has that, and hopefully Hardy will too.

3. Great community. Anyone used to the great community here will feel right at home over there. 

4. Nice startup. Bit smoother and nicer than Ubuntu. Still does a few switches to black text, but it's definitely more polished.

Using their add/remove was onerous. That's it. It's not even Yum I was disliking, it was their gui frontend. And fonts. Anywho... time to look around and see what I've missed....

---

### Post by koleoptero on 2007-11-17
Thanks for the info Arthur. I was going to try fedora too but if the fonts don't look good then I'll skip. Font rendering was the reason I never stayed with linux before ubuntu (and the dreaded kernel panic message).

---

### Post by Incense on 2007-11-17
I've been playing with Fedora a bit on a VM, and so far I really like it. What about the package managment do you not like?

---

### Post by Arthur Archnix on 2007-11-17
@ Kolepetero: I'm not saying the fonts can't look at good, I'm certain they can. But on an lcd screen they won't look as good as ubuntu out of the box, and you'll need to translate instructions written for mandriva (which were based on instructions written for ubuntu) to do it.

@Incense: Well, anyone who has used Ubuntu's add/remove will be shocked to see something with the same name, but vastly different functioning in Fedora. Navigating it by category is quite difficult.

For example, I wanted to add openoffice and remove abiword. I opened add/remove. You have to make sure that "Office" has a check in it, if so, you can click on 'Options" which then takes you into a synaptic style layout. Now, you're essentially working in what looks somewhat like synaptic. Not very user friendly to the new person. But ok, I browse to openoffice, select writer, calc, and math and assume it will do the rest. Click apply. Head over to my main menu, and my office menu is gone. It's installed, but a reboot is required to get it into the menu. 

Then I removed what I always remove in Ubuntu, but there are two differences: It has different dependencies (ok, not a big deal), and it doesn't warn you as clearly that it is removing important stuff. So I removed all the evolution stuff, and in Ubuntu it warns you that you are removing Ubuntu-Desktop, which if you google tells you its just a metapackage and nothing to worry about. In Fedora it pops up a box listing (by package name) what you're adding/removing, then it does a dependency check, then it pops up a box that looks just like the one you just said ok to, but this one has all the dependencies that it's going to remove. You click on details to see what it wants to do, and it just lists package names again, and depending on what you're removing, loads and loads of package names. The first time I completely missed all of this an accidently removed gnome. :( The second time I was a little more cautious, but when I tried to add openoffice I also added something else (tetex maybe?) that installed half of all the kde apps in my menu.

Then there is the fact that it's a little slower than ubuntu's gui front-ends to apt, and a little more unpolished in the details. For instance, if you're working in the list tab and removing apps one at a time so you can check their dependencies it will kick you back to the category tab after removing an app. When you switch back to the list tab it takes a few seconds (5 or so) as it reloads the list. You need to reload the list every time you remove an app, thus discouraging you from removing one at a time.

Just a few of the reasons. I don't think this has anything to do with YUM, just its gui frontend. And perhaps there are fixes to this, alternate programs, but I just gave the default a spin and felt like the appearance reasons for switching and audio benefits weren't compelling enough to warrant investing the time in maxing out the potential of fedora's package management. Debian's got something that's really great already. Plus, another thread turned me on to the new clear-looks, which is really nice.

---

### Post by eljoeb on 2007-11-17
You did try yumex right?  Pirut is a bit junky.

---

### Post by ZuLuuuuuu on 2007-11-17
I also very like Fedora's artwork and "tried to try" Fedora 8 today but no luck, it couldn't be installed :( I tried the Live CD though and it looks really great. But I have font problem, too. Firefox's fonts are too small on my fedora machine and it cannot be fixed via the Firefox's preferences...

---

### Post by ButteBlues on 2007-11-17
> **ZuLuuuuuu said:**
> I also very like Fedora's artwork and "tried to try" Fedora 8 today but no luck, it couldn't be installed :( I tried the Live CD though and it looks really great. But I have font problem, too. Firefox's fonts are too small on my fedora machine and it cannot be fixed via the Firefox's preferences...
Firefox has a setting for minimum font size - which one needs to set to their preferences.

---

### Post by kona0197 on 2007-11-17
I think he was talking about the small text size of the pull down menu fonts. They should be controlled by the OS but I can't adjust them. I can hardly see them in F8 - very small.

---

### Post by ZuLuuuuuu on 2007-11-18
No, the web sites has small font size and I know the preference that you can adjust the font sizes but it does not work :) I tried Fedora 6-7-8 and they all have this problem for me...

---

### Post by RebounD11 on 2007-11-18
Weird ... My Firefox fonts were way too large the after install. BTW has anyone had any problems with Fedora's Network Manager or Firefox? For me NM couldn't connect (I think I fixed it but I'm afraid to reboot, I think it will break again), and Firefox refused to start until reinstalled, and the first start took about an hour... it updated something (even if it was 2.0.0.9 which I think it's the last version). Other than that great distro :D and so far it takes up the least amount of disk space, less than any other distro which I had with Gnome, KDE and Xfce4 installed.

---

### Post by serif on 2007-11-18
I installed Fedora 8 a few days ago and had different problems. My USB mouse connected via a hub, was detected during installation then, after system installed, mouse could be used up to log in, then was ignored. I could live with that, in the hope of a future bug fix. But then found that their new Pulse Audio system failed to detect my sound card - first failure after trying about 10 different Linux distros. That was too much, so back to Ubuntu. Still endure bug here with gnome-power-manager (have to launch it manually each time else Quit takes ages to work), but generally happy. I like the small touches that show how much thought has gone into the design, such as Add/Remove on main menu offering easy way to launch newly installed applications.

---

### Post by dasunst3r on 2007-11-18
I also tried Fedora 8 on a VM, and the first thing I noticed was how it would provide you with purchase options for the codecs.  Put nicely, that was something I was not used to especially when all I have to do is just *apt-get install ubuntu-restricted-extras*.

---

### Post by igknighted on 2007-11-18
> **dasunst3r said:**
> I also tried Fedora 8 on a VM, and the first thing I noticed was how it would provide you with purchase options for the codecs.  Put nicely, that was something I was not used to especially when all I have to do is just *apt-get install ubuntu-restricted-extras*.

This is also an option in Fedora, however the distribution will not package or point a user to anything (a) nonfree or (b) possibly patent encumbered from official sources.  Technically, to use the codecs fluendo provides you do need to pay for the license.  If you use the livna repositories or the freshrpms repositories (think of them as a mix between universe and medibuntu) you can get the codecs in the same ways as Ubuntu (w32codecs, libdvdcss, gstreamer-plugins-ugly, etc.).  But for legal and ethical/philosophical reasons the distro will not officially point users to these.

---

### Post by konungursvia on 2007-11-21
I also tried Fedora 8 for a week, hoping its reputation for laptop ease and SElinux would impress me. To be honest, I hadn't realized how lucky we were in the Debian-based world. Aptitude rocks, yum is feeble at best. I had a 55 package update right after installing. Great!     The same thing happens on most of my ubuntu installs... quite a few very recent updates. In Ubuntu with deb packages, I updated totally within an hour, probably half an hour, on a fairly slow broadband connection. With yum, it took me days. Even after the packages downloaded, it just sat there computing and calculating for about 12 hours, and you can't even tell from status bars or progress reports whether it is hanging, non responding or working! 

Also, the thing detected my Radeon 1200X series card, but wouldn't go above 1180x 700 or some weird resolution like that, no matter what I did to xorg, for six hours or so. 

I had had enough, Red Hat releases stuff that is not only bleeding edge, but soaking blood wet tampon edge.

Back to Ubuntu for good!

---

### Post by igknighted on 2007-11-22
> **konungursvia said:**
> I also tried Fedora 8 for a week, hoping its reputation for laptop ease and SElinux would impress me. To be honest, I hadn't realized how lucky we were in the Debian-based world. Aptitude rocks, yum is feeble at best. I had a 55 package update right after installing. Great!     The same thing happens on most of my ubuntu installs... quite a few very recent updates. In Ubuntu with deb packages, I updated totally within an hour, probably half an hour, on a fairly slow broadband connection. With yum, it took me days. Even after the packages downloaded, it just sat there computing and calculating for about 12 hours, and you can't even tell from status bars or progress reports whether it is hanging, non responding or working! 

Also, the thing detected my Radeon 1200X series card, but wouldn't go above 1180x 700 or some weird resolution like that, no matter what I did to xorg, for six hours or so. 

I had had enough, Red Hat releases stuff that is not only bleeding edge, but soaking blood wet tampon edge.

Back to Ubuntu for good!

Reputation for laptop ease?  Haha... I love fedora, it's my favorite distro.. but laptops tend to need more proprietary drivers and Fedora has none of them.  If anything, fedora is a poor choice for laptops unless you are willing to put in some work to set stuff up.

As for yum, it is actually a really good package manager,  Try installing the yum-presto and yum-fastestmirror packages.  This should speed it up a good deal.

What driver were you using for that card?  The avivo driver is rather poor, the radeonhd driver isn't ready yet, and the proprietary fglrx driver is only available through a third party repo like livna (or direct from ati).  Fedora actually does a great job setting up xorg automatically in almost all cases, so I am surprised by your troubles.  If I had to guess I would guess that it isn't properly detecting all your monitor's modelines.  Either that or the driver you are using isn't the right one.  If you still have the partition feel free to post your xorg.conf.

What is it with Ubuntu users these days?

---

### Post by RebounD11 on 2007-11-22
> **igknighted said:**
> What is it with Ubuntu users these days?

What do you mean?

---

### Post by igknighted on 2007-11-23
> **RebounD11 said:**
> What do you mean?

> **konungursvia said:**
> I also tried Fedora 8 for a week, hoping its reputation for laptop ease and SElinux would impress me. To be honest, I hadn't realized how lucky we were in the Debian-based world. Aptitude rocks, yum is feeble at best. I had a 55 package update right after installing. Great!     The same thing happens on most of my ubuntu installs... quite a few very recent updates. In Ubuntu with deb packages, I updated totally within an hour, probably half an hour, on a fairly slow broadband connection. With yum, it took me days. Even after the packages downloaded, it just sat there computing and calculating for about 12 hours, and you can't even tell from status bars or progress reports whether it is hanging, non responding or working! 

Also, the thing detected my Radeon 1200X series card, but wouldn't go above 1180x 700 or some weird resolution like that, no matter what I did to xorg, for six hours or so. 

I had had enough, Red Hat releases stuff that is not only bleeding edge, but soaking blood wet tampon edge.

Back to Ubuntu for good!

This is at least the 5th or 6th completely thoughtless rip on a distro I've seen this week (certainly not just Fedora).  The "other OS talk" used to be a great forum for discussing pro's and con's of all operating systems, but it's gotten out of hand recently.  The poster I quoted had some perfectly legitimate issues with Fedora.  But instead of either (a) asking for help, or (b) politely noting that Fedora wasn't for him/her, we got a rather grotesque slam that was quite unmerited.  The issues listed are simple fixes that are all of a sudden the end of the world?  Others have recently sworn off distro's for life because of similar issues.

Look, you can call me a fanboy of whatever distro the discussion happens to be on at the moment (I've been called a fanboy of Mandy, Fedora, Suse and many more... and I don't even use suse), but the truth is I love the discussion.  I get frustrated especially because this comes from linux users, who would turn around and tell windows users who are having similar issues adjusting to Ubuntu to learn the new OS before judging.  Fedora is indeed linux, but yum is a new program with its own ins and outs.  To expect it to work exactly like apt is naive.  They both have pro's and con's and excel in their own areas.

I don't care if people review a distro favorably or not, I just get frustrated by those vocal complainers who bash without understanding why, or judge the entire future worth of a distro on how well one release worked.  I find these types of posts to be damaging to good discussion, and popping up more and more frequently.

And yes, if you look back through all my posts I'm sure you will find one or two posts that might fit this mold (*cough* arch *cough*)... all we can do is try, we certainly have our weak moments.

---

### Post by pelle.k on 2007-11-23
> I don't care if people review a distro favorably or not, I just get frustrated by those vocal complainers who bash without understanding why, or judge the entire future worth of a distro on how well one release worked. I find these types of posts to be damaging to good discussion, and popping up more and more frequently.
+1

---

### Post by sophtpaw on 2007-11-23
[Conary]("http://wiki.rpath.com/wiki/Conary") ftw ! ! !

---

### Post by RebounD11 on 2007-11-23
I think it's in the nature of people to throw away something just because it's different from what they know and are used to.

Some of us can suppress that some can't... this is the main reason people don't give up Windows, because Linux is not like Windows. They have to get a major blow from their OS (my case with Windows) to switch (or at least give a fair chance) to another OS.

This is my opinion... please don't take it as an insult if you feel offended by it :D

---

### Post by apastuszak on 2007-11-27
Ok, just to chime in here....

I have Gutsy on a desktop at home and I had it on a laptop, but I had to take it off, and replace the laptop with Fedora 8.  I could not get suspend to work properly in Gutsy.  It worked out of the box in Fedora 8.

Also, I can't get Update Manager to work through an authenticated proxy.  Fedora happily tells me when there are software updates available in the Gnome Panel.

2 big pluses for me.

I too had issues with fonts but found this site, and now I am happy:

[http://www.bevenhall.se/jim/fedora-cleartype/](http://www.bevenhall.se/jim/fedora-cleartype/)

Overall, I am quite happy with yum.  I did cut my teeth on Red Hat 4, so I may be a bit prejudiced.  Both distros have their strengths and weaknesses.  I do wish Fedora 8 used sudo for everything, instead of root, the way ubuntu does...

Andy

---

### Post by igknighted on 2007-11-27
> **apastuszak said:**
> Overall, I am quite happy with yum.  I did cut my teeth on Red Hat 4, so I may be a bit prejudiced.  Both distros have their strengths and weaknesses.  I do wish Fedora 8 used sudo for everything, instead of root, the way ubuntu does...

Andy

Not sure that you can completely disable the root account, but you can easily "turn on" the sudo ability for your user.  Near the bottom of the /etc/sudoers file you can uncomment a line (its labeled) to enable the wheel group to run all commands and set env. variables.  Once you have uncommented this line, simply add your user to the wheel group, then log out and back in.  Now you can use sudo just like Ubuntu.

---

### Post by apastuszak on 2007-11-29
Yeah, that piece I know about.  The problem is that the gui based tools in the Applications menu all ask for Root's password and not your password.  That part would have to get rewritten.

I'm curious what it would take to make that happen.  Perhaps we could modify Fedora to give you an install option to either use sudo or use root for management.

Andy

---

### Post by igknighted on 2007-11-29
> **apastuszak said:**
> Yeah, that piece I know about.  The problem is that the gui based tools in the Applications menu all ask for Root's password and not your password.  That part would have to get rewritten.

I'm curious what it would take to make that happen.  Perhaps we could modify Fedora to give you an install option to either use sudo or use root for management.

Andy

All you would need to do is change the .desktop files I believe.  Instead of having the launch command as root, merely add a 'sudo' in front of it.  I don't think you would have to do any code re-writing per se.  And if you did, you would go to the srpms and make your change in the code, then rebuild and replace the originals.

How many apps are you having issues with?  The only thing I can think of is the nautilus "launch as root" feature.  And the yum-updatesd-helper, but I disable it because it always fails and ties up the yum lock until I manually kill it anyways ;).  I suppose pirut and/or yumex would as well.  But these could all be fixed by adding the sudo prefix to the launch command.

---

### Post by jfank on 2007-11-29
> **Arthur Archnix said:**
> Well, I think I may be back for good. I used Fedora 8 for almost two weeks, and there was an awful lot that I liked about it. Ultimately though, I couldn't get past Fedora's package management system, which made tweaking my system more difficult than on Debian based systems. I also had font troubles (sidenote: If I had to compliment Gutsy Developers on just one thing, beautiful font rendering. No tweaking necessary), that were solveable, in theory.

What does Fedora have going for it right now?

1. Great default theme. I didn't even change it. Nice wallpaper. Icons. The default theme's colours are changeable. Just a great, great job. Kudos to the artwork team over there, you've set the bar high for the hardy crew.

2. The music mixer, pulse audio. One thing I miss in ubuntu from Vista is the ability to set sound volume individually per application. Fedora has that, and hopefully Hardy will too.

3. Great community. Anyone used to the great community here will feel right at home over there. 

4. Nice startup. Bit smoother and nicer than Ubuntu. Still does a few switches to black text, but it's definitely more polished.

Using their add/remove was onerous. That's it. It's not even Yum I was disliking, it was their gui frontend. And fonts. Anywho... time to look around and see what I've missed....

I also used the newest version of Fedora, and I will say it was pretty nice.  The only problem is that the command script is different from Ubuntu, and I decided to stick with Kubuntu.  I do still have that newest version of Fedora on one of my other machines, but I'm just using that to learn Fedora, because I have so many friends that use Fedora.  KUBUNTU ALL THE WAY!!!

---

### Post by Lord Illidan on 2007-12-31
> **apastuszak said:**
> Ok, just to chime in here....

I have Gutsy on a desktop at home and I had it on a laptop, but I had to take it off, and replace the laptop with Fedora 8.  I could not get suspend to work properly in Gutsy.  It worked out of the box in Fedora 8.

Also, I can't get Update Manager to work through an authenticated proxy.  Fedora happily tells me when there are software updates available in the Gnome Panel.

2 big pluses for me.

I too had issues with fonts but found this site, and now I am happy:

[http://www.bevenhall.se/jim/fedora-cleartype/](http://www.bevenhall.se/jim/fedora-cleartype/)

Overall, I am quite happy with yum.  I did cut my teeth on Red Hat 4, so I may be a bit prejudiced.  Both distros have their strengths and weaknesses.  I do wish Fedora 8 used sudo for everything, instead of root, the way ubuntu does...

Andy

Hey, many thanks for suggesting that site. A lifesaver imho.

I am now on Fedora 8..I quite like it. Suspend/Hibernate works, which it didn't on Gutsy, and it's pretty fast/stable too.
Artwork, etc are all pretty nice. Nodoka theme looks great. Yum is also a nice tool, although it did seem a little slow to get packages. Pirut..hmm..well, it needs a lot of improvement. As for the codec-buddy, well, I don't like it at all. I am not a US resident, and I am not going to pay money for codecs which I can get for free. This site helped a lot : [The Unofficial Fedora FAQ]("http://www.fedorafaq.org/#unstable")

Otherwise, my other issues were regarding fonts..which are now solved, and I also mistakenly enabled development repos, and nearly broke my system as I was installing packages intended for FC9..but I solved that in the nick of time. Also, NetworkManager asks me for my password everytime, I think it's more GnomeKeyring nonsense..probably will end up installing wicd.

I think it's a great distro, you just have to wrap your head around it. Yum is a good packaging tool, shame about the frontend, though. IMHO, pirut needs a rewrite, it's slow, and doesn't show enough information when installing packages. Just a progress bar. Fedora Core 1 was my first foray into Linux, and F8 represents a substantial improvement. Thanks to Suspend/Hibernate working now..it might just replace Ubuntu for me.

---

### Post by pelle.k on 2007-12-31
> Also, NetworkManager asks me for my password everytime, I think it's more GnomeKeyring nonsense..probably will end up installing wicd.
[http://www.fedoraforum.org/forum/showthread.php?t=172877&highlight=networkmanager+gnome-keyring](http://www.fedoraforum.org/forum/showthread.php?t=172877&highlight=networkmanager+gnome-keyring)

---

### Post by Mateo on 2007-12-31
I'm using Fedora 8 right now and so far so good.  I'm really liking it.  I'm surprised that it is as different from ubuntu as it is.  I always thought that Gnome is Gnome no matter what OS you're using, but this is a little different.  For example, nautilus doesn't have the Back, Forward, Home, Computer, buttons.  Which is odd. I'll have to find some way to fix that.

I agree that the default fonts are undesirable.  they are too small I think.  That's definitely going to be one of the first things I fix.

I was quite surprised that on my ATI Radeon, Desktop Effects "just worked".  No endless tweaking like I had to do in Ubuntu.  No installing new drivers.  No searching through How-Tos trying to figure out what happened to my Desktops when cube is turned on.  I have to give the Fedora team for solving things for ATI users, who often feel left out in Linux.

One other thing that I loved about the installation process is that I didn't have to select when partition to use (i dual boot).  It just gave an option to overwrite the linux partitions and did everything for me, no input needed on my part.

I'm going to stay with Fedora 8 for now.

---

### Post by mthei on 2007-12-31
> **Mateo said:**
> I'm using Fedora 8 right now and so far so good.  I'm really liking it.  I'm surprised that it is as different from ubuntu as it is.  I always thought that Gnome is Gnome no matter what OS you're using, but this is a little different.  For example, nautilus doesn't have the Back, Forward, Home, Computer, buttons.  Which is odd. I'll have to find some way to fix that.

preferences > behaviour and then check "always open in browser window.

I thought the same thing at first, but now I kind of like it.


Also, I've been using Fedora for about a week, and I really like it. The only thing that bothers me is that in Ubuntu, there were some data DVDs that I had that would only mount via the command line, but here the command line won't even work for that. Although to be honest, I haven't been looking very hard for the solution, and I'm sure it's just a simple edit in my fstab.
I have already praised Fedora in another thread on this board, so I won't again.

---

