---
title: "System problem after game install with Synaptic"
date: 2009-05-24
forum: General Help
---

### Post by ricbritain on 2009-05-24
It seems I have screwed my Ubuntu 9.04 up inadvertently. After finally getting the whole thing going I became over ambitious and decided to use Synaptic Manager to install the game 'Battle for Westnoth'. I've successfully installed other games recently so didn't see a problem. The install seemed too reach 100% before I got some message saying parts had failed. Since then I've had a little 'no entry' red sign in the top right of the screen. My Synaptic no longer functions and when I try to complete installing the remaining games files I'm told I don't have enough space. I go to 'add/remove' to make space but that won't work either. I've tried searching and can not find where the other games are saved, otherwise I would manually delete some of them. I am given various sudo commands which I have tried but come to nothing. I think this might be a big one to solve. I have screen shots showing the result of trying to open synapse manager and add/remove. I've tried turning it off and on again but that never fixed it

---

### Post by albinootje on 2009-05-24
> **ricbritain said:**
> I've tried turning it off and on again but that never fixed it

Can you post the output of the following in a terminal :
```

df -h
sudo apt-get update
sudo dpkg-configure -a
sudo apt-get -f install

```

---

### Post by ricbritain on 2009-05-24
> **albinootje said:**
> Can you post the output of the following in a terminal :
```

df -h
sudo apt-get update
sudo dpkg-configure -a
sudo apt-get -f install

```

Thanks for that. After a lot of searching on forums I found those command lines and experimented. I got the synaptic back and then deleted the broken files in the synaptic. That did the trick. Everything is back to normal again, for the minute at least.

---

