---
title: "Java problem"
date: 2007-08-13
forum: Gaming &amp; Leisure
---

### Post by MWilliams13 on 2007-08-13
I am trying to get the JRE (Java Runtime Enviroment) to work on my laptop. I am not very good at finding out what hardware I have and I am new to Ubuntu...well sorta.....anyway here I go : 

I am trying to install the JRE on my laptop to play runescape. Every time I get to the page in Firefox it says addititional plugins are required to view this page. I clikc install and it begins to install. 
After it attempts to install it it says "Not Avalible" on the finished screen and has a button that says manual install. I click that and it takes me to the Sun Java site's download page. Once I download it I have no idea what to do. Can someone help give me a step by step guide to this process?

---

### Post by shynko on 2007-08-13
go to the synaptic package manager and look for sun java 6 runtime environment then double click it then click apply near the top .Then  restart firefox and cross you're fingers :)

---

### Post by mlind on 2007-08-13
make sure you have multiverse repository enabled, then
```

sudo aptitude update
sudo aptitude install sun-java5-jre
sudo update-java-alternatives -s java-1.5.0-sun

```

You can also use synaptic or similar graphical tool to install java.

---

