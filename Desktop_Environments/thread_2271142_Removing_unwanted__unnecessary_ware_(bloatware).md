---
title: "Removing unwanted / unnecessary ware (bloatware)"
date: 2015-03-27
forum: Desktop Environments
---

### Post by mandar2 on 2015-03-27
Hi guys,

Few months ago i used Manjaro with openbox and loved it. Basically because of Openbox WM. Anyway i wanted to do a minimal install and build my own DE with Openbox. However, I couldn't cause of some problem with mini.iso. Cutting long story short i used following links to put all together with hours of tweaking and googling.

[http://wealsodocookies.com/posts/openbox-a-windows-environment-for-hackers/](http://wealsodocookies.com/posts/openbox-a-windows-environment-for-hackers/)
[http://ndever.net/articles/linux/install-openbox-ubuntu-1304-1310](http://ndever.net/articles/linux/install-openbox-ubuntu-1304-1310)

Now i still have unity and all the basic stuff of Ubuntu 14.04.2 which i don't need. However, due to all the basic stuff many of my function keyboard keys work and networkmanager and batterymanager. So i don't want to loose all that. But want to remove unity-greeter, unity, hud, deja-dup and all that. Can anyone help me with it? Please?

At the end i want to make an iso with systemback and put it on the sourceforge or git or somewhere.

---

### Post by v3.xx on 2015-03-27
You can use Synaptic Package Manager to remove packages.  It will tell you what will be removed, any conflicts and other things before you do the removal.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

Here is a list of all things Ubuntu that are installed.

[http://packages.ubuntu.com/trusty/ubuntu-desktop](http://packages.ubuntu.com/trusty/ubuntu-desktop)

---

### Post by buzzingrobot on 2015-03-27
I've done the remove Unity thing once or twice as an experiment.  My advice:  Remove packages one at time in Synaptic. Make a note of any other packages that may also be removed and be prepared to add them back to maintain a usable system. A minimal batch of Unity-related packages cannot be removed because a number of other non-Unity packages are compiled against them.

---

### Post by ian-weisser on 2015-03-27
> **mandar2 said:**
>  However, I couldn't cause of some problem with mini.iso.

What problem with the mini.iso, exactly?
For what you want to do, the Minimal Image seems ideal.
Otherwise you needlessly waste hours manually pruning packages.

---

### Post by mandar2 on 2015-04-01
Ended up by doing fresh install of Xubuntu. 520mb Ram usage on idle. Fine.

Regarding the mini.iso, everything works fine till select and install. Select and install didn't work, kept on giving me errors. See images. Further it won't even do grub install and be done with the installation.

Sad, i really wanted to make my own O.U.R. (Openbox ubuntu remix)

I guess there can be a problem with the network, however for the base install it worked fine and also didn't give any error for network configuration.

Anyway didn't have anymore time for it so went Xubuntu.

---

### Post by sudodus on 2015-04-01
Maybe you had some bad version of the Ubuntu mini.iso. You can find good versions via [this link]("http://ubuntuforums.org/showthread.php?t=2230389&p=13211730#post13211730"). I build systems from these versions of the mini.iso.

Try the 14.04 LTS versions.

---

### Post by Melodie on 2015-07-15
Hello, I hope it's not too late for you. :)

I have been remixing Ubuntu with Openbox since 2012 and now it's ready for Trusty as well, and also ready to invite more people to join as contributors. Here is a recent post: [Bento Openbox Trusty (Ubuntu Openbox Remix) available for test](http://ubuntuforums.org/showthread.php?t=2286820). 

This post presents the latest Bento Openbox remix full blown, a very small and even lighter is also planned for very soon. (Also I have installed from mini.iso in the paste, it's fun but time greedy and well, I had missed a package or two which where not obvious to guess and some programs, such as Midori never worked well because of that… ).

---

