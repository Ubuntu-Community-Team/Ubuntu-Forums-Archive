---
title: "Unity and Cinnamon - Can they co-exist separately?"
date: 2012-09-04
forum: Desktop Environments
---

### Post by istiska on 2012-09-04
I have both Cinnamon and Unity installed and I would like them to keep separate "profiles". By that I mean different theme and different keyboard shortcut mappings. (The Unity shortcut settings removed some Cinnamon ones and then some Unity keyboard shortcuts stopped working.)

Is this possible & how would I go about it?

---

### Post by cmcanulty on 2012-09-04
I am using classic no effects and it makes unity when I try it have no dash no panels nothing but my desktop picture so  it is totally unusable. So the different desktop environments can certainly interfere with each other on some machines.I have tried reset unity but doesn't help.

---

### Post by alan21276 on 2012-09-04
I haven't tried this yet myself but I remember reading a post with a similar issue and the suggested remedy was to set up each desktop environment under a different user profile thus keeping the settings separate..........let me know how this works out for you.

---

### Post by cmcanulty on 2012-09-05
If I set up a different user then I can't get at my desktop or documents except through sudo right?

---

### Post by alan21276 on 2012-09-05
You may be able to share them via the preferences options, alternatively store them on a separate partition which can be mounted from each user.

Again I haven't tried this yet myself, I only looked into it when I first started using unity and didn't like it......but now I love unity and use only it, so I don't need to use different D.E.s.

Perhaps someone with a bit more knowledge can provide you with more precise details on how to achieve what you require, I'm a bit of a beginner myself having used only windows until last year, but so far I've faced just about every challenge ubuntu has to throw at you and have found solutions on these forums.

Good luck

---

### Post by istiska on 2012-09-06
Hi all,

Thanks for your help. So far I haven't solved anything, hehe.

1. I tried to remove unity and all its dependencies, however there are still some traces of unity/ubuntu-desktop (such as themes, lightdm). Is there a way to completely remove everything that was installed when I originally ran```
sudo apt-get install ubuntu-desktop
```? I'm thinking of re-installing Mint just to be sure that there's no trace of unity left.

2.  I'm a bit confused about the route of installing a different DE under a user profile. Aren't all DEs available to all users before logging in (i.e. in the MDM/lightdm/GDM login screen)? 

Ref: [http://ubuntuforums.org/showthread.php?t=1201738#2]("http://ubuntuforums.org/showthread.php?t=1201738#2")

If so, how does installing the DE when logged in from a different user solve this?

---

### Post by alan21276 on 2012-09-06
> **istiska said:**
> Hi all,

Thanks for your help. So far I haven't solved anything, hehe.

1. I tried to remove unity and all its dependencies, however there are still some traces of unity/ubuntu-desktop (such as themes, lightdm). Is there a way to completely remove everything that was installed when I originally ran```
sudo apt-get install ubuntu-desktop
```? I'm thinking of re-installing Mint just to be sure that there's no trace of unity left.

2.  I'm a bit confused about the route of installing a different DE under a user profile. Aren't all DEs available to all users before logging in (i.e. in the MDM/lightdm/GDM login screen)? 

Ref: [http://ubuntuforums.org/showthread.php?t=1201738#2]("http://ubuntuforums.org/showthread.php?t=1201738#2")

If so, how does installing the DE when logged in from a different user solve this?


Hi again.

1....have a look at the psychocats site for advice on how to achieve this.

here [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

2....the reason for this is to allow the user to change preferences in one D.E. with out effecting another as the changes for each would be saved in the user profile. You should even be able to modify your log in options i.e. on lightdm to only show certain D.E.s for each user although I am unsure how to do this.

Sorry if I cant be more helpful, but hopefully I am pointing you in the right direction.

---

### Post by istiska on 2012-09-10
@alan21276 Many thanks for your reply. I'm still mulling on how to make cinnamon and unity behave well together. So far have reinstalled Linux Mint with Cinnamon to remove all traces of previously installed unity and am still looking for info. Cheers for you help.

---

### Post by alan21276 on 2012-09-10
No problem,

I might not be able to provide exact technical details with my help, but if I can at least point someone in the right direction.

Good luck

---

### Post by Frogs Hair on 2012-09-10
With my Gnome shell Unity installation the same theme is used for each in my user profile even though Unity uses Compiz and the shell uses mutter. I'm thinking you won't be able to accomplish this within the same user profile.

---

