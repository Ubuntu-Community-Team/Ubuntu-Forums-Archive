---
title: "PysolFC Not Working After Day's System Upgrade"
date: 2016-09-28
forum: Gaming &amp; Leisure
---

### Post by KitchM on 2016-09-28
Xubuntu 14.04.4
After today's system upgrade, PysolFC stopped working correctly.  It begins with its progress meter/splash screen, but then just disappears off the screen part way thru, and the program never actually opens.

I did uninstall and then reinstalled with Ubuntu Software Center, but can't be sure of it because of that package manager's flaky performance.  Still, there was no difference. ](*,)

Synaptic Package Manager worked smoothly to do a reinstall, but sadly I received the same results.:rolleyes:

My questions are:
1. What part of the upgrade caused this?
2 What does one have to do to get it working again? :confused:

Thank you.

---

### Post by KitchM on 2016-09-28
```
Traceback (most recent call last):
  File "/usr/games/pysolfc", line 32, in <module>
    sys.exit(main(sys.argv))
  File "/usr/share/games/pysolfc/pysollib/main.py", line 359, in main
    r = pysol_init(app, args)
  File "/usr/share/games/pysolfc/pysollib/main.py", line 335, in pysol_init
    app.loadImages4()
  File "/usr/share/games/pysolfc/pysollib/app.py", line 763, in loadImages4
    v[i] = loadImage(v[i])
  File "/usr/share/games/pysolfc/pysollib/tile/tkutil.py", line 276, in makeImage
    im = PIL_Image(file)
  File "/usr/share/games/pysolfc/pysollib/tile/tkutil.py", line 253, in __init__
    image = Image.open(file).convert('RGBA')
  File "/usr/lib/python2.7/dist-packages/PIL/Image.py", line 2028, in open
    raise IOError("cannot identify image file")
IOError: cannot identify image file
Exception AttributeError: "PIL_Image instance has no attribute '_PhotoImage__photo'" in <bound method PIL_Image.__del__ of <pysollib.tile.tkutil.PIL_Image instance at 0x7f1a058dffc8>> ignored
```

---

### Post by KitchM on 2016-09-29
Maybe we've found a bug in the operating system.

---

### Post by QIII on 2016-09-29
I would suspect the application before even considering the OS.

Can you start the application from the terminal and post the results?

---

### Post by KitchM on 2016-09-29
Of course most of us would do that, except for the stated reasoning.  Further, see above for the requested information already posted.

---

### Post by QIII on 2016-09-29
What stated reasoning?

Where did you post the results of starting in the terminal?  Is that trace part of what is returned when starting from the terminal?  Where is the rest of the output?

Your trace indicates calls internal to the application and appears to indicate a fault or error encountered by image.py.

---

### Post by KitchM on 2016-09-29
> What stated reasoning?
I would have thought that the title of > PysolFC Not Working After Day's System Upgrade would have been enough.

> 
Where did you post the results of starting in the terminal?  Is that  trace part of what is returned when starting from the terminal?  Where  is the rest of the output?
I would have thought that the displayed code would have been easily recognized as coming from a terminal window.  And if there had been more output, I would have included it.  Why did you think there was more?

> Your trace indicates calls internal to the application and appears to indicate a fault or error encountered by image.py.         
Yup, already noticed that too.

---

### Post by QIII on 2016-09-29
Your title is a symptom, not a diagnosis.

You still have not indicated whether the output was generated in an attempt to start and run from the terminal.

If you noticed the trace, why do you surmise that there is an issue with the OS?

Since you appear to be intent on arguing rather than providing diagnostic information, you will have to wait for another community member's help.

---

### Post by KitchM on 2016-09-29
> Your title is a symptom, not a diagnosis.
What does your opinion of that have to do with anything?  Further, what difference does it make?

> You still have not indicated whether the output was generated in an attempt to start and run from the terminal.
That is because it makes no difference, and because you did not ask.  Why do you imply that it does?

> If you noticed the trace, why do you surmise that there is an issue with the OS?
You apparently still do not understand the reasoning.

