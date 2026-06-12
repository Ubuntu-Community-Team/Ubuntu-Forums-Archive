---
title: "Beryl Manager"
date: 2007-04-26
forum: Desktop Effects &amp; Customization
---

### Post by UbieNoobie on 2007-04-26
I have everything working fine but am getting annoyed that everytime I restart the machine I have to startup the Beryl manager (and therefore my emerald themes). Beryl itself is starting up fine every restart, but I have to start the little red diamond up to be able to run emerald. Is there a way to get this started automatically at startup?

---

### Post by orange2k on 2007-04-26
Goto System->Preferences->Sessions. In startup programs add beryl-manager, beryl and emerald.

---

### Post by UbieNoobie on 2007-04-26
I can see what you mean, but it requires a "command" .... does that mean I have to try and work out what starts the programs and where they are and enter the address in that?

---

### Post by visible on 2007-04-26
the command for beryl is beryl-manager.  That is all that I have listed.

---

### Post by Rinzwind on 2007-04-26
> **UbieNoobie said:**
> I can see what you mean, but it requires a "command" .... does that mean I have to try and work out what starts the programs and where they are and enter the address in that?

name beryl
command beryl-manager

name emerald
command emerald --replace
But it seems you allready have those set. I think Beryl doesn't show the icon if you do not. 


Important:  You need to choose, when you login (before you confirm username and pwd), "sessions" "GNOME with XGL" to have Beryl starting from start-up. There you can also make it the default choice.

---

### Post by UbieNoobie on 2007-04-26
> **visible said:**
> the command for beryl is beryl-manager.  That is all that I have listed.

Thankyou - that did the trick.

---

