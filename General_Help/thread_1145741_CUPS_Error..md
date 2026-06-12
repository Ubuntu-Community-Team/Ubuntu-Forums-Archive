---
title: "CUPS Error."
date: 2009-05-01
forum: General Help
---

### Post by Roasted on 2009-05-01
I just tried to fire up this old Lexmark 2500 series printer I had sitting around with an Ubuntu 9.04 machine. I pulled the generic driver and all seemed well. Then I tried to test print.

CUPS Server Error
There was an error during the CUPS operation: 'client-error-document-format-not-supported.'

What can I do?

---

### Post by cmnorton on 2009-05-02
I have been able to our Lexmark using an app jet direct connection. If this printer is hooked up directly to your Ubuntu system, youd use localhost as the network address. 

I would also Google this error as well.

---

### Post by Roasted on 2009-05-02
Meaning... what? I simply went to printing and added the printer, it found it and attached a generic Lexmark driver to it. After that, it errored out. What localhost and all of that am I doing??

---

### Post by cmnorton on 2009-05-02
I am assuming you configured this as a local (direct) connect. I was suggesting a network connect (localhost). Now that you say a Lexmark driver, try a generic driver. Also, you might find a linux driver for it other than what is supplied through Ubuntu.

Lexmark printers are notoriously proprietary; that's why I suggest a generic driver or treating it like another printer. HP LaserJet IV printers are very prolific. You might try a printer that you think Lexmark might emulate. This is a stretch, but you might be able to get something to work.

---

### Post by Roasted on 2009-05-02
But it did pull a Generic Driver... I just assumed it was a Lexmark Generic Driver...

---

### Post by cmnorton on 2009-05-02
If Lexmark shows up in a list of drivers, pick the closest to your model, preferablyly a lower number

---

