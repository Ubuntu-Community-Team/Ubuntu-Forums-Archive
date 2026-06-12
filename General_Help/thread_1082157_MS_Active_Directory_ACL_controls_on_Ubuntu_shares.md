---
title: "MS Active Directory ACL controls on Ubuntu shares"
date: 2009-02-27
forum: General Help
---

### Post by SurfinTurf on 2009-02-27
I am a Windows LAN Administrator, 10 years running.  However, in my latest need for a central file server for the LAN, I've decided to give Ubuntu Linux 8.04 a go because of its low overhead and IP bonding ability (awesome cool, ip bonding!).  Well I have read 2 books and been all over Ubuntu documentation and articles all over the web and feel pretty comfortable moving around and configuring on Ubuntu.  Except I cannot easily manipulate ACL's on network shares that are stored on the Ubuntu box using Active Directory users and groups.

I have installed and configured samba, kerberos, nfs and winbind.  Plenty of documentation on that.  I tie in and authenticate with AD.  I can read my AD users and groups using 
wbinfo -u
wbinfo -g

I have also played around with setfacl, chmod, chown.

Can anyone point me to documentation, book, web page, 2-paragraph-blog, anything on how to 'manipulate Microsoft Active Directory users and groups in ACL's for Ubuntu shares' please?  For instance, one of my shares will be  a 'Common' share. Then I'll have folder's in there that various groups and users can access (i.e. HR folder for HR group to write, but everyone else read, etc....)  These are things I'm very comfortable manipulating on Windows file sharing.  It does not however seem as straightforward in Linux.

---

### Post by ronal on 2009-06-18
> **SurfinTurf said:**
> I am a Windows LAN Administrator, 10 years running.  However, in my latest need for a central file server for the LAN, I've decided to give Ubuntu Linux 8.04 a go because of its low overhead and IP bonding ability (awesome cool, ip bonding!).  Well I have read 2 books and been all over Ubuntu documentation and articles all over the web and feel pretty comfortable moving around and configuring on Ubuntu.  Except I cannot easily manipulate ACL's on network shares that are stored on the Ubuntu box using Active Directory users and groups.

I have installed and configured samba, kerberos, nfs and winbind.  Plenty of documentation on that.  I tie in and authenticate with AD.  I can read my AD users and groups using 
wbinfo -u
wbinfo -g

I have also played around with setfacl, chmod, chown.

Can anyone point me to documentation, book, web page, 2-paragraph-blog, anything on how to 'manipulate Microsoft Active Directory users and groups in ACL's for Ubuntu shares' please?  For instance, one of my shares will be  a 'Common' share. Then I'll have folder's in there that various groups and users can access (i.e. HR folder for HR group to write, but everyone else read, etc....)  These are things I'm very comfortable manipulating on Windows file sharing.  It does not however seem as straightforward in Linux.
I also am facing the similar situation...

Can try sadms.

I am using Doc's @ [https://help.ubuntu.com/8.10/serverguide/C/samba-ad-integration.html](https://help.ubuntu.com/8.10/serverguide/C/samba-ad-integration.html)

Machine is joined to domain but giving specific domain users permissions pending.

---

