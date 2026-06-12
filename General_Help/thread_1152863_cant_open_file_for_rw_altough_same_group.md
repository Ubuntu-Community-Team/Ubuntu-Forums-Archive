---
title: "cant open file for r/w altough same group?"
date: 2009-05-08
forum: General Help
---

### Post by thinking on 2009-05-08
hi all

maybe i missunderstood the linux permission concept so heres what i do
using apache i create a file /tmp/wtf.log and set the permissions to 0660 (rw,rw,)
the user/group is www-data as expected

using usermod i added myself to the group www-data thus
none@DevelopA28:/etc$ groups none
none adm dialout cdrom www-data plugdev lpadmin admin sambashare
none@DevelopA28:/etc$ groups www-data
www-data none

both user none and www-data have membership to the opposite group

i would expect that i can open the /tmp/wtf.log read write as my user is within www-data group but i get permission denied using vi
this brings me to the point where i ask: how does the permission concept work cause it seems i missunderstood? OR why cant i read the file with my user 'none'?

edit: i also know that changing permissions to o+rw works

thx

---

### Post by thinking on 2009-05-10
bump

---

