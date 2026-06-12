---
title: "Fedora 8"
date: 2007-10-30
forum: Fedora/RedHat and derivatives
---

### Post by _simon_ on 2007-10-30
I see Fedora 8 (Werewolf) is out in 9 days time.

Does anyone know if the Fedora 8 Test 3 DVD image has a live session?

---

### Post by igknighted on 2007-10-30
> **_simon_ said:**
> I see Fedora 8 (Werewolf) is out in 9 days time.

Does anyone know if the Fedora 8 Test 3 DVD image has a live session?

The DVD does not, you need the liveCD for that.

i686: [http://mirrors.usc.edu/pub/linux/distributions/fedora/linux/releases/test/7.92/Live/i686/Fedora-7.92-Live-i686.iso](http://mirrors.usc.edu/pub/linux/distributions/fedora/linux/releases/test/7.92/Live/i686/Fedora-7.92-Live-i686.iso)
x86_64: [http://mirrors.usc.edu/pub/linux/distributions/fedora/linux/releases/test/7.92/Live/x86_64/Fedora-7.92-Live-x86_64.iso](http://mirrors.usc.edu/pub/linux/distributions/fedora/linux/releases/test/7.92/Live/x86_64/Fedora-7.92-Live-x86_64.iso)

EDIT: You need to use the development branch of the livna repo if you want any non-free drivers.  Be aware that many packages only get new kmods every 4th kernel build, so use caution when upgrading and deciding what kernel to use.

---

### Post by Hairy_Palms on 2007-11-08
downloading fedora 8 final release now, about 15mins till its finished be the first fedora i tried since fc5, im hoping for improvements especially in the speed department. oh and the speed of yum.

---

### Post by Hairy_Palms on 2007-11-08
ok, i think fedora have screwed up their .iso files, there gnome live dvd is 768MB large, it refuses to burn to a CD becaue the disc is too small, but it refuses to burn to a dvd coz its not a dvd image, stupid fedora project :P great first impression. and it wont boot in vmware :/

---

### Post by ukripper on 2007-11-08
> **Hairy_Palms said:**
> ok, i think fedora have screwed up their .iso files, there gnome live dvd is 768MB large, it refuses to burn to a CD becaue the disc is too small, but it refuses to burn to a dvd coz its not a dvd image, stupid fedora project :P great first impression. and it wont boot in vmware :/

lol what fedora were expecting, miracle from 700MB CD!

---

### Post by igknighted on 2007-11-08
> **Hairy_Palms said:**
> ok, i think fedora have screwed up their .iso files, there gnome live dvd is 768MB large, it refuses to burn to a CD becaue the disc is too small, but it refuses to burn to a dvd coz its not a dvd image, stupid fedora project :P great first impression. and it wont boot in vmware :/

What?  A disk image is a disk image, you can burn any sub 700mb image to a DVD.  There's not really a distinction.  Also, I'm getting the ISO sizes in the high 690mb's.  It's burning to a CD with no issues.  Are you using the x86_64 images?  Both Gnome and KDE i686 images are small enough for CD, but I haven't looked at the 64bit ones.

Interesting about VMWare.  I'll try it out and see when I've finished d/l.  At 26% right now (20 min...).

EDIT: Ahh, the 64bit images are large.  DVD it is for them I suppose.

---

### Post by pirast on 2007-11-08
> You need to use the development branch of the livna repo if you want any non-free drivers. Be aware that many packages only get new kmods every 4th kernel build, so use caution when upgrading and deciding what kernel to use.

Huh? Yum prevents your kernel from being updated if there is no kmod package for that kernel in the Livna repository. Also, Livna builds kmods for every kernel update. I never experienced that they left out 4 versions.

> 
ok, i think fedora have screwed up their .iso files, there gnome live dvd is 768MB large, it refuses to burn to a CD becaue the disc is too small, but it refuses to burn to a dvd coz its not a dvd image, stupid fedora project :P great first impression. and it wont boot in vmware :/

Depends on the application you use to burn the images. When a friend of mine tried to burn Ubuntu's .isos using Nero, it also said that they were too big. When burning using "Burn CD/DVD" in Gnome, it worked fine with the same computer.

I am very pleased with Fedora, switched from Ubuntu to it after the release of Fedora 7.

---

### Post by new2*buntu on 2007-11-08
Downloading Fedora 8 Live now. Their non-torrent mirror must be swamped, dl speeds are at 5 kbps, but the torrent is good. Right now downloading at 150 kbps...

---

### Post by Arthur Archnix on 2007-11-08
Downloading now... just from the webpage I gotta say, I like the usplash. Looking forward to comparing it to my Feist/Gutsy experience.

---

### Post by new2*buntu on 2007-11-08
the screenshots do look nice.

---

### Post by igknighted on 2007-11-08
> **new2*buntu said:**
> Downloading Fedora 8 Live now. Their non-torrent mirror must be swamped, dl speeds are at 5 kbps, but the torrent is good. Right now downloading at 150 kbps...

I'm getting 500 k/s from the mirror right now... use the link to see all the mirrors, then try to find one close to you.  I am using linux.nssl.noaa.gov right now.

---

### Post by new2*buntu on 2007-11-08
now it is at 80% 255 KBps :)
> **igknighted said:**
> I'm getting 500 k/s from the mirror right now... use the link to see all the mirrors, then try to find one close to you.  I am using <edited until my download is done ;)> right now.
I am using a wireless network on my laptop so it doesn't have very high speeds, but 250 k/s is good enough for me.
Well as I am waiting I will post this screenshot:

---

### Post by karellen on 2007-11-08
done. finished downloading. now the interesting part will come. if I like what I see, I'll probably use fedora 8 as my main desktop os

---

### Post by Arthur Archnix on 2007-11-08
I made a mistake my first time through and didn't let fedora install a bootloader. It's easier if you do, unless you feel like adding the fedora one manually.

Typing from Fedora now. First Impressions:

1. Slick. Just a beautiful usplash, login theme, and default theme. Icons, mouse, it all just has a very polished feel. Surprisingly though, Gutsy has a smoother overall transition from power on to the desktop. More time is spent looking at text, and more switches seem to be made with Fedora. You know what was really nice though, was discovering a nice selection of good looking wallpapers that all kind go with the default theme.

2. Strange having to use root account and set it up during install. First thing I'm going to look into is setting up sudo (if it's not already). Also, even though it detected everything perfectly (as did Ubuntu) I'm going to have to install the pam-keyring manager to prevent having to enter my keyring password to connect to my wireless every login (as I did with Feisty, but Gutsy took care of that for me). 

