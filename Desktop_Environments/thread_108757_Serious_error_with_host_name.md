---
title: "Serious error with host name"
date: 2005-12-26
forum: Desktop Environments
---

### Post by harisund on 2005-12-26
> Could not look up internet address for MyHostName. This will prevent GNOME from operating correctly. It may be possible to correct the problem by adding MyHostName to the file /etc/hosts. 

And this is happening after a perfect install.. what is going on? How do I get my GNOME to work. The worst part is, I am not even able to reboot? sudo init 6 / sudo reboot says 
sudo: unable to look up MyHostName via gethostbyname() 

I have to cold reboot and go to Windows.. what exactly is going on? 

Thanks !

---

### Post by joshuapurcell on 2005-12-26
What type of install did you do? Did you ever get the question to name your system (host)? Have you tried adding **MyHostName** to /etc/hosts? The line would look like this:```
127.0.0.1     MyHostName
```
If there is already a line that starts with 127.0.0.1, then just add MyHostName to the end of that line (instead of creating a new line). You can use either nano or vi to add this to the file (**sudo vi /etc/hosts**).

---

### Post by harisund on 2005-12-26
I did the standard desktop installation by pressing on Enter after booting off the install CD. 

Yes, I did get the question to name my system (yes my host name.) 

Oh and sudo doesn't work. 

127.0.0.1 localhost 

is the content of the /etc/hosts file, and I am not able to edit it. It doesn't allow me to edit it as the regular user, and sudo gives me the error: 

sudo: unable to look up MyHostName via gethostbyname() 

How do I edit /etc/hosts then?

---

