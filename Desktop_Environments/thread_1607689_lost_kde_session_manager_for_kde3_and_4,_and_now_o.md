---
title: "lost kde session manager for kde3 and 4, and now only will boot to run level 3"
date: 2010-10-28
forum: Desktop Environments
---

### Post by james2b on 2010-10-28
I lost my kde session manager (for kde3 and kde4), and now Kubuntu 9.10 only will boot to run level 3. This occurred when I used the synaptic package manager to remove all the kde 3 desktop, to then allow an upgrade to Kubuntu 10.04 version, due to a error message about that kde3. I was able to log into either kde 3 or 4 before this, so what do I type in that text mode run level 3 to fix this issue, and to have my KDE session manager back working ? Or do I now need to install a fresh Kubuntu 10.04 with only KDE 4.?

---

### Post by ankspo71 on 2010-10-28
Hi,
> Or do I now need to install a fresh Kubuntu 10.04 with only KDE 4.? 
Not necessarily... You might only be missing the KDM package. Maybe installing KDM or Kubuntu will fix it.

Try using this command:
sudo apt-get install kdm

Optionally, you can try to reinstall Kubuntu:
sudo apt-get install kubuntu-desktop
OR
sudo apt-get install --reinstall kubuntu-desktop

Hope this helps.

---

### Post by james2b on 2010-10-28
Okay I did run that; sudo apt-get install kdm, and update and upgrade while logged in to run level 3 text mode. So then after a reboot the kdm display and login manager screen was back, but the only 2 sessions available are; default and failsafe. The Default one flashes a darker screen quickly, then comes back to the login screen again. I thought it may be my NVIDIA display driver or Xorg so I ran; nvidia-xconfig, but same issue remains. So the removal of the kde3 may have damaged the kde4, so if I now run that other command as; sudo apt-get install kubuntu-desktop, then will that put in the kde4 desktop again ?

---

### Post by ankspo71 on 2010-10-28
Hi,
I thought maybe it was only KDM that got removed, but it appears removing KDE3 also removed the entire KDE4 desktop. Yes, kubuntu-desktop will install Kubuntu and every related package.
Hope this helps.

---

### Post by james2b on 2010-10-30
Okay thanks for the help, I did run; sudo apt-get install kubuntu-desktop and that did re-install my kde4 so I can now boot to full desktop. I had before thought it was; kde4-desktop to install it. Then I did do the full upgrade to Kubuntu 10.04 version, which did complete good, thanks.

---

