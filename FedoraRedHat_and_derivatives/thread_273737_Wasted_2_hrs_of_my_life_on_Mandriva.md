---
title: "Wasted 2 hrs of my life on Mandriva"
date: 2006-10-08
forum: Fedora/RedHat and derivatives
---

### Post by Lord Illidan on 2006-10-08
I am in a freakin rage, guys.

I just tried out the new shiny Mandriva 2007 disk fresh from Linux Magazine.

Installation = nice install..very blueish. Way too many options. Couldn't install cups! EDIT : It also couldn't update because of some wierd error...even Edgy beta works with less bugs

Use = could not use soundcard, fm801 works by DEFAULT on Ubuntu, Debian, Suse, Fedora, Zenwalk...way nearly every distro out there. It found soundcard..but no sound could be heard..and before you ask, alsamixer was not muted.

First time round it failed to detect my mouse, I had to re-install. Ever tried using xorgconfig in mandriva? Apart from the fact that sudo does not work...it is totally useless. /dev/input/mouse didn't work = supposedly default device.

Reinstalled.

Installation full of crappy adverts that I didn't notice first time round. Then...mouse worked..sound did not..could not install cups...just noticed that grub was messed up..and had detected 2 WINDOWS partitions....and I have none btw.

At that stage, I cracked up, threw the DVD across the room and re-installed Ubuntu's grub. This is supposed to be a commercial quality distro??? Come on!!

---

### Post by meng on 2006-10-08
Seems you can rely on Mandriva for this sort of experience!

---

### Post by croak77 on 2006-10-08
/dev/input/mice instead of /mouse. Why couldn't you install cups? Was there no package available? Rpm problem?

---

### Post by rfruth on 2006-10-08
Doesn't sound like a waste to me, a big learning experience maybe, thanks for posting :mrgreen:

---

### Post by RAV TUX on 2006-10-08
> **rfruth said:**
> Doesn't sound like a waste to me, a big learning experience maybe, thanks for posting :mrgreen:

yes, agreed not a waste but a learning process.

---

### Post by coffeecat on 2006-10-09
I'm no fan of Mandriva, but two points:

I read on another forum that the version on the Linux Magazine disc is a pre-release one. The product.id file apparently shows:

> vendor=Mandriva, distribution=Mandriva
Linux, type=basic, version=2007.0, branch=cooker, release=0.6, arch=i586, product=Downloadwhereas on the release disc branch would be 'official' and release=1.1

That /dev/mouse /dev/input/mice thing - I've had that on a couple of other distros. I can't remember the details but it's a hangover from pre-udev days (??).

---

### Post by Lord Illidan on 2006-10-09
Ok..it could be a prerelease thing..but even Edgy is prerelease and it works v. well. You kinda expect more out of a commerical distributor.

About the /dev/mouse /dev/input mouse I just used what xorgconfig told me was default..which didn't work.

About cups..well it told me it couldn't be installed..no idea why..

learning experience? No...why would re-installing mandriva twice be a learning experience?? To learn to stay away from Mandriva, perhaps.

---

### Post by croak77 on 2006-10-09
Don't go by what xorgconfig says, you need to put in your info. xorgconfig does not guess all your hardware/setup. Xorg -configure will try to probe your hardware and auto generate your xorg.conf, but it's not always correct. 

There was no other error meesage with cups? No packages blocking install?

---

### Post by Lord Illidan on 2006-10-09
> **croak77 said:**
> Don't go by what xorgconfig says, you need to put in your info. xorgconfig does not guess your hardware/setup. Xorg -configure will try to probe your hardware and auto generate your xorg.conf, but it's not always correct.

There was no other error meesage with cups? No packages blocking install?

Can't really remember but AFAICR - it detected printer HP PSC 1110 (works on Ubuntu) and offered to install it- but couldn't install cups..I dunno why.

---

### Post by v1o on 2006-11-24
I had better luck with Mandriva One I could actually get on the Internet and it works with Nvidia cards. Ubuntu wont even recognise my network card.

---

### Post by Lord Illidan on 2006-11-24
> **v1o said:**
> I had better luck with Mandriva One I could actually get on the Internet and it works with Nvidia cards. Ubuntu wont even recognise my network card.
Each to his own...my experience was the exact opposite.

---

