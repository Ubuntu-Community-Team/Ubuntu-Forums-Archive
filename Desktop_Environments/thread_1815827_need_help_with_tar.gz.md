---
title: "need help with tar.gz"
date: 2011-08-01
forum: Desktop Environments
---

### Post by giganut on 2011-08-01
I am having problems installing tar.gz files on ubuntu 10.10. Dose any one have any suggestions.:confused:

---

### Post by Shahnawaz Uqaili on 2011-08-01
Hello,

You can use tar -zxvf abc.tar.gz

Regards

Shahnawaz Uqaili

---

### Post by giganut on 2011-08-01
iam not sure how to use that command

---

### Post by Shahnawaz Uqaili on 2011-08-01
First install the tar.gz file, then go to that directory by 

cd directory/abc.tar.gz

tar -zxvf abc.tar.gz

After it untar, go to that directory

./configure

make

make install


I guide you the whole installation process. You can read the INSTALL file in the directory for installation help.

Thanks

Shahnawaz Uqaili

---

### Post by giganut on 2011-08-01
there is no instillation file in the directory the program that i am trying to install is tmac-v1.0beta.tar.gz

---

### Post by Shahnawaz Uqaili on 2011-08-01
tar -zxvf tmac-v1.0beta.tar.gz

Have you tried this or abc.tar.gz?

---

### Post by giganut on 2011-08-01
bash: /home/giganut/Desktop/tmac-v1.0-beta: is a directory
giganut@ubuntu:~$ 


this is what it says now

---

### Post by giganut on 2011-08-01
thanks for the help i will have to pic this up tomorrow ti is 2:00 am where i am at, I have to get some sleep. PS: thanks agin

---

