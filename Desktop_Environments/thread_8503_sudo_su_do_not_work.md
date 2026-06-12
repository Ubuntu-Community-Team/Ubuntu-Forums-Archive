---
title: "sudo su do not work"
date: 2004-12-18
forum: Desktop Environments
---

### Post by l33tman on 2004-12-18
This is what I get when I enter my user password


[B]sudo apt-get update
>>> sudoers file: syntax error, line 21 <<<
sudo: parse error in /etc/sudoers near line[/B] 

suggestions please

 :mrgreen: 
l33tman

---

### Post by Val1472 on 2004-12-18
Give the content of the file.

---

### Post by jodef on 2004-12-19
[QUOTE=l33tman]This is what I get when I enter my user password


[B]sudo apt-get update
>>> sudoers file: syntax error, line 21 <<<
sudo: parse error in /etc/sudoers near line[/B] 

suggestions please

 :mrgreen: 
l33tman[/QUOTE]

As indicated give content of the file, you edited the file and an invalid parameter was included. Always use **visudo** to edit the sudoers file that way when you save if there are any invalid parameters you are immediately warned before saving the file. :wink:

---

