---
title: "synaptic reload problem"
date: 2009-04-10
forum: General Help
---

### Post by icarid_17 on 2009-04-10
hello, I have tried to add the cinerella repo, which did not work, it complained about a GPG key, which i looked up, and i found a post, i followed the instructions, my problem now however, is that if I click reload, synaptic reloads and all of the downloads just fail, but i do not get an error once its all done, i have attached a screenshot and hope that someone will know what my problem is

---

### Post by Elfy on 2009-04-10
Can you run this and post any errors you get please

```
sudo apt-get update
```

---

### Post by icarid_17 on 2009-04-10
> **forestpixie said:**
> Can you run this and post any errors you get please

```
sudo apt-get update
```
ran it, did not get any errors

---

### Post by _khAttAm_ on 2009-04-10
> **icarid_17 said:**
> hello, I have tried to add the cinerella repo, which did not work, it complained about a GPG key, which i looked up, and i found a post, i followed the instructions, my problem now however, is that if I click reload, synaptic reloads and all of the downloads just fail, but i do not get an error once its all done, i have attached a screenshot and hope that someone will know what my problem is

what solution did you follow?

what happens if you try to install a software via synaptic?

---

### Post by icarid_17 on 2009-04-10
> **_khAttAm_ said:**
> what solution did you follow?

what happens if you try to install a software via synaptic?
there was only one, it was to add a few keys from the mediabuntu repo

---

### Post by icarid_17 on 2009-04-10
> **icarid_17 said:**
> there was only one, it was to add a few keys from the mediabuntu repo
synaptic's reload fails, so the package is not the when i quick search

---

### Post by _khAttAm_ on 2009-04-10
Do you also get **Hit**s along with the **Fail**s??

---

### Post by icarid_17 on 2009-04-10
> **_khAttAm_ said:**
> Do you also get **Hit**s along with the **Fail**s??
they all hit in the terminal, the en_CA are ignored, the problem is that despite hitting the sites, nothing actaully happens,(it takes about 2 seconds for the update to complete, because nothing is downloading)and when i try reloading in synaptic, everything fails

---

### Post by _khAttAm_ on 2009-04-10
Hit means that the lists are already up to date. And I think you get the hits with synaptic too. Please scroll down and check.

---

### Post by icarid_17 on 2009-04-10
> **_khAttAm_ said:**
> Hit means that the lists are already up to date. And I think you get the hits with synaptic too. Please scroll down and check.
I see, so if it doesnt say failed, but nothing happens, it just means that everything is fine, but why can't I find cinerella (I added it to my repo list)

---

### Post by _khAttAm_ on 2009-04-10
^ make sure that the repo you selected is for your os version and you added it correctly. BTW, what is the repo you used?

---

### Post by kostkon on 2009-04-11
> **icarid_17 said:**
> I see, so if it doesnt say failed, but nothing happens, it just means that everything is fine, but why can't I find cinerella (I added it to my repo list)
Don't use the quick-search to find it (it fails sometimes) but use the regular search in Synaptic.

Hope that helps.

---

