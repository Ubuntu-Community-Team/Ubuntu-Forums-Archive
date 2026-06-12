---
title: "Myth TV install issues apt-get errors"
date: 2006-01-21
forum: Desktop Environments
---

### Post by mt88 on 2006-01-21
Hi Im a noob to linux and want to run myth tv. The specs of the comp im using to test out myth tv are:

p3 550mhz
ati 128mb graphics card
192mb of ram
wd 40gb hdd
ati tv wonder tv tuner card

I am foolowing the gide on this page:

[http://www.quietglow.com/docs/ubuntumythtv.html](http://www.quietglow.com/docs/ubuntumythtv.html)

I skipped the driver bit for the other tv card.

I have got up to the stage of installing myth tv using the command:

apt-get install

but when i type this in it tells me that it cant find this command beccause of "access denied"

so HELP thanks in advance if not does ne1 no whwere i can find a .deb or .rpm vertion of myth tv so i can install that like in this page:

[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

cheers in advance for any advice you can give me

---

### Post by Hallavej on 2006-01-21
Did you remember sudo
```
sudo apt-get install <whatever>
```

---

### Post by mt88 on 2006-01-21
yes the exact line i typed was

apt-get install mythtv

and i got the error

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

After more research the lock file (whatever it is) is a picture of a green foot with a wite cross in a red box in the corner. What does that mean? is it currupt?

---

### Post by nianhbg on 2006-01-22
You need to run the apt-get commands with "sudo" before like:

sudo apt-get install <packet name>

---

### Post by bonewhat on 2006-01-23
be sure to not have applications like synaptic running cuz they lock those files

---

### Post by pompeyjohn on 2006-01-26
mt88 - how are you getting on?

I am just putting together a myth/ubuntu box at the moment, so if you are still having problems I might be able to help ;)

---

