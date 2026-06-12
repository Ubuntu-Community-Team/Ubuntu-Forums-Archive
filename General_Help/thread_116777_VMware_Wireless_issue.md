---
title: "VMware Wireless issue"
date: 2006-01-13
forum: General Help
---

### Post by silllz on 2006-01-13
I installed Ubuntu with VMware on an IBM laptop.  I ran iwconfig and have no wlan0 and am trying to install a Cisco 352 aironet card.  I am new to linux so if someone can help me out I would be greatful.

How do I get the wlan0? 

Why is my Cisco card not plug and play like it should be?

What do I need to do in more or less step by step directions?

---

### Post by Robor on 2006-01-13
A quick searched turned up a post by m2mike here...  [http://ubuntuforums.org/showthread.php?t=22660](http://ubuntuforums.org/showthread.php?t=22660)  Have a look and see if that helps?

---

### Post by Aaron Hoy on 2006-01-13
wait, so correct me if i' wrong.  you have windows installed as the host OS, and vmware installed on windows and then linux installed in vmware, right?  In this case I would recomend you choose the option in vmware that the guest OS just use the host OS's internet connection.  Then from the perspective of the linux guest OS, it will always have a normal ethernet connection, while as windows switches between the ethernet and wireless it can forward the connection through vmware as one uninterrupted internet connection.  The option is there when you configure the VM, it gives several different options about how to connect the guest os to the internet.

---

### Post by silllz on 2006-01-13
I can try this but really I need Airsnort to recognize my wireless card.

---

### Post by Aaron Hoy on 2006-01-13
If you want a linux program to directly interface with your wireless hardware I think you will have a kind of hard time doing that through vmware since it runs the OS in a virtual environment.  Perhaps it's possible on one of the options though.  Have you considered a dual boot?

---

### Post by 0MG on 2006-12-22
Reviving this thread...

I also would like to use my wireless extensions in a virtual machine. I am running Dapper which has VMware server installed. I have a virtual machine running nUbuntu. I can use the network just fine in the VM but I have no wireless extensions, it's basically acting as a wired connection. Is there a workaround?

---

### Post by mbeierl on 2006-12-22
VMWare does not pass the physical wireless card through to the VM.  Sorry - it can't be done.  You'll need to boot directly into linux using a live CD or a hard drive install if you really want to talk to the wireless card.

---

