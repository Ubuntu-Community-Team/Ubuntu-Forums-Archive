---
title: "User ACLs for Squid"
date: 2009-03-03
forum: General Help
---

### Post by YaAqoB on 2009-03-03
Hello all.
Quick question.... I have setup Squid in a school environment using basic authentication so we can log students browsing. It's all working very well with great reporting etc.
Is it possible with out creating multiple SRC acls and setting static ips every where to tell Squid that User A & B are in an ACL called staff and users C & D are om an ACL called students.
I would then like to tell Squid that Staff can have full access and Students have access except the sites in my banned-sites list.
I currently have a banned sites file working fine but it obviously applies to all proxy users.
It sounds doable to me but I just cant figure out how to get the usernames into an ACL.
So basically to wrap it up I want to be able to separate out my users so I can apply the banned-sites.squid to half and then allow "some" of those via the allowed-sites.squid to the rest without having to have the staff for example on 192.168.1.10-50 and then the students on .1.60-100
The IP solution wouldn't work as staff and students share PC's.

Thanks in advance.


James

---

