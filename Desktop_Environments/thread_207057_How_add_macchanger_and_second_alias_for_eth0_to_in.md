---
title: "How add macchanger and second alias for eth0 to inint scripts?"
date: 2006-07-01
forum: Desktop Environments
---

### Post by JohnRus on 2006-07-01
Hello!

I have network where all computers has dual ip adresses: external and internal. In additional, I need to change mac adress of my network card to corectly working in my network. So, I need to add this actions to init scrips to doing its automaticaly when system loading. How I can do this on Ubuntu system?

When i was used Gentoo, there were rc-update utility which helps this. Also Gentoo has number of init config files to separately configuring hardware, network cards for the sample. Has Ubuntu the same? What should I do or where found information about this?

Big thanks!

---

### Post by JohnRus on 2006-07-01
I was found /etc/networking/interfaces where successfully changing my mac adress.

Next step is to make eth0:1 alias to eth0 interface. What should i write in interfaces file to do this?

---

