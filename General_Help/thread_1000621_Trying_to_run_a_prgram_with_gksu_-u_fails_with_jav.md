---
title: "Trying to run a prgram with gksu -u fails with java not found"
date: 2008-12-03
forum: General Help
---

### Post by VuzeLover on 2008-12-03
Hi.

I'm trying to run a program as the user vuze.  I created the user vuze with "sudo adduser --home /opt/vuze --shell /bin/false --no-create-home --disabled-login vuze"
I changed the permissions to the new user.  But when I try to run vuze I get java not found.  I'm using "gksu -u vuze vuze and I also tried using the -k option, no go.  Seems the user vuze can not pick up the java location.  Running vuze as me works just fine and it picks the java location right up from profile.

I'm trying to run vuze in it's own account because I am using the built in web site server.  I would appreciate any help.

---

