---
title: "smldap LDAP error help please."
date: 2005-10-31
forum: Desktop Environments
---

### Post by joscar on 2005-10-31
Hello all. I am attempting to ditch win 2k3 server and run breezy as my PDC. I am using instructions from [here]("http://usefulinc.com/edd/blog/contents/2005/09/25-ldap/read") . When I do :

root@LinServ:~# ldapsearch -x uid=Administrator
# extended LDIF
#
# LDAPv3
# base <> with scope sub
# filter: uid=Administrator
# requesting: ALL
#

# search result
search: 2
result: 0 Success

# numResponses: 1


and when I do : 
root@LinServ:~# sudo smbldap-passwd Administrator
Can't contact LDAP server at /usr/share/perl5/smbldap_tools.pm line 341, <DATA> line 283.


This is the area containing line 341. I am indicating which one line 341 is, that text is not in my smbldap_tools.pm 

here is my my smbldap_tools.pm lines 341 to 343

    $mesg->code && die $mesg->error;                     < line 341
    foreach my $entry ($mesg->all_entries) {
      $dn= $entry->dn;

can someone please try to point me in the correct direction. Or if there is a better way to accomplish this that I am not aware of, can someone point it out to me. I appreciate any attention given to this issue.

---

### Post by joscar on 2005-10-31
bump. please. I really need some one to assist me.

---

