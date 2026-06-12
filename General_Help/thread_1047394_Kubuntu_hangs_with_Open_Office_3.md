---
title: "Kubuntu hangs with Open Office 3"
date: 2009-01-22
forum: General Help
---

### Post by aseltzer144 on 2009-01-22
I am running Kubuntu 8.10, installed on an HP Mini 1000 with Wubi. Its been running quite nicely, untilt today.

I recently upgraded Open Office to 3.0. I can open and edit in the word processor just fine. However, when I go to save and open the File menu, Kubuntu completely locks up. I can get it to restart with ctrl-alt-del, but the same problem recurs. 

Any thoughts? Will a shift to Ubuntu cure this? Obviously access to a word processor is critical and I need to know if I should abandon OO3, or Kubuntu.

My hardware config is 1.0Gb RAM, 60 Gb HD (not flash drive), Intel Atom N270. Other apps seem to run ok.

Thanks.

---

### Post by gjoellee on 2009-01-22
Which way did you install it?

From repo or source?

Do you have java installed? It is smart to have java installed, try this: ```

sudo apt-get install ubuntu-restricted-extras %% sudo apt-get install kubuntu-restricted-extras 
```

---

### Post by aseltzer144 on 2009-01-22
I installed from repo, I believe. I went to add new thrid party source in Adept and then installed OO3 from there.

I thought I had java installed, but I will try installing the restricted extras.

In general, is OO3 known to be operable and stable under either Ubuntu or Kubuntu 8.10?

---

