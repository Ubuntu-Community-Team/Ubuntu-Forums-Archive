---
title: "Joining Ubuntu Desktop to Ubuntu PDC"
date: 2010-11-01
forum: Desktop Environments
---

### Post by mfaiques on 2010-11-01
Hi, I have successfully deploy/confiugred the Ubuntu PDC and connected Windows XP too.. its all working fine.. but now I wana to connnect Ubuntu Desktop to same Ubuntu PDC.. 

I have changes in SAMBA, as per required for joining Domain.. and execute the <net join MyDomain -u root> to .. its all fine .. NO error.. BUT HOW TO LOGIN..? on startup there is nothing like option for selecting Domain or Workgroup..

Please guide..

---

### Post by gordintoronto on 2010-11-01
The workgroup name is specified in /etc/samba/smb.conf
From command line:
gksudo gedit /etc/samba/smb.conf

It's near the bottom of the first page.

---

### Post by Boondoklife on 2010-11-01
Check this out: [http://ubuntuforums.org/showthread.php?t=5409](http://ubuntuforums.org/showthread.php?t=5409)

---

### Post by mfaiques on 2010-11-05
> **Boondoklife said:**
> Check this out: [http://ubuntuforums.org/showthread.php?t=5409](http://ubuntuforums.org/showthread.php?t=5409)

Dear friend, I am unable to found the reason why ubuntu desktop edittion is unable to show/login via configured Domain.. while the Windows Xp is able to login successfully with the same Ubuntu domain..

in ubuntu desktop.. I have changed in Samba <Workgroup to myDomain>, in command line <net join myDomain> its all success .. NO error.. but still unable to login via domain  user..

---

### Post by mfaiques on 2010-11-11
still I did not found any related information... I think LinuxUbuntu PDC only support Windows Desktop for Domain Logging:confused:

---

### Post by Boondoklife on 2010-11-11
The link I gave you is specifically for using ubuntu to authenticate against a PDC. Ubuntu is not windows and you are not going to get the same prompts!

---

### Post by mfaiques on 2010-11-23
I have configured the following at Ubuntu Client/Samba

WORKGROUP = MYDOMAIN
Security = DOMAIN
Domain Logons = YES
Realm = MYDOMAIN

then execute the following command at terminal

#net join MYDOMAIN

Unable to find a suitable server for domain MYDOMAIN

---

### Post by fdelval on 2011-03-02
Im in the same situation!

I joined the domain with no errors, now, i get my ubuntu desktop client, and in the login screen, where i write down my user / pass, there is no way i can login with a MYDOMAIN\user....

---

### Post by fdelval on 2011-03-03
bump

---

### Post by fdelval on 2011-03-04
last

---

