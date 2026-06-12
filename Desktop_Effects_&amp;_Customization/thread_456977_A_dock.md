---
title: "A dock"
date: 2007-05-28
forum: Desktop Effects &amp; Customization
---

### Post by ENN0 on 2007-05-28
Hi i was wondering if somone would be kind enough to give me some source codes so i can download a dock...im usining fiesty! thanks...a link will be fine im not expecting you to do it:p

---

### Post by notwen on 2007-05-28
Been using AWN for awhile now w/o one complaint.  Check out the thread [here]("http://ubuntuforums.org/showthread.php?t=385981") for more info.  You will also need to be running Compiz or Beryl for AWN to function/look correct.  You may also want to check out Kiba-Dock, which tends to be very popular as well.

---

### Post by P4oL1n0 on 2007-05-28
before you must have installed Beryl or Compiz .. after you can install AVANT or Kiba-Dock....

For Avant: these are the repository:

```
deb http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator
```

to authenticate the packages type this:

```
wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg -O- | sudo apt-key add -
```

And than, to install AVANT:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install avant-window-navigator
```

	
If you want something simpler, without to have need Beryl or Compiz, install gDesklets

bye

---

