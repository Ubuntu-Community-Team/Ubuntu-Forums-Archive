---
title: "login problems - large amount of users , cant select user"
date: 2014-03-11
forum: Desktop Environments
---

### Post by gigoudt on 2014-03-11
Hi everyone !!

Im using ubuntu thing 8.04 and this place was always a common reference when having problems or needing help. Really helpful !!!

Im facing a problem and looking around ionline and configuration cant find a way to solve it.

I have a server with a large amount of users. Its a nis/nfs server. I recently installed Xfce in it to use some funcionalities of desktop environment but when I try to acces cant scroll threw the desire user . Everything is stuck.  Mouse scroll not work either.

Someone has a clue. It could be great to change that no users to be shown and manually choose it.

here is an image :

[IMG]http://ubuntuforums.org/asset.php?fid=248815&uid=1454885&d=1394586518[/IMG]

Im using 12.04 and xfce

thanks for any advice

Andres

---

### Post by steeldriver on 2014-03-11
Hello and welcome (back?) to the forums

If you are using the standard 12.04 display manager (lightdm) then you should be able to configure that by adding

```

greeter-hide-users=true
greeter-show-manual-login=true

```

to the [SeatDefaults] section of the /etc/lightdm/lightdm.conf file

---

### Post by gigoudt on 2014-03-17
Steeldriver ! Thanks a lot for reply !

with your recomendations issue problem was solved.

now only fill in box to select the user I want !

thanks a lot ! kind regards!

Andres

---

