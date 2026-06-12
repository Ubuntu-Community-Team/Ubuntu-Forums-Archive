---
title: "PDF printing stopped working"
date: 2009-05-01
forum: General Help
---

### Post by sunbird on 2009-05-01
I installed cups-pdf and it was working fine. Then I installed an IPP printer from my server that worked fine under 8.04. Now that printer doesn't work and cups-pdf has disappeared from my available printers.

I've tried purging the install files and reinstalling. No dice.

I'm troubleshooting the IPP problem separately, but in the interim it would sure be great if someone could tell me how to get cups-pdf working again.

---

### Post by sunbird on 2009-05-02
*bump*

I really need pdf printing to work again. does anyone have any idea how to fix this?

---

### Post by unutbu on 2009-05-02
Do you have a ppd file in /etc/cups/ppd for the printer?
If so, perhaps open a terminal (Applications>Accessories>Terminal) and type:
```

gksu system-config-printer
```

Click New
LPD/LPR Host or Printer
Host: localhost (change as appropriate)
Click forward
Provide PPD: /etc/cups/ppd/PRINTER.ppd   (Change PRINTER, as needed)

---

### Post by sunbird on 2009-05-03
I removed everything using package manager and then reinstalled. I still don't know what the problem was, but everything is peachy now.

Thanks for the help!

---

