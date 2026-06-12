---
title: "Wireless help."
date: 2005-12-16
forum: General Help
---

### Post by madsalty on 2005-12-16
Can someone help please? i have a 802.11g Wireless Desktop Network Card Part # F5D7000uk and i need it to connect to the internet can someone please tell me which drivers and programs are needed?

---

### Post by fishbroetchn on 2005-12-16
hi,

you need to give some more information, please. What kind of a network do you want to connect to? Can you log onto the internet via cable for a short time? what distro do you have?....

greets fishbroetchn

---

### Post by earobinson on 2005-12-16
[https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)

---

### Post by madsalty on 2005-12-16
thanks

---

### Post by earobinson on 2005-12-16
did it work, let us know how it goes

---

### Post by madsalty on 2005-12-16
i'm having trouble because i have to make the file can you show me how to do that

---

### Post by earobinson on 2005-12-16
can you link and quote to the file part of the document you are having problems with

---

### Post by madsalty on 2005-12-16
Basically what happens i si can't install it because, i presume it wants me to make the file but i have no idea how.

---

### Post by aclaunch on 2005-12-16
What it's talking about is compiling the application. You have to have the package "build-essentials" and probably the linux-kernel-headers for your kernel (install with Synaptic). Then go to a terminal, change (cd) to the directory where the source code is (remember it should be in a directory that you have write permissions in so, someplace in /home is good); now type "configure" and hit Enter. Let it do its thing; then type "make" and let it do its thing; then type "sudo make install" (the sudo allows the compiled application to be installed in some system directory like /usr that you as a regular user cannot write to).

That's it but you need to post more information to get a better answer.

Good Luck,
Alan

---

### Post by madsalty on 2005-12-17
thanks mate

---

### Post by madsalty on 2005-12-17
Well it works, considering i am writing this meesage in linux!!!!!!!!!!!!!!

---

### Post by earobinson on 2005-12-17
grats

---

### Post by earobinson on 2005-12-17
diouble post forum bug? :(

---

