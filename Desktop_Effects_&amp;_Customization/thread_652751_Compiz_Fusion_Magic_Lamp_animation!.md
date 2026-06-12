---
title: "Compiz Fusion Magic Lamp animation!"
date: 2007-12-29
forum: Desktop Effects &amp; Customization
---

### Post by snakeeyes on 2007-12-29
Hi, how can I get the magic lamp effect in this youtube video?

[http://www.youtube.com/watch?v=xC5uEe5OzNQ](http://www.youtube.com/watch?v=xC5uEe5OzNQ)

I am running Kubuntu 7.10 with compiz fusion though, not beryl.

Any idea about the skydome they r u using as well?

Thanks!

---

### Post by chewearn on 2007-12-29
I assume you have install CCSM; if not, then:

```
sudo aptitude install compizconfig-settings-manager
```

Open CCSM, find the Animations plug-in (under Effects category), and you can add the Magic Lamp animation.

I'm not sure about the skydome image he is using, but he has "animate skydome" turned on (Desktop Cube plug-in > Appearance tab); that's why the skydome can move like it did in the video clip.

---

### Post by snakeeyes on 2007-12-29
I found out a way to hack magic lamp to make it have 0 waves, thats what I wanted actually. Skydome, I know how to set i up, but thanks anyway. Also do u know how to get the window water wave effect like u have in beryl for compiz fusion, I really miss that effect.

---

### Post by sailor2001 on 2007-12-29
have never been able to get water effect on beryl or fusion, on feisty or gutsy. I think it because of the in-box nvidea card not strong enough.

---

### Post by overdrank on 2007-12-29
> **snakeeyes said:**
> I found out a way to hack magic lamp to make it have 0 waves, thats what I wanted actually. Skydome, I know how to set i up, but thanks anyway. Also do u know how to get the window water wave effect like u have in beryl for compiz fusion, I really miss that effect.

Hi and have you enabled it in CCSM. Like the previous poster pointed out I have had similar luck and upgraded my graphics. What is the model of your graphics card?

---

### Post by snakeeyes on 2007-12-29
> **overdrank said:**
> Hi and have you enabled it in CCSM. Like the previous poster pointed out I have had similar luck and upgraded my graphics. What is the model of your graphics card?
everything works I just wanted to know how to reduce maximum waves from 3 to 0 like in that video. then I had to change some compiz settings to make magic lamp have 0 waves.

Any ide how we can get that title bar water effect like in that video, thats the one effect I really miss from Beryl.

---

### Post by overdrank on 2007-12-29
> **snakeeyes said:**
> everything works I just wanted to know how to reduce maximum waves from 3 to 0 like in that video. then I had to change some compiz settings to make magic lamp have 0 waves.

Any ide how we can get that title bar water effect like in that video, thats the one effect I really miss from Beryl.

I believe you are speaking of the tidle wave. Make sure it is checked in CCSM under water effect.

---

### Post by snakeeyes on 2007-12-29
> **overdrank said:**
> I believe you are speaking of the tidle wave. Make sure it is checked in CCSM under water effect.
Its not there in the water effect for some reason in compiz fusion. I am running Kubuntu 7.10 though. Any ideas?

---

### Post by overdrank on 2007-12-29
> **snakeeyes said:**
> Its not there in the water effect for some reason in compiz fusion. I am running Kubuntu 7.10 though. Any ideas?

Other than going to adept manager and searching for compiz-fusion-plugins-extra or main or even unsupported.

---

### Post by snakeeyes on 2007-12-29
> **overdrank said:**
> Other than going to adept manager and searching for compiz-fusion-plugins-extra or main or even unsupported.
I will try that right now!

---

### Post by snakeeyes on 2007-12-29
compiz fusion plugins main and extras r allready installed, but I couldn't find any unsupported ones.

---

### Post by overdrank on 2007-12-29
> **snakeeyes said:**
> compiz fusion plugins main and extras r allready installed, but I couldn't find any unsupported ones.

Ok then you may want to check your repos
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
To make sure you have all enabled or you can search here for which plugins is the water effect you are looking for.
[http://ubuntuforums.org/forumdisplay.php?f=223](http://ubuntuforums.org/forumdisplay.php?f=223)
Good luck!

---

### Post by snakeeyes on 2007-12-29
> **overdrank said:**
> Ok then you may want to check your repos
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
To make sure you have all enabled or you can search here for which plugins is the water effect you are looking for.
[http://ubuntuforums.org/forumdisplay.php?f=223](http://ubuntuforums.org/forumdisplay.php?f=223)
Good luck!
I will check it right now and tell u, thanks for all ur help so far.

---

### Post by overdrank on 2007-12-29
> **snakeeyes said:**
> I will check it right now and tell u, thanks for all ur help so far.

No problem and sorry for not posting instruction for the repos as I have only used KDE a couple of times and could not remember. :(

---

### Post by snakeeyes on 2007-12-29
Nope nothing, my repos r fine, have u got water title bar with ur compiz fusion version, if so can u tell me from where did u install it or r u using the default Gutsy version?

---

### Post by overdrank on 2007-12-29
> **snakeeyes said:**
> Nope nothing, my repos r fine, have u got water title bar with ur compiz fusion version, if so can u tell me from where did u install it or r u using the default Gutsy version?

HI and I have been using my Feisty system along with Hardy. The Gutsy install doesn't have it installed but I am working on it so will post back with the answer.

---

### Post by overdrank on 2007-12-29
> **snakeeyes said:**
> Nope nothing, my repos r fine, have u got water title bar with ur compiz fusion version, if so can u tell me from where did u install it or r u using the default Gutsy version?

Ok under CCSM in Gutsy 7.10 look under water effect, actions tab and title wave and check that box.

---

### Post by snakeeyes on 2007-12-29
> **overdrank said:**
> Ok under CCSM in Gutsy 7.10 look under water effect, actions tab and title wave and check that box.
I did that right now but I don't notice anything.

---

### Post by snakeeyes on 2007-12-29
I just found out something, witht that option it works on system bell only but other wise it is disabled for some reason. Any idea about that please!

---

### Post by Forlong on 2007-12-29
It's disabled on my machine as well. I guess it has something to do with your graphics card. Compiz has higher requirements in terms of water and blur then Beryl used to have.

---

### Post by snakeeyes on 2007-12-29
> **Forlong said:**
> It's disabled on my machine as well. I guess it has something to do with your graphics card. Compiz has higher requirements in terms of water and blur then Beryl used to have.
No my graphics card supports but I heard on the compiz forums that fusion does not have the water effects beryl has for some stability reasons. Some people have hacked compiz for fedora but I am not sure if it can be done on Ubuntu or Kubuntu.

[http://forum.compiz-fusion.org/showthread.php?t=5650](http://forum.compiz-fusion.org/showthread.php?t=5650)

---

### Post by snakeeyes on 2007-12-29
Here is a screenshot of the effect I want:

---

### Post by LinuxIsInnovation on 2007-12-30
Hmm... Even Ive been searching for this since a week.. no good news yet :(

---

### Post by snakeeyes on 2007-12-30
> **sayakb said:**
> Hmm... Even Ive been searching for this since a week.. no good news yet :(
I hope the compiz fusion developers make a patch for this for us or some one finds a way to install the current patch on our systems cause the one in the compiz community forums only works on fedora so far.

---

### Post by snakeeyes on 2007-12-31
Any news about this effect?

---

