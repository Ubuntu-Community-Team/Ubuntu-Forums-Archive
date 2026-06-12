---
title: "Get back to 'stock' Light themes?"
date: 2011-07-13
forum: Desktop Environments
---

### Post by ?#Yhf%*&amp; on 2011-07-13
I'm currently using the popular Ambiance and Radiance Evolution themes, but now I want to get back to the regular Ambiance theme. I have locked folders in my home folder labelled Ambiance and Radiance, which I think was left over from the install. Does anyone know how how to get my old themes back? :confused:

P.S - I already removed the Ambiance Evolution PPA and reloaded Synaptic Package Manager, but it did nothing.

---

### Post by wildmanne39 on 2011-07-14
> **Corbin052198 said:**
> I'm currently using the popular Ambiance and Radiance Evolution themes, but now I want to get back to the regular Ambiance theme. I have locked folders in my home folder labelled Ambiance and Radiance, which I think was left over from the install. Does anyone know how how to get my old themes back? :confused:

P.S - I already removed the Ambiance Evolution PPA and reloaded Synaptic Package Manager, but it did nothing.
Hi, if you uninstalled the themes open synaptic and put in themes then look for the themes you want and install them.

---

### Post by donato roque on 2011-07-14
Normally, you would not uninstall the old themes and they're still there. Go to Appearance and select the Ambiance or Radiance.

---

### Post by ?#Yhf%*&amp; on 2011-07-14
The Ambiance Evolution theme replaced the standard themes. These are the instructions I followed:

```
sudo apt-add-repository ppa:tiheum/equinox
sudo apt-add-repository ppa:victored/ambiance-evolution
sudo mv  /usr/share/themes/Ambiance ~/
sudo mv  /usr/share/themes/Radiance ~/
sudo apt-get update
sudo apt-get install --reinstall light-themes
```I'm going to try to do this:

```

sudo mv ~/Ambiance /usr/share/themes/
sudo mv ~/Radiance /usr/share/themes/
sudo apt-get update
sudo apt-get install --reinstall light-themes

```I'll post back if it works...

EDIT: I had to delete the old theme folders first, but it seemed to work - until the last command. It said the package could not be downloaded for some reason. I'm going to Launchpad.net to see if I can download it myself.

---

### Post by ?#Yhf%*&amp; on 2011-07-14
These were the magic commands:

```

rm -rf /usr/share/themes/Ambiance
rm -rf /usr/share/themes/Radiance
sudo mv ~/Ambiance /usr/share/themes/
sudo mv ~/Radiance /usr/share/themes/
sudo apt-get update
sudo apt-get install --reinstall light-themes

```

Thanks anyway!

---

### Post by wildmanne39 on 2011-07-14
Hi, your welcome I am glad you got them back.

I just wanted to let you know that the way used that remove command can be very dangerous if you put the wrong path by mistake you could wipe out your entire system, would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

