---
title: "Compiz Issue - No workspaces or wobbly windows after a botched source install."
date: 2010-09-15
forum: Desktop Environments
---

### Post by masen on 2010-09-15
In order to correct bug #[459647]("https://bugs.launchpad.net/ubuntu/lucid/+source/compiz/+bug/459647") in compiz (as I have done on 2 other PCs) I downloaded, modified, and compiled the source with apt-src and make. Then I installed the produced .deb files with dpkg -i.

For whatever reason the new compiz didn't have wobbly windows nor could I switch workspaces. Compiz is running and I do know however that compositing is working as Docky is still functional (and doesn't really work without compositing).

So I uninstalled all of the compiz packages and reinstalled the versions from the official repository. The same issue remained. During this time I have restarted my computer several times with different configurations. I tried to install compiz packages from the [http://ppa.launchpad.net/compiz/ppa/ubuntu](http://ppa.launchpad.net/compiz/ppa/ubuntu) PPA and still the same problems exist. I'm not sure if there are any other problems that I haven't noticed yet.

Finally, in an attempt to fully purge my computer of all things compiz and start over, I got the following error:

```

masen@dv6000m:~$ sudo apt-get autoremove --purge compiz*
[sudo] password for masen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compiz-code
masen@dv6000m:~$ 

```I'm not sure what "compiz-code" is, but that's the name of the folder that I downloaded the source into. After this command, no packages are removed

I'm currently running Lucid 10.4.1 with all the latest updates. My graphics card is an Intel 945M mobile chipset. I run a similar configuration on 2 other computers with no issues.

Has anyone ever seen this? Or have any idea how I can get compiz-code out of my package database. I know the problems I'm encountering aren't high priority, but not having workspaces gets annoying and I have no clue what else is broken with my 'half-broken' compiz.

Thanks in advance

---