### Post by ComplexNumber on 2006-11-25
last night, i waster more than 2 hours on mandriva 2007. first install, it didn't even configure my mouse correctly so that i had no mouse. for the 2nd install, i changed it from"any usb & ps/2 mouse" to "generic ps/2 mouse", and it worked. the mandriva control centre annoys me because i have to click all over the place (i'm sure anyone who has used mandriva will know what i mean). 
rpmdrake is a nightmare to use because it will only list application under their headings(eg games, multimedia, documentation, etc) and there doesn't seem to be a way of seeing a complete list of the packages available without the headings. it never used to be like that. 
what on earth has happened to mandriva!? it used to be amongst the best. now its the crappiest, most buggy, and unuserfriendly(apart from ubuntu, gentoo, and slackware) out there.
after about 4 hours, i rebooted and installed pclinuxos back again. phew! 

as an aside, i tried simplymephis(again). it wouldn't see my sound card and i kept on getting dependency errors (ie deb dependency hell). simplymephis didn't last long on my hard drive.

---

### Post by Lord Illidan on 2006-11-25
> **ComplexNumber said:**
> last night, i waster more than 2 hours on mandriva 2007. first install, it didn't even configure my mouse correctly so that i had no mouse. for the 2nd install, i changed it from"any usb & ps/2 mouse" to "generic ps/2 mouse", and it worked. the mandriva control centre annoys me because i have to click all over the place (i'm sure anyone who has used mandriva will know what i mean). 
rpmdrake is a nightmare to use because it will only list application under their headings(eg games, multimedia, documentation, etc) and there doesn't seem to be a way of seeing a complete list of the packages available without the headings. it never used to be like that. 
what on earth has happened to mandriva!? it used to be amongst the best. now its the crappiest, most buggy, and unuserfriendly(apart from ubuntu, gentoo, and slackware) out there.
after about 4 hours, i rebooted and installed pclinuxos back again. phew! 

as an aside, i tried simplymephis(again). it wouldn't see my sound card and i kept on getting dependency errors (ie deb dependency hell). simplymephis didn't last long on my hard drive.

Ubuntu rules -oh well, that and Zenwalk!

---

### Post by dvarsam on 2006-12-15
Hello!

> **Lord Illidan said:**
> Ubuntu rules -oh well, that and Zenwalk!

And thanks for the info!

I was thinking of buying Mandriva just to support the whole Linux Project...

But after this experience of yours, I need to re-think & cancel my previous "intentions"...

Again, thanks for your Feedback!

