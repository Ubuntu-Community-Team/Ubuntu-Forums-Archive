---
title: "Black screen at startup after upgrading to 18.10"
date: 2018-11-20
forum: Desktop Environments
---

### Post by madtyn2 on 2018-11-20
Hello, I have just upgraded Kubuntu from 18.04.1 to 18.10 and when restarting it, my Mountain laptop showed the Kubuntu logo and after that it freezes.

I can access the terminal with Ctrl+Alt+F2, and I did a couple of screenshots of useful info from command outputs (dmesg, dkms...):

[https://imagebin.ca/v/4NFhzuOFNPsE](https://imagebin.ca/v/4NFhzuOFNPsE)
[https://imagebin.ca/v/4NFimIo0E41W](https://imagebin.ca/v/4NFimIo0E41W)
[https://imagebin.ca/v/4NG5yNXMLb5j](https://imagebin.ca/v/4NG5yNXMLb5j)

I'm thinking some nVidia problems. Please, help. I don't know where to start diagnosing the problem and don't know even what to Google for.

---

### Post by Autodave on 2018-11-20
Upgrading rarely works well (at least for me) and I learned a long time ago to only do clean installs. Also, I only use the LTS releases.  Unless there is something that you just have to have in 18.10, I would suggest a reinstall of 18.04 and be happy with that until 20.04 comes out.  You can use the installer to access your files and copy everything you need to an external source before doing the reinstall.

---

### Post by madtyn2 on 2018-11-21
I fixed it.

There was a commented line (the "Driver" line) at /etc/X11/xorg.conf at Section "Device".

Just uncommenting (remember using sudo) and installing nvidia-415 did the work.

---

