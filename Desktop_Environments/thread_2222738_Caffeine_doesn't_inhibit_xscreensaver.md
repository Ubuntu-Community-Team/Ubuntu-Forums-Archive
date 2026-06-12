---
title: "Caffeine doesn't inhibit xscreensaver"
date: 2014-05-07
forum: Desktop Environments
---

### Post by peterx14 on 2014-05-07
Hi all,

I'm just test-installing Ubuntu 14.04 (64bit), and I can't get Caffeine to work!

I've purged gnome-screensaver and installed xscreensaver but caffeine won't work. I know in a previous version, there was an issue if you install caffeine and ***then*** install xscreensaver and caffeine configured itself during installation... I did the installs in the wrong order again, but I've since tried to purge and re-install caffeine in case that was causing a problem.

I'm working with caffeine from the official PPA - ppa:caffeine-developer/ppa which is version 2.6.2.

I've also tried caffeine 2.5 from a DEB, but that didn't work either!

Clearly caffeine has changed a lot in recent versions as mentioned in the bug report:
[https://bugs.launchpad.net/caffeine/+bug/1266953](https://bugs.launchpad.net/caffeine/+bug/1266953)

...but I get the impression that it _should_ be working now.

Can anyone help?!

Thanks in advance! :D

Peter.

---

### Post by peterx14 on 2014-05-08
I've just removed the old PPA and switched to [Paulius Vitkus's PPA]("https://launchpad.net/~behda/+archive/ppa")... and that didn't work either!

```
$ sudo apt-get purge caffeine
$ sudo apt-get autoremove
$ sudo add-apt-repository --remove ppa:caffeine-developers/ppa
$ sudo add-apt-repository ppa:behda/ppa
$ sudo apt-get update
$ sudo apt-get install caffeine
```

I assume therefore that Caffeine thinks I've got gnome-screensaver (or something else) installed and is not noticing that xscreensaver is active?

Has anyone else managed to get Caffeine working on Ubuntu 14.04 with xscreensaver?

---

### Post by peterx14 on 2014-05-08
I've got it working!!! :D

