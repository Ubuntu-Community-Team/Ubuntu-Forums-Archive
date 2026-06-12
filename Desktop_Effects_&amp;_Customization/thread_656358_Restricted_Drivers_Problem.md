---
title: "Restricted Drivers Problem"
date: 2008-01-02
forum: Desktop Effects &amp; Customization
---

### Post by t.z0n3 on 2008-01-02
I use an ATI Radeon 9600 graphics card. I got Gutsy installed this morning, and I was told I needed to install restricted drivers for my card. The desktop effects worked prior to their installation. After I restarted my computer to complete the restricted drivers install, they would not work. 

Any ideas?

---

### Post by jonray74 on 2008-01-02
hello,

i too have the Radeon 9600, and yes I did encounter the same problem like you. As for the solution to the restricted drivers thing, i never used them. After so many attempts to try the restricted drivers, everything failed for me.

So, for my ubuntu installation, whatever was the default video that Ubuntu used/detected for my system was pretty much it and thus i never had any problems so far. I was able to run Compiz even without the restricted drivers.

After my ubuntu installation, here's what I did:

1.) sudo apt-get install update
2.) sudo apt-get install compizconfigsettings-manager

I then enabled them from the Desktop settings.

And that was it. From what i've been researching and reading in the forums, ATI seems to have not yet stabilize their driver for LINUX and thus it is quite risky to use. I would wait and see in the next versions of Ubuntu if this will be resolved. So for now, I try not to use the 3rd party drivers.

cheers

---

### Post by Mr Greencastle on 2008-01-02
If effects worked fine for you without the restricted drivers than there is no point in having them. To remove them paste this into a terminal:
```
sudo restricted-manager
```
Then uncheck the ATI restricted Driver, restart and it should work. Good Luck!

Mr Green

---

### Post by t.z0n3 on 2008-01-02
Thanks both, I did that and they work just fine. That's the same conclusion I came to. 

:) Here's to hoping they figure it out before the next release!

---

