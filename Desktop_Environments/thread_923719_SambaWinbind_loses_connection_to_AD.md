---
title: "Samba/Winbind loses connection to AD"
date: 2008-09-18
forum: Desktop Environments
---

### Post by dgordons on 2008-09-18
Hi All,

Having a winbind issue when showing AD user/group information in Hardy with Samba 3.0.28a.  I can connect to the domain fine each time I login, but over the course of some time the connection between winbind and AD looks like it goes stale.

Initially everything works fine when looking up user uid/gid information when doing an ls -l on a network share.  After some time the uid/gid information only returns the uid/gid numeric information for the user and group.  It will no longer resolve the proper name of the user/group.  This mostly happens on the "Domain Users" group which resolves out at a numeric in the 10000's.  Normally a restart of the winbind service will fix the issue, but I'm not sure why this keeps happening.

My log.winbind file shows me that it looks like my winbind to domain connection goes away, but I'm not sure why.

[2008/09/10 16:38:00, 1] libads/ldap_utils.c:ads_do_search_retry_internal(87)
  ads_search_retry: failed to reconnect (Operations error)
[2008/09/10 16:38:00, 1] nsswitch/winbindd_ads.c:lookup_groupmem(907)
  ads: lookup_groupmem ads_search: Operations error
[2008/09/10 16:38:00, 1] nsswitch/winbindd_group.c:fill_grent_mem(365)
  could not lookup membership for group sid S-1-5-21-3075435673-67716032-3571901955-513 in domain X (error: Operations error)
[2008/09/11 07:35:07, 1] nsswitch/winbindd_ads.c:ads_cached_connection(128)
  ads_connect for domain X failed: Operations error
[2008/09/11 07:35:07, 1] nsswitch/winbindd_group.c:fill_grent_mem(365)
  could not lookup membership for group sid S-1-5-21-3075435673-67716032-3571901955-513 in domain X (error: NT_STATUS_UNSUCCESSFUL)
[2008/09/11 07:35:08, 1] nsswitch/winbindd_group.c:fill_grent_mem(365)
  could not lookup membership for group sid S-1-5-21-3075435673-67716032-3571901955-513 in domain X (error: NT_STATUS_UNSUCCESSFUL)
[2008/09/11 08:44:52, 1] nsswitch/winbindd_group.c:getgrgid_got_sid(606)
  could not lookup sid
[2008/09/11 08:58:48, 1] nsswitch/winbindd_group.c:winbindd_getgrnam(519)
  group domain users in domain X does not exist

Any help would be greatly appreciated.

Thanks
--Daryl

---

