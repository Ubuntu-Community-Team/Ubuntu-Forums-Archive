---
title: "Tilda, possible Compiz issue?"
date: 2007-09-21
forum: Desktop Environments
---

### Post by MrSootentai on 2007-09-21
I've had Tilda for a while now, but now it give's me this weird problem.
All goes well up until I i press the shortcut key more than once.
Check the first attachement to see the first time my Tilda loads up and i select the shortcut key,
now click the second photo to see what happens when i click the shortcut key again.
Any help?

---

### Post by mrashley on 2007-09-23
I am having the exact same issue.
I have turned off "Desktop Effects" (aka Compiz Fusion) and ran Tilda. I hotkey-opened the window three times, and after the third time all sub-sequent openings were like the third time.

These are the results:

1) Run the program.
2) Press F1 to activate the terminal

*see 1st attachment

3) Press F1 twice, to hide and re-show the window a second time

*see 2nd attachment 

4) Press F1 twice, to hide and re-show the the window a third time

*see 3rd attachement

All subsequent re-shows of the window are the same as the third time.

---

### Post by MrSootentai on 2007-09-23
I found the best way to fix this is to close the program and reload it. But this is annoying and gets real annoying real fast.

---

### Post by Lord Illidan on 2007-09-23
You have to rightclick on it, select preferences and then Enable double buffering

---

### Post by mrashley on 2007-09-23
To MrSootentai,

If I have to close it each and every time I want to look at the terminal that entirely defeats the purpose of this particular program. This isn't just something that happens once in a while, this happens first time every time I run the program.

To Lord Illidan,

Double buffering was enabled in the example I showed.

---

### Post by Lord Illidan on 2007-09-23
> **mrashley said:**
> To MrSootentai,

If I have to close it each and every time I want to look at the terminal that entirely defeats the purpose of this particular program. This isn't just something that happens once in a while, this happens first time every time I run the program.

To Lord Illidan,

Double buffering was enabled in the example I showed.

Interesting...well, I am running Gutsy, perhaps there's been an update somewhere? Is transparency enabled in tilda?
In gutsy, with transparency enabled, if I don't have double buffering enabled, I get your exact symptoms...

---

### Post by mrashley on 2007-09-24
> **Lord Illidan said:**
> Interesting...well, I am running Gutsy, perhaps there's been an update somewhere? Is transparency enabled in tilda?
In gutsy, with transparency enabled, if I don't have double buffering enabled, I get your exact symptoms...

I am running Gutsy. Transparency can be enabled or disabled and I get the same result, except of course that there is no transparency when it's turned off (for the first drop down).

---

### Post by MrSootentai on 2007-09-24
MrAshley,
I wrote that just to tell you how I found a way to fix the problem. But it's anoying like I said and DOES completely defeat the purpose.
Double Buffering has been enabled so I have no idea what to do now.

---

### Post by pingpongboss on 2007-09-25
crap i'm having the same problem. i'm hoping someone has a solution

---

### Post by Lord Illidan on 2007-09-25
Is animated pulldown enabled? If not, try enabling it, and see what happens.

---

### Post by MrSootentai on 2007-09-25
Animated Pulldown IS enabled.
With or Without it, Tilda still has this problem.

---

### Post by Lord Illidan on 2007-09-25
No idea.. mine works fine..
Can you send screenshots of all the tabs in the configuration window?

---

### Post by MrSootentai on 2007-09-25
Here are my first five tabs...

---

### Post by MrSootentai on 2007-09-25
Here are my last two...

---

### Post by mrashley on 2007-09-27
And mine.

If it's worth mentioning the shell is still running because ctrl+d works to exit the program.
It's just hidden behind this white backdrop.

---

### Post by mrashley on 2007-09-27
My last two.

---

### Post by Lord Illidan on 2007-09-27
Damn, now mine started acting up. I ditched the thing. Tilda needs a rewrite in my opinion..it doesn't use transparency like gnome-terminal.

---

### Post by tezem on 2007-09-27
Just upgraded to Gutsy and have the same problem with tilda.
There is something going on in launchpad about this issue too. [https://bugs.edge.launchpad.net/ubuntu/+source/tilda/+bug/144175](https://bugs.edge.launchpad.net/ubuntu/+source/tilda/+bug/144175)

---

### Post by tlacuache on 2007-10-16
I have the problem as well. A temporary workaround I found was to enable animation, but choose either left or right. You can set the usec value quite low. Now I don't have the problem, and it's usable.

---

### Post by Dirk_McJerk on 2007-10-18
> **tlacuache said:**
> I have the problem as well. A temporary workaround I found was to enable animation, but choose either left or right. You can set the usec value quite low. Now I don't have the problem, and it's usable.

I was having the same problems as others, however enabling animation has seemed to fix the problem.

---

### Post by depi on 2007-10-20
Damn, I've just upgraded to 7.10 and have the same problems, please give us back the good old Tilda! :)

---

### Post by cccccccc on 2007-10-22
yes, the animation orientation selected to right solved my problem. at least...
thanks

---

### Post by ayoli on 2007-10-22
I've just installed tilda on my fresh gusty : no problem ATM.
I have the default config, just changed the font size and enabled the transparency, animated pulldown xas enbled by default I did'nt change anything here.
Offtopic : shame that tilda does not have a true transparency like gnome-terminal.

---

### Post by dustigroove on 2007-10-24
> **tlacuache said:**
> A temporary workaround I found was to enable animation, but choose either left or right. You can set the usec value quite low [...] and it's usable.

Good call, that did the trick.

> **ayoli said:**
> Offtopic : shame that tilda does not have a true transparency like gnome-terminal.

With Compiz enabled under Gutsy this is easily remedied by opening the CompizConfig Settings Manager, going to the General settings, click on the Opacity tab, click on the Add button, and enter the following and set your desired opacity (mine is set to 85) .```
(title=^tilda$)
```

Cheers

---

### Post by ayoli on 2007-10-24
> **dustigroove said:**
> Good call, that did the trick.



With Compiz enabled under Gutsy this is easily remedied by opening the CompizConfig Settings Manager, going to the General settings, click on the Opacity tab, click on the Add button, and enter the following and set your desired opacity (mine is set to 85) .```
(title=^tilda$)
```

Cheers

yep i know that but that's not really the same, the output will also be transprent, not too much if you dont choose a too low opacity value, but gnome-term transparency does the transparency without changing output.

---

### Post by gubemton on 2007-12-06
Disable the "vsync to blank" display option in the general options menu of compizconfig settings manager.

---

### Post by avrelus on 2008-01-31
Hello, the solution may be installing new tilda version (0.9.5).
It works for me...

First uninstall old version and remove preferencies :
```
$ sudo aptitude purge tilda
$ rm -rf $HOME/.tilda
```

Install all of the dependencies:
```
$ sudo apt-get build-dep tilda
$ sudo apt-get install flex libglade2-dev
```

Download the source package of Tilda from [here]("http://downloads.sourceforge.net/tilda/tilda-0.9.5.tar.gz"). Then extract the tarball file:
```
$ tar zxvf tilda-0.9.5.tar.gz
```

Configure, build and install Tilda:
```
$ cd tilda-0.9.5/
$ ./configure
$ make
$ sudo make install
```

sources ([http://phorolinux.com/how-to-install-tilda-095-on-ubuntu-710-gutsy-gibbon.html](http://phorolinux.com/how-to-install-tilda-095-on-ubuntu-710-gutsy-gibbon.html))

---

### Post by xand on 2008-06-25
Just did that for the 0.9.6, still not going with the animation from the top.

---

