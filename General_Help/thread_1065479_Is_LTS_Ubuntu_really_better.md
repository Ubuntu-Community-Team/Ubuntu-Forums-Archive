---
title: "Is LTS Ubuntu really better?"
date: 2009-02-09
forum: General Help
---

### Post by kapok on 2009-02-09
I have had two major problems that have made me want to downgrade Ubuntu:

the first is that for some reason my usb ports are not even recognized when i start up the computer. every time i start up the computer, i get an error message which i can't copy/paste here because i have no mouse at that time. after that, i must unplug and replug my mouse, which isn't so bad, but i also have to unplug and replug my wireless adapter, and it only works about half the time on the consecutive plugs. so if my wireless doesn't decide to connect i must restart my computer again. and if it doesn't connect again... and so on, until i get lucky.

the second is that my sound has completely stopped working for no reason. i've run the software test. i've restarted the computer, trying to boot into every available linux kernel. nothing. i've tried plugging the sound cord into every other possible port on my computer. i've tried plugging in headphones. i've tried using different sound producing programs. i've tried looking on the internet for advice. i've tried every available sound setting on my computer. i've tried every available sound setting on my monitor. nothing.

i think this is quite a nice spot to thank all of the ubuntu people for helping me learn to program. aside from all of the other fantastic applications (all of which i like better than their windows counterparts), you have provided me with a free compiler. i've always wanted to learn to program, and you have supplied with the means.

don't get me wrong. i will never go back to windows; i am just frustrated with technology. also, all that i have on this computer of any value to me is my music collection and a few documents.

i am considering dumping all of my important things onto an external hard drive, and reinstalling hardy heron. from the reviews i've read, i think that will solve my problems. intrepid is still being considered 'experimental' by some sites.


so my question to you is: is hardy heron actually better and more stabler than intrepid ibex?

---

### Post by markusf21 on 2009-02-09
The LTS by definition will be more stable. If LTS works for you and you don't have to have the latest, then just stick with the LTS and ugrade to the next one after its been around for a while.

---

### Post by mb_webguy on 2009-02-09
Newer releases would likely have better hardware support.  LTS releases are mostly for people (and particularly businesses) who don't want to reinstall or upgrade Ubuntu for extended periods of time, but still want to receive security updates and bug fixes.  Though LTS releases do tend to be very stable because their lifespan is much longer, allowing more time for bugs to be spotted and fixed.

If any site considers Intrepid as experimental, it's either outdated or doesn't understand the meaning of the word.  Jaunty is about to be released in a few months -- it's experiemental.  Intrepid was released four months ago and is the current release, while Hardy is the most recent LTS release.

That said, some people do seem to have better compatibility with older releases than newer ones.  If you want to downgrade to Hardy (which would involve a complete reinstall) to see if it works better, it's easy enough to upgrade if you decide you want to go back to Intrepid later.

---

### Post by Shazaam on 2009-02-09
Did you upgrade Hardy to Intrepid or was Intrepid a fresh install? A lot of people have had great success doing an upgrade. Others haven't. Since I have the drive space I usually keep two versions installed just in case of trouble. The main thing is to run whatever works best for you.

---

### Post by mb_webguy on 2009-02-09
That's a good point.  I tend to have better results with a clean installation of a new version than with an upgrade.

---

### Post by Therion on 2009-02-09
A clean install, IMO, is a must.  If you did a dist-upgrade, I'd try a clean install before making up your mind.

All that being said, Hardy simply runs better on my system.  No two ways about it.  I've triiiied to love Intrepid, I really have, but it's just not meant to be.

---

### Post by mb_webguy on 2009-02-09
And conversely Intrepid works better on my system than Hardy. :)

---

### Post by Yashiro on 2009-02-09
Preposterous! :D

---

### Post by mpsii on 2009-02-09
Did you do the following to upgrade from Hardy to Intrepid?

```
user@system:~/ $ sudo update-manager -d
```

I find this to work superbly and much better than:

```
user@system:~/ $ sudo apt-get update && sudo apt-get dist-upgrade 
```

---

### Post by pansz on 2009-02-10
If you did things properly (i.e. use do-release-upgrade instead of apt-get dist-upgrade), an upgrade is usually better than clean install.

I have had a very well set-up 7.04 and uses sudo do-release-upgrade to 7.10 without any problems, then I use sudo do-release-upgrade to 8.04 which works perfectly. I'd even use do-release-upgrade to 8.10 and it works.

My fresh install of 8.04 and 8.10 all have problems, install 7.04 on them and then do-release-upgrade has no problem at all.

