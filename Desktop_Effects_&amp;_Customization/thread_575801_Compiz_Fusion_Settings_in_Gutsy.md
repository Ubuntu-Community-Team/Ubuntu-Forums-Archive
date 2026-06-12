---
title: "Compiz Fusion Settings in Gutsy"
date: 2007-10-14
forum: Desktop Effects &amp; Customization
---

### Post by mlyons16 on 2007-10-14
I understand that Compiz Fusion comes pre-installed in 7.10. One can not run automatically the command "ccsm".

Is that because compiz-settings-manager package is not installed? Can one install it through Synaptic?

---

### Post by wadpro on 2007-10-14
yeah you can install it in adaptec manager, search the keyword "compiz".

i installed compiz-settings-manager but i coudnt start it?

---

### Post by slkuhn on 2007-10-15
I was having this issue too. To fix it I uninstalled the version of compiz settings manager that I had, (through synaptic). I then reinstalled through synaptic.  
The settings manager is now called 'Advanced desktop effects settings" and is located in system>preferences

I hope this helps!!

---

### Post by leejohn on 2007-10-15
first you got to enable 3D your video card - system-administration-restricted device manager, make sure your card select and correct or enable.
Next System-Preference-Appearance-Visual Effects and select what is apply ...

---

### Post by Tachyon1000 on 2007-10-15
Good luck in using most of Compiz with the Compiz Settings Manager.  I couldn't get the scale plug-in to work without installing the manager and configuring a screen edge area to activate it.  I don't understande the purpose of having Compiz integrated into Ubuntu by default in the manner that it has been implemented if you have to install the CCSM to actually configure and use the features of Compiz.

---

### Post by nraney on 2007-10-16
I was just wondering if anyone who has compiz-fusion and their manager working together has some good setting techniques.. I got mine working, but my settings were cooler in fiesty.. I was messing with it and I found that it is difficult to get everything tweaked  just so.. a handy config file would by nice.

---

### Post by ericdegen on 2007-10-19
Here's a somewhat related question guys...

I have two Gutsy / CF systems. I took the time to get one all dialed in with the CF settings I like, and I really don't want to do that again on the other system, is there a .XXXXX file in my profile I can just copy to other systems to retain those settings?

Thanks,

---

### Post by bluepowder7 on 2008-04-12
> **ericdegen said:**
> Here's a somewhat related question guys...

I have two Gutsy / CF systems. I took the time to get one all dialed in with the CF settings I like, and I really don't want to do that again on the other system, is there a .XXXXX file in my profile I can just copy to other systems to retain those settings?

Thanks,


dunno if you found a solution, but all you need to do is copy the ~/.gconf/apps/compiz folder with all its *.xml files from the set-up machine to the new machine.

---

