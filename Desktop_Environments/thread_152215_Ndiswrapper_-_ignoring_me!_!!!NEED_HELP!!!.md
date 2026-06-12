---
title: "Ndiswrapper - ignoring me! !!!NEED HELP!!!"
date: 2006-03-29
forum: Desktop Environments
---

### Post by samdude9 on 2006-03-29
Hi
I have just installed Dapper drake flight 5 and i figured it needed ndiswrapper for my wifi card so i installed that off the disc. That went fine and i installed the driver, wrote to modprode tried to run 'modprobe ndiswrapper' and it does not work. I checked the list of drivers and it said... hardware present, driver present'. The card has worked before with ubuntu.

please help!
Need the Net ASAP!

thx in advanced
bye
](*,) ](*,) ](*,)

---

### Post by seoatway on 2006-03-29
Apologies if this sounds obvious but, you did sudo modprobe didn't you ? - modprobe needs root privileges.

Cheers

---

### Post by samdude9 on 2006-03-29
done that
ndiswrapper does not work without it anyway!
thx anyway

---

### Post by sal on 2006-03-29
in dapper you have to blacklist the bmc43xx drivers:

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

then add ndiswrapper to /etc/modules

reboot and do an sudo modprobe ndiswrapper

---

### Post by samdude9 on 2006-03-29
Thankyou Thankyou Thankyou :) :) :) 
bye!

---

