---
title: "Lacking a lot of softwares?"
date: 2008-12-08
forum: General Help
---

### Post by Fzang on 2008-12-08
First I tried installing kiba-dock - not in synaptic or add/remove

Then I tried installing some themes and it turned out that I needed the aurora GTK engine... well, I tried installing it and it told me that I needed GTK+ 2.10 which I apparently don't have..

I looked through synaptic and add/remove again and didn't find any GTK update or the likes so I decided to google GTK 2.10 and found a download

I tried installing it and it said I needed some packages before it could install it, I looked through add/remove and synaptics and didn't find these packages as well!

Am I very low on software sources? I have the default ones as it's only been a couple of days ago since I installed ubuntu, shouldn't they be sufficient?

---

### Post by halovivek on 2008-12-08
go to [www.appnr.com](www.appnr.com)
you can find some good applications for ubuntu.

---

### Post by prshah on 2008-12-08
> **Fzang said:**
> 
Am I very low on software sources? I have the default ones as it's only been a couple of days ago since I installed ubuntu, shouldn't they be sufficient?

You need to enable the "additional" repositories; click on System-Administration-Software Sources-Ubuntu Software and enabled the universe, restricted and multiverse repositories.

After you click OK, you will be asked to reload the software list. You will need an Internet connection for this. Once this is done, you will have a lot more software available to you.

I'd suggest: Open a terminal (Applications-Accessories-Terminal) and the following commands: ```
sudo apt-get install ubuntu-restricted-extras
``` as a first step (if suitable) and then you can install kiba with ```
sudo apt-get install kiba-dock
```

---

