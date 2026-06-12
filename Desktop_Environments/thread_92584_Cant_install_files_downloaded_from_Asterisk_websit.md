---
title: "Cant install files downloaded from Asterisk website"
date: 2005-11-19
forum: Desktop Environments
---

### Post by dghundt on 2005-11-19
I am trying to down load the current release of Asterisk open source PBX software from their website (synaptic has older version).  I get to the part where I select where to extract the files but then it says I do not have user rights.  

1.  How do I set myself up to have permission to do this?

2.  Once I extract the files to a particular folder, how do I install it?

Thanks!! :confused:

---

### Post by not_yet on 2005-11-20
use sudo to give yourself admin rights

example: if I wanted to edit the file "test" and have admin rights

sudo gedit test

sudo <name of app you are using >   <name of file>

now press enter, and put in your password

to extract the files right click and choose extract

once extracted you will have to build the program

typically you would use three steps 1. configure  2. make  3. make install

check the readme as this can vary

---

### Post by dghundt on 2005-11-20
thanks for your reply.

the problem i had was their was no apparent place to use sudo.

i was on the web at digium site.  clicked on asterisk 1.2.   a new window came up asking me essentially where to unzip the downloaded file.  I pointed to /usr/src/asterisk, then said ok.  thats where i received the permission error.  

thanks

---

### Post by not_yet on 2005-11-20
when you click on 1.2 to download you should recieve a dialog box that asks you where you would like to save the file to

if you didn't get this,  perhaps there was a server problem, just try again

I just tried it and it downloaded ok

good luck

---

### Post by not_yet on 2005-11-20
oops.......

should have added / download to your home directory
make a new folder Asterisk, then download to /home/<your username>/Asterisk

---

