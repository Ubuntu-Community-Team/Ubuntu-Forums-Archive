---
title: "sudo doesn't work anymore"
date: 2006-08-06
forum: Desktop Environments
---

### Post by chloraldo on 2006-08-06
sudo doesn't do anything anymore.
I got a message when trying to open synaptic. It said something about sudoers and didn't open.

I restarted the PC and tried to open synaptic from the menu, but it and many other items have disappeared from the menu...

what's wrong?

BTW, I have a sound problem with skape and was trying to repair that and reinstalled alsa (and ubuntu-base, ubuntu-something?) while doing that (unsuccessfully). Perhaps there's a connection.

---

### Post by taurus on 2006-08-06
What's the error message if you run this command from a terminal (Applications -> Accessories -> Terminal)?

```

sudo apt-get upgdate

```

---

### Post by chloraldo on 2006-08-06
nothing, I just get a new line...

---

### Post by taurus on 2006-08-06
What is the output of this command then?

```

id

```

---

### Post by chloraldo on 2006-08-06
uid=1000(chloraldo) gid=1000(chloraldo) groups=29(audio),1000(chloraldo)

---

### Post by taurus on 2006-08-06
> **chloraldo said:**
> uid=1000(chloraldo) gid=1000(chloraldo) groups=29(audio),1000(chloraldo)
Sorry but to use sudo, you need to belong to groups adm & admin in /etc/group!!!  So, reboot your machine and at the GRUb menu, pick the recovery mode and boot from it.  Wait for it to finish booting and at the prompt, edit your /etc/group and add your username to the end of adm & admin...

```

nano /etc/group

```

---

### Post by chloraldo on 2006-08-06
works now, thanks!

---

