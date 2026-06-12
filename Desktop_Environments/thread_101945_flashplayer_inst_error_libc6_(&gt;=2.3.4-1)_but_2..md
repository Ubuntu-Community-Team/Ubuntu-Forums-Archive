---
title: "flashplayer inst error libc6 (&gt;=2.3.4-1) but 2.3.2.ds1-20ubuntu14 is to be installed"
date: 2005-12-10
forum: Desktop Environments
---

### Post by dosadi on 2005-12-10
Hi,

I've read the starter guide on how to install java and flashplayer, but they fail on my system. I'm running Breezy, and I did an upgrade using apt-get like the starter guide instructed to move up from Hoary. Flashplayer and java never worked in Hoary for me either. 

I try to install flashplayer through either Synaptic or using apt-get and get this error


flashplayer-mozilla:
  Depends: libc6 (>=2.3.4-1) but 2.3.2.ds1-20ubuntu14 is to be installed


I'm not sure how to tell apt-get or dpkg to allow for the fact that my libc6 is actually newer than the one required by the app and that it should ignore this. 


root@taprisot:/home/mrreg # apt-get -m=yes install flashplayer-mozilla
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  flashplayer-mozilla: Depends: libc6 (>= 2.3.4-1) but 2.3.2.ds1-20ubuntu14 is to be installed
E: Broken packages


I'm really shooting in the dark here . . . . anyone run into this or know how I could approach it? I've tried Google and the starter guide and searched this forum but can't find the answer. Thanks in advance to anyone who can help!

Nicole

---

### Post by dcstar on 2005-12-11
[QUOTE=dosadi]Hi,

I've read the starter guide on how to install java and flashplayer, but they fail on my system. I'm running Breezy, and I did an upgrade using apt-get like the starter guide instructed to move up from Hoary. Flashplayer and java never worked in Hoary for me either.

I try to install flashplayer through either Synaptic or using apt-get and get this error

flashplayer-mozilla:
  Depends: libc6 (>=2.3.4-1) but 2.3.2.ds1-20ubuntu14 is to be installed
.....
I'm really shooting in the dark here . . . . anyone run into this or know how I could approach it? I've tried Google and the starter guide and searched this forum but can't find the answer. Thanks in advance to anyone who can help!

Nicole[/QUOTE]
I'd bet you haven't changed your Repositories from the old "hoary" ones to the new "breezy" ones.

In Synaptic-Settings-Repositories, edit each one and substitute every occurrence of "hoary" you can find.

Once that is done, you will probably find a big load of updates that can be installed - the libc6 I currently use is v2.3.5-1ubuntu12.

---

### Post by dosadi on 2005-12-11
[QUOTE=dcstar]I'd bet you haven't changed your Repositories from the old "hoary" ones to the new "breezy" ones.[/QUOTE]

oh crud . . . I thought I had gotten them all in /etc/apt/sources.list but I had missed a few lines. Now I've got it all switched over to breezy rather than just the universe and multiverse ;)

# apt-get update
# apt-get upgrade
# apt-get dist-upgrade
# apt-get install flashplayer-mozilla

still didn't work though. I got these errors:  [http://www.neoprimitive.net/~dosadi/misc/errors.txt](http://www.neoprimitive.net/~dosadi/misc/errors.txt)

at this point it looks like /usr is now out of space, so I'm screwed for now. I tried removing evolution but it won't, that would have freed up disk space. There's nothing else that's big I can remove. I'll have to work on this part and see if I can get back to square one. I'm not opposed to switching to kubuntu for a while, so I might just give up and do that, not sure yet ;)

flashplayer didn't work for me when it was Hoary, so maybe a fresh install is a good idea? Or am I taking the Windoze solution to the problem in that way ???? ;)

I think I should repartition . . . . whether I do a clean install or copy things around and change mount points . . . and then only run Windoze on top of linux rather than wasting disk space to have it installed separately. If I could get flash and java working in Ubuntu, I really wouldn't use M$ anyway; I have a lot more respect for UNIX . . . .

---

### Post by dosadi on 2005-12-11
Yeah, actually I'm really in trouble here . . . I got half an upgrade to breezy or like 75% of an upgrade and then /usr filled up. Now terminal doesn't launch, and I bet when I shut the system down less will work when I start it up again. I'm going to move data off and do the easy thing and just re-build. I seriously was thinking of repartitioning to get rid of all the WinXP space that does't benefit me anyway . . . so now I have an excuse. So nevermind! But thanks dcstar!

---