Edit: 2.5 Almost forgot, when installing, I chose advanced options for grub and it gave me the option of disabling ipv6 support on boot for both my devices. Superb!

3. Too soon to say much more other than, give it a try if you have some spare time. It installs real fast from the live cd, about 10 minutes on my dual core with 1 gb ram.

4. As I write this I realized, it's quieter than ubuntu. Could be a kernel thing, but my laptop fan isn't running as much or as loudly when browsing the internet.

---

### Post by igknighted on 2007-11-08
> **Arthur Archnix said:**
> I made a mistake my first time through and didn't let fedora install a bootloader. It's easier if you do, unless you feel like adding the fedora one manually.

Typing from Fedora now. First Impressions:

1. Slick. Just a beautiful usplash, login theme, and default theme. Icons, mouse, it all just has a very polished feel. Surprisingly though, Gutsy has a smoother overall transition from power on to the desktop. More time is spent looking at text, and more switches seem to be made with Fedora. You know what was really nice though, was discovering a nice selection of good looking wallpapers that all kind go with the default theme.

2. Strange having to use root account and set it up during install. First thing I'm going to look into is setting up sudo (if it's not already). Also, even though it detected everything perfectly (as did Ubuntu) I'm going to have to install the pam-keyring manager to prevent having to enter my keyring password to connect to my wireless every login (as I did with Feisty, but Gutsy took care of that for me). 

3. Too soon to say much more other than, give it a try if you have some spare time. It installs real fast from the live cd, about 10 minutes on my dual core with 1 gb ram.

4. As I write this I realized, it's quieter than ubuntu. Could be a kernel thing, but my laptop fan isn't running as much or as loudly when browsing the internet.

