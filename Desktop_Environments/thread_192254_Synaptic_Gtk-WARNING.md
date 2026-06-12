---
title: "Synaptic Gtk-WARNING"
date: 2006-06-08
forum: Desktop Environments
---

### Post by drews_blunted on 2006-06-08
Something or another has broken my synaptic it no longer will open, ive tryed restarting my computer, still no sucess. Does anyone know why synaptic would do this and or how this can be fixed. Also the Add/Remove programs application will not work anymore either, all my gui apt programs seem to depend on synaptic.

(synaptic:26121): Gtk-WARNING **: cannot open display:

Any help would be greatful!:D

---

### Post by RavenOfOdin on 2006-06-08
Have you tried reinstalling Synaptic through the command line via:

```

sudo apt-get remove synaptic
sudo apt-get install synaptic

```

?

---

### Post by drews_blunted on 2006-06-10
ive tryed it doesnt work.

---

### Post by drews_blunted on 2006-06-12
Ok so i have determined that synaptic itself is fine. I can start the program as my normal user but not as root, when i try to start it as root it gives me the gtk error. Does anyone know what might be wrong.

Most of my other adminastration tools do not work for me either such as GDMSetup and etc. Is there some package i shoudl isntall to compleat my ubuntu desktop

---

