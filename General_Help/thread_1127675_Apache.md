---
title: "Apache"
date: 2009-04-16
forum: General Help
---

### Post by Alexmimeur on 2009-04-16
Hello,

I have just installed unbuntu on my laptop (with wubi to keep windows) and I would like to have Apache on it. I have tried to use the command 'sudo apt-get install apache2' but it doesn't recognise it and says this file doesn't exist . I have tried the same command but with 'apache' but it still doesn't work. What can I do?

Thank you for your reply.

---

### Post by aaronp on 2009-04-16
go to System > Administration > Synaptic Package Manager

then search for apache - you should be able to find it in the search results and mark it for installation from there.

Not sure if apache is in some of repositories that need to be enabled manually after install. If your search in Synaptic finds nothing, go to System > Administration > Software Sources and enable the unchecked repositories.

htth
Aaron

---

### Post by cariboo on 2009-04-16
Seeing as you are fairly new I would suggest you use Add/Rmove Programs or Synaptic Package Manager to installl any thing. I would suggest you install the LAMP stack, as you can't do much with just apache2. To install the LAMP stack go to System-->Aministration-->Synaptic Package Manager-->Edit-->Mark Packages by Task, and select LAMP from the menu, then click apply and follow the prompts.

Jim

---