1) Technically, it's rhgb, not usplash.  Usplash is "ubuntu splash", which is an Ubuntu thing.  Rhgb is "red hat graphical boot", the fedora equivalent.  They actually work very differently.  If you notice, the Fedora bootsplash actually is loading an xserver, which is why you see text until it gets to the point it can load that.  This is something that is being worked on.

2) Just add your user in /etc/sudoers.  It works very well.  Actually, the best way is to make sure that the group "wheel" can use sudo powers, then add yourself to "wheel".

3) Indeed, fastest install I have done.

4) I believe it is the tickless kernel.  The kernel doesn't send requests to the processor unless it has to, so it cuts down on the work your cpu does.  I don't entirely understand it myself, but it's supposed to be one of F8's big features.

---

### Post by mivo on 2007-11-09
> **Hairy_Palms said:**
> ok, i think fedora have screwed up their .iso files, there gnome live dvd is 768MB large, it refuses to burn to a CD becaue the disc is too small, but it refuses to burn to a dvd coz its not a dvd image, stupid fedora project :P great first impression. and it wont boot in vmware :/

The 64-bit Live versions only fit on DVDs. It's not a bug, and was the same for Fedora 7. You can burn the ISO on a DVD just fine -- worked for me. It does not have to be a 4 GB+ large. :)

---

### Post by Arthur Archnix on 2007-11-09
Anyone else just lovin' their fedora experience?

I've tried Debian, Slack, Arch, and Ubuntu. Slack and Arch were too advanced for me. Debian was doable, I just didn't 'feel' the fit. Fedora has been an interesting experience so far.

Not that I'm going to drop the buntu, but so far I think Fedora has earned its way onto my third partition (Vista, you slacker).

---

### Post by P4man on 2007-11-09
Downloading it as well now. Never tried any other distribution besides Ubuntu (and red hat half a decade ago). It looks nice, and I hope it solves some of my problems with my notebook

---

### Post by Phil Airtime on 2007-11-09
The release notes say that only the i686 live CD will actually fit on a CD. It gives instructions on how to transfer the ISO to your hard disc from a USB stick, which might be an option for anyone running on 64-bit. I've downloaded it (thank you, fast work network) and I'll be trying it out later or at the weekend. Wish me luck!

---

### Post by P4man on 2007-11-09
Question: can I easily install Fedora alongside Ubuntu  (assuming I prepare the partitions correctly) ?
Will grub give me the choice between both ? 
Can both distro's share the same swap partition ?

---

### Post by rsambuca on 2007-11-09
> **P4man said:**
> Question: can I easily install Fedora alongside Ubuntu  (assuming I prepare the partitions correctly) ?
Will grub give me the choice between both ? 
Can both distro's share the same swap partition ?

Yes
Yes (although you may have to manually edit the grub menu.lst
Yes

---

### Post by MellonCollie on 2007-11-09
Fedora 8 is very slick, and very lovely indeed. :) My only complaint is that, yet again, font rendering seems to be worse out-of-the-box in comparison to Ubuntu; could someone more knowledgeable take a guess as to why this might be?

