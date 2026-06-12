---
title: "trying to install Usenext.deb"
date: 2009-04-27
forum: General Help
---

### Post by poodpood on 2009-04-27
Hi, I use Usenext as my newsreader, binary downloader service and on Intrepid, the deb package installed ok. I updated, clean install, to Jaunty and now when I try to install it, I get the message "Error: Dependency is not satisfiable: libgnome2.0-cil (>= 2.16.0)"

Any ideas what I can do?:(

---

### Post by manamaga on 2009-05-15
Hi, i`m having the same problem, i`m on ubuntu 9.04. I emailed usenext and they sent me an email back including a download link, only thing is, they replied to me in German!!!, i emailed them back weeks ago and as yet i`ve had no reply. I downloaded from the link they gave, so now i have a usenext.rpm package and i dont know what to do with it. I`ve copied/pasted their reply below, if anybody can translate. Any help would be great.

Bei dem Fehler handelt es sich um einen bekannten Bug bei Janty. Laut Entwickler ist dieser bereits bekannt und in Bearbeitung.
 
Um die Software aktuell nutzen zu können, versuchen Sie bitte folgendes:
 
1. Downloaden Sie sich die UseNeXT-Software als .rpm-Paket unter folgendem Link:
[http://www.usenext.de/usenextde/download/usenext.rpm](http://www.usenext.de/usenextde/download/usenext.rpm)
 
2. sudo apt-get install alien 
3. sudo alien usenext.rpm --scripts
4. Sie haben dann ein neues Paket: usenext_4.6.3-2_all.deb
5. Dieses können Sie dann über die Synaptic-Paketverwaltung installieren.
Wichtig: "sudo apt-get install libmono-winforms2.0-cil" muss installiert sein, ansonsten startet UseNeXT nicht.
Bei weiteren Fragen stehen wir Ihnen gerne zur Verfügung.

---

### Post by manamaga on 2009-05-16
OK, a bit of an update. Somehow i have managed to install usenext but now when i try to run it i get "Error: Failed to start Usenext"  but no reasons as to why. I have been on this for weeks now to try to find a resolution but no joy :(  Now i`m getting desperate.

---

### Post by chriskin on 2009-05-16
> **manamaga said:**
> Hi, i`m having the same problem, i`m on ubuntu 9.04. I emailed usenext and they sent me an email back including a download link, only thing is, they replied to me in German!!!, i emailed them back weeks ago and as yet i`ve had no reply. I downloaded from the link they gave, so now i have a usenext.rpm package and i dont know what to do with it. I`ve copied/pasted their reply below, if anybody can translate. Any help would be great.

Bei dem Fehler handelt es sich um einen bekannten Bug bei Janty. Laut Entwickler ist dieser bereits bekannt und in Bearbeitung.
 
Um die Software aktuell nutzen zu können, versuchen Sie bitte folgendes:
 
1. Downloaden Sie sich die UseNeXT-Software als .rpm-Paket unter folgendem Link:
[http://www.usenext.de/usenextde/download/usenext.rpm](http://www.usenext.de/usenextde/download/usenext.rpm)
 
2. sudo apt-get install alien 
3. sudo alien usenext.rpm --scripts
4. Sie haben dann ein neues Paket: usenext_4.6.3-2_all.deb
5. Dieses können Sie dann über die Synaptic-Paketverwaltung installieren.
Wichtig: "sudo apt-get install libmono-winforms2.0-cil" muss installiert sein, ansonsten startet UseNeXT nicht.
Bei weiteren Fragen stehen wir Ihnen gerne zur Verfügung.


i do not speak german at all,but their guide is easily undestandable

it says to download the rpm package, install alien, make rpm into a deb and then install the deb

now about the missing dependency, if it is not installed on its own, all you have to do is search and download it from the internet
do you want me to search?

edit : oh, i didn't see the update, have you installed all the dependencies said in the email?


> **poodpood said:**
> Hi, I use Usenext as my newsreader, binary downloader service and on Intrepid, the deb package installed ok. I updated, clean install, to Jaunty and now when I try to install it, I get the message "Error: Dependency is not satisfiable: libgnome2.0-cil (>= 2.16.0)"

Any ideas what I can do?:(

you have to find libgnome2.0-cil . it should install itself automatically if it is on the repositories, or you might have to search for it (probably given in the same site as the deb?)

---

### Post by manamaga on 2009-05-16
Hi, i thinks thats how i managed to install it. I got the libgnome2.0 and if i remember correctly, it created a .deb file from my .rpm so i used package manager to install the .deb file. All seemed to go OK, Usenext is showing in the Applications>Internet list but when i start it i get the  "Error: Failed to start Usenext" message. Thats the stage i`m at now, i think even though the install seemed to go OK, something obviously didnt go right along the way.

Edit:  One thing i have noticed, when the .deb package was built, it has a padlock symbol next to it, i cant changes the permissions on this because it says i`m not the owner?? Maybe this has something to do with it not installing correctly??

---

### Post by jlperry on 2009-05-17
I had the same problem but I translated the response manamaga got from usenext.

When the error is a known bug in Janty. According to developers this is already known and in process. 


 To use the software to be able to use currently, please try the following: 

 1. Download the software as Usenext. Rpm package by following this link: 
 [http://www.usenext.de/usenextde/download/usenext.rpm](http://www.usenext.de/usenextde/download/usenext.rpm) 

 2. sudo apt-get install alien 
 3. sudo alien usenext.rpm -- scripts 
 4. You then have a new package: usenext_4.6.3-2_all.deb 
 5. This you can then use the Synaptic package management to install. 
 Important: "sudo apt-get install libmono-winforms2.0-cil" must be installed, otherwise starts Usenext not. 
 For further questions, please do not hesitate to contact us.


You might want to try to instal libmono-winforms2.0-cil as mentioned in the **Important** note. I followed the instruction at it is working for me now.

Thnx manamaga for posting the usenext response. Works for me!.. :D

---

### Post by manamaga on 2009-05-17
Fantastic! I now have it working, many thanks to jlperry for opening my eyes to the libmono-winforms install, i`d completely overlooked it. Only thing i have now is, i can log in to usenext OK,  but i seem to be getting an error message completely at random and i think its just some setting i need to change but i`m not sure where or how, here is the messgae i`m getting:

"The connection was refused when attempting to contact localhost:8080."

I have a feeling this maybe something to do with my network settings but i dont want to go changing things at random as i might mess things up totally, so one final favour if possible, what do i do here.

Thank you so much guys!

---

### Post by manamaga on 2009-05-27
I hate to bump this thread but i wondered if anybody has had this before and found a fix for it, cheers.

---

### Post by spiri7 on 2009-05-29
Hi, after installing usenext.deb without any problems I can't log in. 
Does nobody have the same problem ?

edit:
I've solved my problem. There is a different login and password for the site-login and the software.

---

