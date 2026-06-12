---
title: "ATI Radeon X1400+Compiz on 8.04RC"
date: 2008-04-19
forum: Desktop Effects &amp; Customization
---

### Post by xtremesupremacy3 on 2008-04-19
Hey everyone, 

Hope you can help me.
I been a long user of Ubuntu now and been using Ultimate Edition for a while now too, which is basically Ubuntu but added features.
After Hardy entered Release candidate I thought it be the time to attempt an upgrade.
All went well and nothing was wrong and I was able to use everything.
However, as per usual ATI was causing a stir.
This time, however, it was unusual.
I had my Radeon X1400 succesfully installed and the resolution was perfect, but only one thing struck me...compiz. It had been working great aaaaall the time and now it just will not work, whatever I do, all it says is that it cannot enable effects and thats what I so love.

Anyone got any ideas?

Thanks
Arthur

---

### Post by DUfire on 2008-04-19
Restart/Install your XGL? 

What's compiz --replace say?

---

### Post by xtremesupremacy3 on 2008-04-19
I had reinstalled that many times but no avail this is the output i got:
```
arfee@arfee-laptop:~$ compiz --replace
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
/usr/bin/compiz: 406: /usr/local/bin/compiz: not found

```

---

### Post by Zorael on 2008-04-19
Um, curious. Does this help?
```
$ sudo ln -s /usr/bin/compiz /usr/local/bin/compiz
```
Else something's wrong with your compiz installation.

---

### Post by jcooper24 on 2008-04-24
Hi I am also getting this problem on 8.04 LTS downloaded today. I have a HP nx7000 running an ATI Mobility Radeon 9200. 

This was all previously working under 7.10 so not sure what the problem is?

Below is the results of a compiz--replace

jason@jason-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity 

Help!

---

### Post by Ohwii on 2008-04-24
I have the same problem 

it get ```
fglrxinfo

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.1.7415 Release

```

and for compiz--replace ```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:7145 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity 

```

Terrible. makes me want to stop using ubuntu.:(

I hope someone will solve it.

Cheers 

ohwii

---

### Post by leo_rockway on 2008-04-25
sudo nano /usr/bin//compiz

Search for "whitelist"
add fglrx

Try compiz again.

---

### Post by -=Relic=- on 2008-04-26
Well this issue has finally forced me to post, and I hope I might be able to "patch" this problem for some, at least until the issue can be fixed in due time.  I get the exact same error when trying to start up compiz in 8.04LTS previously working fine in 7.10.

The way I worked around this issue was installing Compiz Fusion Icon,
do a search for "compiz" in add/remove found in the Applications menu (make sure you have it set to show "all available applications").

Once installed add a new item to your session, this can be done as follows:

System->Preferences->Sessions
click Add

Name:    (appropriately)
Command:   fusion-icon

restart X (ctrl+alt+backspace).

Note: do not add the --no-start flag to the command line for fusion icon.  I won't pretend to know why, but the fusion icon is able to start compiz where a terminal command fails. Different internal flags that prevent xgl check possibly? No real clue why.

If this is a work around that does the trick for you great, otherwise sorry it couldn't be of more help to you.

In another attempt to get this fixed I installed the xserver-xgl package which does allow compiz to run, however it disabled my direct rendering making everything choppy.  It also had a side effect of clobbering my xorg.conf file which I replaced with a known good one after uninstalling the xserver which restored my direct rendering.

My system is a Thinkpad T42 with a Radeon 7500 vid card, with a fresh install of 8.04LTS.

If you do come across an honest fix for this please post where you found it or what you did in detail, it would be much appreciated, also if it did work for you if you could post your system specs stating that it is working it might help more people work around the issue until it is resolved.

Thanks and Good Luck.

---

### Post by veniatregnum on 2008-04-26
Same problems with compiz here as well.  Everything was working fine until the upgrade to 8.04 - my graphics card (ATI Technologies Inc: Radeon Mobility M7 LW [Radeon Mobility 7500]) was ok after the upgrade but compiz wouldn't start for anything.

cicero@localhost:~$ compiz --replace
Checking for Xgl: not present. 
Found laptop using radeon driver. 
aborting and using fallback: true 
no true found, exiting

The fusion-icon workaround gets everything going for me again - Thanks -=Relic=-. Lets hope something gets worked out so we don't have to use this longterm.

---

### Post by _aluminium23 on 2008-04-29
I have the same GPU and didn't work.

---

