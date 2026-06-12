---
title: "Synaptic problem"
date: 2006-08-23
forum: Desktop Environments
---

### Post by hraposo on 2006-08-23
I tried install mldonkey-serve by synaptic. But the installation did't finish because an script that not end. Now everytime I install a package in synaptic, in the end, appears the message that mldonkey-serve no finish the installation. The synaptic message is ```
Error: The fallow problems was found in your system: E: mldonkey-server:subprocess post-installation script give an error of the end status of output 1
```How can I remove this message of synaptic?

---

### Post by fakie_flip on 2006-08-23
Try reinstalling that package that did not get installed correctly.

---

### Post by hraposo on 2006-08-23
I tried but I can not remove or reinstall this pakage. Appears always the same error. (problem with a scritp).

---

### Post by hraposo on 2006-08-23
I solved the problem. I did #nautilus and go to /var/log/dpkg/info/, then a delete all the files with the name "mldonkey-server". Now the error mensage don't appears any more.

---

