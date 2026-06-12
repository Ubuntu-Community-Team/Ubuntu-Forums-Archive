---
title: "printer drivers for USB printer needed"
date: 2010-12-01
forum: Desktop Environments
---

### Post by tapas_mishra on 2010-12-01
Hi,
I am having a printer to which I have a USB connection.I want to know which drivers should I install for it.
The model is LBP 3000.
The reason I have to do this manually is I do not have internet connection when I am connected with printer.

---

### Post by nrabett on 2010-12-01
[http://radu.cotescu.com/how-to-install-canon-lbp-printers-in-ubuntu/](http://radu.cotescu.com/how-to-install-canon-lbp-printers-in-ubuntu/)

... probably the easiest way. Worked for me after some trial and error. The drivers seem to be very sensitive concerning the paper formats which are used. They must identical in the printer and the document you want to print - otherwise, you are likely to experience problems.

When the driver is installed, you can access your printing system by writing localhost:631 in the address bar of a web browser.

Be sure that you have full root access before installing the drivers. Set a root password with sudo passwd.

---

