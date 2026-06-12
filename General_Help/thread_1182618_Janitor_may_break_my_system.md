---
title: "Janitor may break my system ?"
date: 2009-06-09
forum: General Help
---

### Post by its_jon on 2009-06-09
I ran the Janitor....

I got a big list...... so I thought... go with it !.... this is sure to free up a lot of space.... however I got this confirmation message which has me worried... so I never went ahead with the cleanup..... should I have worried ?

"You are removing 93 .deb packages. This may break your system, if you need them. Do you want to continue?"

will my system break if I remove them ?..... Not sure I should trust the machine hence me asking the question

Thanks !


PS.... 

I have just had a problem resolved with update manager not working..... may this have effected the janitor ?

---

### Post by paul_anders on 2009-06-09
im not sure about janitor, i have read mixed results.
my way of a safe removal of unwanted file is something
similar to this

***** A tutorial found on the Ubuntu forums ****** 

1. Go to System>Administation>Synaptic Package Manager

2. Click the Status button (bottom left) then click Residual config.

3. If anything comes up in the right hand window, select it and Mark for Complete Removal, then click Apply.

4. Click on All, then on any name on the right hand side. Type localepurge and check whether it is installed or not. If not, install it. When it install it asks you for your locale. I selected en-uk - this is the locale that it will leave on my system, getting rid of anything else.

5. Do the same for the deborphan package.

6. Open a Terminal and type: sudo apt-get autoclean
to install deborphan type sudo apt-get install deborphan

7. Type: sudo deborphan | xargs sudo apt-get -y remove –purge

PA

---

### Post by mike555 on 2009-06-09
Be very careful with janitor , I bonked an installation using it and had to reinstall, I think it should be removed from the menu ...

---

### Post by Therion on 2009-06-09
I remember reading SEVERAL accounts of people totally borking their system by using Computer Janitor back when Jaunty was still in it's Alpha, Beta and RC stages.  So many in fact I was shocked to see it in the final release.  I've removed it from my system.  

My advice would be to avoid Computer Janitor like the plague.  

If you want a good system cleaner, get **QuickStart** instead.  It's "House Cleaning Option" is safe and effective.  I've used it and I recommend it highly.

[http://quickstart.freeforums.org/quickstart-download-pics-t2.html](http://quickstart.freeforums.org/quickstart-download-pics-t2.html)

Be SURE you read the very simple install instructions.

---

### Post by its_jon on 2009-06-10
I had a problem with update manage/add remove/synaptic.... I took advice and tried this code "which appears to reset things"

just wondering if doing this made Janitor think all my apps were unused or dead ? or something ? I messed around with software sources as well to try to get it resolved ...andyway that code

```
sudo mv /var/lib/apt/lists /var/lib/apt/lists-old  # rename old lists folder
sudo mkdir /var/lib/apt/lists  # create new lists folder
sudo mkdir /var/lib/apt/lists/partial # create new lists/partial folder
sudo apt-get update  # run update to create new lists
```


?????

---

### Post by Soul-Sing on 2009-06-10
I should not recommend janitor take over your/our computer(s)
It (janitor) does sometimes recommend strange and weird things....

---

### Post by Camilia on 2009-06-12
I used janitor, for couldn't get my printer to print with new black cartridge. I got that problem solved. Since then documents in the flash disk are open only read mode.

---

