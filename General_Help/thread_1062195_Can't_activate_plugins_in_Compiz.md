---
title: "Can't activate plugins in Compiz"
date: 2009-02-06
forum: General Help
---

### Post by xX-Felipao-Xx on 2009-02-06
I simply can't activate or disable any plugin in ccsm.
I can only if I run sudo ccsm, and in that case, I don't know why, It doesn't save to the session.

Its strange, I could do it before, I don't know what happened.

Any idea?
Thanks

---

### Post by Crafty Kisses on 2009-02-06
I'm not sure what you're real issue is, but have you installed the following package?
```
sudo apt-get install compizconfig-settings-manager
```
Then you can access CCSM by going to **System->Preferences->CompizConfig Settings Manager**.

---

### Post by meinvateristnein on 2009-02-06
your problem is your video hardware you cannot activate them becuase your video hardware is too bad or the drivers for either nvidia or ati RESTRICTED are not installed ............... if that is not the case then goto system>>>>preferences>>>>>appearance>>>>>>>visual effects>>>>>>Extra ....then try enabling plug-ins.......>>> 

if the extra effects says cannot activate extra option or something or rather then its your video hardware if not then i completely am lost

---

### Post by Yashiro on 2009-02-06
Did you install it as sudo or as actual root? This may cause these symptoms.
Try removing CCSM and re-installing it.

Try resetting it back to defaults. (Preferences Section)
Look further into the Preferences section too. If the bottom selector is set to flat file you may not have permissions to update the file it's pointing to. Change it to Gconf backend and test that.

---

### Post by xX-Felipao-Xx on 2009-02-06
@Codename: Yes, I obviously have CCSM installed :P

@meinvateristnein: That's not the case, I could do it previously and I used envy some time ago to install nvidia drivers, and it worked fine.

@Yashiro: I'll try reinstalling it, after trying some other things.

Thanks everybody.

---

### Post by xX-Felipao-Xx on 2009-02-07
Solved, I had unchecked "Order automatically plugins" in CCSM preferences.

Thanks everybody

---

