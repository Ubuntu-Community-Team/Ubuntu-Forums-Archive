---
title: "Compiz fusion on Dell d830 with intel graphic card"
date: 2007-10-07
forum: Desktop Effects &amp; Customization
---

### Post by Marc Duval on 2007-10-07
I installed Gutsy on my Dell D830 laptop. It has an Intel graphics adapter. When i ran the live CD compiz worked fine. After installing i can't enable the desktop effects.

Compiz --replace shows the following output:

Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 
Windowmanager waarschuwing: 0 opgeslagen in GConf-sleutel /apps/metacity/general/num_workspaces is geen redelijk aantal werkbladen, huidige maximum is 36
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.


Would welcome some assistance

---

### Post by bertvv on 2007-10-08
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/148805](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/148805) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm having the same problem. The answer can be found here: [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

Cheers,

bert

---

### Post by Marc Duval on 2007-10-11
OK, that did the trick for me... thanks!

Now i must see to get the sound working :-)

---

### Post by JoSch on 2007-10-18
to get sound working just follow one of the steps explained here: [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

I did compile alsa manually on my d830 and it worked like a charm.

---

