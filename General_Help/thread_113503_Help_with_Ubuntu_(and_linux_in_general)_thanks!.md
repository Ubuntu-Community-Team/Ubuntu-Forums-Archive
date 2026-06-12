---
title: "Help with Ubuntu (and linux in general) thanks!"
date: 2006-01-06
forum: General Help
---

### Post by JSchrage on 2006-01-06
Hey everyone,

I aplogize in advance if this belongs in "Absolute Beginner", I am very new. I have the latest version of Ubuntu on a Gateway laptop here at work and we are trying to get Ethereal to work on it. There are about 20 different package types for Linux you can download, all different. I have a bit of OSX Unix shell experiance, so I can navigate but am lost trying to install and run this program.

Could you suggest what package file to download to work with Ubuntu?

How do you go about installing it if it does not show up in Synaptic?

Any other tips I need before I spend more and more time on this?

Thank you very much!

-Jimmy

---

### Post by Dr. Nick on 2006-01-06
Ethereal should show up in synaptic after enabling the extra repositories. Enable the universe repo and you should be able to install it. Its under the repository menu in synaptic, or you can search forums for more detailed and other ways to enable them

For other apps that dont appear in synaptic get a .deb or if you need to compile it get the .tag.gz.

If you have a .deb use **sudo dkpg -i *filename ***to install it, but taht doesnt automatically handle dependencies

---

### Post by healychan on 2006-01-06
This short guide will led you to enable Multiverse and Universe.
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)

---

### Post by JSchrage on 2006-01-06
Thank you guys so much!

I am trying now...

-JS

---

### Post by JSchrage on 2006-01-06
hmm something must be wrong with my Ubuntu, it gives Rep list package errors after I enable all of them. Also, it wont freaking update with sudo apt-get update...all the updates just hang and timeout....

weird

I'm going to reinstall the OS and try this again.

-JS

---

### Post by nalmeth on 2006-01-06
Hopefully you don't find after reinstalling that it is a net connection problem :razz: 
Search automatix and install it when you're back up

---