I configured [Jeffery To's Faux Gnome Screensaver]("https://github.com/jefferyto/faux-gnome-screensaver")... but at the time I was still using Caffeine from Paulius Vitkus's PPA, and it didn't work. So I purged that Caffeine, removed that PPA, re-added the caffeine-developers PPA, re-installed Caffeine and it worked - finally!

Based on the[ comments here]("https://bugs.launchpad.net/caffeine/+bug/1266953"), I guess that means Caffeine will work on it's own once xdg-screensaver has been updated.

---

### Post by oldos2er on 2014-05-08
Thanks for sharing the solution to your problem. Would you please mark the thread as 'Solved' under Thread Tools?

---

### Post by memilanuk on 2014-05-09
> **peterx14 said:**
> I've got it working!!! :D

I configured [Jeffery To's Faux Gnome Screensaver]("https://github.com/jefferyto/faux-gnome-screensaver")... but at the time I was still using Caffeine from Paulius Vitkus's PPA, and it didn't work. So I purged that Caffeine, removed that PPA, re-added the caffeine-developers PPA, re-installed Caffeine and it worked - finally!

Based on the[ comments here]("https://bugs.launchpad.net/caffeine/+bug/1266953"), I guess that means Caffeine will work on it's own once xdg-screensaver has been updated.


Okay, I'm having similar problems - updated from Ubuntu 13.10 to Xubuntu 14.04 and caffeine stopped working :(

What I'm seeing is that you went thru a bunch of different PPAs for caffeine and/or screensavers, and ended up back at the original caffeine-developers ppa, and now it magically works?  Or am I missing something here?

---

### Post by peterx14 on 2014-05-09
> **memilanuk said:**
> Okay, I'm having similar problems - updated from Ubuntu 13.10 to Xubuntu 14.04 and caffeine stopped working :(

What I'm seeing is that you went thru a bunch of different PPAs for caffeine and/or screensavers, and ended up back at the original caffeine-developers ppa, and now it magically works?  Or am I missing something here?

**SUMMARY:**
Firstly, what I believe the problem is - [based on comments here]("https://bugs.launchpad.net/caffeine/+bug/1266953") - is that Caffeine has had a lot of code removed to simplify it but it turns out not everything plays by the freedesktop specs. So it doesn't work! There's a patch to xdg-screensaver in the pipeline, but that doesn't appear to be on Ubuntu 14.04 yet, however, using [Jeffery To's Faux-Screensaver]("https://github.com/jefferyto/faux-gnome-screensaver"), this problem can be "worked around".

**THINGS THAT MIGHT BE IMPORTANT:**
For my testing, I'm doing a fresh install - not an upgrade. For your upgrade, I'd guess you were previously running Caffeine from the normal Caffeine PPA ([ppa:caffeine-developers/ppa]("https://launchpad.net/~caffeine-developers/+archive/ppa")), and I'd also guess that the Ubuntu installer will have disabled that PPA during upgrade. I might be wrong about this though!

I'm also guessing you already had xscreensaver installed. And probably you had already removed the gnome-screensaver package... but it's possible that the Ubuntu upgrade will have reinstalled this.

So your circumstances are a little different to mine!

**WHAT TO DO:**
Probably worth removing and reinstalling a few bits to make sure we're in the right place:

```

sudo apt-get purge caffeine
sudo apt-get autoremove

```
Next, go to System Settings -> Brightness and Lock, and change **Turn screen off when inactive** to **Never**
```

sudo apt-get purge gnome-screensaver
sudo apt-get install xscreensaver xscreensaver-gl-extra xscreensaver-data-extra

```
You might now like to search for "screensaver" in the Applications lens of dash and set what xscreen savers you want and the timeout you'd like... but I think the default is something sensible like 10 minutes.

If you have a Caffeine related PPA active that isn't the "official" one: [ppa:caffeine-developers/ppa]("https://launchpad.net/~caffeine-developers/+archive/ppa"), then you should remove it, e.g. if you were using Paulius Vitkus's PPA, then remove it using:
```

sudo add-apt-repository --remove ppa:behda/ppa
sudo apt-get update

```
And next, if the official Caffeine PPA is not active, re add it:
```

sudo add-apt-repository ppa:caffeine-developers/ppa
sudo apt-get update

```
And now we re-install Caffeine:
```

sudo apt-get install caffeine

```
And at this point, things *should* work... but they don't, and I believe that's because we're waiting for an updated xdg-screensaver. So to get around this problem, we use Jeffery To's code:
```

mkdir -p /tmp/fauxgs && cd /tmp/fauxgs
wget -O- https://github.com/jefferyto/faux-gnome-screensaver/archive/master.tar.gz | tar -xpzf -
sudo cp faux-gnome-screensaver-master/faux-gnome-screensaver*.py /usr/local/bin/
cd /usr/local/bin/
sudo ln -s faux-gnome-screensaver.py gnome-screensaver
sudo ln -s faux-gnome-screensaver-command.py gnome-screensaver-command

```
Open Startup Applications (gnome-session-properties) and click Add and enter:
[INDENT]**Name:** Faux Screensaver
**Command:** gnome-screensaver
**Comment:** Makes xscreensaver and caffeine play nicely.
[/INDENT]

NOTE: If you've already got an xscreensaver startup-application entry, you can remove it (or just uncheck it) because the faux-screen-saver will start xscreensaver itself.

And that should do it! One slight-snag that I've noticed is that sometimes instead of a screen saver, the monitor switches off. I could be wrong, but I suspect this happens every other time the screen saver should start... I'm still playing with that one. But the main thing (for me anyway) is being able to disable the screensaver when watching videos. I've not had much chance to test it yet though, but it did seem to automatically inhibit the screensaver when watching flash video through Firefox... dunno if Caffeine is detecting flash and/or full screen activity but whatever, it did stop the screensaver without me even needing to toggle the indicator icon.

Hope this works for you... 'cos I haven't got any other ideas!!

---

### Post by memilanuk on 2014-05-09
Actually... what I have is a fresh install of Xubuntu 14.04.  I tend to do a wipe-n-clean-reinstall for the LTS versions.

No screen saver installed.  Generally don't need/want one.

What I want - and what I had, previously - is where I can, when running on the battery and need the display to stay on, not dim, and not go to sleep until the battery is just about flat and the whole machine shuts down on low battery anyway.  That was what I used caffeine for previously.  Now, when I had it installed (fresh install from the caffeine-developers/ppa) ... nothing happens when I toggle 'Disable screensaver'.  Previously it worked as expected.  Now it doesn't.

---

### Post by chili_g on 2014-05-10
This isn't 100% what you are asking but it may help.  It's what I did because of another issue I was having with Caffeine in 14.04 (v2.6 doesn't appear to monitor specific applications anymore).

Basically I just downloaded the 2.5 tarball and it just works - ./bin/caffeine -  on 14.04 (and I can still auto-disable based on certain apps).

It's just a python script.  There may be some dependencies I got by installing the 2.6 from the PPA - so you might need to do that if it doesn't work right off the bat.

---

### Post by hako1 on 2014-06-09
> **peterx14 said:**
> **SUMMARY:**
Firstly, what I believe the problem is - [based on comments here]("https://bugs.launchpad.net/caffeine/+bug/1266953") - is that Caffeine has had a lot of code removed to simplify it but it turns out not everything plays by the freedesktop specs. So it doesn't work! There's a patch to xdg-screensaver in the pipeline, but that doesn't appear to be on Ubuntu 14.04 yet, however, using [Jeffery To's Faux-Screensaver]("https://github.com/jefferyto/faux-gnome-screensaver"), this problem can be "worked around".

...

And at this point, things *should* work... but they don't, and I believe that's because we're waiting for an updated xdg-screensaver. So to get around this problem, we use Jeffery To's code:
```

mkdir -p /tmp/fauxgs && cd /tmp/fauxgs
wget -O- https://github.com/jefferyto/faux-gnome-screensaver/archive/master.tar.gz | tar -xpzf -
sudo cp faux-gnome-screensaver-master/faux-gnome-screensaver*.py /usr/local/bin/
cd /usr/local/bin/
sudo ln -s faux-gnome-screensaver.py gnome-screensaver
sudo ln -s faux-gnome-screensaver-command.py gnome-screensaver-command

```

Open Startup Applications (gnome-session-properties) and click Add and enter:[INDENT]**Name:** Faux Screensaver
**Command:** gnome-screensaver
**Comment:** Makes xscreensaver and caffeine play nicely.
[/INDENT]

NOTE: If you've already got an xscreensaver startup-application entry, you can remove it (or just uncheck it) because the faux-screen-saver will start xscreensaver itself.

And that should do it! One slight-snag that I've noticed is that sometimes instead of a screen saver, the monitor switches off. I could be wrong, but I suspect this happens every other time the screen saver should start... I'm still playing with that one. 
...

Using Caffeine 2.5 (with auto-detection of certain programs running, and possibility for manual inhibition) in 14.04, the inhibition works, the screen stays on and no screensaver comes up.
However, when caffeine is not inhibiting, unfortunately, that monitor turn-off is the only thing that happens, always. xscreensaver does not show up.
Any idea?

---

### Post by hako1 on 2014-06-13
Status should not be solved. The original problem was only "solved" at the cost of having no screensaver.
And that is no solution, because without a screensaver, you also don't need Caffeine.

---

### Post by gannet2 on 2015-03-24
I'm running Linux Mint 17.1 with xfce (Ubuntu 14.04) and had a problem with XScreenSaver interrupting my videos.  I tried Caffiene from the developers and it worked straight away:

>     sudo add-apt-repository ppa:caffeine-developers/ppa
    sudo apt-get update
    sudo apt-get install caffeine

After that, you just need to run caffeine or stick it in autostart.  The current version doesn't have a graphical interface, it now runs invisibly in the background and inhibits the screensaver WHENEVER THE MACHINE IS IN FULL SCREEN MODE.  There don't seem to be any options but it certainly does what I want!

---

