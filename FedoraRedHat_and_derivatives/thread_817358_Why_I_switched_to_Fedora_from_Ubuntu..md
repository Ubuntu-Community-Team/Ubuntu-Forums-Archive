---
title: "Why I switched to Fedora from Ubuntu."
date: 2008-06-03
forum: Fedora/RedHat and derivatives
---

### Post by trident on 2008-06-03
(from my [blog.](http://trident.wordpress.com/2008/06/03/why-i-switched-to-fedora-9-from-ubuntu-804/))

[Photos.](http://www.flickr.com/photos/trident/sets/72157605413209490/) 

I’ve used linux on and off since, well, it feels like forever to me. The earliest linux install I remember was right before FC3, on my very old lappy. Took breaks in-between of on-off use, then came back to linux when my laptop… with a 64-bit processor … was shipped with Vista 32-bit.

So, I remembered that I had the “easiest” time with ubuntu, downloaded, installed, and was back in linux land. Then I heard that fedora 9 came out. Now, I had a tough time deciding between the two, but here’s what it boiled down to to me. I ended up installing, and keeping fedora.

Scores? Arbitrary. Each is worth two points. If both were relatively easy, half point to the easiest.

Installation: Fedora. When I installed ubuntu, the partitioner included with the installer simply did not work. I was told to go boot into vista, and resize from there, then install ubuntu onto the free space.

For fedora, I just chose to resize windows, and use the free space. And it worked. +2 fedora.

Getting off the ground: Ubuntu. So, I imported my music library. Ubuntu asked to install some codecs, it did, and the music played. Wanted 3d acceleration, checked a box, rebooted, was working.

Fedora asks that you buy codecs, and makes it not that easy to install the free codecs. Finally, on day 4, I got all the codecs I need, after searching around the forums. When I wanted 3D, I had to enable another repository, and go install from there.  +1.5 ubuntu.

Looking nice (from the start to customization): Fedora. Fedora has backrounds that change based on the time of day, is not brown, and emerald theming actually came with themes when I installed it.

Ubuntu presented me with it’s signature brown and orange, and I ran to appearance and changed it to clearlooks.
+1.5 fedora.

Performance: I’m not making this comparison, simply due to different software versions. It would be unfair. My opinon though: Fedora has a very slight speedy edge to me.

Support: Fedora. Look, everywhere I go on the internet, I hear how wonderful the ubuntu community is. I agree. ‘cept, the ratio of knowledgeable people to people who need help is simply too great. This is probably the main reason I left. The community is flooded, and I, the average user, don’t feel all that welcome. Sure, I spent some time in #ubuntu (on freenode), tried to offer some support, lurked the forums… and more. But, there was no real sense of a truly small community. Ask a question, get an answer. For the fedora community, ask a question, get a reason you were off slightly, and what you should do. I also felt more welcome in #fedora, with conversation mixed with support. +2 fedora.

Yum (rpm) vs Apt-get (deb): Ubuntu/Debian. .debs were simply faster for me. Downloading especially, since I had a local mirror that took two clicks to set up. +2 ubuntu.

Mono (Trap?): Don’t care, really, at all. When it doesn’t work, I’ll start caring.

More Fun/Opinions (no score): Fedora. A little harder to get working, but when it does, it’s awesome. Every thing looks nicer, feels faster, and I feel as if I have total control over it.

Ubuntu works though. Tried and tested, it has never failed me. While not the fastest, it made up for that with the most things working right away. Though, when using it, I felt a severe lack of total control. It seemed like lots of things were happening behind my back, instead of directly telling me.

---

### Post by squirrel_chaser on 2008-06-05
Interesting post.  I admin a number of Linux servers at work, which are mostly CentOS, so I tried Fedora 9 and wanted to like it.  The issues I ran into were vpnc and wireless.  On Ubuntu or Debian vpnc worked immediately, but I couldn't get vpnc working in Fedora 9.  I tried disabling SELinux and the firewall but still no joy.  I am probably missing a step or just plain screwing up, the latter all too common for me.  Ubuntu's ease of use on the desktop side saves more time to work on other projects.  Of course sticking with only one distro would save time, but what fun is that?  

Fedora is a fine distribution and is, in my opinion, ahead of Ubuntu in the areas of virtualization, security with SELinux, and documentation through Red Hat's excellent work.  Although, Ubuntu will probably rise to the same level in these areas eventually.

The allure of apt and family is sweet and hard to resist.

---

### Post by mthei on 2008-06-05
Yes, the one thing I really miss from Ubuntu is not just APT, but the fact that DEBs work on all Debian based distros, whele there are different RPMs for Fedora, RHEL, Mandriva, Suse, etc.

As for the original post, I found it to be a very fair comparison of the two. Although I still don't get the YUM vs APT thing. Both are just as fast, although that may be because both have Canadian mirrors hosted from the same University. Though it would be nice to have an equivelent to "apt-get autoremove" for YUM, as I currently have to remove some dependencies manually after removing something (and I just gave KDE4 a try yesterday, only to remove it!)
For my computer use, it doesn't really matter if I run Fedora or Ubuntu, but Fedora works better with my hardware, and suspend/resume works. But this time around, with the current versions of both distros, I think it's a really close race for me. Both are solid, both require very little tinkering with to get them to work properly (not counting installing Livna/FreshRPMs/Whatever the reader prefers in Fedora, and the large amount of software I've had to remove from Ubuntu after install, which is close to 500mb, most of which is OpenOffice).
I can't wait to see what these fine distributions come up with for their next releases this fall. Hardy ran as well on my computer as Fedora 8 did, but Fedora 9 improved a lot of those features.

---

### Post by igknighted on 2008-06-06
> **mthei said:**
> Yes, the one thing I really miss from Ubuntu is not just APT, but the fact that DEBs work on all Debian based distros, whele there are different RPMs for Fedora, RHEL, Mandriva, Suse, etc.

Deb's don't work across all debian distro's.  Yes, apt (well, dpkg) will install them (or try to), but you are taking a risk every time.  RPM works the same way, it will install and often work across Mandriva, Suse, Fedora and more; but you are not guaranteed any success.

---

### Post by mthei on 2008-06-06
Really? I'm sure I've read what I said about DEBs somewhere, and I've used some of the stuff on getdeb.net on Etch. But you are right (an actual search confirms). I guess I assumed otherwise as every RPM site I come across actually specifies the distribution in the name.

---

### Post by AdamWill on 2008-06-06
mthei: it is basically never entirely safe to use a package intended for one distribution on another. You'll not find any distribution vendors who recommend this practice.

The reason it works more often with .debs than .rpms is simply that all distros that use .debs are originally derived from Debian, and they haven't really diverged very far yet. But it still breaks, sometimes.

Not all distros that use .rpms come from the same common base (they're not all initially Red Hat forks) and even those that are have diverged massively since. Mandriva is technically a Red Hat fork, but given that the fork happened in 1998 and the two have been developed entirely independently since then, there's really not much similarity between them.

So this has nothing to do with any difference between .deb and .rpm formats, it's simply a function of how different any two given distributions are.

---

### Post by mthei on 2008-06-06
That makes sense. Thanks for clearing it up.

---

### Post by RedDwarf on 2008-06-07
To make it clear. Install a RPM/DEB from version X of a distribution into version X+1 of the *SAME* distribution isn't entirely safe.

We need libstdc++.so.7 to remember people how funny install packages not designed for your distribution could be :)

---

### Post by mthei on 2008-06-07
[img]http://blogsap.files.wordpress.com/2006/10/nbc_the_more_you_know.jpg[/img]


(Edit: I guess people outside of North America may not get the reference to those PSAs)

---

