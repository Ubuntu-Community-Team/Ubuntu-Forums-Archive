---
title: "Have Problems getting on windows network"
date: 2006-07-25
forum: Desktop Environments
---

### Post by Magiczero on 2006-07-25
Today I was trying to get on my windows and it wouldn't let me so I unmounted it and tried to remount it this is what i get
Autheration Reqired
Please login to access the network
I dont even have a password set for my network!!
My workgroup name is HOME

What do I do?  By the way it wasnt doing this yesterday!!
Help Please
Thanks

---

### Post by Thund3rstruck on 2006-07-27
You always have a password for a windows network whether you know it or not. You used to be able to leave your accounts in windows unpassworded and just create a linux username which was identical to the windows one to connect but that was back in Win98 (before kerboros). 

In order to connect out to your windows network you'll need to create an account and set a password for it. That's the account you'll use for crudentials when prompted by "mount -t smbfs", smbmount, and smbclient

---

