---
title: "Don't see kubuntu-desktop in Synaptic"
date: 2007-04-24
forum: Desktop Environments
---

### Post by obenauer on 2007-04-24
I've been using Ubuntu and Kubuntu for a year at work and home (Dapper and Edgy), and installed Feisty Fawn on my laptop at home.  Usually I install the Ubuntu CD and install kubuntu-desktop to get KDE (which I prefer).  But unlike with Dapper and Edgy, when I try:

sudo apt-get install kubuntu-desktop

I get a message that "kubuntu-desktop" is not a recognized package.  I also tried running Synaptic and searching for Kubuntu or KDE, and neither search showed "kubuntu-desktop" or anything looking similar.

I also tried installing Kubuntu directly, which worked, but I wanted Synaptic installed, and apt-get again didn't recognize "synaptic".  I tried searching with "sudo apt-cache search synaptic", and I tried searching Adept, but still couldn't find it.  I was also unable to install "ubuntu-desktop" (package not recognized).

Have these packages been renamed?  Does anyone know how I can add Kubuntu to my Ubuntu installation?  I like being able to switch desktops when it's useful.  It hasn't been a problem with the previous two releases.

---

### Post by Sherlock Holmboy on 2007-04-24
It shows up in my repos, check to make sure they are all enabled and do ' sudo apt-get update '

---

### Post by obenauer on 2007-04-24
> **Sherlock Holmboy said:**
> It shows up in my repos, check to make sure they are all enabled and do ' sudo apt-get update '

Thanks for the advice -- I hadn't thought of updating the repositories (it was just a few days after the release, so I didn't think there'd be any updates yet).  I'll try it when I get home tonight.

---

### Post by obenauer on 2007-04-25
Yep, I tried it at home, and all I needed to do was "sudo apt-get update".  Thanks for the help.

---

