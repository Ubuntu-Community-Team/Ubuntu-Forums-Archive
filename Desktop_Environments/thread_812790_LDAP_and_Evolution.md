---
title: "LDAP and Evolution"
date: 2008-05-30
forum: Desktop Environments
---

### Post by nlavon on 2008-05-30
I have been trying to get an LDAP directory to show up in Evolution 2.12.

I finally connected to my office VPN through vpnc. I have entered the settings for the LDAP server in the Contacts box but I cannot get into the directory (it's for e-mail addresses). Nothing happens when I perform a search.

I double checked the setup on my Windows machine and using Thunderbird, I can get the e-mail addresses through the VPN connection and LDAP server parameters successfuly.

I spent a couple of days configuring the vpnc connection with changed Firestarter settings, etc., so I don't think that is the issue. There is some setting or tweak I have not made somewhere that should enable me to see these addresses.

I haven't tried using Thunderbird yet to see if I can get to the LDAP server using my VPN connection but I would like to keep things in Evolution.

Any suggestions gratefully appreciated or direction to go. Thank you.

Neal Lavon
Takoma Park, MD
USA

---

### Post by borobudur on 2008-06-11
There is a couple of things you should try:
- I'm not sure with VPN but are your ports open  389 or 636 in firestarter. Try scanning localhost over the network tools.
- Can you reach the LDAP service with an other tool from your Linux box? Example with LAT
- In evolution settings I had to set the search scope to SUB
- In evolution you will only see entries if you write something to the search, you won't see all your entries if search is empty
- have you tried with the terminal commands:```
ldapsearch -LLL -x -b 'ou=addressbook,dc=subdomain,dc=dyndns,dc=org' -H ldap://subdomain.dyndns.org -D 'uid=you,ou=users,dc=subdomain,dc=dyndns,dc=org' -W
```

Cheers
borobudur

---