P.S.> You know what is even worse:
It took me 5 days to download OpenSUSE v10.2 _DVD_ version!
I decided to download the DVD version, because the v10.1 _CDs_ could not install on my PC!
(I was getting huge errors & crashes...)
Only the v10.1 OpenSUSE _DVD_ could install on my PC successfully!
When I finally opened the download folder to look for the .iso _DVD_ file for OpenSUSE, I found 5 different .iso files instead (each of 600MB capacity) !!! (#$@%@^#@$&!#) ](*,) 
I guess you are Not the only one who is waisting his time trying out other Linux Distros...:D 
I hope that makes you feel better!

---

### Post by Lord Illidan on 2006-12-15
> **dvarsam said:**
> Hello!



And thanks for the info!

I was thinking of buying Mandriva just to support the whole Linux Project...

But after this experience of yours, I need to re-think & cancel my previous "intentions"...

Again, thanks for your Feedback!

P.S.> You know what is even worse:
It took me 5 days to download OpenSUSE v10.2 _DVD_ version!
I decided to download the DVD version, because the v10.1 _CDs_ could not install on my PC!
(I was getting huge errors & crashes...)
Only the v10.1 OpenSUSE _DVD_ could install on my PC successfully!
When I finally opened the download folder to look for the .iso _DVD_ file for OpenSUSE, I found 5 different .iso files instead (each of 600MB capacity) !!! (#$@%@^#@$&!#) ](*,) 
I guess you are Not the only one who is waisting his time trying out other Linux Distros...:D 
I hope that makes you feel better!

I also had a similar experience with OpenSuse 10.1.
I didn't download, it was on a LXF DVD.
Installation was nice, etc, etc.

But package manager sucked, and sucked hard. Not to mention that certain apps are crippled by default. I mean, synaptic is really really good in Ubuntu, and in Debian, why does YaST have to be so slow? Even Fedora which uses RPM is faster.

That, and dependency errors got me off it in 1 week.

---

### Post by Hendrixski on 2007-02-13
I just installed Mandriva 2007 as well.  I like how it comes installed with Compiz.  At least, if you selected XGL when you were booting the live CD.  I also like how the installer is easier on the surface, but always has advanced options so that you can get more control if you need it.  I don't like how many steps you have to go through during the installation.  But the install is fast :)

urpmi may take me a while to get used to.  At least it seems better than YaST, which is a royal pain.  I've been a Debian user for years, and never really bothered with RPM based package managers.   So ... yeah.

It looks like the commercial version comes with TONS of stuff, like a legal way to play DVD's!!! Courtesy of LinSpire.  I keep meaning to try out LinSpire as well.  Anyway, I'll post more when I've been trying it for a while.

---

### Post by 4KvRMU7Nnv on 2007-02-14
I agree whole-heartedly.  The original poster of this thread obviously had a skewed expierence with Mandriva 2007.  I installed "Mandriva 2007 One" and so far is at least as good as ubuntu in all areas.  In the areas where it isn't equal with ubuntu, it is better.  Everything was easily set up.  Compiz worked perfectly on the live cd as well as after it was installed.  Compiz in general works lots faster, and completely than it ever did for me on ubuntu.  All the things I used to need the terminal for come with a graphical interface in Mandriva which make it infinitly more easy to use.  Simplicity is not, however, restricting, as you can also work with the nitty-gritty details if you so please.  Overall,  I am impressed enough with this distrobution that I have favored it over my longstanding favorite, ubuntu.  I'm sorry the thread starter had such a bad experience but i would seriously reccomend that you download it from the site as opposed to using a magazine install cd as, like others have mentioned, it may have been a beta release or something like that.

---

### Post by justin whitaker on 2007-02-14
I wanted to support a commercial version of Linux, and remembering my fond early memories of Mandrake, I became a Silver Level Club Member. 

Mandriva uses the "metadistribution model" which means, lots of options: it is equally at home as a multimedia desktop, server, graphics or audio workstation, or a development environment. You choose at install, and after via urrpmi or the command center. 

What you get is a very polished system that overwhelms you a bit with the amount of tweaking you can do. It's not a bad thing: it just takes some getting used to. There are wizards for everything, which is great for neophytes....for me, Mandriva and Ubuntu are about on par: both are graphically right on, both have alot of packages available, both have issues with updating and with hardware. 

I would recommend that people avoid the pre-releases and go for the free One version...I prefer the PowerPack myself, which is stacked with goodies. :)

---

### Post by picpak on 2007-02-17
When I tried a couple years ago I used Mandrake 10.1. Then I tried 10.2...I dunno, it had way more bugs and was less user-friendly. And it's been getting worse ever since.

---

### Post by Skia_42 on 2007-03-01
I to tried to install Mandriva from the Linux World Magazine. Grub was messed up beyond belief and I had no way of getting back to my Ubuntu partition. Thankfully, when I deleted the partition my ubuntu grub menu showed up without issue. Does anyone know a good tutorial on editing grub menu's for multiple linux partitions manually?

---

### Post by rocknrolf77 on 2007-03-01
> **Skia_42 said:**
> I to tried to install Mandriva from the Linux World Magazine. Grub was messed up beyond belief and I had no way of getting back to my Ubuntu partition. Thankfully, when I deleted the partition my ubuntu grub menu showed up without issue. Does anyone know a good tutorial on editing grub menu's for multiple linux partitions manually?

Install ubuntu and it will fix your grub. :)  

Trying mandriva 2007 now. Oh , RPM H****  How I hate it. Trying to get firefox2. You are missing depency 1, 2, 3, 4. :mad: And adding sources takes forever. Once you "aptituded" rpm's suck. 

I'll try to hang on for a little while. At least I'm probably learning to stay away from rpm based distros forever. :)  

Aptitude :guitar:

---

### Post by igknighted on 2007-03-02
> **rocknrolf77 said:**
> Install ubuntu and it will fix your grub. :)  

Trying mandriva 2007 now. Oh , RPM H****  How I hate it. Trying to get firefox2. You are missing depency 1, 2, 3, 4. :mad: And adding sources takes forever. Once you "aptituded" rpm's suck. 

I'll try to hang on for a little while. At least I'm probably learning to stay away from rpm based distros forever. :)  

Aptitude :guitar:

I have never liked Mandriva's package management.  You know there is an apt4rpm that uses synaptic and apt-get, but deals soley with RPMs, right?  I know PCLOS (basically Mandriva) uses it as default, and many suse/fedora users use it as well.  I find Fedora's YUM tool to be quite up to the task... not quick, but does a better job than debians tools (no need for an 'apt-get update', it does it for me).  Suse's yast2 is very slow, but is also the most straightforward package tool.  Mandriva is an oddball, it seems to use older RPM tools, but in RPM distro's like Suse and Fedora the "RPM hell" that many remember is a thing of the past.

---

