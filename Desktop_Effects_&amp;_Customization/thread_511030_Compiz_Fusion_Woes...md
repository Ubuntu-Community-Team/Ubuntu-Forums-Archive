---
title: "Compiz Fusion Woes.."
date: 2007-07-27
forum: Desktop Effects &amp; Customization
---

### Post by transatlant1c on 2007-07-27
Hey guys, sorry for being a pest but I have been trying to install Compiz Fusion onto my Toshiba Satellite M60 and it's putting up a fight :( I have used Beryl on this computer without a single problem before but whenever I try to install it.. This happens:

```
Err http://au.archive.ubuntu.com feisty/main libfuse2 2.6.3-1ubuntu2
  503 Service Unavailable
Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/f/fuse/libfuse2_2.6.3-1ubuntu2_i386.deb  503 Service Unavailable
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

I followed [**this guide**]("http://ubuntuforums.org/showthread.php?t=481314") to the letter but I've had some problems.. As you can see :( I did also try a 'sudo apt-get update --fix-missing' but nothing happened.. And I'm in over my head :( I don't know anything much about Linux as I am faaairly new. Only been using it a month or two :(
Is it anything to do with this:

```
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz  503 Service Unavailable
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz  503 Service Unavailable
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz  503 Service Unavailable
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

?

Can anyone help me out? Pleeeeeeeeeease? I have enabled the 'nvidia restricted drivers' as well.. And got my video card (Geforce Go 6600) working with the correct resolution but apart from that.. Nothing. Any sort of help would be grealy appreciated :)
Thanks guys :)

---

### Post by benny2uf on 2007-07-27
i'm pretty new to ubuntu myself but it seems that your pc cannot contact the package servers. is your pc properly connected to the internet? if so try switching to a differnt locale maybe the australian (au stands for australia i guess) servers are down. to do that go to System-->Administration-->Software Sources and change the dropdown menu "Download from" to a different country

---

### Post by chrisblue on 2007-07-27
> **transatlant1c said:**
> Hey guys, sorry for being a pest but I have been trying to install Compiz Fusion onto my Toshiba Satellite M60 and it's putting up a fight :( I have used Beryl on this computer without a single problem before but whenever I try to install it.. This happens:

```
Err http://au.archive.ubuntu.com feisty/main libfuse2 2.6.3-1ubuntu2
  503 Service Unavailable
Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/f/fuse/libfuse2_2.6.3-1ubuntu2_i386.deb  503 Service Unavailable
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```I followed [**this guide**]("http://ubuntuforums.org/showthread.php?t=481314") to the letter but I've had some problems.. As you can see :( I did also try a 'sudo apt-get update --fix-missing' but nothing happened.. And I'm in over my head :( I don't know anything much about Linux as I am faaairly new. Only been using it a month or two :(
Is it anything to do with this:

```
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz  503 Service Unavailable
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz  503 Service Unavailable
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz  503 Service Unavailable
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz  503 Service Unavailable
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```?

Can anyone help me out? Pleeeeeeeeeease? I have enabled the 'nvidia restricted drivers' as well.. And got my video card (Geforce Go 6600) working with the correct resolution but apart from that.. Nothing. Any sort of help would be grealy appreciated :)
Thanks guys :)

Just delete all referenced to au. in the source.list file. I had the same issue and after that it d/l everything fine.

---

### Post by transatlant1c on 2007-07-28
> **chrisblue said:**
> Just delete all referenced to au. in the source.list file. I had the same issue and after that it d/l everything fine.

It's all good now :) The Australian servers must have just been down or something, I didn't change anything and they just updated this time.. Oh well. Anybody help me with my Compiz problem?

Thanks by the way :)

---

