---
title: "WiFi Problems in Ubuntu"
date: 2006-02-19
forum: Desktop Environments
---

### Post by krypto_wizard on 2006-02-19
At school, I have the wireles servie from University which is open based on MAC address filtering. At home I have my own wireless network and I use a WEP key for that. I want myself to be able to shift to the best network I am in.

For example, if I am at home I want my Ubuntu to directly logon to my wireless network (with WEP key already supplies) and if I am at school it automatically takes the University wireless network.

How can we do this thing in  Ubuntu.

Every help is appreciated.

Thanks

---

### Post by claes on 2006-02-19
You have to make your own script to handle that.
The profile handling in gnome network-settings are broken and can't handle it. 
In dapper there is a tool called network-manager that can handle this but in breezy you are on our own.

Claes

---

### Post by krypto_wizard on 2006-02-19
Has anybody written any such script.

I would assume that there are so many people who are good at scripting and they might have writen such script. This is very trivial problem and I thought it should automatically solve it. Can we install network-manager in breezy.

Any head start for writing such WiFi scripts.

thanks for al the input

[QUOTE=claes]You have to make your own script to handle that.
The profile handling in gnome network-settings are broken and can't handle it. 
In dapper there is a tool called network-manager that can handle this but in breezy you are on our own.

Claes[/QUOTE]

---

### Post by patrickfromspain on 2006-02-19
Try GTKwifi

---

