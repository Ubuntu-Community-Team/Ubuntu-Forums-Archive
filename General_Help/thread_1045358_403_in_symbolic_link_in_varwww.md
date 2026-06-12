---
title: "403 in symbolic link in /var/www"
date: 2009-01-20
forum: General Help
---

### Post by Shachiel on 2009-01-20
I installed a LAMP Server via Mark Packages by Task in Synaptic, everything went smoothly and I've already seen the "It works!" screen. However when I tried to create a symbolic link targeting a folder in my /home/username directory I get a 403 Forbidden error.

Here's what I did:

First, I installed the LAMP Server in Synaptic

Then I wrote in terminal
```
sudo ln -s /home/schl/nls /var/www/nls
```

Then I typed [http://localhost/nls](http://localhost/nls) in my browser and got the error.

Any help would be very much appreciated, this is driving me crazy

---

### Post by dcstar on 2009-01-20
> **Shachiel said:**
> I installed a LAMP Server via Mark Packages by Task in Synaptic, everything went smoothly and I've already seen the "It works!" screen. However when I tried to create a symbolic link targeting a folder in my /home/username directory I get a 403 Forbidden error.

Here's what I did:

First, I installed the LAMP Server in Synaptic

Then I wrote in terminal
```
sudo ln -s /home/schl/nls /var/www/nls
```

Then I typed [http://localhost/nls](http://localhost/nls) in my browser and got the error.

Any help would be very much appreciated, this is driving me crazy

"Forbidden" usually means a permission problem, check them.

---

### Post by jjrp78 on 2009-11-26
Did you solved the issue? Im having the same problem

---

