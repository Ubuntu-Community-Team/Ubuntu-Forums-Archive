---
title: "Can't change options in Compiz"
date: 2007-10-16
forum: Desktop Effects &amp; Customization
---

### Post by sgtkwol on 2007-10-16
I open ccsm and try to click and unclick options in there.  When I do, it doesn't respond.  If I try to edit the settings for that option, it shows greyed out.  I have tried enabling/disabling plugins through gconf-edit, and that has no effect.  I have tried a full uninstall and reinstall, deleting the .compiz folder, still, nothing.  I had this problem with 7.04, same issue with 7.10.

---

### Post by Rupertronco on 2007-10-16
Some options are grayed out in gutsy because they're not stable and not installed. Which plugins are you referring to?

---

### Post by sgtkwol on 2007-10-17
All plugins are unable to be checked or unchecked, same thing was happening in 7.04.

---

### Post by cwhitehouse on 2007-10-17
Does your video card support Compiz?

---

### Post by Rupertronco on 2007-10-17
More specifically what video card do you have? Do you have XGL installed if you have ATi? Need some more info.

---

### Post by sgtkwol on 2007-10-17
Yes, I have it running, at times, and it runs the cube and everything, but I am unable to check the option for windows decorations, or uncheck/check other plugins in ccsm.

---

### Post by Rupertronco on 2007-10-18
That sounds like a compiz install problem, but if you're using gutsy you should have the default install. Did you alter it or install new plugins? Also I'd suggest installing the version of Gutsy that was released today.

---

### Post by Forlong on 2007-10-18
Could be an authorizations issue. Did you run ccsm at any time being root?
Try this:
```
sudo chown $USER:$USER $HOME -R
```
Then:
```
chmod -R u+rwX $HOME
```

---

### Post by sgtkwol on 2007-10-19
I ran both of those commands, same issue.  I tried running ccsm in root, just to see, same issue.  I have tried complete removal through synaptic and reinstall.  Is there a more thorough way to remove compiz and reinstall?

---

### Post by drdrewusaf on 2007-10-19
Can you at least go into the plugins' settings?  If so, you need to click the "Preferences" button and in the "Plugin List" tab check the "Automatic plugin sorting" box.  This will allow you to turn plugins on/off.


Drew

---

### Post by yinglcs2 on 2007-10-19
HI,

I have problem even starting ccsm. Can you please help?

I tried:
# ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

---

### Post by sgtkwol on 2007-10-19
That may be it.  I'm not at home right now, but it may be simple enough to work.

---

### Post by Doctoxic on 2007-10-19
> **yinglcs2 said:**
> HI,

I have problem even starting ccsm. Can you please help?

I tried:
# ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

i have the same problem:
doctoxic@linux:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

can't run the config settings at all

doc

---

### Post by sgtkwol on 2007-10-19
> **drdrewusaf said:**
> Can you at least go into the plugins' settings?  If so, you need to click the "Preferences" button and in the "Plugin List" tab check the "Automatic plugin sorting" box.  This will allow you to turn plugins on/off.


Drew
Not sure what you mean by the preferences tab, are you talking about in the "General" section in ccsm?  Or is this somewhere else?

---

### Post by burgoy on 2007-10-19
i also have this problem.. i only encountered this problem after installing kiba-dock.. things are all ok before i install kiba-dock.. i also tried reinstalling everything.. still end up at the same problem..:(

---

### Post by Hoosier205 on 2007-10-19
Same problem here...

---

### Post by AN@S on 2007-10-20
> **yinglcs2 said:**
> HI,

I have problem even starting ccsm. Can you please help?

I tried:
# ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

I have the same problem ... any help? :confused:

---

### Post by themusicwave on 2007-10-20
I too get the following:

 File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

I installed avant-window-navigator

I have no idea if it is related.

I do have to say the defaults look pretty good, though I would like to tweak them.

---

### Post by Quickdood on 2007-10-20
> **Forlong said:**
> Could be an authorizations issue. Did you run ccsm at any time being root?
Try this:
```
sudo chown $USER:$USER $HOME -R
```
Then:
```
chmod -R u+rwX $HOME
```

I tried running ccsm as root and I was able to edit the options:

I did: gksudo ccsm

Now I tried the code you said, replaced $USER with $quickdood which is my root name but still no luck, any sugestions?

---

### Post by Quickdood on 2007-10-20
I think I figured it out, open advanced desktop settings manager goto prefernces, goto the plugin list tab, and then click the check box that says "automatic plugin sorting, now I can select text boxes without being in root!

---

### Post by themusicwave on 2007-10-20
Strangely I don't even have Advanced Desktop Setting Manager on my menu.

I tried uninstalling and reinstalling it.  Still no showing up.

All I have is CompizConfig Settings Manager under preferences.  This however does nothing, when I look at it's command, it calls ccsm.  When I call ccsm even as sudo it still simply fails and gives me the errors posted above.

Any ideas?

The strange thing I was able to get into the settings manager esterday when I first upgraded.  I wonder what's going on....

---

### Post by mohnkern on 2007-10-20
I'm seeing exactly the same problem.  How do you open the "advanced Desktop Settings Manager"  I can't find it anywhere in the menus.

---

### Post by Doctoxic on 2007-10-20
> **mohnkern said:**
> I'm seeing exactly the same problem.  How do you open the "advanced Desktop Settings Manager"  I can't find it anywhere in the menus.

is it this:

system
preferences
appearances
visual effects tab

or something else??

if i then click on preferences nothing happens though


doc

---

### Post by sgtkwol on 2007-10-20
Same issue, I click on the advanced preferences, but that just links to ccsm.

---

### Post by Quickdood on 2007-10-20
> **sgtkwol said:**
> Same issue, I click on the advanced preferences, but that just links to ccsm.

Advanced desktop effects settings is ccsm, just named differently in Gutsy.  If you don't have the advanced preferences Icon goto the package manager and install compizconfig-settings-manager.  Now go into the Advanced desktop effects settings which is ccsm and then click preferences, then goto the plugin list and check automatic plugin sorting.  This should allow you to use the check boxes  in the main menus.

good luck

---

### Post by sgtkwol on 2007-10-20
Finally got it :)

