---
title: "No compizconfig ccsm adavanced desktop effects settings"
date: 2007-10-30
forum: Desktop Effects &amp; Customization
---

### Post by sirab on 2007-10-30
Alright I've googled this, lurked the forums, and have rtfm still cant find a solution

there is no compizconfig package on synaptics.

when i go into terminal and type ccsm it tells me its not installed when i sudo apt-get install it tells me that package is not found.

When i try  add/remove i get "list of applications not available every time i click the advanced desktop effects settings file.

so please help i think it might have something to do with my repositories or something...

thank you in advance

---

### Post by Jose Catre-Vandis on 2007-10-30
```
sudo apt-get install compizconfig-settings-manager
```

```
ccsm
```

make sure you have universe enabled in the repos

---

### Post by Zorael on 2007-10-30
I don't quite follow you as I'm running Kubuntu, but have you tried installing compizconfig-settings-manager? I think that's the one.

---

### Post by sirab on 2007-10-30
Thanks guys. It's all good now it was my repositories.

KInda feeling stupid for not checking them from the start but whatever... at least i knew it was my repositories maybe not a complete ubuntu noob anymore..

---

