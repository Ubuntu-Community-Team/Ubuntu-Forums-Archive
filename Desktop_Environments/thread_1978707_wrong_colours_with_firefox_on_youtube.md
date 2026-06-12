---
title: "wrong colours with firefox on youtube"
date: 2012-05-12
forum: Desktop Environments
---

### Post by daxbau on 2012-05-12
Hi everybody!

I have a confusing problem....

Just when i get to you-tube red and blue are exchanged.... (I know blood i red and not blue) all the people look like "blue man group"...

I had this problem for about 2 Weeks and decided to format my Ubuntu 10.10 and get up to 12.04. after installing everything works... but youtube....

any ideas how i can check what's going on on my machine....

(hp 8510w) 

I can download the video from youtube and watch it with mplayer... the colors are ok... but during firefox-youtube-mode all videos seem to be from "blue man group"


thanks for your advice and help

kind reguards


daxbau

---

### Post by CrocoDuck on 2012-05-12
Interesting... Are you using flash plugins on firefox? Try to use a different browser, maybe chromium,  with flash (or the other plugin your are using), if you have not already tried it. I think is the easier way to understand if the issue is caused by a bug rather than plugin or firefox bad configuration.

---

### Post by tpheiska on 2012-05-12
> **CrocoDuck said:**
> Interesting... Are you using flash plugins on firefox? Try to use a different browser, maybe chromium,  with flash (or the other plugin your are using), if you have not already tried it. I think is the easier way to understand if the issue is caused by a bug rather than plugin or firefox bad configuration.

I have the same problem with Chromium and Mythbuntu. The problem began after a Mythbuntu version upgrade last week, I used Youtube for the first time and the colors are wrong.

---

### Post by ajgreeny on 2012-05-12
This is a well known problem with the latest flash versions, and is related to the graphic acceleration of your graphic card and nvidia cards in particular.

See [http://ubuntuforums.org/showthread.php?t=1948626](http://ubuntuforums.org/showthread.php?t=1948626) which I started after the problem began a while ago.  The solution will depend on your hardware and OS version, but in my case was solved only by downgrading the flash version as discussed in that thread to 11.1r102.

Good luck!

---

### Post by Shadius on 2012-05-12
This is a well known issue with the new Flash version 11.2. There are countless threads on the issue. It doesn't seem that Adobe intends to release a fix for the Firefox plugin, but it works just fine on Google Chrome. You might want to try that instead.

---

### Post by CrocoDuck on 2012-05-12
/*Uhm... Did you work some configuration file or installed proprietary drivers related to video stuff?*/ Sorry, I have not seen the previous answers... I agree with ajgreeny and Shadius.

---

### Post by lovinglinux on 2012-05-12
[Flash 11.2.202.228 solutions](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by ex_isp on 2012-05-15
> **lovinglinux said:**
> [Flash 11.2.202.228 solutions]("http://ubuntuforums.org/showthread.php?t=1953796")


Adobe...  pssst (noise of discontent)

And their solution is to not support Linux?   pssst

---

