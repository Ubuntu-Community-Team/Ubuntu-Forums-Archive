---
title: "No Boot Loader is installed"
date: 2006-06-26
forum: Desktop Environments
---

### Post by a30264 on 2006-06-26
Hi.
I’m having a problem installing the latest release of Ubunto-Desktop version.

1) It appears that the installation doesn't detect my installation of windows and doesn't install any boot loader... So, at the end of the installation, when the computer reboots, it always go to the windows and i can't load the linux...
I don't know if this is relevant, but my hard disc is a SATA.

2) Where can I configure the packages to be installed before installing Ubuntu?

Thanks in advance for any help! :)

ps: Sorry about my english...

---

### Post by Ramses de Norre on 2006-06-26
Can you try to install grub with a live disc? Look [here]("http://ubuntuforums.org/showthread.php?t=203976") for instructions.

---

### Post by a30264 on 2006-06-26
[QUOTE=Ramses de Norre]Can you try to install grub with a live disc? Look [here]("http://ubuntuforums.org/showthread.php?t=203976") for instructions.[/QUOTE]

I've installed the Ubunto with the live cd... but i'll try those steps!!
Thank you very much!!

and about the second question? how can i choose the packages?

---

### Post by Ramses de Norre on 2006-06-26
It's really very odd there is no boot loader installed then.. I've installed dapper on a computer of a friend of mine a couple of days ago with a live cd and grub was installed fine (though I wasn't asked anything about it which I didn't like..).
But try the steps, I hope it'll work.

---

### Post by a30264 on 2006-06-26
Maybe the problem is because the hard disc is a SATA? Or isn't any problem in there?

Well, i'll try your solution later, at night! i'm currently at work and need to work!! If my boss sees me in here I’m dead!!

Thank you very much again for your help

---

### Post by Ramses de Norre on 2006-06-26
I've got a sata myself (containing the /boot/ folder, first grub stage is on an ata though) and the friend I installed ubuntu for had a sata too on which grub installed perfectly.. so that shouldn't be any problem.

---

### Post by quedigg on 2006-06-26
i think it's partitioning problem, even if he intsalled ubuntu , the system should boot to ubuntu not windows ,regardless the boot loader configuration was successful or not

---

