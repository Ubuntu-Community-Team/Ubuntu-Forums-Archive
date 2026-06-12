---
title: "gnome-art crashing"
date: 2006-01-04
forum: Desktop Environments
---

### Post by adventurepants on 2006-01-04
Hiya,

breezy 5.10 on a Dell inspiron 8600. 

have installed gnome-art through synaptic. It opens fine, but does not show any themes, and when i try to select anything through the menu ie 

art-backgrounds-gnome, 

it just crashes to the desktop. If i run it in a root terminal, i get the following:

/usr/local/lib/site_ruby/1.8/gnome-art/get_art.rb:155:in `main': no implicit conversion from nil to integer (TypeError)
        from /usr/local/lib/site_ruby/1.8/gnome-art/gnome_art.rb:132:in `main'
        from /usr/bin/gnome-art:25

I have also installed it from the tar on the webpage, but it gives the same result. 

Any ideas?

---

### Post by CodyJarrett on 2006-03-17
I have exactly the same problem - please help!!!!

---

### Post by stalefries on 2006-03-18
I've tried it before. It's not really useful, you may as well just go to [http://art.gnome.org](http://art.gnome.org) yourself. I think it's easier than the program itself.

---

### Post by CodyJarrett on 2006-03-18
funny thing - it's working now.
Re-installed Automatix, which seemed to do the job somehow...

---