Regards 8.04 vs 8.10, yes 8.04 is certainly better for me! but you've got to try yourself to see if 8.04 is better for youself, not somebody else.

---

### Post by mb_webguy on 2009-02-10
> **pansz said:**
> If you did things properly (i.e. use do-release-upgrade instead of apt-get dist-upgrade), an upgrade is usually better than clean install.

It depends on the changes between versions, and what changes you've made to your system.  If you don't mess with system configuration files much, then you're probably right.  But if you're like me and edit those config files to customize and streamline your system, then an upgrade can break your installation if the upgrade process doesn't take those changes into account.

Here's an example that comes to mind since it relates to another post I was just reading a while ago...  Suppose some user had made some extensive edits to their inittab in Dapper, and then upgraded to Edgy.  Well, Edgy replaced the sysvinit system with Upstart.  So maybe his system still works, but perhaps not how he thinks it should, or how he wants it to.  An upgrade simply can't take into account all of the nigh-infinite possible alterations a person might make to their system, especially if the new version of the OS uses different systems than the older version, or uses the same systems in different ways.

So, if you've ever made any changes to any system files ever, it might be better to do a clean install and start over rather than upgrading and having no idea what might be the cause of any problems that crop up.

---

### Post by kapok on 2009-02-10
thanks to everyone.

for the askers, i did a fresh install.

my sound not working at all and usb ports not working well are still  major issues; i will most likely downgrade to hardy within the week.

is there a GUI ndiswrapper under hardy like there is under intrepid?
i tried copy/pasting the commands first when i installed my system, which gave me some weird error message, but then when i used the interface of ndiswrapper (windows wireless drivers), it worked fine, even though i was doing exactly the same thing. that was after i blacklisted the default wireless driver.

i have both a WUSB54G v.1 and v.4 (my brother left it when he went to colledge). i use the v.1 right now because it works (sort of), and i've noticed that the setup for the v.4 is completely different. (i installed the v.4 exe from linksys.com under wine and there was no *.inf file in the folder.) i've tried google and searching these forums, and can't find a tutorial for v.4. maybe my problems are just based in my usb ports though. is there a place where error messages during the boot process are stored?

the thing that really irks me is the sound; it just stopped working, for no reason. :*(

---

### Post by unutbu on 2009-02-10
For the WUSB54G v.4 see [https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB54Gv4](https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB54Gv4)

For the sound issue, perhaps try psyke83's HOWTO: PulseAudio Fixes: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by theDaveTheRave on 2009-02-11
LTS or current version... Hmm good thoughts!

Clean install or upgrade... I allways do a clean install of the LTS, and then again every couple of years.

I allways stay one release behind the times, if I can (so when Jaunty comes out I'll clean install to Intrepid).

I must admit a few months back I did brake my own "rules" after having a wifi problem, and others! so I though "I know I'll clean install to Intrepid, it's been around a few months now".... bad move!

Intrepid loaded up fine, and everything worked out of the box, but things just felt "strange" and the new release of firefox kept on hanging the system... and I didn't like some of the other "new" firefox features. But these have now been added into Hardy via various upgrades and everthing seems to be ok and I'm getting used to them. Truth be told I hardly notice them, because I'm not having other problems related to running out of memory etc.

In fact when I find my Hardy disk I'm going to re-install my version of that, as I'm having some "problems" again with wifi connectivity, and USB support of external drives, I may try Intrepid... if I'm feeling up to it! But these are issues that have materialised after a failure of my power board, so may be related to that also (ie, I opened the laptop and replaced the part).

good luck with your USB problems.

David

---

### Post by kapok on 2009-02-11
hmm..
i went there and in part C there is a section that says 'ensure that your sound card's PCM is not muted or set to zero.

well, that's the bug i have, because it is set to zero, but nowhere there does it tell me how to change that. :*(

so how do i change it?

---

### Post by dcstar on 2009-02-12
> **markusf21 said:**
> The LTS by definition will be more stable. If LTS works for you and you don't have to have the latest, then just stick with the LTS and ugrade to the next one after its been around for a while.

And if anyone does use a LTS version of Ubuntu (of any version), I recommend **never** ticking the "Backports" option in Synaptic.

In my experience using backported packages from the next version can deliver you the problems you may have specifically avoided from that version in the first place.

If you do really (really) want a backported package or two, then manually download and install them from the specific backport area for your version at: [http://packages.ubuntu.com](http://packages.ubuntu.com)

A LTS version just set to receive LTS updates from the basic repositories is the way to get the most stable platform, IMHO.

---

