---
title: "Beryl/Compiz update issues"
date: 2007-06-01
forum: Desktop Effects &amp; Customization
---

### Post by shinythings on 2007-06-01
Hi!

I've just done an update of beryl (and a few other things, including firefox) and initially beryl would no longer start. Starting from the console it failed on:

```
beryl: symbol lookup error: /usr/lib/beryl/libbench.so: undefined symbol: benchGetOutput_console
```

Thankfully I got it to work by disabling the 'benchmark' plugin. Has anyone else had problems with the plugin since the last update?

Not sure whether the second issue is related: compiz does not want to update:

```
The following packages have been kept back:
  compiz compiz-core compiz-gtk compiz-plugins
```

and on 'dist-upgrade':

```
The following packages are BROKEN:
  compiz-gnome 
The following NEW packages will be automatically installed:
  compiz-config-gnome 
The following NEW packages will be installed:
  compiz-config-gnome 
The following packages will be upgraded:
  compiz compiz-core compiz-gtk compiz-plugins 
4 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 690kB of archives. After unpacking 827kB will be used.
The following packages have unmet dependencies:
  compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but 1:0.5.0-1~3v1ubuntu2 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
compiz-gnome

Score is -301

```

I have a feeling that removing compiz-gnome is not the best idea, unless compiz-config-gnome is a replacement for it. I've never really figure out whether I need to have it installed at all, since I only use beryl...

---

### Post by orb9220 on 2007-06-05
> Thankfully I got it to work by disabling the 'benchmark' plugin. Has anyone else had problems with the plugin since the last update?

Yep this fix was provide in another thread AFTER I pulled all my hair out!

I wonder if they know of the benchmark plugin proglem?

---

