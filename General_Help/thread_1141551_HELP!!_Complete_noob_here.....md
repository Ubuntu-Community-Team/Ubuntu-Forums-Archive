---
title: "HELP!! Complete noob here...."
date: 2009-04-28
forum: General Help
---

### Post by phoules gold on 2009-04-28
I'm running eeeXubuntu 7.1 on my ASUS 4g. I'm trying (and have been trying for quite some time) to install compiz. All of the walkthroughs are the same, and say that libgl1-mesa-dri is required...but I can't find it anywhere. It's not in the synaptic package manager, and when i try the apt-get, it tells me "...libgl1-mesa-dri is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source. However, the following packages replace it: libgl1-mesa-glx."
 
Is there any way that I can get libgl1-mesa-dri to get compiz running. 
 
Any help would be greatly appreciated.....
 
Thanks in advance.

---

### Post by prem1er on 2009-04-28
Did you expand your repositories?

---

### Post by phoules gold on 2009-04-28
No I have not....how does one do that...as I said...complete linux noob...sorry if the questions seem silly.

---

### Post by snowpine on 2009-04-28
Support for 7.10 (the Oct. 2007 release) ended earlier this month. I would recommend installing a more up-to-date OS. Xubuntu 9.04 (April 2009) has excellent support for the Asus eee pc. Compiz is a waste of resources on a machine of such limited specs, in my opinion, but go for it if it makes you happy. :)

ps I should add that eeeXubuntu is not an official Ubuntu project. You should ask your question on the eeeXubuntu forums as well. I am sure other users are probably in the same boat.

---

### Post by prem1er on 2009-04-28
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

But you should be using libgl1-mesa-glx anyway.  So after you expand your repos do this.

```
sudo apt-get install libgl1-mesa-glx
```

---

