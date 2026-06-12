---
title: "Updated testing/reporting howto"
date: 2007-01-29
forum: Development CD/DVD Image Testing
---

### Post by Henrik on 2007-01-29
[SIZE=3]We are approaching the Herd 3 series Alpha release which means a new round of release testing. To help us track the the test information that comes in we will be using the Malone bug tracking system. In addition to filing and tracking actual bugs we will also be using it in a slightly non-standard way to [track the test results]("https://bugs.launchpad.net/ubuntu-iso-tests/+bugs"). Before the release we will focus on those images that are candidates to be released and afterwards on the released images themselves.

The wiki pages used last time will not be used for Herd 3, nor the forum threads, which means that both the emerging forum-based team and the established core-dev testing team will be using the same result tracking system.

The procedure is described [here]("https://wiki.ubuntu.com/Testing/ReportingResults"). I've updated the [HOW-TO]("http://www.ubuntuforums.org/showthread.php?t=331123") to link to that description.
[/SIZE]
Comments, questions?

---

### Post by UBfusion on 2007-01-29
These are much more precise instructions, thanks for the time you invested in clearing things up!

Some comments:

[LIST=1]
[*]I find that the wiki is a bit linux-oriented and rather discouraging for windows users. The instructions give the impression they are addressed to seasoned linux users that have a spare box to install the daily builds, and therefore are dloading the isos and testing them with linux tools in their main box. Cculd perhaps some information be added for testers whose main box (and expertise) is windoze? E.g. we could start by adding how to do md5sum tests and get daily builds with rsync in XP.


[*]I think that md5sum checking is not so important as checking the burned cd itself. After all, getting the iso as a torrent or by rsync will ensure a correct mdsum (unless the files in the repository are mismatched). The burned iso however, using default (maximum) writing speed has a 20% or more probability of being defective according to my experience (especially if burned in windows). So, after the "Using rsync" and before "Testing" sections of the wiki, I would propose a "Burning and testing the CD" section with appropriate instructions.
[/LIST]

Some thoughts: It took me two weeks of active testing to begin to understand the meaning of the previous testing howto and thus become able to make (hopefully useful) suggestions as the above ones. However I am still kinda afraid submitting a new bug. It's not that I will say something stupid or submit a duplicate bug (almost inevitable, since searching if a bug exists already or is a duplicate seems to be more an art than a science if you are new to linux), but mainly that I am not sure that the bug is worth posting and that it can be confirmed by others. Perhaps a "worked example" of a real bug being reported could help. E.g. a real story written by an experienced tester who finds a bug and reports it in the proper way, following the howto step by step, would be invaluable (a video of the process would be awesome). 

Some more ramblings on testing: In an ideal world, I imagine a more interactive testing procedure like this: Daily builds (and especially Herds) are released **together with a list of bugs to be tested** and instructions (in a txt file on the cd and on the wiki). Instructions would recommend sequential testing in two stages:

[LIST=1]
[*]"priority testing": testing for bugs that most probably are fixed but need be tested thoroughly in various hardware settings and scenarios to ensure that the live cd experience and the installation are 99.5% ok. For example, such bugs today would be related to ubiquity, apt-install and network.


[*]"normal targeted testing by subsystem": when the urgent bugs disappear, then we proceed in further testing **organised by subsystems** and above all, **according to debuggers' own priorities**. By 'subsystems' I mean the system tools, administrative tasks, vga system, audio system, video playback, codecs, disk management, mounting devices etc.
[/LIST]

In the above scheme, the priorities for testing are set by the developers and not by the users who unguided will be randomly testing several functionalities.

Of course, the prioritisation of urgent and normal bugs (and the instructions to testers) would change for each subsequent build, focusing on the current major problems.

I feel that such a procedure would have some advantages. First, we would know explicitly and beforehand what is important to test, and what is second priority (e.g. playing movies, watching tv, etc) at each phase of testing. Second, debugging would tend to cluster on one subsystem at a time, and not towards parallel debugging of every possible aspect of ubuntu usage (which is what inevitably happens when you leave us test as we please).

This reply is starting to become an essay, so I'd better stop. Forgive me for being boring and perhaps rediscovering the wheel here (after all, debugging is a 50 year old art and science).  I'm just enthusiastic about testing feisty and am trying to apply my 25 years of experience in troubleshooting various systems (circuits, electronics, devices, computers and girlfriends) to linux testing.

If "Linux testing for dummies" had been written, this post would not be that long. For me, the "big picture" question (and challenge) is the following: *Can Feisty set a new paradigm for the process of developing and debugging future versions of Ubuntu?* And a more ambitious one: *Is work on effective, meaningful and productive standardisation of debugging in the context of the complex dynamics between the tester and the developer communities a good investment for the future of free/open software?*

---

