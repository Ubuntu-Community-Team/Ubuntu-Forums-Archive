---
title: "Newbie needs help with updates"
date: 2009-01-20
forum: General Help
---

### Post by Davessubaru on 2009-01-20
High new here. How do I correct this.  E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. Please be gentle Im new at this stuff.

  Thanks
                                                 Dave :redface:

---

### Post by Therion on 2009-01-20
Open a Terminal and enter:```
sudo dpkg --configure -a
```
Enter your password when prompted and... *Voila*, problem solved.

Ubuntu, unlike some other operating systems, frequently will help you solve the problem when there's an error instead of just spitting out some cryptic error message.

---

### Post by Davessubaru on 2009-01-20
> **Therion said:**
> Open a Terminal and enter:```
sudo dpkg --configure -a
```
Enter your password when prompted and... *Voila*, problem solved.

Ubuntu, unlike some other operating systems, frequently will help you solve the problem when there's an error instead of just spitting out some cryptic error message.Sorry for my ignorance, but what is a terminal?:redface:

---

### Post by scouser73 on 2009-01-20
Hi Davessubaru, open **Accessories**, and scroll to **Terminal** and click.

Then copy and paste **sudo dpkg --configure -a** into the Terminal window and press enter, you will then be asked for your password. Once you have typed the password then press enter.

****When you type your password in terminal it won't show, not even asterisks will appear**** This is normal and is nothing to worry about, it's just a quirk of Terminal.

---

### Post by Davessubaru on 2009-01-20
> **Davessubaru said:**
> High new here. How do I correct this.  E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. Please be gentle Im new at this stuff.

  Thanks
                                                 Dave :redface: Thank you very much!:) Problem solved!:KS

---

