---
title: "How do I set up stereo bluetooth on Ubuntu?"
date: 2008-12-10
forum: General Help
---

### Post by jcm4 on 2008-12-10
Thanks.

---

### Post by s.fox on 2008-12-10
Hi,

Can you please give more information.  It would be useful to know the brand and model of your blue tooth stereo headphones.  (I assume you mean headphones)

You will probably need to look into the [Alsa]("http://bluetooth-alsa.sourceforge.net/") project.

Ash R

---

### Post by jcm4 on 2008-12-10
I have a pair of Plantronics 590Es. Thanks.

---

### Post by s.fox on 2008-12-10
[This]("http://ubuntuforums.org/showpost.php?p=2071407&postcount=73") post is about your headphones.  This person got it them to work.  Looks like he used the Alsa project.

---

### Post by jcm4 on 2008-12-10
Sick. Thanks.

---

### Post by s.fox on 2008-12-10
> **jcm4 said:**
> Sick. Thanks.

So are they now working?  If so can you please mark this thread as solved.  

Thanks

---

### Post by jcm4 on 2008-12-10
Hmm...
I don't understand what 
"Editing /etc/bluetooth/hcid.conf and adding auto instead of user in security" means.
And when I type "sudo apt-get install kdebluetooth" in the terminal it tells me an application is using it.

---

### Post by s.fox on 2008-12-10
hcid.conf is a file.


open a file manager window and type in ```
 /etc/bluetooth/hcid.conf 
```   That should open the file in a text editor.  You will be able to edit it from there.  It would also be an idea to make a backup before you change the file,  just in case.

---

### Post by jcm4 on 2008-12-10
> **Ash R said:**
> hcid.conf is a file.


open a file manager window and type in ```
 /etc/bluetooth/hcid.conf 
```   That should open the file in a text editor.  You will be able to edit it from there.  It would also be an idea to make a backup before you change the file,  just in case.

There's nothing in the file...

---

