---
title: "Setting up a net top"
date: 2009-06-23
forum: General Help
---

### Post by aja626 on 2009-06-23
Hi,
I'm  new to ubuntu and I'm looking for some advice/guidance. I own a web development company and want set-up a net top as an apache server with mysql and php to use when talking to potencial new accounts, since most don't have internet access. I want to use Ubunto over windows because of drive capacity. I have been experimenting with Ubuntu and have found problems with networking to windows drives and using web plugins like flash. 

My first question is:  I'm I going about this the right way or is there another option I should think about.  Any suggestions on moving files from the windows unit to the Ubuntu unit. An d last, any general guadance reging what I'm trying to do.

I hope I have articulated myself correctly.

Thanks

---

### Post by blueridgedog on 2009-06-23
If I read your post right, you have a windows laptop that you want to install Ubuntu on as a virtual machine, once loaded you want to install the typically LAMP stack for web development and have it answer http requests from the windows system.  

This should work fine using vmware or VirtualBox from Sun and is actually a common task.  The two will communicate on a dedicated IP network (guest os talking to host os).  It should work well as long as you use virtual machines rather than a wubi install.

The first step would be to get the virtual manager (wichever one you choose) working, then install ubuntu server.  Since the web browsing will happen in the windows OS, you will not have the flash issues you mentioned.

An added bonus is that you can develop virtual os images at the office and load them on the laptop as you need.

---

### Post by aja626 on 2009-06-24
Thanks for that advice. I actually want to make the net top a dedicated Ubuntu machine without windows. I will use your suggestion and install an Ubuntu server instead of the OS. Do they work the same? Does that make sense.... I'm very new to Linux,  I think once I get to understand it a little better I will be able to articulate myself better.

Thanks

---

### Post by 3rdalbum on 2009-06-24
Ubuntu Server doesn't contain a GUI. From the sounds of it, you want a GUI (and web browser etc).

You can install regular Ubuntu and then put Apache, MySQL and PHP on it. When you've installed Ubuntu, run:

```
sudo tasksel lamp-server
```

It will download and install those three programs for you, and configure them to work with eachother.

What problems have you been having with networking? And what problems with Flash? I haven't experienced any problems with either; maybe it's a lack of familiarity issue?

---

### Post by aja626 on 2009-06-24
Network problems: I can't get  my mshome network to mount on the Ubuntu machine. I can see the ubuntu machine on my windows machine. I get opening MSHOME, then I get unable to mount location

Flash, sometime works sometimes does not... should I reinstall the OS and start from the begining.... maybe I did something that cause a problem... I'm very new at this and as you know a little bit of knowledge is dangerous

---

