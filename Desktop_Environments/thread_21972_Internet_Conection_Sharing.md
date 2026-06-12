---
title: "Internet Conection Sharing"
date: 2005-03-24
forum: Desktop Environments
---

### Post by CB201 on 2005-03-24
My wireless card isn't supported, so I installed ndiswrapper and set up my network using the driver on my card's CD.  I belive it's configured properly, because I am able to ping the other computer on my network, but I can't access the Internet.  I *am* able to access the Internet from Windows XP, so I'm pretty sure I'm doing something wrong from within Ubuntu.  Any suggestions?

---

### Post by cwaldbieser on 2005-03-24
What does your routing table look like?
```

$ route
```

Maybe you just don't have a default route to your gateway?  How is your netwok set up?  What is physically connected to the Internet?  How does your Ubuntu machine fit into your network?

---

