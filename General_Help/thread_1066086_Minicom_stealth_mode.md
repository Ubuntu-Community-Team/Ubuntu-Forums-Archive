---
title: "Minicom stealth mode?"
date: 2009-02-10
forum: General Help
---

### Post by Nachtkriecher on 2009-02-10
so is there any way i can run minicom in a sort of stealth mode so that it doesn't interfere with another program that is also attempting to use the serial port?

my goal is to use it as a packet sniffer.



also, on an unrelated note, pidgin keeps closing on me as soon as I load it! anyone else encounter this?

---

### Post by HermanAB on 2009-02-10
Hmm, look into things like 'serproxy' and 'tee'.

Otherwise, use another PC and wire up only the Rx wire and Ground, to the serial comms link.  Also, you may want to try 'cutecom', since it is a lot better than 'minicom'.

Hope that helps!

Herman

---

### Post by Nachtkriecher on 2009-02-10
thanks! that might be what im looking for... i suppose i could also hook up another computer, but i really dont want to have to do that.

thanks again

---

### Post by chronos00 on 2011-05-04
Have any of you managed to successfully sniff a serial communication?

I need to log (dump, sniff, or whatever you like to call it) the communication between a serial device and a certain program running on the computer. How can this be done?

---

