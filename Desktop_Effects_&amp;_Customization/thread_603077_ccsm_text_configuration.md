---
title: "ccsm text configuration"
date: 2007-11-04
forum: Desktop Effects &amp; Customization
---

### Post by Prospero2006 on 2007-11-04
Is there a way to configure the behavior within compiz through the modification of a text file?

Thanks,
Pros

---

### Post by khughitt on 2007-11-04
I believe there is an option within compiz manager to save configuration data as a flat-file instead of in a database. I'm not exactly sure where that file would be stored, but at least there should be one :)

---

### Post by Happy_Man on 2007-11-04
I don't think so. Do you need something in particular?

---

### Post by 23meg on 2007-11-04
The userspace file system plugin lets you adjust settings by tweaking files. I don't know how exactly though; I haven't found any documentation for it. Let me know if you do

---

### Post by Prospero2006 on 2007-11-04
> **Happy_Man said:**
> I don't think so. Do you need something in particular?

I run a middle school computer lab that has compiz installed on 30 machines. 
I have scripts that do things like change the wallpaper in the whole lab, change the skydome, etc.. However, I'd like to be able to duplicate system-wide changes based on a master configuration of Compiz. For example, Let's say I want all 30 computers to have a cube that has 5 sides instead of 4, I configure my first computer to do what I want, then I copy the correct configuration information to the rest of the lab using scp.

That's the goal.
Pros

---

### Post by khughitt on 2007-11-04
You might want to try asking at the [Compiz forums]("http://forum.compiz-fusion.org/"), there should be some people there with a more in-depth understanding of how ccsm configurations are stored.

Goodluck!

---

### Post by Forlong on 2007-11-05
The flat-file configuration backend does exactly that. The text file is stored in ```
~/.config/compiz/compizconfig
```

---

### Post by Prospero2006 on 2007-11-07
> **Forlong said:**
> The flat-file configuration backend does exactly that. The text file is stored in ```
~/.config/compiz/compizconfig
```

The compizconfig directory has a file called config that contains this info:

```

[gnome_session]
profile =
plugin_list_autosort = true

```

I don't have ccsm up atm, but does it need to be enabled?

Thanks,
Pros

---

### Post by DjBones on 2007-11-07
i don't think so, i use ccsm and mine looks exactly the same.. lol

you can export the profile of your main computer inside ccsm into a profile.config ..
there might be a way to efficiently change all the other computers to yours if you know where that file is stored
or atleast i'd think haha

---

### Post by Forlong on 2007-11-08
> **Prospero2006 said:**
> I don't have ccsm up atm, but does it need to be enabled?
I strongly recommend installing ccsm:
```
sudo apt-get install compizconfig-settings-manager
```
Afterwards, run it via *System &#8594; Preferences &#8594; Advanced Desktop Effect Settings* or ```
ccsm
```
and click on **Preferences**
In the Backend section choose **Flat-file Configuration Backend**
There should be a line in ~/.config/compiz/compizconfig/config indicating you are using the textfile now:
```
backend = ini
```
The file to configure will be** ~/.config/compiz/compizconfig/Default.ini**
If you want to use another one, just create it in ccsm or change
```
profile = 
```
(in config) to
```
profile = YourProfile
```
(you have to make sure there's a textfile called YourProfile.ini in compizconfig, of course)


Just fiddle with the options in ccsm to understand the parameters in the textfile and soon you will be able to set things yourself. It's pretty self explanatory.

---

