---
title: "Noob question about upgrading software"
date: 2009-01-23
forum: General Help
---

### Post by pixelpaul on 2009-01-23
I installed 8.10 and really love it!  As a lifelong windows user, I had no idea what I was missing.

I'm still confused about upgrading / updating software packages.  I cannot seem to find a clear-cut answer in these forums.

Let's say I have VLC media player 0.9.4 and I notice on their website that they now have a version 0.9.8a.  First of all, is this considered an update or an upgrade?

On their website they have the following 2 commands:
% sudo apt-get update
% sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc

Do I just enter those commands?  Will that give me an upgraded / updated install?

I go to synaptic, do a search on 'VLC'. I can see that all my results reference 0.9.4, which is what I have now.

So SPECIFICALLY, what is the EASIEST SIMPLEST way to update / upgrade to 0.9.8a?

Do I just enter the 2 commands?  This is not at all clear in ubuntu. For new user, this process is not spelled out and does not seem to be like win xp.

---

### Post by drs305 on 2009-01-23
*apt-get udpate* updates the repository package index based on the settings you have set in either synaptic or 'software sources' - which repositories, server, third-party sources, etc

*apt-get upgrade* downloads and installs the latest version of *installed* packages on your system. It will install the latest version in the repositories you have enabled.

The packages in the 'official' ubuntu repositories have been tested with ubuntu. They are often not as recent as the ones available from the package developer, which releases new versions for linux but may not have tested them specifically with ubuntu. The individual providers often offer downloads of the latest version and usually offer instructions on how to install them.  The usual package formats are .deb and .rpm files  Deb packages are fairly easy to install while RPM packages involve a few more commands. 

Again, unofficial packages have not been tested by ubuntu team members and unless you have a specific need for a newer package it is safer to continue to use the ones available in the repositories.

For more information about the apt-get command and options, you can review the 'man' page of apt-get:
```

man apt-get

```

Welcome to the ubuntu forums!

For more information about the repositories, see this from the ubuntu documentation wiki:
[Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by oldos2er on 2009-01-23
Usually the program versions in Ubuntu's repositories are only upgraded every six months, when a new Ubuntu is released. There may be bug or security updates though. You can stick with the repository version, or update manually from a program's website (which may mean compiling the program from source). It's your choice.

---

### Post by mb_webguy on 2009-01-23
To specifically address your example of VLC...   The most up-to-date version of VLC available for Ubuntu (in an easy-to-install form) is 0.9.4, which is in the official repositories.  The instructions on the Ubuntu page of the VLC website are simply to install VLC, and not to upgrade to a newer version.  If they had a .deb file, you could install that with a couple of clicks, but I don't see one available.

However, they *do* have the source code available.  Compiling source code is a daunting task for new users, but not nearly as complicated as it seems at first.  If you want to compile the latest version of VLC, download the source code from [this page]("http://www.videolan.org/vlc/download-sources.html"), then follow [these instructions]("https://help.ubuntu.com/community/CompilingEasyHowTo").

However, sometimes some very nice people will do the heavy lifting for you, and provide the software on a PPA (Personal Package Archive), which is essentially a mini-repository.  Christopher Korn has the latest version of VLC available in [his PPA]("https://launchpad.net/~c-korn/+archive/").  Once you add his PPA to your sources, you can upgrade to the latest version of VLC using Synaptic or apt as you would anything in the repositories.  As he notes on his PPA page, you can also download the .deb files [here]("http://archive.getdeb.net/dump/intrepid/vlc/"), if you'd rather not add his PPA to your software sources.

---

### Post by fragos on 2009-01-23
What Synaptic shows you is controlled by the repositories that are registered with it. Many users add some additional repositories but don't get carried away with that or your system could become unstable. Goto [http://medibumtu.org](http://medibumtu.org) and follow the instructions for adding that repository. Also bring up System-> Administration-> Software sources. The first tab has check boxes that control the main Ubuntu repositories. I recommend you insure all of these are checked although source code probably doesn't need to be. Then click the "Updates" tab. You'll see a check box for "Unsupported updates (interip-backports)" that will get you newer releases of some packages than come with the standard distribution. I check that one but not the one for "Pre-released updates". The Third-Paty Software tab is where additional repositories are placed. If you added Medibuntu you'd see it there. The Authentification tab would also have an entry for Medibuntu. In addition to doing this I also daily check [http://getdeb.net](http://getdeb.net). These packages are built specifically for Ubuntu and there are some usefull ones there. What you don't want as a noobie is packages not specifically built for Ubuntu.

---

### Post by mb_webguy on 2009-01-23
That link provided by fragos should be [http://medibuntu.org]("http://medibuntu.org"), btw.

---

### Post by fragos on 2009-01-23
> **mb_webguy said:**
> That link provided by fragos should be [http://medibuntu.org]("http://medibuntu.org"), btw.

Sorry for the typo.

---

### Post by pixelpaul on 2009-01-24
"Once you add his PPA to your sources, you can upgrade to the latest version of VLC using Synaptic or apt as you would anything in the repositories.  As he notes on his PPA page, you can also download the .deb files here, if you'd rather not add his PPA to your software sources."

As a Noob, this is a perplexing instruction.

In Software Sources, I tried to add: deb [http://archive.getdeb.net/dump/intrepid/vlc/](http://archive.getdeb.net/dump/intrepid/vlc/)   under the third party software tab.  I clicked on 'Add' then copied that address, however, the 'Add Source' button remains greyed out.

When I went to that address, there are at least a dozen deb file with '0.9.8a' in the name. Which ones do I choose???

Again, my original question: what is the SIMPLEST EASIEST way to go from VLC 0.9.4 to VLC 0.9.8a?

---

### Post by fragos on 2009-01-24
Ubuntu packaged VLC 0.9.4 for a reason of stability when 8.10 was released. Unless you know specificaly why you need 0.9.8a I wouldn't bother. The URL address you have isn't for a repository. Those packages might not even work with Ubuntu. You might want to try mplayer if there's something VLC doesn't do for you. It's very popular.

---

### Post by pixelpaul on 2009-01-24
Fragos:

At this point, I will take your advice and not try to upgrade/update to VLC 0.9.8a

Paul

---

