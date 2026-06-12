---
title: "I think I broke my Ubuntu..."
date: 2013-02-27
forum: Desktop Environments
---

### Post by FourLetterUsername on 2013-02-27
Ok, so I recently installed Ubuntu 12.10 to upgrade from the older version I had, which was still Narwhal. 

The issue: Upon being ticked at Lugaru's non-mouse-capturing window (it's a game with ninja rabbits and stuff), I went searching for a config file of sorts to change that. I found the file, but since it was under /usr/games, I couldn't edit it. So instead of just changing the specific file and it's directory to my ownership via sudo chown, I changed the entire /usr directory.

Yeah. I'm an idiot.

Anyways, I got the sudo command back and I *think* I reset the rest of the permissions back to normal, but everything is still royaly borked to high heaven. I now have to use the alsamixer command to change my sound, as there is no icon on the upper bar. Also, I always get the "system has encountered an error" message, and a few other errors. On top of all that, the little shutdown/gear symbol used to logout, shutdown, reboot, etc. now shows absolutely nothing when clicked upon.

I know that I could and probably should reinstall my Ubuntu, but is there anyway to nurse my Ubuntu back to health?

Thanks for your time,
     FourLetterUsername

---

### Post by unheeding on 2013-02-27
Try setting it to have root as the owner with chown

Then, set the permissions with:

```
sudo chmod -R 755 /usr
```

I hope this works for you!

---

### Post by FourLetterUsername on 2013-03-06
Sorry for delayed response...

So I went to double check the permissions for sudo, and guess what. It was borked again. Thanks for the suggestion, wish I coulda used it...

---