> Since you appear to be intent on arguing rather than providing  diagnostic information, you will have to wait for another community  member's help.
It is not I that is asking inane questions and making short-sighted comments.  If you wish to be of help, offer some helpful suggestions rather than being argumentative.  You have yet to even attempt to answer either of my two initial questions nor any others. Exactly how do you justify your opinion that you are somehow offering help?  That is simply bizarre.

---

### Post by deadflowr on 2016-09-29
*Thread moved to **Gaming & Leisure**.*

> My questions are:
1. What part of the upgrade caused this?
2 What does one have to do to get it working again?

Unknown.
But perhaps looking at what was updated, that could help.
the apt package manager has logs you can look at, (or post)
look in /var/log/apt.
two log files get generated there, history.log, and term.log.
history will show the list of packages that got upgrade, where as the term log will show how it updated the packages.

Hope it helps.

---

### Post by KitchM on 2016-09-30
deadflowr, you are a breath of fresh air.  Thank you for that great idea.  Right on point.

Here is the pertinent info from the logs:
> Start-Date: 2016-09-28  09:05:48
Commandline: aptdaemon role='role-commit-packages' sender=':1.68'
Upgrade: bind9-host:amd64 (9.9.5.dfsg-3ubuntu0.8, 9.9.5.dfsg-3ubuntu0.9), liblwres90:amd64 (9.9.5.dfsg-3ubuntu0.8, 9.9.5.dfsg-3ubuntu0.9), libdns100:amd64 (9.9.5.dfsg-3ubuntu0.8, 9.9.5.dfsg-3ubuntu0.9), libisccfg90:amd64 (9.9.5.dfsg-3ubuntu0.8, 9.9.5.dfsg-3ubuntu0.9), isc-dhcp-common:amd64 (4.2.4-7ubuntu12.6, 4.2.4-7ubuntu12.7), libbind9-90:amd64 (9.9.5.dfsg-3ubuntu0.8, 9.9.5.dfsg-3ubuntu0.9), python-pil:amd64 (2.3.0-1ubuntu3, 2.3.0-1ubuntu3.2), python-imaging:amd64 (2.3.0-1ubuntu3, 2.3.0-1ubuntu3.2), dnsutils:amd64 (9.9.5.dfsg-3ubuntu0.8, 9.9.5.dfsg-3ubuntu0.9), isc-dhcp-client:amd64 (4.2.4-7ubuntu12.6, 4.2.4-7ubuntu12.7), python-pil.imagetk:amd64 (2.3.0-1ubuntu3, 2.3.0-1ubuntu3.2), python-imaging-tk:amd64 (2.3.0-1ubuntu3, 2.3.0-1ubuntu3.2), libisccc90:amd64 (9.9.5.dfsg-3ubuntu0.8, 9.9.5.dfsg-3ubuntu0.9), libisc95:amd64 (9.9.5.dfsg-3ubuntu0.8, 9.9.5.dfsg-3ubuntu0.9)
End-Date: 2016-09-28  09:06:35

I am noticing python-pil.image jump out at me.  Could it be related?  What do you think?

---

### Post by deadflowr on 2016-09-30
This related, you think?
[https://bugs.launchpad.net/ubuntu/+source/pysolfc/+bug/1628349]("https://bugs.launchpad.net/ubuntu/+source/pysolfc/+bug/1628349")

(BY-the-way, is this your bug, or entirely unrelated to you, aside from the problems)

---

### Post by KitchM on 2016-09-30
Hot damn!  You are the man (or woman)!!!  You found the solution.  \\:D/

Thanks very much indeed.

And  did you notice that it affected many people?  I knew it had something  to do with the bad Ubunutu update.  It was just too darn coincidental  that it happened as it did.  It is just another example of these  problems.  A couple months ago the update process bricked the whole OS  and I had to reinstall.  (Perhaps it is time to find a more stable  environment.?.?)

Very simple cause and simple solution.

You are actually helpful, as your signature info states.  Very.  Thanks again.

(No, that is not my bug.  It is from David Wise.  My search must have just crossed that post in the stream.  Timing is indeed everything.)

---

