---
title: "Intrepid only boot to GRUB after installation"
date: 2009-03-31
forum: General Help
---

### Post by kincanonmi on 2009-03-31
I have an older MPC computer with removable hard drive tray that I use to aboot different OS's. Wen I installed Intrepid the system will only boot to GRUB. The HD is a 250G Maxtor and I have a ATI video card and a NET Gear wireless G NIC. I've re-installed the system twice with the same results. I'm pretty new ti Linux so any help would be helpfull.

---

### Post by meierfra. on 2009-03-31
How old is  your computer?
How much ram?

In order to get a clearer picture of your setup, I suggest to boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by kincanonmi on 2009-03-31
It seems I left out part of my question when I submitted my request. What I really need to fix is getting the machine to boot in Gnome Desktop. As to the question to the computers age it's about 5 years old and runing with a Gig of ram.

---

### Post by meierfra. on 2009-03-31
Do you get the grub menu where you can choose between the different OSs?
  If yes, what exactly happens when you try to boot Intrepid?
Could you run the boot info script and post the "RESULTS.txt"?

---

### Post by kincanonmi on 2009-04-01
> **meierfra. said:**
> Do you get the grub menu where you can choose between the different OSs?
  If yes, what exactly happens when you try to boot Intrepid?
Could you run the boot info script and post the "RESULTS.txt"?
No! Intrepid is the only operating system on the HD. After the install and the system re-booted it started and loaded only as far as the Grub command line prompt.

---

