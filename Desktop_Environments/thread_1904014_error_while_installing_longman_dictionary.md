---
title: "error while installing longman dictionary"
date: 2012-01-03
forum: Desktop Environments
---

### Post by forsubhi on 2012-01-03
I visit 
[http://thanhsiang.org/faqing/node/105](http://thanhsiang.org/faqing/node/105) 
to install longman dictionary but when I try to execute this command 
sudo apt-get install libgtk1.2 
the terminal tell me that package not available 
I use ubuntu 11.10

---

### Post by stinkeye on 2012-01-03
> **forsubhi said:**
> I visit 
[http://thanhsiang.org/faqing/node/105](http://thanhsiang.org/faqing/node/105) 
to install longman dictionary but when I try to execute this command 
sudo apt-get install libgtk1.2 
the terminal tell me that package not available 
I use ubuntu 11.10
See [**_[COLOR="DarkRed"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=9232968&postcount=2")

Download each deb for your Architecture (i386=32bit) to your home folder then run the command
specified for each deb in the order listed
eg install in this order
```
sudo dpkg -i --force-architecture libgtk1.2-common_1.2.10-18.1build2_all.deb
sudo dpkg -i --force-architecture libglib1.2ldbl_1.2.10-19build1_i386.deb
sudo dpkg -i --force-architecture libgtk1.2_1.2.10-18.1build2_i386.deb
```

---

### Post by forsubhi on 2012-01-26
I try this with amd64 but the installer doesn't start

---

### Post by forsubhi on 2012-01-26
I also try to install longman using wine but I get this error 
please insert the LDOCE5 DVD-ROM if you want to listen to the pronunciation

---

### Post by stinkeye on 2012-01-26
Is there any reason you want to specifically use the longman dictionary?
Artha is a good dictionary for Ubuntu.
Set artha to autostart and it will sit in the panel.
Highlight a word and you can see the meaning using ctrl+alt+w.

---

### Post by forsubhi on 2012-01-26
I want to listen to pronunciation !

---

### Post by forsubhi on 2012-01-26
this work for me 

[http://starodubtsevss.wordpress.com/2010/05/09/install-ldoce5-longman-dictionary-on-ubuntu-64-bit/#comment-113](http://starodubtsevss.wordpress.com/2010/05/09/install-ldoce5-longman-dictionary-on-ubuntu-64-bit/#comment-113)


but now I need crack for it

---

### Post by forsubhi on 2012-01-26
I fixed previous errors but I get this 
no such group dict in undefined 

what is the problem ?

---

### Post by stinkeye on 2012-01-27
> **forsubhi said:**
> I want to listen to pronunciation !
Buy the cd.

---

