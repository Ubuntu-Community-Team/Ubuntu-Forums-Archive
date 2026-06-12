---
title: "Audacity does not record after upgrade"
date: 2009-05-02
forum: General Help
---

### Post by paydaydaddy on 2009-05-02
Have been using audacity for a while with no problems. I upgraded to kubuntu 9.04 last week. After the upgrade audacity would record about a half second of audio then stop. I thought it might be a problem with the upgrade so I did a fresh install. No change. Any suggestions?

---

### Post by tripolitan on 2009-05-02
You said "Have been using audacity for a while with no problems". What version of Ubuntu were you using then? and why not go back to it, instead of using BETA software?

---

### Post by paydaydaddy on 2009-05-02
I do not believe that 9.04 is beta. It is the latest official release. The idea of this post is to seek help/suggestions with a problem encountered following installation of the latest release. Please consider this when replying.

---

### Post by paydaydaddy on 2009-05-02
It looks like the version of Audacity that loads by default after the upgrade is a beta version. I will see if I can get the older version. It does not seem to be in the repositories.

---

### Post by tripolitan on 2009-05-03
Audacity is what I meant by "BETA" software, not so much 9.04 which I consider flaky, as all new Linux distros (but thats another story). They are Beta until fully tested by the users and patched by the developers and that takes months.

I think the problem that you're experiencing with Audacity is caused by 9.04 and your hardware (together). There have been several reports on broken drivers in 9.04 but without any knowledge of your hardware, its a guessing game.

Older versions of Audacity might not be compatible with the gc version in 9.04, you might have to install two versions of gc.

Because I use Audacity on Windows as well, I had to go for the beta version on both platforms (you have to pick one or the other because they are not compatible) Once you've opened/saved your aup files with 1.3, you will not be able to open them again with 1.2, or so the warning says...

---

### Post by paydaydaddy on 2009-05-03
bump. Any other thoughts?

---

### Post by paydaydaddy on 2009-05-03
After much perusing of the web I found the solution. By changing the default sampling bit rate to 48000 Hz through preferences I got it working.

---

### Post by msumurph on 2009-05-11
> **paydaydaddy said:**
> After much perusing of the web I found the solution. By changing the default sampling bit rate to 48000 Hz through preferences I got it working.

Thanks!  This fixed my problem as well. :P

---

### Post by fontman on 2010-06-25
I found that KMix capture settings was inhibiting my ability to record streams in Audacity. I have to ensure that "Mic" is set to capture for GTalX and "Mix" is set to capture for Audacity.

---

