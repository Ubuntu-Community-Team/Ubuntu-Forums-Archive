---
title: "Compiz ppa issue"
date: 2010-10-13
forum: Desktop Environments
---

### Post by verymadpip on 2010-10-13
Hey guys.

I did a clean maverick install on Sunday & added the compiz ppa to software sources last night (Tuesday).  My system then did a partial upgrade which pretty much borked compiz.  I couldn't close the appearance window once it was open, nor could I start the fusion icon.  This resulted in me doing another clean install.  I added the ppa again & my system wanted to do another partial upgrade.  Obviously I didn't do that & I removed the ppa from software sources.  Anyone else had this issue?
I'm using an ATI radeon 4870 & the xorg drivers in a GNOME desktop.

---

### Post by nilarimogard on 2010-10-13
The Compiz PPA package for Maverick is experimental and shouldn't be used for now. You can fix this:

Install PPA Purge (is available in the official repositories starting with Ubuntu 10.10):
```
sudo apt-get install ppa-purge
```

Then run the following command:
```
sudo ppa-purge ppa:compiz/ppa
```

The above command will disable the Compiz PPA and downgrade all the packages you've installed from this PPA to the version in the official Ubuntu repositories.

Once PPA Purge finishes, restart (or log out and log back in) and Compiz should work now.

---

### Post by 3Miro on 2010-10-13
What ppa was it? Ubuntu comes with compiz, unless you want some extra functionality and/or there is some strange bug, you should not have to install any extra ppa (but you probably know that).

What is the ppa and my guess is that the page with it is more likely to have an answer regarding a bug.

---

### Post by nilarimogard on 2010-10-13
> **3Miro said:**
> What ppa was it? Ubuntu comes with compiz, unless you want some extra functionality and/or there is some strange bug, you should not have to install any extra ppa (but you probably know that).

What is the ppa and my guess is that the page with it is more likely to have an answer regarding a bug.

It was most probably ppa:compiz/ppa which comes with Compiz 0.9 (experimental packaging) for Maverick

---

### Post by cpmman on 2010-10-13
> **nilarimogard said:**
> The Compiz PPA package for Maverick is experimental and shouldn't be used for now. You can fix this:

Install PPA Purge (is available in the official repositories starting with Ubuntu 10.10):
```
sudo apt-get install ppa-purge
```

Then run the following command:
```
sudo ppa-purge ppa:compiz/ppa
```

The above command will disable the Compiz PPA and downgrade all the packages you've installed from this PPA to the version in the official Ubuntu repositories.

Once PPA Purge finishes, restart (or log out and log back in) and Compiz should work now.

Thank you - that resolved my compiz problem.

---

### Post by verymadpip on 2010-10-13
> **3Miro said:**
> What ppa was it? Ubuntu comes with compiz, unless you want some extra functionality and/or there is some strange bug, you should not have to install any extra ppa (but you probably know that).

What is the ppa and my guess is that the page with it is more likely to have an answer regarding a bug.

Errrrrrrrrrr...no I didn't know that (embarassed noob here:))
The ppa came from here: [https://launchpad.net/~compiz/+archive/ppa]("https://launchpad.net/%7Ecompiz/+archive/ppa")
It all works splendidly well at the moment with the downloads from the software centre, including extra plugins, .  I just thought it would be wise to add it to keep up to date.  Is that not necessary? 
I'm really sorry if this is basic stuff I should know, I'm only just starting to get to grips with Ubuntu & its workings.  (I'm still afraid of the terminal).
So, if I install Docky, for instance, I don't need to add that ppa to software sources either?

Thanks for helping me out BTW guys :)

---

