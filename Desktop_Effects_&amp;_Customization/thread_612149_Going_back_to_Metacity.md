---
title: "Going back to Metacity?"
date: 2007-11-13
forum: Desktop Effects &amp; Customization
---

### Post by RTrev on 2007-11-13
I'm unclear on the relationship between Metacity and Compiz.  If I go to System | Preferences | Appearance | Visual Effects, and then simply choose "None", am I then running Metacity again, or am I running a stripped-down Compiz?  It seems to behave a bit differently than the Feisty version, in that it doesn't remember window positions correctly and login is slow.  (I'm not sure if that's compiz' fault.)

Compiz holds no attraction for me, and I liked Metacity better, partly because it seemed faster and partly because it seemed to remember window positions better.  

Is Compiz "the future", so that going back to Metacity would ultimately be a dead-end road?

I'd like to clean off all of the compiz stuff, but experiments with a bare-bones install seemed to indicate that I had to have compiz installed in order to have any Window control.. e.g., being able to move windows, grabbing the border (which wasn't there), and so on.

Finally, how would I get back to Metacity without having compiz installed at all?  Why was I not able to do a minimal install that worked without having compiz installed?

Thanks,
Bob

---

### Post by ericesque on 2007-11-13
Just click 'none' in the effects options and you'll be back to metacity.

question:  were you using emerald with compiz fuzion?  I know things got shaky for me when I tried using emerald.  When I got rid of it, compiz fusion ran just fine again.  Yes, getting to the desktop after a reboot takes a bit longer, but the beauty of such a stable (in my experience) OS is that I never have to reboot.

No, I am certain that good ol' metacity will not be phased out.  Remember also that compiz fusion is still alpha software!  Many of the effects or plugins are not intended to be enabled by Ubuntu devs--who do consider stability.  They are well aware of the buggy pitfalls of doing so.  

In earnest, I wouldn't worry about a compiz-free install.  I'd just do the standard install and select 'none' like you mentioned.

---

### Post by RTrev on 2007-11-13
> **ericesque said:**
> Just click 'none' in the effects options and you'll be back to metacity.

question:  were you using emerald with compiz fuzion?  I know things got shaky for me when I tried using emerald.  When I got rid of it, compiz fusion ran just fine again.  Yes, getting to the desktop after a reboot takes a bit longer, but the beauty of such a stable (in my experience) OS is that I never have to reboot.

No, I am certain that good ol' metacity will not be phased out.  Remember also that compiz fusion is still alpha software!  Many of the effects or plugins are not intended to be enabled by Ubuntu devs--who do consider stability.  They are well aware of the buggy pitfalls of doing so.  

In earnest, I wouldn't worry about a compiz-free install.  I'd just do the standard install and select 'none' like you mentioned.

Thanks.  No, didn't try Emerald on this go around.  Just messed around with the Advanced Settings options to see if there was any way for it to remember window placements.

Unfortunately, using "None" seems to leave me with the same problem.  I can live with it, of course, but would prefer it the old way.

Bob

---

### Post by MNICY on 2007-11-13
Well, if you use synaptic package manager to remove all packages related to compiz from your OS, then it should not be able to use it at all ;)

---

### Post by RTrev on 2007-11-13
> **MNICY said:**
> Well, if you use synaptic package manager to remove all packages related to compiz from your OS, then it should not be able to use it at all ;)

Yeah, but then do I have to tell it somewhere to use metacity instead?  

Like I said, I tried to configure a basic system and couldn't get any window control until I installed compiz.  So it's got to be told somewhere, I presume, to use metacity?

---

### Post by amadeus266 on 2007-11-13
```
metacity --replace
```

---

### Post by RTrev on 2007-11-13
> **amadeus266 said:**
> ```
metacity --replace
```

That's it??  No sudo?  Jeez, that's too easy!  :)  Thanks.

---

### Post by RTrev on 2007-11-13
> **amadeus266 said:**
> ```
metacity --replace
```

Okay, I tried that command, but I have no idea what it's doing.  It seems to have worked, I guess, but it never returned me to a command prompt.  Should I Ctrl-C out of it and then save the session, then uninstall all of the compiz stuff?

Thanks,
Bob

---

### Post by amadeus266 on 2007-11-13
> **RTrev said:**
> Okay, I tried that command, but I have no idea what it's doing.  It seems to have worked, I guess, but it never returned me to a command prompt.  Should I Ctrl-C out of it and then save the session, then uninstall all of the compiz stuff?

Thanks,
Bob

It simply causes metacity to replace compiz. that's all and nothing more. I have a launcher on my panel that allows me with a single click to turn on or off compiz (read: switch back and forth between compiz and metacity) With the help of some others on this forum, I concocted a script that does just that and put a shortcut on my panel to point to it.


```
#!/bin/bash
if ps ax | grep -v grep | grep compiz.real > /dev/null
then
killall compiz.real && xfwm4 | metacity --replace
else
compiz --replace
fi
```

---

### Post by RTrev on 2007-11-13
> **amadeus266 said:**
> It simply causes metacity to replace compiz. that's all and nothing more. I have a launcher on my panel that allows me with a single click to turn on or off compiz (read: switch back and forth between compiz and metacity) With the help of some others on this forum, I concocted a script that does just that and put a shortcut on my panel to point to it.


```
#!/bin/bash
if ps ax | grep -v grep | grep compiz.real > /dev/null
then
killall compiz.real && xfwm4 | metacity --replace
else
compiz --replace
fi
```

That's cool.. I'll make a copy of that and save it somewhere.  In the meantime, I've uninstalled all of the compiz stuff, and am loving being back to metacity.  A couple of odd things going on, though.  Every now and then I find Nautilus eating all of one of my dual cores, and the top panel got odd in the properties.. the background color I'd chosen keeps changing.  Maybe I removed a tad too much.  <g>

Thanks... it feels much snappier now!

---

