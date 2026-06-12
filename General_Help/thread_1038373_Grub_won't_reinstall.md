---
title: "Grub won't reinstall"
date: 2009-01-12
forum: General Help
---

### Post by joey-elijah on 2009-01-12
I've followed several tutorials on how to reinstall GRUB using both a live cd and unetbootin from inside windows. HOwever, GRUB is still not installed and i have no way of using Ubuntu. 

Using a terminal inside a live CD i can "sudo grub" etc and follow the most common steps - which all go fine until i reboot and bam! Straight into the Windows splash. 

I've manually tried booting from each harddrive - One boots into Windows, the other gives me "gRUB Loading... Error 17".

I'm started to get really frustrated by this. I really hope Ubuntu follows OpenSUSE and loads a helpful recovery section to the install media. 

Where do i go next? I'd hate to have to reinstall. I've only just got around to installing Ubuntu again after similar issues before, so to have to.... *not gonna think about it* lol

---

### Post by bodhi.zazen on 2009-01-12
How are you installing grub ?

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

---

### Post by caljohnsmith on 2009-01-12
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

