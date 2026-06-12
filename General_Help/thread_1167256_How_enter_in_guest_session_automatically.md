---
title: "How enter in guest session automatically?"
date: 2009-05-22
forum: General Help
---

### Post by gaiterin on 2009-05-22
Hi!
Can I enter in the guest session automatically when I startup the computer?
Thanks! ;)

---

### Post by sim-value on 2009-05-22
THe only thing i found is that you can automatically log in a User ...

But i dont know for guest session ...

---

### Post by gaiterin on 2009-05-25
Hi!
I did this for have a "guest" false session with GDM Login:

1.- Create a count without privileges (example Guest).

2.- Configure this count (Guest).

3.- Add all files (included hidden) to a .tar file and save it (example /etc/init.d/guest.tar)

4.- Create this file /etc/init.d/guest.sh
With this context:
```
#!/bin/sh
rm -rf /home/guest
mkdir /home/guest
chown guest:guest /home/guest
tar -C /home/guest -xvf /etc/init.d/guest.tar
```

5.- In terminal:
```
sudo chmod +x /etc/init.d/guest.sh
sudo update-rc.d guest.sh defaults
```


With this 5 steps, all configuration user is restart to "default" (in .tar file), in each restart :)
Cheers!

---

