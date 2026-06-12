---
title: "sssd/realmd login issue after hostname change"
date: 2015-10-15
forum: Desktop Environments
---

### Post by Shadow aok on 2015-10-15
Hello,

With an Ubuntu 14.04 x86 desktop computer, i'm using sssd/realmd to login using active directory (windows 2008 r2) accounts.
I followed this tutorial : [http://www.ubuntugeek.com/how-to-join-ubuntu-14-04-to-active-directory-using-realmd.html](http://www.ubuntugeek.com/how-to-join-ubuntu-14-04-to-active-directory-using-realmd.html)

Everything worked fine until I had to rename the computer.
Here's what I did :
[LIST]
[*]realm --verbose leave lan.domain.tld 
[*]deleted computer entry in AD 
[*]updated /etc/hostname file 
[*]updated /etc/hosts file
[*]reboot, checked new hostname is valid 
[*]realm &#8211;verbose join lan.domain.tld &#8211;user-principal=NEWHOSTNAME/administrator@LAN.DOMAIN.TLD &#8211;unattended 
[*]reboot 
[/LIST]

Everything seemed fine but I can't login with AD accounts anymore (new ones or old one which I already used on the computer).
Unity displays a wrong password error.
Local logins works fine.

AD accounts can login using ssh AND su.

Auth.log
```
Oct 15 16:06:16 NEWHOSTNAME lightdm: pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=ADACCOUNT
Oct 15 16:06:17 NEWHOSTNAME lightdm: pam_sss(lightdm:auth): authentication success; logname= uid=0 euid=0 tty=:0 ruser= rhost= user=ADACCOUNT
Oct 15 16:06:17 NEWHOSTNAME lightdm: pam_sss(lightdm:account): Access denied for user ADACCOUNT: 6 (Permission denied)
```

I got nothing relevant in sssd.log, even with debug set to 10.

sssd_lan.domain.tld.log is empty unless I start manually sssd with -d9 parameter
```

(Thu Oct 15 16:37:14 2015) [sssd[be[lan.domain.tld]]] [check_wait_queue] (0x1000): Wait queue for user [ADACCOUNT] is empty.
(Thu Oct 15 16:37:14 2015) [sssd[be[lan.domain.tld]]] [be_pam_handler_callback] (0x0100): Backend returned: (0, 0, <NULL>) [Success]
(Thu Oct 15 16:37:14 2015) [sssd[be[lan.domain.tld]]] [be_pam_handler_callback] (0x0100): Sending result [0][lan.domain.tld]
(Thu Oct 15 16:37:14 2015) [sssd[be[lan.domain.tld]]] [be_pam_handler_callback] (0x0100): Sent result [0][lan.domain.tld]
(Thu Oct 15 16:37:14 2015) [sssd[be[lan.domain.tld]]] [sbus_dispatch] (0x4000): dbus conn: 0x181cfc0
(Thu Oct 15 16:37:14 2015) [sssd[be[lan.domain.tld]]] [sbus_dispatch] (0x4000): Dispatching.
(Thu Oct 15 16:37:14 2015) [sssd[be[lan.domain.tld]]] [sbus_message_handler] (0x4000): Received SBUS method [pamHandler]
(Thu Oct 15 16:37:14 2015) [sssd[be[lan.domain.tld]]] [be_req_set_domain] (0x0400): Changing request domain from [lan.domain.tld] to [lan.domain.tld]
(Thu Oct 15 16:37:14 2015) [sssd[be[lan.domain.tld]]] [be_pam_handler] (0x0100): Got request with the following data
(Thu Oct 15 16:37:14 2015) [sssd[be[lan.domain.tld]]] [pam_print_data] (0x0100): command: PAM_ACCT_MGMT
(Thu Oct 15 16:37:14 2015) [sssd[be[lan.domain.tld]]] [pam_print_data] (0x0100): domain: lan.domain.tld
(Thu Oct 15 16:37:14 2015) [sssd[be[lan.domain.tld]]] [pam_print_data] (0x0100): user: ADACCOUNT
(Thu Oct 15 16:37:14 2015) [sssd[be[lan.domain.tld]]] [pam_print_data] (0x0100): service: lightdm
(Thu Oct 15 16:37:14 2015) [sssd[be[lan.domain.tld]]] [pam_print_data] (0x0100): tty: :0
(Thu Oct 15 16:37:14 2015) [sssd[be[lan.domain.tld]]] [pam_print_data] (0x0100): ruser:
(Thu Oct 15 16:37:14 2015) [sssd[be[lan.domain.tld]]] [pam_print_data] (0x0100): rhost:
(Thu Oct 15 16:37:14 2015) [sssd[be[lan.domain.tld]]] [pam_print_data] (0x0100): authtok type: 0
(Thu Oct 15 16:37:14 2015) [sssd[be[lan.domain.tld]]] [pam_print_data] (0x0100): newauthtok type: 0
(Thu Oct 15 16:37:14 2015) [sssd[be[lan.domain.tld]]] [pam_print_data] (0x0100): priv: 1
(Thu Oct 15 16:37:14 2015) [sssd[be[lan.domain.tld]]] [pam_print_data] (0x0100): cli_pid: 3815
(Thu Oct 15 16:37:14 2015) [sssd[be[lan.domain.tld]]] [simple_access_obtain_filter_lists] (0x0200): Deny users list is empty.
(Thu Oct 15 16:37:14 2015) [sssd[be[lan.domain.tld]]] [simple_access_obtain_filter_lists] (0x0200): Allow groups list is empty.
(Thu Oct 15 16:37:14 2015) [sssd[be[lan.domain.tld]]] [simple_access_obtain_filter_lists] (0x0200): Deny groups list is empty.
(Thu Oct 15 16:37:14 2015) [sssd[be[lan.domain.tld]]] [simple_access_check_send] (0x0200): Simple access check for ADACCOUNT
(Thu Oct 15 16:37:14 2015) [sssd[be[lan.domain.tld]]] [simple_access_check_send] (0x1000): No group restrictions, end request
(Thu Oct 15 16:37:14 2015) [sssd[be[lan.domain.tld]]] [simple_access_check_recv] (0x1000): Access not granted
```

upstart/sssd.log
```
(Thu Oct 15 16:36:03:125248 2015) [sssd[be[lan.domain.tld]]] [ldb] (0x0400): server_sort:Unable to register control with rootdse!
(Thu Oct 15 16:36:03:393953 2015) [sssd[nss]] [ldb] (0x0400): server_sort:Unable to register control with rootdse!
(Thu Oct 15 16:36:03:394558 2015) [sssd[pam]] [ldb] (0x0400): server_sort:Unable to register control with rootdse!
; TSIG error with server: tsig verify failure
update failed: REFUSED
```

Any idea ?

Thanks

---

### Post by Shadow aok on 2015-10-16
I reinstalled the system, set the wanted hostname, and integrated the computer in AD again.
Problem solved.

---