Weak looking, smudged fonts on F8
[[IMG]http://img130.imageshack.us/img130/6262/fedora2xu7.th.png[/IMG]](http://img130.imageshack.us/my.php?image=fedora2xu7.png)


7.10 comparison
[[IMG]http://img80.imageshack.us/img80/8436/ubuntu2wj9.th.png[/IMG]](http://img80.imageshack.us/my.php?image=ubuntu2wj9.png)


Edit: After doing a little sniffing around, it seems that the difference is due to Ubuntu having the bytecode interpreter enabled by default, whereas Fedora doesn't.

Edit2: I didn't realise that Fedora's DPI is set to 90 by default. Upping it to 96 improves things, but rendering still isn't as good as 7.10

---

### Post by graphicsdude on 2007-11-09
Hey, I don't no if anyone else has noticed this?
I have Ubuntu 7.4, Win XP and currently trying Fedora 8 on a third part.
Fedora 8 is pretty, but noticeably slower than Ubuntu 7.4 or 7.10 for that matter.  Win is a joke, speed wise, of course...!

---

### Post by mivo on 2007-11-09
It wasn't slower for me, ran really well actually, but I had the same font rendering problem that MellonCollie mentioned (in 1680x1050 too). I spent a couple days trying to fix it, even copied over files from Ubuntu, but I never got the fonts to look as clear, sharp and crisp as in Ubuntu.

---

### Post by Hairy_Palms on 2007-11-10
its just as fast as ubunut here, im really liking it, especially as gutsy was so dissappointing for me, you may well not see me using ubuntu again till hardy tribes start coming out, but one problem i would still like to know, why is pirut/yumex/yum so ******* SLOW! seriously its a joke, anyone know anything i can do to speed it up? (noone mention apt4rpm, i kindof like my system non-broken)

---

### Post by Antman on 2007-11-10
Oh well, I gave F8 a try today. I'm not really that impressed. Pirut seems slower than Opensuse's Yast. Also I had Firefox crash twice on me while browsing sites I can browse fine in other distros. Also some other minor annoyances I had to get around.

I'll stick with Opensuse and Sidux on my machines for now.

---

### Post by igknighted on 2007-11-10
> **Antman said:**
> Oh well, I gave F8 a try today. I'm not really that impressed. Pirut seems slower than Opensuse's Yast. Also I had Firefox crash twice on me while browsing sites I can browse fine in other distros. Also some other minor annoyances I had to get around.

I'll stick with Opensuse and Sidux on my machines for now.

I don't know why pirut is default, it's just a bad app.  Try yumex instead.  Or just call yum from the command line.  It's a really great package manager when used that way.  Slightly slower than apt (it's default behavior is to update the repo's each time, for example), but much much faster than zypper or the yast tools in suse.  Of course, apt and smart are available to handle package management as well.  But yum via the CLI seems best to me.

@ whoever was wondering about fonts.

First, I don't see a noticable difference in the fonts in your pictures.  Honestly if you asked me which font rendering I preferred, I would lean towards Fedora's.  If you want to adjust it, I would try turning up the font anti-aliasing in the gconf-editor.  Turn grayscale to rgba and turn hinting from medium to full.

---

### Post by ButteBlues on 2007-11-10
> **Antman said:**
> Oh well, I gave F8 a try today. I'm not really that impressed. Pirut seems slower than Opensuse's Yast. Also I had Firefox crash twice on me while browsing sites I can browse fine in other distros. Also some other minor annoyances I had to get around.

I'll stick with Opensuse and Sidux on my machines for now.
The GUI front-ends always suck.

Command-line YUM is quite nice.

---

### Post by Antman on 2007-11-10
> **ButteBlues said:**
> The GUI front-ends always suck.

Command-line YUM is quite nice.

Yeah, after trying Pirut I just used Yum instead. I could live with Yum, but the firefox crashing was getting on my nerves. I guess I could have tried reinstalling it.:-k

---

### Post by foxmulder881 on 2007-11-10
> **new2*buntu said:**
> the screenshots do look nice.

Hehe, the screenshots for Fedora always look great, but unfortunately, imo, the actual release never performs as good as it looks.

---

### Post by foxmulder881 on 2007-11-10
> **MellonCollie said:**
> Fedora 8 is very slick, and very lovely indeed. :) My only complaint is that, yet again, font rendering seems to be worse out-of-the-box in comparison to Ubuntu; could someone more knowledgeable take a guess as to why this might be?

Weak looking, smudged fonts on F8
[[IMG]http://img130.imageshack.us/img130/6262/fedora2xu7.th.png[/IMG]](http://img130.imageshack.us/my.php?image=fedora2xu7.png)


7.10 comparison
[[IMG]http://img80.imageshack.us/img80/8436/ubuntu2wj9.th.png[/IMG]](http://img80.imageshack.us/my.php?image=ubuntu2wj9.png)


Edit: After doing a little sniffing around, it seems that the difference is due to Ubuntu having the bytecode interpreter enabled by default, whereas Fedora doesn't.

Edit2: I didn't realise that Fedora's DPI is set to 90 by default. Upping it to 96 improves things, but rendering still isn't as good as 7.10

Whether it's me or not, but the fonts on your Fedora screenshot looked fine to me. In fact, they looked sharper than your Ubuntu screenshot.

---

### Post by mivo on 2007-11-10
> **foxmulder881 said:**
> Whether it's me or not, but the fonts on your Fedora screenshot looked fine to me. In fact, they looked sharper than your Ubuntu screenshot.

Heh. :) I think when it comes to fonts, it is mostly a matter of personal preference and taste. I agree with him/her that the fonts in Fedora seem worse (I actually had trouble doing email in Fedora because the font rendering gave me a headache), but to others they seem not only fine but even superior.

What puzzles me still is that even though I had identical settings (both in gconf and in various other places), fonts in Ubuntu looked crisper and better to me (or at least "different").

---

### Post by Colro on 2007-11-10
Other then a much nicer default theme (I'm a blue/silver lover) I find gutsy to be a more polished OS. Fedora 8 seems to be slower overall for me.

---

### Post by foxmulder881 on 2007-11-10
> **mivo said:**
> Heh. :) I think when it comes to fonts, it is mostly a matter of personal preference and taste. I agree with him/her that the fonts in Fedora seem worse (I actually had trouble doing email in Fedora because the font rendering gave me a headache), but to others they seem not only fine but even superior.

What puzzles me still is that even though I had identical settings (both in gconf and in various other places), fonts in Ubuntu looked crisper and better to me (or at least "different").

I think I'll download it and run the live CD and see for myself.

---

### Post by foxmulder881 on 2007-11-11
Ok, this is really annoying me how you think that the font is clearer in Ubuntu over Fedora.

I've zoomed in on your screen shots. And the font rendering in Fedora is clearly, well, clearer than that of Ubuntu!

See for yourself...

Fedora
[IMG]http://img.techpowerup.org/071111/Screenshot-2.png[/IMG]

Ubuntu
[IMG]http://img.techpowerup.org/071111/Screenshot-3.png[/IMG]

---

### Post by mivo on 2007-11-11
> **foxmulder881 said:**
> Ok, this is really annoying me how you think that the font is clearer in Ubuntu over Fedora.

Well, it didn't look like this on my machine. Video card is a 8800GTS, monitor a NEC LCD225WXM (22", 1680x1050). I agree that in your screenshots the fonts are really nice in Fedora. :)

---

### Post by foxmulder881 on 2007-11-11
Probably depends a lot on the vid card and display combination.

---

### Post by asimon on 2007-11-11
> **MellonCollie said:**
> 
Edit: After doing a little sniffing around, it seems that the difference is due to Ubuntu having the bytecode interpreter enabled by default, whereas Fedora doesn't.
You can find a freetype package with bytecode interpreter enabled in the livna repository, IIRC it's called freetype-freeworld or something like that.

But even with this, Fedora still has problems with the bold default font. Non-bold fonts look at least as crisp as with Ubuntu (well, for my eyes at least), but bold fonts look 'smeared'.

---

### Post by screaminj3sus on 2007-11-11
> **foxmulder881 said:**
> Whether it's me or not, but the fonts on your Fedora screenshot looked fine to me. In fact, they looked sharper than your Ubuntu screenshot.

On an LCD they look way too sharp and spindly, the way ubuntu does it is more like windows, and IMO it looks so much more soothing to the eyes and easier to read then fedora's sharp spindly fonts, fedora's fonts are also spaced strangely.

---

### Post by pirast on 2007-11-11
I tried the freetype-freeworld package and I have to say that I find the fonts shipped with Fedora my default much better to the eyes.

---

### Post by karellen on 2007-11-11
I liked the fonts in fedora 7 much more than those of ubuntu. in fact, it was the only distro I didn't feel the need to adjust the fonts

---

### Post by ButteBlues on 2007-11-11
> **karellen said:**
> I liked the fonts in fedora 7 much more than those of ubuntu. in fact, it was the only distro I didn't feel the need to adjust the fonts
Ditto.

---

### Post by punkybouy on 2007-11-11
And why are we talking about Fedora on the Ubuntu site/

---

### Post by igknighted on 2007-11-11
> **punkybouy said:**
> And why are we talking about Fedora on the Ubuntu site/

Because lots of Ubuntu users like to try other distro's, and then discuss them with the people they know.  Oh yeah, and because this is the Fedora/Red Hat board at ubuntuforums.org.

---

