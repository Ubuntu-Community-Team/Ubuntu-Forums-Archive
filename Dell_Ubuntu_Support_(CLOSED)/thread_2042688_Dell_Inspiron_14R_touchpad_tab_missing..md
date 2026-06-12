---
title: "Dell Inspiron 14R touchpad tab missing."
date: 2012-08-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by krakspider on 2012-08-15
In System Settings --> Mouse and Touchpad, Touchpad tab is missing.
Because of that side scroll and multi-touch settings are not accessible and not working.

---

### Post by ramsharan065 on 2012-08-16
> **krakspider said:**
> In System Settings --> Mouse and Touchpad, Touchpad tab is missing.
Because of that side scroll and multi-touch settings are not accessible and not working.

[LIST]
[*]You can use "**pointing devices**" for this.
[*]I think this might work for you. It has not worked for me but has worked for some others according to its review.
[*]**Read its review** before installing it.
[*]Install this software using **Ubuntu software center** or using command: **sudo apt-get install gpointing-device-settings**.
[/LIST]

---

### Post by krakspider on 2012-08-17
Unfortunately .. i got an error with my MBR and grub. 
cant see the boot options with AHCI ..
will be able to try later on..
thnx for reply :)

---

### Post by Spectre630 on 2012-08-20
I think I had to manually install the **xserver-xorg-input-synaptics** package to get my touchpad working.  Check to see that it is installed?

---

### Post by daviferreira on 2012-09-04
Same problem here on my Inspiron 14R. Tried on both ubuntu 12.04 and 12.10. Trackpad was detected as a ps/2 mouse and configuration tab is missing.

---

### Post by krakspider on 2012-09-07
> **Spectre630 said:**
> I think I had to manually install the **xserver-xorg-input-synaptics** package to get my touchpad working.  Check to see that it is installed?

its already installed. still cant make it work.

---

### Post by awe1 on 2012-09-19
I have the same problem on my Inspiron N5110

---

### Post by MaikoID on 2012-10-21
Same here with Ubuntu 12.10 and Inspiron 15R

---

### Post by bra|10n on 2012-10-21
> [kubuntu-dev] investigate kde touchpad enabler for packaging/inclusion -  find out what exactly this means and what it does and bleh: [COLOR=DarkRed]POSTPONED[/COLOR][https://blueprints.launchpad.net/ubuntu/+spec/kubuntu-q-packaging](https://blueprints.launchpad.net/ubuntu/+spec/kubuntu-q-packaging)

  You could try enabling pre-release updates...:KS

_EDIT:_

Updates from the standard repo's seem to have fixed this issue.

---

### Post by MaikoID on 2012-10-23
> **MaikoID said:**
> Same here with Ubuntu 12.10 and Inspiron 15R

After reboot it started to work but now my X doesnt work correctly.

---

