---
title: "I've broken Evolution"
date: 2009-03-28
forum: General Help
---

### Post by momist on 2009-03-28
I was editing my email settings, as I've changed ISP.  I use POP3.  However, Evolution crashed during the process, and will not re-start even after a few re-boots.  I've now moved to using Thunderbird, but would like to recover my old mails and address books.
I first renamed home/ian/.evolution to .evolution_Old.
Evolution still will not start (it flashes up the splash screen and then closes instantly).
I then did sudo apt-get remove --purge evolution
followed by sudo apt-get install evolution
but I still get exactly the same response.

Does anyone have any other ideas?

Thanks,

Ian

PS Ubuntu 8.10 Intrepid - I can't tell which Evolution, but the latest from the repositories.

---

### Post by momist on 2009-03-28
I still can't get Evolution to run, but find if I launch it using the terminal, it returns this error:

(evolution:11706): camel-pop3-provider-WARNING **: Bad server response: 


(evolution:11706): camel-pop3-provider-WARNING **: Bad server response: .

Segmentation fault

Can anyone tell me how to launch Evolution without it trying to use the pop3 provider?

Thanks

---

### Post by oldos2er on 2009-03-28
"Can anyone tell me how to launch Evolution without it trying to use the pop3 provider?"

 Try "evolution --offline"

---

### Post by momist on 2009-03-28
> **oldos2er said:**
> "Can anyone tell me how to launch Evolution without it trying to use the pop3 provider?"

 Try "evolution --offline"

Thanks Ann!

That worked a treat.  Now to get to rescuing my address book!  :P

---

