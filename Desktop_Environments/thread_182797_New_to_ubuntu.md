---
title: "New to ubuntu"
date: 2006-05-26
forum: Desktop Environments
---

### Post by tiwaris on 2006-05-26
Hello all,

I am giving ubuntu (version 6.0.6) a shot and would like to stick to it.

For ubuntu to be useful, I need to install several apps such as (acroread,gv,kile,xfig,gnuplot,kdevelop,gcc etc.) I searched in the synaptics package manager for some of these and it does not have these applications in its database.

I have just setup ubuntu few hours ago. 

Do I need to do something extra to install above mentioned packages?

Thank you.

---

### Post by johnc4510 on 2006-05-26
If you haven't enabled the extra repositories in synaptic, you need to. 
Launch Synaptic, choose settings from the tool bar, then choose repositories. Put a check in each one that is not checked. Then click on the Reload button, once it has done it's thing, click on the Mark all Upgrades button, then Apply. After that you should be able to find and install your apps

---

### Post by Sef on 2006-05-26
Easiest way to install apps:

System > Administration > Synaptic Package Manager

Read these:

[RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

[AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

You need to add the repositories to get packages that are in Universe (free as in freedom software) and Multiverse (nonfree software.)

---

### Post by Super King on 2006-05-26
Yup, you just need to install the extra software repositories. 

I'm in Windows right now but in Synaptic you just need to click on Options->Repositories. Then click Add and choose 'multiverse' and 'universe' from the list. Then click Reload and they should be there.

---

### Post by tiwaris on 2006-05-26
Thanks to all of you for your informative replies.

I am able to get the packages, I want.

---

