---
title: "blank screen after upgrade to 8.10"
date: 2009-01-17
forum: Desktop Environments
---

### Post by toobitz on 2009-01-17
Hello all,

Today, I upgraded my perfectly working desktop from 8.04 to 8.10. I have a Nvidia GeForce 6100. After rebooting and after the boot messages run through, I am presented a blank screen. I hear the Ubuntu drums, I can blindly enter my username/password and hear the Ubuntu login sound, but the screen remains blank.

I tried removing compiz et al at the console but that did not help. Please, anynone has a hint for me? I'm stuck with an unusable system...

---

### Post by utnubuuser on 2009-01-17
I've heard nothing but problems with upgrading from 8.04 to 8.10.  Especially with the Nvidea cards.  You should be able to find a thread here if you do an advanced search.

I usually upgrade by making room on the HDD, installing the new version and importing all settings, then removing old partitions -- More tedious in some ways, but a better overall result.

---

### Post by toobitz on 2009-01-18
Just as a follow-up to my own post: I tried the nvidia packages 96, 173, 177 and manually installed the newest drivers directly from nvidia (180.22). Nothing did the trick. The only way I could get a desktop is using the nv driver in xorg.conf which gave me a 800x600 resolution.

I've wiped 8.10 from my drive and reinstalled 8.04. Works as expected, including 3D desktop effects.

Yes, I know that the release notes for Intrepid Ibex state that basically most users of Nvidia and ATI boards will not be able to use 3D effects. However, I could not even get a decent non 3D desktop to work. At some point, I had 1280x1024, but before every login, I was told that my config was broken, needed to be reconfigured (which did not help) or that I could run in low graphics mode. 

And I somehow hoped that, after several months since the release of Intrepid Ibex, either nvidia or Ubuntu would have done something to prevent a stuck-with-a-blank-screen-situation. I've been using and upgrading Ubuntu since 5.04 and I don't remember many upgrades after which I did not have to deal with graphic issues.

Conclusion: even now, nearly 3 months after the release of 8.10, it's a no-go for most nvidia users.

PS: sorry for the rant in my post, I'm basically very happy with Ubuntu and I think that, overall, the developers are doing a great job. It's just that those graphic issues keep popping up and from my personal, limited end-user point of view, I don't see a real progress here.

---

