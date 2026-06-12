---
title: "how to know if snap, appimage or deb package was installed"
date: 2018-10-12
forum: Desktop Environments
---

### Post by boskabouterj on 2018-10-12
Sooo

i just stumbled upon something rather stupid as in, it never happened to me before. In addition, searching for an answer is not returning the hoped answer so i'm posting it here.

I installed a program (Rambox). Now, after a while, there is an update but for the life of me, i can't remember if installed it as a snap, appimage or deb.

It's not in my snap list so i can exclude that. The deb is not doing anything either. So i ended up with the appimage and that was it.

Question: how do you know if you installed the snap, appimage or deb version of a program?

Software center is not showing the appimages so that's not it. I wouldn't know if there is a single command to tell me this.

Regards

---

### Post by ajgreeny on 2018-10-12
If installed as a snap package the command ```
snap list
``` will show it, so as you say, that was not how you installed it.
If you used a rambox.deb package file, installed using ```
sudo apt install
``` or one of the GUI programs it will show if you search using synaptic.
You can also use command ```
dpkg -l rambox
```, though using that on my 18.04 install seems to suggest it is not in the repos.

We may get some more clues from you running commands ```
sudo updatedb
locate -i rambox
```
Is there any possibility you installed it from source-code?

---

