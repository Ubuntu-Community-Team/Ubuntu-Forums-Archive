---
title: "Updates this week killed Unity. Point me in direction"
date: 2016-02-28
forum: Desktop Environments
---

### Post by Michael_Dullea on 2016-02-28
In a weak moment I clicked the update icon and wiped out login box, unity sidebar and top menu bar on the HTPC when rebooting the next morning. This problem has a long history as I read all herein a googled elsewhere and many solutions. However a couple folks said it is quicker to reinstall. I'm now looking at that fork in the road. Here is my set up. Ubuntu 14.04, I have two drives in the box. The main one is SSD and I believe I have a separate "home" on it. The processor is AMD APU and I'm using ubuntu drivers. I have run:  sudo unity, sudo compiz, sudo usr/lib/nux/unity_support_test -p and LSPCI for example. Got unable to open display but saw nothing relating to the drivers library like many have. I normally boot without login so it acts like a TV. I have been able to get the login screen from the terminal typing "unity" that has the clock, wheel and a couple items. It is a guest screen, and I don't remember if I boot root, or guest normally because I never see that screen. The dot, top right of the login box lets me go into kodi. But without the brower I can't go online. Anyway if I click ubunto in the login it goes to the blank pink screen just like it now boots. I have installed, reinstall desktop, unity and tried maybe 15 different suggestions of installs and reinstalls, etc. I would like suggestions if it is a driver issue, or looks like some other issue so I can focus or are you folks finding it better to just reinstall ubuntu. If so what version would I download of 14.04 that would not have updates more recent than say a month ago. 

   	 	 	 	   **Typed sudo unity and got:**
 

 Warning: no display variable set, setting it to 0
 stop:  Unknown job: unity -panel -service  
 start: Unkown job: unity-panel-service
 compiz (core) loading plugin,   
 compiz (core) starting plugin
 Invalid MIT-MAGIC-COOKIE-1 keycompiz (core) -Fatal: couldn't open display 0
 compiz (core)  Stopping plugin  
 compiz (core)  Unloading plugin  
                              starting plugin
 

 

 **Typed sudo compiz**
 loading plugin
 starting plugin
 couldn't open display
 stopping plugin
 unloading plugin
 

 Typed: usr/lib/nux/unity_support_test -p,   got:
 no such file or directory
 

 

 Typed: sudo /usr/lib/nux/unity_support_test -p,
 Error: unable to open display
 

 Typed:  LSPCI,  got no errors or problems
  
Thanks folks

---

### Post by coldraven on 2016-02-29
> If so what version would I download of 14.04 that would not have updates more recent than say a month ago. 
It looks like 14.04.4 is the most up to date. Scroll down to see checksums and download options. I usually use the torrent link, it's fast

[http://releases.ubuntu.com/trusty/](http://releases.ubuntu.com/trusty/)

---

### Post by Michael_Dullea on 2016-02-29
Thanks coldraven, I was looking at that and was getting ready to reload ubuntu but decided to go back to the answer most given for the solution and see if I did something wrong. I had executed rm in the wrong directory. Well, momma was right, they can't cure stupid. sudo apt-get install --reinstall compiz-core sudo rm -rf ~/.config/dconf/user

---

### Post by coldraven on 2016-03-01
> **Michael_Dullea said:**
> Thanks coldraven, I was looking at that and was getting ready to reload ubuntu but decided to go back to the answer most given for the solution and see if I did something wrong. I had executed rm in the wrong directory. Well, momma was right, they can't cure stupid. sudo apt-get install --reinstall compiz-core sudo rm -rf ~/.config/dconf/user
  :lolflag:

---

