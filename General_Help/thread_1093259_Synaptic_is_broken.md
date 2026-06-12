---
title: "Synaptic is broken"
date: 2009-03-11
forum: General Help
---

### Post by pjalegria on 2009-03-11
Hi 

I need help, trying to install songbird 1.1 and during installation my laptop freeze,i have to reboot now I have an error in synaptic ...

"E:The package songbird needs to be reinstalled, but i cant find an archive for it"

i try to reinstall the deb package but i get a error thats says 	
"package corrupt"

How can i fix that, please

Thanks

---

### Post by konqueror7 on 2009-03-11
try doing in the terminal,
```
sudo apt-get -f install
```

---

### Post by pjalegria on 2009-03-11
noop... same error:(

---

### Post by MaxIBoy on 2009-03-11
```
sudo dpkg --purge songbird
```

---

### Post by pjalegria on 2009-03-11
Thanks, it works :D

---

