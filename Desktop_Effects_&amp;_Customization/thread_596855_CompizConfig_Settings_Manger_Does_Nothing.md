---
title: "CompizConfig Settings Manger Does Nothing"
date: 2007-10-30
forum: Desktop Effects &amp; Customization
---

### Post by CLUGENHEIM on 2007-10-30
I've seen a lot of people ask this, but no truly helpful answers that I have found. I followed this guide: [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385) and did everything it said. (or I'm pretty sure I did.. heh) And when I click System > Preferences > CompizConfig Settings Manger nothing happens. 

Also, ever since I did that, the bar that has the minimize button and everything that is usually on the top of most/every app is GONE! :( 

*sigh* this is really annoying. Can someone help? If you need any more info, just tell me how to get it for you and I will do so. :)

---

### Post by CLUGENHEIM on 2007-10-30
Bump..

Also, here is what happens when I type "compiz --replace" in the terminal:

> /usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libccp.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'ccp'


And ccsm

> Info: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'


I just notice those were 2 things people asked for when trying to help people with compiz. I don't know if they are needed or not, but meh. :)

---

