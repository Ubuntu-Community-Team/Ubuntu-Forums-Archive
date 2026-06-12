---
title: "ubuntu 12.04 problem with screen brightness"
date: 2012-08-16
forum: Desktop Environments
---

### Post by alvpizz on 2012-08-16
hello! i am using ubuntu 12.04 on a samsung RC530-S02. since i have updated my system, i have a strange problem with the screen's brightness. normaly my pc had 7 different brightness values (and i could use all 7 of them!), but now i have olny 2, because if I am using the highest grade of brightness and i want to decrease it, the screen goes straight to the lowest grade of brightness. the same thing happens the other way round. 
i underline that this has happened since i have updated the last time my system. 
totaly, this problem has happened to me twice, because trying to solve it, i have already re-installed once my computer. after that, i have bravely updated it again, and the problem is re-occurred. 
becasue of the great number of upgrades that the update manager installs all toghether, I don't know which of theese is the bad one.

can someone help me:confused:?

---

### Post by black veils on 2012-08-16
when you boot the computer, hold the shift key down, you will soon see grub, choose older kernel from the list, boot the system from that list item, and see if you still have the problem

---

### Post by alvpizz on 2012-08-16
fantastic;)! i did not thought about it. i selected the only other kernel option that i had, and now the brightness is working as it should.
but now i have a question: to make the system start always from this other kernel i have to install startupmanager and modify some options?

---

### Post by black veils on 2012-08-16
> **alvpizz said:**
> fantastic;)! i did not thought about it. i selected the only other kernel option that i had, and now the brightness is working as it should.
but now i have a question: to make the system start always from this other kernel i have to install startupmanager and modify some options?

that would be my method, and there is nothing wrong with it, just change what the default system is in startup manager, it may boot to the wrong thing though, because ubuntu seems to confuse that app, but it is consistent in the error, it will be about 2 off.

another way to deal with it would be to remove the newer kernel (though i dont know if you should or if there is a proper method) and lock the version which works for you, using synaptic.


or if it is newly installed, the laziest way might be to reinstall and then lock the kernel version in synaptic. first you will need to install it. open the terminal and paste ```
sudo apt-get update && sudo apt-get install synaptic
```

---

### Post by alvpizz on 2012-08-16
yeah I've already installed synaptics.. i found an other way, i'm using grub-costumizer.. i will soon restart and see if i manage to get the working kernel as first option :popcorn:

---

### Post by black veils on 2012-08-16
would have been safer to use startup manager, depending on your hdd configuration i suppose. its an easy app to use.

---

### Post by alvpizz on 2012-08-16
yes, but startupmanager has been removed from the Precise repositories. it is no more available...

---

### Post by black veils on 2012-08-16
weird, i see it.. i have the canonical partners software source enabled, if that makes a difference.

```
startupmanager
```

---

### Post by alvpizz on 2012-08-16
ok it's workink now! thank you very much :) !!

---

