---
title: "Firefox 1.5.0.3 crash"
date: 2006-06-02
forum: Desktop Environments
---

### Post by Lux Perpetua on 2006-06-02
I just experienced a Firefox crash. I wasn't doing anything fancy; in fact, I was trying to write a howto for this forum. There was no error report of any kind; the window simply closed itself silently. (Yes, I lost all my work.)

Is this a known issue?

---

### Post by hotani on 2006-06-02
It seems to happen quite a bit, I've experienced it several times. Someone in another thread suggested running FF from the terminal so you can get some feedback next time it crashes.

---

### Post by CronoDekar on 2006-06-02
Interestingly, I've been getting the same problems, except with Opera.  I think I had Firefox open when it's closed too (though I'm not sure), so that may have something to do with it.

---

### Post by aysiu on 2006-06-02
See if [this](http://www.ubuntuforums.org/showthread.php?t=103930) makes a difference.

---

### Post by hotani on 2006-06-03
I just ended a session initiated from CLI which ran for a few hours. No crash, but there were some hic-ups:

```

GTK Accessibility Module initialized

(Gecko:5400): GLib-GObject-WARNING **: gsignal.c:1017: unable to lookup signal " activate" of unloaded type `MaiAtkObject'

(Gecko:5400): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `signal_ id > 0' failed

(Gecko:5400): GLib-GObject-WARNING **: gsignal.c:2269: signal name `link_selected' is invalid for instance `0xa35c400'

(Gecko:5400): GLib-GObject-WARNING **: gsignal.c:2269: signal name `link_selected' is invalid for instance `0x8c8f650'

(Gecko:5400): GLib-GObject-WARNING **: gsignal.c:2269: signal name `link_selected' is invalid for instance `0xb238050'

```

---

### Post by blueturtl on 2006-06-03
Firefox and Mozilla crashing in Ubuntu seems to be the most common known issue that annoys people. There have been numerous posts on the subject and nobody seems to be able to pinpoint a direct cause for the crashing. Terminal output most of the time is Segfault. The Windows version of Firefox doesn't crash as often, but then again the Windows version also has more mature plug-ins.

So here:

1. Check your installed plug-ins. Check that they are installed and configured correctly and that you are using the latest versions. I have noticed for example that the mplayerplug-in seems to be relevant to a lot of Firefox crashes.

2. Check that your userprofile isn't corrupt. Instructions on how to check and create a new profile have already been posted above.

3. Finally (and note this especially if Firefox isn't the only program that is misbehaving) check that your RAM is using proper timings and that it is good quality. Poor quality RAM or overclocked RAM often causes weird and most definately inconsistent behaviour. Some applications are more sensitive to RAM errors than others.

---

### Post by wmcbrine on 2006-06-03
I just went to Dapper and FF 1.5 this morning, and I had this happening every time I went to Gmail. So I set Gmail to use the plain HTML interface (which is faster anyway... I dunno why I don't just leave it that way), and so far, no other problems.

In my case, I was kind of assuming it was because my profile was suffering from bit rot, after upgrading all my extensions. See, that's just what happened to me before, on Windows, with FF 1.x -- problems with Gmail (hanging instead of crashing), unless I switched to plain HTML. I eventually made a new profile (installing extensions from scratch, copying over bookmarks.html, etc.), and the problem went away.

FF 1.5 on my Mac is giving me trouble, too...

---

### Post by Lux Perpetua on 2006-06-03
[QUOTE=wmcbrine]I just went to Dapper and FF 1.5 this morning, and I had this happening every time I went to Gmail. So I set Gmail to use the plain HTML interface (which is faster anyway... I dunno why I don't just leave it that way), and so far, no other problems.[/QUOTE]So is it related to...javascript? Because I was using the post editor of this forum when it crashed, which seems to use a lot of javascript.

---

### Post by wmcbrine on 2006-06-03
I believe it is, somehow. (This also fits with the "corrupt profile" idea, in that the extensions are mostly javascript.) However, I have no problem (so far) with the post editor, while my Gmail crashes are totally reproducible.

---

### Post by vrih on 2006-06-03
The google toolbar extension has been making my firefox crash.

---

### Post by Ultraviolence on 2006-06-04
I have had my Firefox crashing on GMail, regardless of if I am using a fresh profile or not, and regardless of what extensions I use.

---

### Post by sinfree on 2006-06-05
Firefox crashes for no apparent reason on random sites.  It just goes away.  Needless to say, since this is a machine I built for my mom to surf the web, etc, this is quite a big problem.  Yeah, I know there are other browsers, but I want to use this one, as it seems to be the most compatible and best for her to use.

---

### Post by zikki on 2006-06-05
[QUOTE=blueturtl]

2. Check that your userprofile isn't corrupt. Instructions on how to check and create a new profile have already been posted above.
[/QUOTE]

OMG, did as you'd said and lost all my settings with extensions. 
You can do the same by purging firefox and installing it back.

---

### Post by gotthardt on 2006-06-05
I was having random disappearing FF probs. I went to synaptic and marked FF for re-installation. I 'think' it helped because I dont see it as often now.

Steve

---

### Post by lolocaust on 2006-06-06
Firefox crashes my entire system, and I have to press the power button. It always happens while a page is loading. :(

---

### Post by ZipoTe on 2006-06-06
wow! more people with problems runnig FF... here is another post taliking about FF crashes but when opening flash applications

[http://www.ubuntuforums.org/showthread.php?t=187207]("http://www.ubuntuforums.org/showthread.php?t=187207")

we need functional FF, with java and flash support!!

let's work ;)

---

### Post by mlind on 2006-06-06
Most of the FF crashes are due badly implemented extensions. I'm running only with
Adblock, All-in-one gestures and Tabbed prefs and I haven't had a single crash yet.

---

### Post by srunni on 2006-06-06
Try going here: [http://ubuntuforums.org/showthread.php?t=186337&highlight=firefox+1.5.0.4](http://ubuntuforums.org/showthread.php?t=186337&highlight=firefox+1.5.0.4)

and using the script available to update to Firefox 1.5.0.4. The problem you're having might be a bug that was fixed in the update.

---

### Post by magomago on 2006-06-07
i'll try that
i came here b/c i've beeen experiencing MANY MANY crashes after Dapper final I never had dating all the way back to Flight 5.

In fact, I thank god for crash recovery plug in because it is saving my butt so many times when I have 30 tabs open per window, and five windows or so

---

### Post by wmcbrine on 2006-06-07
[QUOTE=zikki]OMG, did as you'd said and lost all my settings with extensions.[/quote]Yeah, that's kind of the point of creating a new profile. You have to back up whatever you want to save, and reinstall your extensions.

> *You can do the same by purging firefox and installing it back.*No, actually you can't. Your profile is kept all in your home directory, while the Firefox binary package -- the part that's installed and uninstalled -- is kept all in /usr. You can remove and reinstall it without affecting your profile at all. So, if the problem is in your profile, it won't help.

---

### Post by wmcbrine on 2006-06-08
My Gmail crashes appear to be resolved by disabling the Flashblock extension. (I went through the process of creating a new profile, and it still crashed, until I disabled Flashblock. So I'm back on my old profile now...)

---

### Post by ZipoTe on 2006-06-09
My linux is crazy lol one day FF works correctly and the next day it doesn't 

I give up 8)

---

### Post by hotani on 2006-06-09
caught me a crash!!

```

(Gecko:14542): GLib-GObject-WARNING **: gsignal.c:2269: signal name `text_caret_moved' is invalid for instance `0x98a4e50'
./run-mozilla.sh: line 131: 14542 Segmentation fault      "$prog" ${1+"$@"}

```

---

### Post by Psquared on 2006-09-19
> **wmcbrine said:**
> I just went to Dapper and FF 1.5 this morning, and I had this happening every time I went to Gmail. So I set Gmail to use the plain HTML interface (which is faster anyway... I dunno why I don't just leave it that way), and so far, no other problems.

In my case, I was kind of assuming it was because my profile was suffering from bit rot, after upgrading all my extensions. See, that's just what happened to me before, on Windows, with FF 1.x -- problems with Gmail (hanging instead of crashing), unless I switched to plain HTML. I eventually made a new profile (installing extensions from scratch, copying over bookmarks.html, etc.), and the problem went away.

FF 1.5 on my Mac is giving me trouble, too...

Same problem. I even uninstalled the Gmail Manager extension and just went directly to gmail and FF just quits quietly. No complaints it just quits. I'm going to uninstall each extension until I find the one that is causing this. If that doesn't work then I'll try the profile thingy.

---

### Post by hotani on 2006-09-20
Another extension that will crash it every time is the del.icio.us tagger. If you hit 'return' in the tags list FF goes down in flames. Otherwise the extension works great, I just have to remember to tab down to the button rather than submitting via 'return'.

The random crashes are completely unpredictable and tend to happen when I have several tabs open and the browser has been up and running for several hours. Maybe it just gets tired...

---

### Post by Psquared on 2006-09-21
Hmmm.... I just got a kernel update "27" from "26" in Xubuntu and some others... and Xubuntu and FF work well together. I almost switched to Opera, but plugins don't work nearly as well.

I also have trouble with my IP configuration and DNS resolutions. I find I have to keep clicking on the link and it will finally go through. Sometimes it takes 3 -4 clicks. I know its not the website itself because it happens too much. I've even had to click the stop loading button and click again.

Anyone else experienced this? Happens with Swiftfox and Firefox. Not with Opera; but as I said, Opera seems to have more problems with Flash plugins and such.

---

