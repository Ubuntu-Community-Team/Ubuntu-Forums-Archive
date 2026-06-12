---
title: "3D problems with ATI radeon X1650"
date: 2008-01-11
forum: Desktop Effects &amp; Customization
---

### Post by kodiak66 on 2008-01-11
Hi I have been using Windows for 15 years. Stumble across Ubuntu just a few days ago and for the first time in many years it&#347; fun working with the system.

I have installed drivers for my ATI Radeon X1650 and restricted driver is working aswell as ATI control center. However when trying to enable Visual Effects Normal, Extra or Custom I get Error: The Composite extension is not available

I found[ THIS LINK]("http://cybernetnews.com/2007/10/21/how-to-enable-compiz-fusion-in-ubuntu/") and installed xserver-xgl and also compizconfig-settings-manager via synaptic.

After re-booting I lost my swedish keybord and graphics were really slow. The ATI control center were also not working. I unistalled xserver-xgl via synaptic and re-booted and I got the keybord back aswell as decent graphics.

The ATI driver is listed in restricted Drivers, status=in use and Enabled.

Would really appreciate if someone could help me out and get my graphic card working like it should in Ubuntu. Please keep in mind that after 15 years with Windows my computer intellect  is on a low level...

Best regards

---

### Post by kodiak66 on 2008-01-11
When running compiz in terminal I get
:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

However I can access Advanced Desktop setting but settings are not implemented.
 
It seems xserver-xgl needs to be installed. Since the installation from synaptic did nor work  
how should I install and configure xserver-xgl?

---

### Post by kodiak66 on 2008-01-11
All installation problems solved with Envy!

Envy should really be a part of the Ubuntu package!

For anyone who's having problems installing graphic driver try [http://albertomilone.com/](http://albertomilone.com/)

---

