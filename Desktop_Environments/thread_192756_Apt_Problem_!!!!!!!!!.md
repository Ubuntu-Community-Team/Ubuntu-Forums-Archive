---
title: "Apt Problem !!!!!!!!!"
date: 2006-06-09
forum: Desktop Environments
---

### Post by d4vid3 on 2006-06-09
Hi,
recently i've upgraded breezy to dapper drake, and now i can't upgrade/install any package from synaptic and i can't run apt-get update. This is the output of apt-get update:

root@benny:/home/davide# apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Impossible to connect to 192.168.1.13:8080 (192.168.1.13). - connect (113 No route towards the host)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Impossible to connect to a 192.168.1.13:8080 (192.168.1.13). - connect (113 No route towards the host)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Impossible to connect to 192.168.1.13:8080 (192.168.1.13). - connect (113 No route towards the host)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release


(I've traslated the output to english.....)
what i can do? Pls help me](*,) ](*,) ](*,) ](*,)

---

### Post by WakkiTabakki on 2006-06-09
Sounds like you don't have a working internet connection...

And, 192.168.1.13, is that the address to your gateway?

/N

---

### Post by d4vid3 on 2006-06-09
no....the router ip is 192.168.1.1,and my connection under linux work. Apt don't want to run correctly...

---

### Post by scxtt on 2006-06-09
port 8080 is the "Remote Management" port on my router (a linksys), which i think is pretty standard - seems strange that there's a reference to that port in the output you provided ...

do you know anything about the 192.168.1.13 box it's referring to?

---

### Post by d4vid3 on 2006-06-09
i dunno.....no pc have this ip :roll: :roll: :roll: :roll: :roll: :roll: :roll:

---

### Post by scxtt on 2006-06-09
are you opposed to using synaptic? -- there's a nice preferences gui that might shed some light on the setting apt is using ... Settings --> Preferences --> Network (tab) ...

---

### Post by d4vid3 on 2006-06-09
yes i know...but there aren't any proxy configured. Is configured to "Direct internet connection"

---

### Post by d4vid3 on 2006-06-09
?

---

### Post by drtvasudevan on 2006-06-09
i too have this apt problems.
in zenwalk, ubuntu kubuntu .....
seemed a common problem for such flavours.
but with vector linux vlapt worked.
can i try it here somehow.
i know it is configured fro vector linux servers.
still......?

tv

tv

---

### Post by Darthuan on 2006-06-09
Just disable proxy in system-preferences-network proxy, and reboot the computer (re-activating the network connection wont help, tried it, tried everything, only reboot helped me), and everything will work ok.

---

### Post by drtvasudevan on 2006-06-09
it is already like that -no proxy.
the usual error message is "connection timed out."

tv

[QUOTE=Darthuan]Just disable proxy in system-preferences-network proxy, and reboot the computer (re-activating the network connection wont help, tried it, tried everything, only reboot helped me), and everything will work ok.[/QUOTE]

---

