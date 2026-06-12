---
title: "Evince problem again"
date: 2009-04-02
forum: General Help
---

### Post by Ian Sinclair on 2009-04-02
A week ago, I could use Evince to print a complete pdf document. After a recent CUPS update, I cannot print a PDF with Evince; get a message "Too many failed attempts". I can print with Gimp, with epdf (very badly - minus signs missing) and other types of documents. Adobe Reader will print, but insists on reducing the scale so that four pdf pages are fitted in one physical page.
Hints on modifying the printers.conf file require permissions and I don't know how to get around that (or if I should try). Is there any way I could get back to the CUPS version I was using before?
I tried uninstalling Evince and then rebooting and reinstalling, and it worked perfectly - for one document. After that it went back to the same error message.

---

### Post by taurus on 2009-04-02
If you need to modify printers.conf, run it with root privilege.

Applications -> Accessories -> Terminal
```
gksudo gedit /path_to/printers.conf
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Ian Sinclair on 2009-04-05
Thank you, but the printers.conf file does not contain the **AuthInfoRequired username,password** entry. It's still a mystery why Evince will not print a pdf document.

---

