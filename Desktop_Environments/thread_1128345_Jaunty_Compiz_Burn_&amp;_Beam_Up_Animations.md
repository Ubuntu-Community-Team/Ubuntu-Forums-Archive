---
title: "Jaunty Compiz Burn &amp; Beam Up Animations?"
date: 2009-04-17
forum: Desktop Environments
---

### Post by jg1395 on 2009-04-17
Jaunty Compiz Burn & Beam Up Animations?  Are these missing for some odd reason?

---

### Post by leonardo_neo on 2009-04-17
No they are not missing and I have enabled them on my comp. If you need to know how to install them, then follow the link....

[http://ubuntuforums.org/showthread.php?t=1126175]("http://ubuntuforums.org/showthread.php?t=1126175")

---

### Post by jg1395 on 2009-04-17
no Burn & Beam up in Jaunty clean install?

compiz-fusion-plugins-extra is installed.

---

### Post by leonardo_neo on 2009-04-17
> **jg1395 said:**
> no Burn & Beam up in Jaunty clean install?

compiz-fusion-plugins-extra is installed.

I am sorry, but I am not getting what you want to say? Have you tried to enable 'animation' and "animation add on"? Have you tried to enable burn and beam effect the way I mentioned in the link??

---

### Post by jg1395 on 2009-04-18
Yes i've been using compiz for a long while... they aren't listed in the animations section of the manager.

Other animations like dodge effect are working fine.

I only have 11 animations.  I know there is way more than that.
Should i add a custom source list and try to pull from it?
If so which one.

---

### Post by Genesius on 2009-04-20
I had the same issue. Fixed it by going into Synaptic & purging compiz-fusion-plugins-main, extra, and unsupported and then reinstalling them.

---

### Post by acebrain01 on 2009-04-20
> Have you tried to enable 'animation' and "animation add on"?  
The only problem is there is no Animation Add on in CCSM. And yes compiz-fusion-plugins-extra is installed.

---

### Post by acebrain01 on 2009-04-20
> **Genesius said:**
> I had the same issue. Fixed it by going into Synaptic & purging compiz-fusion-plugins-main, extra, and unsupported and then reinstalling them.

Will try when I get home tonight.


Did not fix issue. complete uninstall of plugins and compiz fixed nothing.

---

### Post by thethimble on 2009-04-21
I'm having the same problem. Reinstall of compiz-fusion-plugins-extras didn't work.

It was working fine yesterday... Then the burn animation (amongst others) just disappeared...

Plus there isn't any animation addons in CCSM.

---

### Post by jg1395 on 2009-04-22
Problem solved for me.

Not 100% sure what i did...  my best guess is i went into system -> preferences -> appearance -> visual effects -> extra & rebooted.

so much for sudo & ccsm :lolflag:

---

### Post by ubman on 2009-04-22
I have found that "simple ccsm"
is easier and always works.
"sudo apt-get install simple-ccsm"
After installed is found under system>preferences>simple config compiz-settings.:popcorn:

---

### Post by tdeboeser on 2009-04-24
I too have the problem... I miss my burn.  Did everything in this thread, no luck.  So far my other effects still work after upgrade to 9.04 64-bit.  I can't remember if burn was working directly after the upgrade.

:(

Tom de

---

### Post by Zoowey on 2009-04-24
I too have this problem and I have tried everything in this forum but I just can't get the "Animations Add-on" tab to show in the compiz settings manager. I used Intrepid for 2 months and had it working perfectly then when I upgraded to Jaunty it still worked. Then one day, when I turned on my computer, bam, some of my animations just disappeared. It's just strange and I simply can't explain it.

[[IMG]http://img49.imageshack.us/img49/7534/screenshotcompizconfigsd.th.png[/IMG]](http://img49.imageshack.us/img49/7534/screenshotcompizconfigsd.png)

---

### Post by Zoowey on 2009-04-24
Ok guys, I think I've figured out the problem. I have been using the 3rd party Compiz repository, when I upgraded to Jaunty there was an update to a compiz package which then made the "Animations Add-on" tab disappear. 

So what I did is disable the 3rd party compiz repository, reloaded my sources, went into synaptic and searched for "compiz-fusion" I then marked both "compiz-fusion-plugins-main and "-extra" for "complete removal" then logged out and logged back in and then installed those 2 again and it worked. So basicly disable the 3rd party compiz repository, uninstall those 2 packages and reinstall them making sure the 3rd party repository is disabled.

I hope this helps you guys.

---

### Post by ESM on 2009-04-26
This one worked in Jaunty. Thanks man!

---

### Post by tdeboeser on 2009-04-27
I tried Zoowey's fix but it didn't help me.  I think it had to do with session/config settings.  I also notice my sidekick, wave ( focus animation ), and some other effects were not working - but some did.  


After doing a "complete removal" of compiz-fusion-plugins-main and extra's, logging out, and re-installing - I still  didn't have burn or the other effects working.  

More googling found the last post in this thread:

[http://ubuntuforums.org/showthread.php?t=767467&page=2](http://ubuntuforums.org/showthread.php?t=767467&page=2)

Basically, setting your chosen effect (close animation, minimize, etc.) back to default with the "brush/cleanup" icon.  Then choosing the effect of you choice.  The change is immediate.
 
Afterwards I recalled my compiz animation settings were still in place ( i.e. longer burn time, more particles, etc. ), after the "complete removal" of the compiz-fusion-plugin-main and extra.  

Seems to be a weird upgrade issue, the thread above is from the ubuntu version upgrade to 8.04.

Tom de

---

### Post by thethimble on 2009-04-28
> **Zoowey said:**
> Ok guys, I think I've figured out the problem. I have been using the 3rd party Compiz repository, when I upgraded to Jaunty there was an update to a compiz package which then made the "Animations Add-on" tab disappear. 

So what I did is disable the 3rd party compiz repository, reloaded my sources, went into synaptic and searched for "compiz-fusion" I then marked both "compiz-fusion-plugins-main and "-extra" for "complete removal" then logged out and logged back in and then installed those 2 again and it worked. So basicly disable the 3rd party compiz repository, uninstall those 2 packages and reinstall them making sure the 3rd party repository is disabled.

I hope this helps you guys.

You, sir... are a genius...

Thank you SO much! (I totally forgot I enabled the third party compiz repo)

---

### Post by quall on 2009-05-01
Thanks, that worked for me too. The Animation-Addon plug-in appeared and all started working great.

---

### Post by reefdiver5 on 2009-05-01
I had the same problem with the upgrade, I was able to get the animation add-on tab to come back by turning off the 3rd party repo and reinstalling the compiz plugins packages.  However I also had to clear the package cache so it would redownload the package from the new source.  I did this through ubuntu tweak but I think it can be done elswhere (not exactly sure where)

---

### Post by rotary12 on 2009-05-02
Zoowey


it worked thanks,good one

---

### Post by stanca on 2009-05-08
Worked for me too.Thank you very much.:)

---

### Post by firebug2 on 2009-05-08
I also had the third-party repositories enabled.  When I disabled them, compiz-fusion-plugins-extra was stuck on the version from there (guess because it was 0.8.2-0ubuntu1.2, higher than official 0.8.2-0ubuntu1).  I didn't try complete removal because that suggested removing compiz.  What worked was using the "force version" option to "downgrade" to official release.  Fire is back!

---

### Post by hariks0 on 2009-09-09
> **Zoowey said:**
> Ok guys, I think I've figured out the problem. I have been using the 3rd party Compiz repository, when I upgraded to Jaunty there was an update to a compiz package which then made the "Animations Add-on" tab disappear. 

So what I did is disable the 3rd party compiz repository, reloaded my sources, went into synaptic and searched for "compiz-fusion" I then marked both "compiz-fusion-plugins-main and "-extra" for "complete removal" then logged out and logged back in and then installed those 2 again and it worked. So basicly disable the 3rd party compiz repository, uninstall those 2 packages and reinstall them making sure the 3rd party repository is disabled.

I hope this helps you guys.

Great post... Thank U veryyyyyyyyy much. Please publish this with titiles like "Missing Animations add-on" or "where are the effects o compiz gone" so that people will find it easy to reach.

Thank u hundred times again !

---

### Post by Curbuntu on 2009-09-15
> **Zoowey said:**
> So what I did is disable the 3rd party compiz repository, reloaded my sources, went into synaptic and searched for &quot;compiz-fusion&quot; I then marked both &quot;compiz-fusion-plugins-main and &quot;-extra&quot; for &quot;complete removal&quot; then logged out and logged back in and then installed those 2 again and it worked. So basicly disable the 3rd party compiz repository, uninstall those 2 packages and reinstall them making sure the 3rd party repository is disabled.  This, indeed, worked perfectly for the problem I was having in 9.04.  I think I must have turned on the 3rd-party repository via Ubuntu-Tweak, not knowing what I was doing.  Thank you, Zoowey.

---

### Post by Sambie on 2009-11-07
I was having the same exact problem (I've upgraded from Jaunty to Kermic Koala ) and did what you did and it worked for me, thanks Zoowey :)


> **Zoowey said:**
> Ok guys, I think I've figured out the problem. I have been using the 3rd party Compiz repository, when I upgraded to Jaunty there was an update to a compiz package which then made the "Animations Add-on" tab disappear. 

So what I did is disable the 3rd party compiz repository, reloaded my sources, went into synaptic and searched for "compiz-fusion" I then marked both "compiz-fusion-plugins-main and "-extra" for "complete removal" then logged out and logged back in and then installed those 2 again and it worked. So basicly disable the 3rd party compiz repository, uninstall those 2 packages and reinstall them making sure the 3rd party repository is disabled.

I hope this helps you guys.

---

### Post by stinkeye on 2009-11-07
For those who like the tile plugin this worked for me on karmic.
[_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=8248487&postcount=20[/COLOR]_]("http://ubuntuforums.org/showpost.php?p=8248487&postcount=20")
There may be other updates from the compiz repo but only update
compiz-fusion-plugins-unsupported.
So basically for me to get burn and beam to work I down loaded compiz-fusion-plugins-extra from the ubuntu repos
and for tiling to work I downloaded compiz-fusion-plugins-unsupported from
the compiz repo

---

