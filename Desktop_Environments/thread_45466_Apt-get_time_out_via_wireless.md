---
title: "Apt-get time out via wireless"
date: 2005-06-30
forum: Desktop Environments
---

### Post by IchBin on 2005-06-30
Does anyone have a problem with apt-get using this wireless? I cannot use apt-get with my wireless card. I get timed out when I'm on my wireless. As soon as I plug in my wired eth0 I can apt-get just fine. Anyone have any ideas?

---

### Post by Lunde on 2005-06-30
[QUOTE=IchBin]Does anyone have a problem with apt-get using this wireless? I cannot use apt-get with my wireless card. I get timed out when I'm on my wireless. As soon as I plug in my wired eth0 I can apt-get just fine. Anyone have any ideas?[/QUOTE]
 Works fine for me. 

We need some more information like speed of your network, model of your wireless card, how you instaled it the first time. 
Also check your syslog for any messages related to wour network / wireless adapter

---

### Post by IchBin on 2005-06-30
[QUOTE=Lunde]Works fine for me. 

We need some more information like speed of your network, model of your wireless card, how you instaled it the first time. 
Also check your syslog for any messages related to wour network / wireless adapter[/QUOTE]
 hhmmm.... it seems to be something to do with ipv6. I'm not sure what doesn't like it on my network but once I disabled it everything seemed to work fine. I'm running a ipw2200 Intel centrino wireless on a Actiontec wireless DSL router. Not sure even where to look, But I'm ok with ipv6 being disabled as long as it doesn't affect me in some other way.

---

### Post by holr on 2005-06-30
hmm, i dont get any problems with mine timing whilst its downloading something through apt-get, U do get an issue when the connection is dropped when nothing is coming or going. I leave a ping command run indeffinately to keep the connection alive. Maybe something like this would help???  :)

---

### Post by Lunde on 2005-06-30
Not missing out much by disableing the IPV6, I disable it in firefox to gain some extra speed

---

