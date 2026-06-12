---
title: "Turning off the X server"
date: 2009-06-12
forum: General Help
---

### Post by k_squired on 2009-06-12
Uh, how?
Thanks.

---

### Post by Magnificence on 2009-06-12
ctrl+alt+F1, to go to a command line without DE.
Login.
Type "sudo /etc/init.d/gdm stop" to close your X server, but you'll need another command if you're not running GNOME.
Then do wathever you need to do with the X server off.

---

### Post by cariboo on 2009-06-12
If you want to start X manually, you can stop gdm from starting at boot by running the following command:

```
sudo update-rc.d -f gdm remove
```

The above command must be run in a terminal. To start X, type at the prompt:

```
startx
```

---

### Post by k_squired on 2009-06-12
Thanks, but I whenever I say suod /ect/... it says command not found and then prints the path.  Whenever I do stop /ect/ it says unknown job.  How can I find out what command I'm supposed to be using?

---

### Post by cariboo on 2009-06-12
I hope that is a typo and not how you type **sudo**. :) or **etc**

---

### Post by k_squired on 2009-06-12
Uh... I was qouting that preatty literally.
"sudo /etc/init.d/gdm stop"

WAIT!  Did'nt even see that.  Ah, but no, thanks.

---

