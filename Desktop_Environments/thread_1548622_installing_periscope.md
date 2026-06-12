---
title: "installing periscope"
date: 2010-08-08
forum: Desktop Environments
---

### Post by shkelzen on 2010-08-08
Hello,

I was trying to install periscope, from the instructions here: [http://code.google.com/p/periscope/wiki/NautilusSupport](http://code.google.com/p/periscope/wiki/NautilusSupport)

The problem is that at:
cd ~/.nautilus/python-extensions 

I get an error:
bash: cd: /home/mycomp/.nautilus/python-extensions: No such file or directory

I am not good at command line and new to Ubuntu so I guess I am doing something wrong.

Anybody has any idea what the problem is?

Thank you

---

### Post by shkelzen on 2010-08-08
no idea?

---

### Post by patd on 2010-08-17
Hi,

I'm the developer of periscope. As a Ubuntu user, you can better install the periscope-gnome package. Follow the wiki:
[http://code.google.com/p/periscope/wiki/UbuntuRepository](http://code.google.com/p/periscope/wiki/UbuntuRepository)

Then search and install from Synaptic:
python-periscope (the code for periscope)
periscope-gnome (the Nautilus integration)

Note that you need to restart Nautilus in order to have it appear (either by typing 'killall nautilus' in the console or by restarting your Gnome session)

But if you wish to install it manually (which I don't recommend as you'll loose the ability to get updates from the Application Manager) : you should create the missing folder:

cd ~/.nautilus
mkdir python-extensions

If you have issues, please reply and I'll help you out, thanks for trying periscope.

---

### Post by shkelzen on 2010-08-17
> **patd said:**
> Hi,

I'm the developer of periscope. As a Ubuntu user, you can better install the periscope-gnome package. Follow the wiki:
[http://code.google.com/p/periscope/wiki/UbuntuRepository](http://code.google.com/p/periscope/wiki/UbuntuRepository)

Then search and install from Synaptic:
python-periscope (the code for periscope)
periscope-gnome (the Nautilus integration)

Note that you need to restart Nautilus in order to have it appear (either by typing 'killall nautilus' in the console or by restarting your Gnome session)

But if you wish to install it manually (which I don't recommend as you'll loose the ability to get updates from the Application Manager) : you should create the missing folder:

cd ~/.nautilus
mkdir python-extensions

If you have issues, please reply and I'll help you out, thanks for trying periscope.

Thank you for your reply.

Actually, I tried what you suggest but still, even after adding to the repositories what you say, i can not find anything relating to periscope.

---

### Post by patd on 2010-08-17
Ok, I just found out there was a problem with my latest build in the repository. I'll try to fix this and upload a new version of periscope.

---

### Post by shkelzen on 2010-08-17
Looking forward, then.

---

### Post by patd on 2010-08-21
I've uploaded the python-periscope package and periscope-gnome packages for Lucid Lynx.

This should appear in Synaptic if you've got the following ppa by doing:
sudo add-apt-repository ppa:patrick-dessalle/ppa

---

