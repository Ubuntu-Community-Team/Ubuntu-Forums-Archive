---
title: "network printer"
date: 2005-05-19
forum: Desktop Environments
---

### Post by Oblivious Hazard on 2005-05-19
Hello, I can see my Other computer Running windows XP I have the drive maped on here, I see all the files. But I'm having trouble setting up the printer. I tryd putting a test page, and it said to run a test. so I did and heres what i came up with...
> 
$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Global parameter wins support found in service section!
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
params.c:Section() - Empty section name in configuration file.
params.cm_process() - Failed. Error returned from params.carse().
Error loading services.



any suggestions?

---

### Post by shakin on 2005-05-19
I recommend you install kcontrol (will need kde libs) and use its printer configuration wizard. It's excellent.

---

### Post by Oblivious Hazard on 2005-05-19
kcontrol is installed how do i use it?

---

### Post by Oblivious Hazard on 2005-05-19
found out how to launch it... but theres no printer setup?

---

### Post by Oblivious Hazard on 2005-05-19
I found out what was wrong... I forgot I had setup this computer to be the server in that cfg. so i whent back and edtied it, and now it works fine...

---

