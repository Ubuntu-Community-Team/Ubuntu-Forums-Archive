---
title: "Xubuntu 19.10 blackscreen when opening Nvidia Optimus laptop lid after closing it."
date: 2019-12-18
forum: Desktop Environments
---

### Post by cheese-e-boi on 2019-12-18
Hi, I just install Xubuntu 19.10 on my Dell XPS 9570 (having run Xubuntu 18.04 in the past) and I have run into this issue that I can't find any documentation on. Whenever I normally suspend the laptop and power it back on, it works fine. However, when I close the lid, wait a few seconds, and open it I get a black screen and I have to restart lightdm through tty. I am not exactly sure how each of the power manager options affects this, however I had it set to suspend for both battery and with AC power. 

For now, I have installed the Budgie desktop and I am having no issues with it, but I still would like to use XFCE. All of the info I find online refers to an older issue from around five years ago, so any help would be appreciated!

EDIT: Found a bug on Launchpad for this issue and confirmed it, I guess I'll have to wait and see.
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1853709](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1853709)

---

### Post by mörgæs on 2019-12-26
For this kind of problems it's often a good idea to begin with a hardware description. Please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it onto the command line, run it and post lshw.txt in CODE tags.

---

