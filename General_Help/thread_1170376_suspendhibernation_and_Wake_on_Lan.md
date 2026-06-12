---
title: "suspend/hibernation and Wake on Lan"
date: 2009-05-26
forum: General Help
---

### Post by chamrog on 2009-05-26
Greetings,
I have a servers that is currently running 24/7, this is not really nessasary, as most of the time its not needed, but i cannot tell the specific times its needed as that depends on clients connecting, so what i need is a way put the server into hibernation/suspend and then when the clients come online they wake the server.
My problem is that i have no idea how to initiate the hibernation/suspend from the command line. 

Can anyone point me in the right direction?

br
Lasse

---

### Post by kerry_s on 2009-05-26
wouldn't that make the connection take to long thus timing out who ever is trying to connect?

---

### Post by chamrog on 2009-05-26
I will have the clients have their boot process, wait until the server is up. 
Then why not just power the serverfully off? i want to keep the client waiting as low as possible. And i figure suspend/hibernate would fit well with those

-lasse

---

### Post by kerry_s on 2009-05-26
the command for suspend is " sudo pm-suspend "
the command for hibernate is " sudo pm-hibernate "
there is also a pm-powersave, never used it but might be something you should look into. make sure you set "wake on lan" or " pme(power management event) " in your bios power section.

[http://xlife.zuavra.net/index.php/60/](http://xlife.zuavra.net/index.php/60/)
or
just google "linux wake on lan how to"

---

### Post by chamrog on 2009-05-27
Thank you Kerry,

this looks just like what i need :)

-lasse

---