---

### Post by Quickdood on 2007-10-20
I am happy to hear that, now you can begin to enjoy the upgrade! :)

---

### Post by themusicwave on 2007-10-21
I still haven't got it so please post your solution.

It will not load from command line, menus or preferences within Appearance.

So no luck here...

---

### Post by Doctoxic on 2007-10-21
> **Quickdood said:**
> Advanced desktop effects settings is ccsm, just named differently in Gutsy.  If you don't have the advanced preferences Icon goto the package manager and install compizconfig-settings-manager.  Now go into the Advanced desktop effects settings which is ccsm and then click preferences, then goto the plugin list and check automatic plugin sorting.  This should allow you to use the check boxes  in the main menus.

good luck

my compizconfig-settings-manager is and has been installed :(

doc

---

### Post by NS2-10 on 2007-10-21
Hey!

Same problem here. I have tried over and over again to install ccsm but I still get the same error each time I try to run it, either its in terminal or from "Preference->Appearance->Visual Effects Tab->Custom Effects Preference Button"

I get the same output from terminal as everyone else in here.

About going into "Preferences->Plugin List" I dont have a list like that in preferences. Is it referring to something inside ccsm? If so, its an utterly useless tip since most of us aren't even able to start ccsm.

Please help!! I was so happy with my beryl effects in Feisty and now I thought, YEAI, Gutsy, now things'll be even better. Instead they it looks old and boring. Not good! NOT GOOD!

Help!

---

### Post by mohnkern on 2007-10-21
Ditto here.  I've installed the compizconfig-settings-manager but when I run ccsm I get:


Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

Going into the preferences, if I try to turn on the enhanced effects, I get an error, saying it couldn't turn it on, because a "string was expected."

---

### Post by bobbob1016 on 2007-10-21
Go here: [http://forum.compiz-fusion.org/showthread.php?p=32526](http://forum.compiz-fusion.org/showthread.php?p=32526)
and follow Kubist's post.

NS2-10, from your sig, you have an ATI x1400.  You should install the proprietary driver and use XGL.  Neither of which I can help with.  I know this since I have an x600 in my desktop, and I looked into if I should, and it said x1xxx or greater, I think 200m or greater on laptops.

---

### Post by sgtkwol on 2007-10-21
click on preferences in the left hand side, then enable your plugins from there

---

### Post by KClough on 2007-10-21
I had the same problem. I removed the compizconfig-settings-manager. package and then reinstalled it . I can access CCSM now.

---

### Post by damir_1105 on 2007-10-21
if you updated to gutsy from feisty probably you use compiz from that repositories. try this:

synaptic package manager -> select compizconfig-settings-manager -> Menu -> Package -> Force Version then use 0.5.2 instead 0.6.99.

---

### Post by themusicwave on 2007-10-21
> **damir_1105 said:**
> if you updated to gutsy from feisty probably you use compiz from that repositories. try this:

synaptic package manager -> select compizconfig-settings-manager -> Menu -> Package -> Force Version then use 0.5.2 instead 0.6.99.


That fixed it thanks!!!

The fnny thing is now Ubuntu is buggin me to upgrade the package......I guess I should ignore that right?

Thanks again for your help, now all my Gutsy problems(all 2 of them) are solved!

---

### Post by damir_1105 on 2007-10-22
> **themusicwave said:**
> That fixed it thanks!!!

The fnny thing is now Ubuntu is buggin me to upgrade the package......I guess I should ignore that right?

Thanks again for your help, now all my Gutsy problems(all 2 of them) are solved!

now select that version for gutsy 0.5.2 and in meni -> package > force version and he will not ask to upgrade.

---

### Post by NS2-10 on 2007-10-22
I thought that Gutsy ran every session as XGL regardless of card and settings?

---

