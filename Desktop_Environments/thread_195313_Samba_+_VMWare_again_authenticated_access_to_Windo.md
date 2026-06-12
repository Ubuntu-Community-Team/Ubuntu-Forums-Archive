---
title: "Samba + VMWare again: authenticated access to Windows share?"
date: 2006-06-12
forum: Desktop Environments
---

### Post by temcat on 2006-06-12
Shortly after I successfuly solved the problem described in [http://ubuntuforums.org/showthread.php?t=193726](http://ubuntuforums.org/showthread.php?t=193726), I had to recreate Windows XP VM and set up Samba again. Now access from XP to Linux is OK, but I can't set up authenticated access to the share that resides on XP. 

Here's what I did:

1) I turned off Simple File Sharing on XP.
2) I set the folder Artem on XP to be shared. In Permissions for this folder, I removed the group "Everyone" and added the user "Artem" which is a password protected local user with admin rights. The name of XP machine is "hell", so actually in Permissions window it looked like Artem (HELL\Artem). So presumably it should allow access only for user Artem or HELL\Artem.

Here's what I got instead.

a) If net access for guest account is enabled (by issuing "net user guest /active:yes" at command prompt):

Username "Artem" with valid password:
============================
temcat@eden:~$ smbclient -U Artem //hell/Artem
Password: <valid password>
session setup failed: NT_STATUS_LOGON_FAILURE

Username "Artem" with no password (just pressing Enter)
=========================================
temcat@eden:~$ smbclient -U Artem //hell/Artem
Password: <press Enter>
Anonymous login successful
Domain=[WORKGROUP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
tree connect failed: NT_STATUS_ACCESS_DENIED

Username "HELL\Artem" with valid password:
================================
temcat@eden:~$ smbclient -U HELL\Artem //hell/Artem
Password: <valid password>
Domain=[HELL] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
smb: \>

Success, I got connected! BUT:

Username "HELL\Artem" with no password (just pressing Enter)
=============================================
temcat@eden:~$ smbclient -U HELL\Artem //hell/Artem
Password: <here I don't enter any password, just press Enter key>
Domain=[HELL] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
smb: \>

I got connected without any password... And most importantly:

Any username with no password
========================
temcat@eden:~$ smbclient -U anyname //hell/Artem
Password: <press Enter>
Domain=[HELL] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
smb: \>

User "anyname" does not exist on XP machine, but still got connected!!!

b) If net access for guest account is disabled (by issuing "net user guest /active:no" at command prompt):

Username "Artem" with valid password:
============================
temcat@eden:~$ smbclient -U Artem //hell/Artem
Password: <valid password>
session setup failed: NT_STATUS_LOGON_FAILURE

Username "Artem" with no password (just pressing Enter)
=========================================
temcat@eden:~$ smbclient -U Artem //hell/Artem
Password: <press Enter>
Anonymous login successful
Domain=[WORKGROUP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
tree connect failed: NT_STATUS_ACCESS_DENIED

Username "HELL\Artem" with valid password:
================================
temcat@eden:~$ smbclient -U HELL\Artem //hell/Artem
Password: <valid password>
session setup failed: NT_STATUS_LOGON_FAILURE

Username "HELL\Artem" with no password (just pressing Enter)
=============================================
temcat@eden:~$ smbclient -U HELL\Artem //hell/Artem
Password: <here I don't enter any password, just press Enter key>
Anonymous login successful
Domain=[WORKGROUP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
tree connect failed: NT_STATUS_ACCESS_DENIED

Any username with no password
========================
temcat@eden:~$ smbclient -U anyname //hell/Artem
Password: <press Enter>
Anonymous login successful
Domain=[WORKGROUP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
tree connect failed: NT_STATUS_ACCESS_DENIED

Any username with any password
========================
temcat@eden:~$ smbclient -U anyname //hell/Artem
Password: <any password>
session setup failed: NT_STATUS_LOGON_FAILURE

I honestly don't know how to interpret this.... Help?

---

### Post by temcat on 2006-06-13
Bump :-(

Can anybody help?

---

### Post by fede on 2006-06-13
Hello temcat. 

I suppose you've checked your windows firewall settings, have you? 
I am using two virtual networks in my vmware server, one uses NAT and the other one host only networking. I disable the windows firewall on the host only virtual adapter ( vmnet1), and I use that to connect from XP to samba. I __think__ that the windows firewall was stopping me from connecting from linux to XP before that. 

Thanks for your post on samba config somewhere else, it really helped me get going. Regards,

Fede.

---

