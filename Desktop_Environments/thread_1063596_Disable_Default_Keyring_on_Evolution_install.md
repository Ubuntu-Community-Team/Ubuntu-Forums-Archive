---
title: "Disable Default Keyring on Evolution install"
date: 2009-02-08
forum: Desktop Environments
---

### Post by jono2009 on 2009-02-08
Wanting to disable "Default Keyring" on Evolution(Ubuntu 8.10)

When I first installed Ubuntu 8.10 on a friends PC, he had Wireless and  Default Keyring would have to be given it's password before using the Desktop. Later we changed to Ethernet connection and disabled Wireless. But during activating Evolution we get Default Keyring back again asking for it's password which is now rejected and thus the full activation cannot be completed.

I've removed all the information from the installation process to Evolution, removed Evolution by Synaptic Package Manager and then reinstalled it. Started the installation of Evolution again, but Default Keyring comes back!

Help me, please.:rolleyes:,

---

### Post by Pengwyn44 on 2009-05-11
The problem is common to all Evolution users because of an update. Go to System>Preferences>Encryption and Keyrings.
Select 'login automatically unlocked when user logs on'
Click OK, click on 'Change unlock Password'
Enter the old password (the one you use to login)- leave other fields blank, when prompted to Store Passwords Unencrypted? Click on Use Unsafe Storage.
I read this on this Forum and it worked for me on 8.04.

---

### Post by wygee on 2009-11-01
> **Pengwyn44 said:**
> The problem is common to all Evolution users because of an update. Go to System>Preferences>Encryption and Keyrings.
Select 'login automatically unlocked when user logs on'
Click OK, click on 'Change unlock Password' 



im using jaunty 9.04 and when i go to keyrings, i cant find the tab that you mention. any thoughts on this? thanks!

---

### Post by wygee on 2009-11-02
i was able to resolve my evo default keyring pop up issue. i found the answer to another thread, it was posted by yuki86. in 9.04 this worked for me:

1. application > Accessories > Passwords and Encryption Keys > Passwords, right click on login passwords and remove

2. start evolution, it asks for mail passwords just type, than it asks for keyring pass, just type nothing and click ok, it says to store passwords unsafely so click on it

now the default keyring pop up doesnt show. :)

---

### Post by msimon1960 on 2009-12-14
I had the same problem...I'm using V91.0 Koala.

Go to Applications->Accessories->Passwords & Encryption.
Right click on the 'default' item and select 'unlock'

That seemed to allow Evolution to get in without freaking about the default keyring.

I'm probably violating 58 security rules...but it works!

Matt.

---

