---
title: "Limewire and Edubuntu"
date: 2006-05-06
forum: Desktop Environments
---

### Post by guitarman on 2006-05-06
Has anyone successfully installed Limewire on their Edubuntu system?  I downloaded  the latest version and when I go to install it tells me that JAVA needs to be updated.  But when I check using "java -version", I get a response back saying that I have version 1.42 .  How do I make JAVA available to the whole system when I install it as the administrator?

thanks,

;)

---

### Post by imdeemvp on 2006-05-07
maybe automix will work....

---

### Post by Ramses de Norre on 2006-05-07
Check whether the right one is default and otherwise set it correctly with:
```
 sudo update-alternatives --config java
```

---

