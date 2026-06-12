---
title: "Issues with install - something is wrong?"
date: 2006-07-22
forum: Desktop Environments
---

### Post by worstofboston on 2006-07-22
Hi,

Yes, this is all brand new to me - but I am trying and have looked for these answers elsewhere.

I didnt know if I should install the desktop or server version. I want to run LAMP, but I also want the GUI. It was determined that the best thing for me to do would be to install Ubuntu Desktop and then install the LAMP stuff afterwards. 

1. I just installed Ubuntu. I was never asked for a root password. Consequently, I created one user and I believe that is all that I have. At the least, I dont know root's password. 

2. When I go to add applications, Apache, Php, MySQL are not there. How will I add them?

Thank you.

---

### Post by philippe_carlo on 2006-07-22
For security reasons, the root account is disabled. Running commands as root has to go through 'sudo' (use your own password). Installing programs can be done by using the synaptic package manager (in the system->administration menu). Consider reading an introductory manual for ubuntu to get familiar with this kind of stuff.

---

### Post by worstofboston on 2006-07-22
They are not available in the package manager. They are not there for me to select for download. 

And I asked about root because I read that I would be asked to create a root password and was not.

---

### Post by Wyrm_1972 on 2006-07-22
Have you updated your sources.list

[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)

Gets me most things I want.

---

### Post by worstofboston on 2006-07-22
I reinstalled and everything is all set.

Thank you for your time.

---

