---
title: "X86 Compiz ring and shift switcher crashes X"
date: 2009-05-13
forum: Desktop Environments
---

### Post by Siggma on 2009-05-13
I've had a nasty issue with the compiz ring and shift effects crashing the X server. it's easy to reproduce, just enable the ring or shift switcher and hold down window+tab for a sec. This only seems to occur in the x86 version. X86_64 seems to run flawlessly. I'm back to 86 because the moonlight firefox plugin failed and I wasn't able to compile mono and moon from git. There are bugs filed against the x crash issue. 

In the mean time I've found a correction. 
[LIST=1]
[*]Go into the compizconfig-settings-manager and save your settings (preferences->export). 
[*]Using Synaptec remove all compiz and emerald packages from your system. 

[*]Add this ppa to your apt lists.
```
sudo echo "deb http://ppa.launchpad.net/compiz/ppa/ubuntu jaunty main " > /etc/apt/sources.list.d/compiz.list
```

This creates a new apt list for you in /etc/apt/sources.list.d/ named compiz.list. Just delete it when the update comes out.

[*]Now to add the ppa key use this little snippet I found here:
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

```
sudo apt-get install libhtml-parser-perl libio-socket-ssl-perl
wget http://savvas.radevic.com/launchpad/launchpad-ppa-fix.tar.gz -O launchpad-ppa-fix.tar.gz
tar xzvf launchpad-ppa-fix.tar.gz
perl launchpad-ppa-fix.pl
sudo apt-get update
```

This should run apt-get update, install the ppa key then update again.

[*]Now run Synaptec again and install the compiz package plus any plugin packages you want.[/LIST]

**Suggestion:**
[LIST]
[*]Open Synaptic. 
[*]Hit the "Origin" button. 
[*]Select the ppa we just added and select all three plugin packages.
[*]Hit "Section"
[*]Do a full search for compiz and select compiz, CCSM and optionally emerald.
[*]Apply
[*]Import your saved settings
[/LIST]

Eat some :popcorn: while you watch the switcher(s) go round and round and round without crashing x...
-Tom

---

