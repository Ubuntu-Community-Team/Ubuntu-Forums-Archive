---
title: "update something and grub menu got alot option"
date: 2009-05-06
forum: General Help
---

### Post by StormRoBoT2 on 2009-05-06
update something and grub menu got a lot option then usual look at the picture

is it safe to use the new kernal? 2.6.28.12? or should i just use the old one?2.6.28.11?

---

### Post by mcduck on 2009-05-06
When the kernel is updated the new version doesn't overwrite the old one. This allows you to boot the machine with the old kernel if the new one, for some reason or other, doesn't work correctly on your machine.

After the update you should use the new kernel, and if it works fine for you, you can later on uninstall the old kernel with Synaptic Package Manager. Removing the old kernel also automatically removes it's entry from the Grub menu.

Many people prefer always keeping at least one old kernel version available, but personally I've never found any use for that and just uninstall the old kernel after couple of days.

---

### Post by kpkeerthi on 2009-05-06
To remove the unused kernel, search for **linux-image** in Synaptic and mark the versions you don't need for complete removal. You grub will also be updated.

---

### Post by StormRoBoT2 on 2009-05-06
aright thanks for the quick reply, and the new kernel work fine for me, and faster the the old one, i can see it on the boot, its boot and load the system faster then the old kernel, ill just keep the old kernel for a couple days, and will remove it, and i might need some help when removing it i guess

---

### Post by wolfestine on 2009-05-06
If you don't like this many entries, and wish to keep the old kernel as well as the new one, you could edit menu.lst to remove the unwanted entries, n then in case you have a problem, you could always boot using the old kernel by using the command mode of the grub.

---

### Post by mcduck on 2009-05-06
> **StormRoBoT2 said:**
> aright thanks for the quick reply, and the new kernel work fine for me, and faster the the old one, i can see it on the boot, its boot and load the system faster then the old kernel, ill just keep the old kernel for a couple days, and will remove it, and i might need some help when removing it i guess
It's really quite easy to remove the old kernels. What I usually do is search for "linux" in the package name in Synaptic to find the **linux-image**, **linux-headers** and **linux-restricted-modules** packages. Then  just right-click on the old versions and select "Mark for Complete Removal" & hit the Apply-button. Just make sure you only remove the old kernel versions. :)

For example to remove 2.6.28-11 kernel you'd need to uninstall packages linux-image-2.6.28-11-generic, linux-headers-2.6.28-11-generic and linux-restricted-modules-2.6.28-11-generic (assuming you use the generic kernel).

---

