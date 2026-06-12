---
title: "Beagle indexes fine, but best crashes"
date: 2005-10-14
forum: Desktop Environments
---

### Post by wezzer-foo on 2005-10-14
Hi,

I installed beagle to Breezy with command
```
sudo apt-get install beagle
```
and followed instructions from beagle's site.
Data is indexed because command beagle-index-info says:
> 
Index information:
Name: EvolutionDataServer
Count: 85

Name: Mail
Count: 2570


Name: Files
Count: 54759

Name: GaimLog
Count: 20



But when I run command best it crashes saying:
> 
Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for Gnome.ModuleInfo ---> System.EntryPointNotFoundException: gnomesharp_gnome_moduleinfo_get_name_offset
in (wrapper managed-to-native) Gnome.ModuleInfo:gnomesharp_gnome_moduleinfo_get_name_offset ()
in <0x00008> Gnome.ModuleInfo:.cctor ()--- End of inner exception stack trace ---

in <0x00000> <unknown method>
in <0x00025> Gnome.Modules:get_UI ()
in <0x00022> Best.Best:Main (System.String[] args)


---

### Post by manicka on 2005-10-14
I'd suggest checking manually that all the required packages that are suggested at the beagle site have been added. You may have missed one.

---

### Post by wezzer-foo on 2005-10-14
Thanks, few new packages were installed. And two of them didn't install.
Here are the errors:
 - Package libgmime-cil is not available, but is referred to by another package.
 - Package mono-assemblies-arch is not available, but is referred to by another package.

All other packages required by beagle have installed and yes, I have universe enabled in my repositories :-)

---

### Post by manicka on 2005-10-14
try libgmime2.1-cil

mono-assemblies arch isn't available anymore and doesn't seem to be needed.

---

### Post by wezzer-foo on 2005-10-14
"libgmime2.1-cil is already the newest version."

And best still crashes... strange...

---

### Post by manicka on 2005-10-14
have you tried restarting the beagle daemon.

killall mono
beagled

---

### Post by wezzer-foo on 2005-10-14
That didn't have any effect :(

---

### Post by wezzer-foo on 2005-10-15
Well, I had some spare time and decided to compile Beagle from sources. That wen't fine and supricingly beagle and even best are working perfectly now! Problem solved!

---

