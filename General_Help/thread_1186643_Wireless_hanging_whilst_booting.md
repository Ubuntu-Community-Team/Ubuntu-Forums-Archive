---
title: "Wireless hanging whilst booting"
date: 2009-06-13
forum: General Help
---

### Post by Tomo74 on 2009-06-13
Hi, I hope you can help.. I'm completely new to ubuntu and linux and i have just enabled my wireless lan and connected to my infrastructure. I have rebooted and system is hanging at Ubuntu logo.. I have gone in via recovery mode and discovered it is hanging whilst loading hardware drivers

12.051742 wlan: 0.9.4
12.100856 ath_pci: 0.9.4
12.102672 ACPI: PCCI Interrupt link [LN4A] enabled at IRQ 19
12.102770 ath_pci 000:05:00.0: PCI INT A -> Link[LN4A] -> GSI 19 (Level, low) -> IRQ 19

How do i remove this line so i can boot it back up and then how do i remove the dodgy driver that is causing this problem

Thanks

Neil

---

### Post by synapsys on 2009-06-13
First, add ath_pci to your blacklist so that you can boot.
Your best bet would be to boot to a livecd. 
Mount the partition with your filesystem.
Edit /etc/modprobe.d/blacklist so that it contains blacklist ath_pci.
You may have to un-comment a line or add a line.
Also check if there are any files in modprobe.d already named blacklist ath_pci or something like that.
Then reboot.

Oh yeah... the line should read

blacklist ath_pci

---

### Post by Tomo74 on 2009-06-15
Thanks for your help.. I will give it a try later.

---

### Post by Tomo74 on 2009-06-18
Superb that sorted it out.. Now onto fixing HDMI Adudio

---

### Post by Mr. Natural on 2009-06-30
Hi there,

I just wanted to say thanks for this handy solution. I'm not that familiar with Ubuntu and Linux in general... That's why I rely on awesome posts like this one!

Keep up the excellent work...

Any ideas how I can bring my network adapter back to life now? 

Regards
Matt

Edit: Sorry folks, I was being stupid. Figured it out myself... Just activated ath5k using a solution from the German Ubuntu Forum

```
sudo modprobe -rf ath_hal 
sudo modprobe -rf ath_pci
echo blacklist ath_pci | sudo tee -a /etc/modprobe.d/blacklist.conf
echo blacklist ath_hal | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe ath5k
echo ath5k | sudo tee -a /etc/modules
sudo /etc/init.d/networking restart
```

---

