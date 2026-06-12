---
title: "Problem with firefox going grey and scrolling up and down"
date: 2009-06-03
forum: General Help
---

### Post by JPD2010 on 2009-06-03
Hi,

I'm having the following problem: 

o/s ver: Jaunty Jackalop 9.04

Browser: Firefox

flash Plugin: adobe latest

Desc: When am browsing mainly flash sites my firefox will greyout , on some occasions it will repeatedly scroll up and down for 20 seconds upto 3-4 mins :( 


Any help appreciated,
Thanks, JP

---

### Post by gettinoriginal on 2009-06-03
First of all, check your System > Administration > Software Sources and be sure the first 4 boxes are checked.  If it tells you that you are out of date, that's ok, just reload.
Be sure your browser is closed. Now  try this from terminal:

Remove your old flash plugin using the following command

   ```
 sudo apt-get remove flashplugin-* --purge
```

Install the flash plugin using the following command

    ```
sudo apt-get install flashplugin-nonfree
```

and restart browser, it should fix things.  Welcome to Ubuntu :p

---

### Post by JPD2010 on 2009-06-04
Thank you, i shall try that tonight! :)

---

