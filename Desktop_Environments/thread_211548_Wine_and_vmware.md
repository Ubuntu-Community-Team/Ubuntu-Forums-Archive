---
title: "Wine and vmware"
date: 2006-07-08
forum: Desktop Environments
---

### Post by dwith on 2006-07-08
ubuntu 6.06

I am trying to use wine to install Internet Explorer 7. As an IT manager, I need Internet Explorer's Active X to remote into my company's MS server. I would rather not buy another computer or dual boot just to use XP.

This is the error when initiating wine from the root console:

wine: could not load L"c:\\windows\\system32\\IE7BETA3-WindowsXP-x86-enu.exe": M                                 odule not found

vmware? Do I have to install XP with vmware first before I can install and use IE7? If this is the case, wine seems like an easier solution.

Thanks for your help

---

### Post by hscottyh on 2006-07-08
> **dwith said:**
> I need Internet Explorer's Active X to remote into my company's MS server

Are you sure? I connect to my work's MS server with the Terminal Server Client Applet. Works great! Use RDPv5 for the protocol.

> **dwith said:**
> vmware? Do I have to install XP with vmware first before I can install and use IE7? If this is the case, wine seems like an easier solution.

That would be correct. I think you'll have a harder time to get IE 7 to work under wine. IE 6 can be easy with third party tools like winetools.

---

### Post by dwith on 2006-07-08
Do you have any information on how to run Terminal Server Client Applet and winetools? I know that the web is full of information, but perhaps you have a few concise examples. 

Thanks

---

### Post by hscottyh on 2006-07-09
> **dwith said:**
> Do you have any information on how to run Terminal Server Client Applet and winetools? I know that the web is full of information, but perhaps you have a few concise examples. 

Thanks

Right Click on your panel and click 'add to panel', then drag the 'Terminal Services Client Applet' to it. Now you have a an Icon on your panel. When you click on it choose 'new connection' and configure it. 


For winetools go to [http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/) and download it. Then extract it to a directory and run it. You'll have all kinds of options for stuff to install, including IE6.

---

