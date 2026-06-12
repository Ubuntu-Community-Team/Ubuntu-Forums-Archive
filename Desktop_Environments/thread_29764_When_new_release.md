---
title: "When new release?"
date: 2005-04-25
forum: Desktop Environments
---

### Post by Terracotta on 2005-04-25
Hye,

Is the Ubuntu-team going to release a new kubuntu version soon, with a lot of problems solved? 
I am still having troubles wich noone apparently can solve :s

---

### Post by bored2k on 2005-04-25
> K/Ubuntu is a free, open source operating system that starts with the breadth of Debian and adds regular releases **(every six months)**, a clear focus on the user and usability (it should "Just Work", TM) and a commitment to security updates with 18 months of support for every release. Ubuntu ships with the latest Gnome release as well as a selection of server and desktop software that makes for a comfortable desktop experience off a single installation CD.
[http://www.ubuntulinux.org/ubuntu/](http://www.ubuntulinux.org/ubuntu/)

---

### Post by moopere on 2005-04-26
[QUOTE=Terracotta]Hye,

Is the Ubuntu-team going to release a new kubuntu version soon, with a lot of problems solved? 
I am still having troubles wich noone apparently can solve :s[/QUOTE]


What problems?

List em here, maybe we can help.  There are plenty of 'newness' problems as someone else mentions.  I've not found anything yet that can't be fixed with a bit of a hack though.

The Breezy verison of Kubuntu should be awesome - I'd expect that most of the 1st rev problems (ie, hoary based) will dissapear, but only with the help of you and me, fixing ourselves what can be fixed and letting others know about the stuff that we can't do ourselves.

Cheers,
Craig

---

### Post by ltmon on 2005-04-26
I wonder if what the original poster was actually asking is if there are going to be any bug-fix point releases between hoary and breezy?  That's my question in any case.

Personally I think that it would be a worthwhile effort, given that there are at least 2 fairly showstopping bugs that various people are encountering (for reference, I'm refering to refresh rate detection on some generic monitors and the frequent Konqueror crashes that a number of people are reporting). 

It would be sad to see a distribution that gets so many of the "hard" things right lose some popularity due to bugs in areas that most linux users expect to work out of the box in any current distribution.

Cheers,

L.

---

### Post by Terracotta on 2005-04-26
Indeed, I was refering to a bug-release,

and euh for the problems, I can't get solved:
[http://www.ubuntuforums.org/showthread.php?t=25095](http://www.ubuntuforums.org/showthread.php?t=25095)
I have been looking for people to help me with that on several fora, since I encounter the same problem with suse 9.2, I think it's something related to xorg and 64 bit or kdm and 64 bit, if so it wouldn't be a real kubuntu problem, but there should be at least a way to solve this.

---

### Post by moopere on 2005-04-26
[QUOTE=Terracotta]Indeed, I was refering to a bug-release,

and euh for the problems, I can't get solved:
[http://www.ubuntuforums.org/showthread.php?t=25095](http://www.ubuntuforums.org/showthread.php?t=25095)
I have been looking for people to help me with that on several fora, since I encounter the same problem with suse 9.2, I think it's something related to xorg and 64 bit or kdm and 64 bit, if so it wouldn't be a real kubuntu problem, but there should be at least a way to solve this.[/QUOTE]

From reading your post and the others in that link it certainly does appear to be an X problem, not necessarily a KDE one.  

Kubuntu however is not just a nice version of KDE, so I can see why this would be frustrating for you.  First up, I don't have a x64 system so might be talking rubbish, however,  I'd try this:

1) When you get the boot prompt from booting off the CD, install using 'server' instead of just hitting enter.  This will install a basic system with no GUI components.  As you appear to be having problems with X (the GUI) this would make sense to me.

2) Obviously you'll want a GUI at some point, so once this basic install is finished (it works no?) try "aptitude install kubuntu-desktop"

3) After this, I can't remember if KDM (the login screen) starts immediately, I think it might not, in any event if it does, ctl-alt-f1 to get back to a VT and:
  
  dpkg-reconfigure xserver-xorg

This will lead you through the X configuration.  I don't know what type of VGA adaptor you have, but it sounds like it might be causing you trouble - just to get things working, try choosing the VESA driver.  The VESA driver should work on just about anything out there that 5-10 years old or younger

If it won't come up with VESA try VGA (yuk!), if this doesn't work either then something is very likely seriously broken with either a) the x64 compile of xorg - go looking in dejanews about this, or b) your hardware is foo.  Hard to test b) unless you have a lot of spares though.

I wouldn't mind betting that you're seeing a driver (module) problem.  If you can get X working with VESA or VGA then this is the most likely scenario.  Might be that a newer (or even older!) kernel with a slightly different build of driver set will work better for you.

Cheers,
Craig

---

### Post by Terracotta on 2005-04-26
haven't tried what you suggested yet, am going to as soon as possible, but I a have working yoper system WITH nvidia drivers (i686 optimised of course), I have an Asus V9999 GE (geforce 6800), it has caused me trouble, but the new nvidia drivers worked on mepis too, though these systems are both x86 and not x86_64. But I have had things workings on suse 9.1 x86_64, and they still use xfree. mmm yeah I'm repeating myself, gonna try it anyway, soon.
Thanks for your kind and quick respons, I've been looking for help quite some time to have a native x86_64 system, feels quite stupid working on a x86 system on a x86_64 pc  ](*,)

Edit:
AAARGh, grmbl, tried to install fedora core 4,  and it crashes firing up X during anaconda install, exactly the same result as described above, I'm getting really fed up with this crashing always have to solve problems stuff. I don't mind working on problems, but hey, I need time for other stuff as well (exams are coming up). I hope this stuff gets solved soon.

---

### Post by Terracotta on 2005-04-27
Jieha, it works, well ok, working with the VESA drivers now. trying to install the nvidia drivers as soon as possible :-). Thank you very MUCH MOOPERE, I finally get to see a shining KDE 3.4, as far as I can see, way more eye-candy than kde 3.3.2 from Mepis :-), love the blue.

---

### Post by Terracotta on 2005-04-28
re-Installing the new NVIDIA drivers (the 7174- version) helped as well.
Thank you all for your kind replies.

---

