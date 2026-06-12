---
title: "how do i restart gdm after kdm has been running"
date: 2006-08-12
forum: Desktop Environments
---

### Post by blastradius on 2006-08-12
If i type gdm -restart i get:-


(process:5549): GLib-CRITICAL **: g_hash_table_lookup: assertion `hash_table != NULL' failed

(process:5549): GLib-CRITICAL **: g_hash_table_lookup: assertion `hash_table != NULL' failed

(process:5549): GLib-CRITICAL **: g_hash_table_lookup: assertion `hash_table != NULL' failed


(process:5549): GLib-CRITICAL **: g_hash_table_lookup: assertion `hash_table != NULL' failed

(process:5549): GLib-CRITICAL **: g_hash_table_lookup: assertion `hash_table != NULL' failed

(process:5549): GLib-CRITICAL **: g_hash_table_lookup: assertion `hash_table != NULL' failed

and if i try gdmsetup i get this 5 times:-

failed to connect to socket

please help

---

### Post by rjwood on 2006-08-12
just log out, and change the session to ubuntu or gdm. I am not sure how it will be worded but you will see it.

---

### Post by the-linux-guy on 2006-08-12
A quick question: why on earth would you want gdm if you already running kdm (or visa versa) ? It's only a login manager, just stick with one of them and de-install the other through synaptic or apt-get...

---

### Post by blastradius on 2006-08-12
I have un-installed kdm but for some reason it's still the default!  It actually throws up an error at the splash screen which i have to cancel to get the log-in box.

I shouldn't have messed with it really, Gnome worked great but I tried Kdevelop and was impressed so thought I'd run it alongside Gnome.

---

### Post by rjwood on 2006-08-12
> **blastradius said:**
> I have un-installed kdm but for some reason it's still the default!  It actually throws up an error at the splash screen which i have to cancel to get the log-in box.

I shouldn't have messed with it really, Gnome worked great but I tried Kdevelop and was impressed so thought I'd run it alongside Gnome.Did you get it to work ok? Log out go to options then to sessions and choose gnome. 

I had the same problem with kdm taking over the log-in manager but I forget what I did to fix it. Search the forums and I am sure you will find your answer..GOOD LUCK!!

---

### Post by westep23 on 2006-08-12
# sudo update-rc.d -f kdm remove
# sudo update-rc.d gdm defaults


These commands should work.

---

### Post by the-linux-guy on 2006-08-13
Or you could try with a "sudo dpkg --reconfigure gdm" on a command line...
Good luck !

---

### Post by blastradius on 2006-08-13
> **westep23 said:**
> # sudo update-rc.d -f kdm remove
# sudo update-rc.d gdm defaults


These commands should work.

worked fine, thanks very much for the help

---

