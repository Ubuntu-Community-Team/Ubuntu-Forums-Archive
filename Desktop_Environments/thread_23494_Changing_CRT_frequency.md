---
title: "Changing CRT frequency?"
date: 2005-04-02
forum: Desktop Environments
---

### Post by trenths on 2005-04-02
Is there a way to configure the make and model of my CRT or at least change the CRT frequency? 60 hz. at 1024x768 can be a little rough on the eyes. The monitor is capable of 100 hz. at that resoultion (I run it that way in Windows) and so is the video card. The monitor is a Cornerstone 21_75 and the video card is a Radeon 9500 Pro. The video card was correctly configured by Ubuntu.

I did not notice an opportunity in Ubuntu setup to choose the CRT model, something you have opportunity to do in Fedora. Is there an add on that will enable me to configure the CRT according to make and model in Ubuntu?

---

### Post by Buffalo Soldier on 2005-04-02
Go to the Top Panel and click at System -> Preferences -> Screen Resolution -> (drop-down menu) Refresh Rate.

---

### Post by trenths on 2005-04-02
I've done that. That's how I know it's running at 60 hz. 60 hz. is the only choice there.

---

### Post by jeremy on 2005-04-02
[QUOTE=Buffalo Soldier]Go to the Top Panel and click at System -> Preferences -> Screen Resolution -> (drop-down menu) Refresh Rate.[/QUOTE]
 If this doesn't offer you the resolution you want, then you will have to edit  /etc/X11/xorg.conf
If you are not sure how to do this then do a search of the forums, [http://ubuntuforums.org/showthread.php?t=21984](http://ubuntuforums.org/showthread.php?t=21984) is a good place to start

[edit] sorry trenths, you posted back while I was writing this! [/edit]

---

### Post by dcraven on 2005-04-02
By editing /etc/X11/xorg.conf and changing the HorizSync/VertRefresh to your preferences, your preferred changes will take affect when you restart X.

Back up your current xorg.conf first though so you can revert to it if something gets messed up.

HTH,
~djc

---

