---
title: "dictionary"
date: 2006-06-24
forum: Desktop Environments
---

### Post by murataht on 2006-06-24
Hi there,
I am looking for a program that can be used as a dictionary. i know gnome dictionary but it does not work when there are no network. is there any program like this? 
thanks in advance.
Murat

---

### Post by murataht on 2006-06-28
wow? no program like this???:confused:

---

### Post by barisurum on 2006-06-28
Well there are dictionaries for different languages in different names. For example I use Ksocrat to translate english/russian/english. And mueller7 dict server for english/russian. Setting up a dict server can be a daunting task since I think there isn't an automated way for it. But you can find good dict apps like Ksocrat.

---

### Post by murataht on 2006-07-03
thanks for the tip. I installed the dict and dictd from synaptic and now everything is running without any configuration. thanks. ubuntu rocks!!!

edit: 
after you have installed the dict and dictd, you should run gdict and open "edit->preferences".

from the "source" tab you push "add" button. a add dialog will come out. 

specify the source name: "localhostEnglish", or whatever you like.
specify the  Transport : "Dictionary Server",
specify the hostname: "localhost"
specify the port: "2628"

in the advanced extension you can also specify the database, like different database for the different language. but i never have to messed up with that. 

hope this helps somebody.

---

