---
title: "I need help with getting a XGL session to happen"
date: 2007-08-11
forum: Desktop Effects &amp; Customization
---

### Post by Adactuslatem on 2007-08-11
Well I have looked at every thread I can find to try and get xgl to work. I am running  a P4 3.5ghz single core processor with 512MB of ram and an ATI radeon 9550 agp video card. 

I have got beryl installed and got the scripts to run, but when I start up the xgl session it will only show a black screen and very messed up graphics. I cannot get beryl/the fglx drivers working. 

Can anyone help me out?

---

### Post by stido on 2007-08-12
if you use the restricted/proprietary driver from ATI, it comes bundled with a kind of settings GUI (Catalyst or something)
i believe there are some extra driver tweaking/settings in the general tab.
try changing some settings there first

---

### Post by hidden_leaf_sasuke on 2007-08-12
head on to my tutorial for ATI+XGL+Compiz Fusion at ubuntu4life.blogspot.com..if you success or fail to install one, please leave me a comment..:) i love to hear from you..:)

---

### Post by Adactuslatem on 2007-08-13
Geh, I forgot what site I used for the install, but I got it working!!!  I installed the proprietary drivers that feisty found for me. 

I configured them with sudo dpkg reconfigure-xserver-xorg 
I restarted
I made the Xgl start up script and changed the desktop profile, then I logged out and started in xgl, and it worked! I had beryl!

So I think before I didn't configure the drivers properly, and who says the radeon 9550 doesn't work well with Beryl :P

---

