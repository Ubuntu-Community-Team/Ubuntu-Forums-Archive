---
title: "Change File Location in Evolution and KMail"
date: 2007-02-16
forum: Desktop Environments
---

### Post by R0sbif on 2007-02-16
Hi all,

Basically I am trying to find a way of separating my data from my programs...  As a new Linux convert I am concerned about having my data on the same disk as the OS because of the number of times I have reinstalled it already and if I make a mess, I would like to just reinstall and not have to worry about having to extract and export data first.

There are 2 PCs that I would like to do this with.  One is running Kubuntu 6.10 amd64 and the other one is running Ubuntu 6.10 x86.

Is there a way of moving the mail files from wherever they are to a location on another partition that is mounted automatically on boot?

The Ubuntu PC is using Evolution and the Kubuntu PC is using Kmail. 

I can't even find where the files are currently :)


If this seems particularly weird, what is the "normal" way of keeping Data on this OS?  Everything in the home/user directory?

Thanks for any help :)

Best regards

Rich

---

### Post by aysiu on 2007-02-16
Sure, try this:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Or, you can just move that one mail folder and symlink it back to /home/rich

For example (I don't use KMail or Evolution, so I'm guessing the files locations), let's say you have your Evolution mail in /home/rich/.evolution and want to move it to /media/external, you can move the folder there: ```
mv /home/rich/.evolution /media/external/
``` Then you can symlink it back ```
ln -s /media/external/.evolution /home/rich/.evolution
``` That way, the folder will *appear* to be in ~/.evolution but really be in /media/external/.evolution.

---

### Post by R0sbif on 2007-02-17
Well that's brilliant - thank you very much :)

I'll try and think of a more challenging question next time

Thanks again. Have a good weekend 

Rich

---

