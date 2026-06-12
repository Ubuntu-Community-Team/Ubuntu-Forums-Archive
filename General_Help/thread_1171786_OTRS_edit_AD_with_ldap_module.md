---
title: "OTRS: edit AD with ldap module?"
date: 2009-05-27
forum: General Help
---

### Post by bcdudley on 2009-05-27
I am playing around with OTRS and trying to move our company in that direction. I know it has been said that the OTRS user management interface can not update Active Directory (or any LDAP database) and it is read only.

My problem is, our users hop from location to location on a weekly basis(sometimes daily). I need to be able to update locations, address's and phone numbers quickly. Having the help desk personal go into AD and change this info really is not an option and will kill the entire OTRS project. 

My backup plan is to use dual backend sources. I will use AD for names and email, while I use MySql (or possibly our M$ SQL Server) for phone numbers, location and address's.

I would very much prefer to use our AD LDAP connection if possible. Has anyone found a way to do this.

Thank you,

---

