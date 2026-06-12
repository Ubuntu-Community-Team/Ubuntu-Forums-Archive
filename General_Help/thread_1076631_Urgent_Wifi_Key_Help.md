---
title: "Urgent Wifi Key Help"
date: 2009-02-21
forum: General Help
---

### Post by dazzler on 2009-02-21
Hi all, wondered if someone could help, I've got a laptop which is a friends sons (XP), i got sick of removing malware etc so thought i'd treat him to an Ubuntu install.

Alls well except for the life of me i cant get it to stick with the correct wep key, in fact it has never connected to my router yet.

It comes up with the type in wep key box, i type it in correctly, checked with show key tickbox, however it doesnt connect then why i press show key again there is a long list of random characters it does this everytime.

Is this a problem with the keyring somehow.

I would really like to give him it back working but ive had it for days now.

:(

---

### Post by RedSingularity on 2009-02-21
What type of WEP encryption is it?

---

### Post by dazzler on 2009-02-21
WPA-PSK my laptop running Ubuntu 8.10 connects fine aswell as a little eeepc

---

### Post by RedSingularity on 2009-02-21
Ok so you have one connected to the router already.  Obviously it is nothing wrong with the router.  Does ubuntu recognize the wireless device installed in that computer?

---

### Post by dazzler on 2009-02-21
Yes it does, it picks up all the different signals around including neighbours.

---

### Post by dazzler on 2009-02-21
No tips, i really dont wanna put xp back on

---

### Post by RedSingularity on 2009-02-21
Did you try editing the settings in System>Preferences>Network Configuration?

---

### Post by dazzler on 2009-02-21
Yep im sure it has something to do with the keyring as it asks for the keyring password when it first tries to connect

---

### Post by Miaxi on 2009-02-21
I had that problem. It was a driver problem, the driver kinda worked but not really. Check if network-manager is reporting the correct channels and encryption types for detected networks. If it is showing WEP and channel 6 (or something) for every SSID, it's a clue that you need a different driver.

---

### Post by RD1 on 2009-02-21
I think your problem may be right in your posting. You speak of entering a WEP key but the you say your security is WPA. Try using the dropdown box, in the wireless security settings, and change to WPA - WPA PERSONAL. Then enter your encryption key.

---

### Post by Agent ME on 2009-02-21
> **dazzler said:**
> Yep im sure it has something to do with the keyring as it asks for the keyring password when it first tries to connect
It sounds like the keyring has a different password than the user account itself.
Go to Applications -> Accessories -> Passwords and Encryption. Edit -> Preferences. Click the "login" keyring, and then the "Change Unlock Password" button. Set it to have the same password as the user account and it will stop prompting you for the keyring's password.

However I don't think this will solve the actual wireless connection problem. Are you making sure to select the right type of wireless encryption from the drop-down box?

---

### Post by dazzler on 2009-02-22
Sorry guys im a right dick at times, dug a bit deeper into my router settings and realised i had set up an authorised access list awhile back.

Once i allowed this laptops mac address on all was hunky dory.

Sorry for the waste of time, hopefully someone might also check this in future and save them a bit of embarrassment.

:-\"

---

