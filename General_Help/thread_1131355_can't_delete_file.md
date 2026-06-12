---
title: "can't delete file"
date: 2009-04-20
forum: General Help
---

### Post by terryq on 2009-04-20
I have inadvertently copied a file onto my desktop which I can't delete. Tried but keep getting error permission denied. The permissions are for root and I have tried and tried to no avail to change the permissions. Any advice veeeeeery welcome!

---

### Post by Bakon Jarser on 2009-04-20
> gksu nautilus

that will open nautilus as root and you can delete anything

---

### Post by terryq on 2009-04-20
Thanks Bakon but that doesn't work. Tried it before my post but nautilus said something about not being able to locate/display desktop items. Any other ideas?

---

### Post by maheshasolkar on 2009-04-20
Can open Terminal (Applications -> Accessories -> Terminal) and do the following:

```
  cd ~/Desktop
  ls -al
```

Then locate the name of the file to be deleted and run:
```

  sudo rm <name of the file>
```

If this does not work, share the output of all the above commands here in a reply.

---

### Post by JC Cheloven on 2009-04-20
Perhaps it's a matter of ownership of the archive. You can try:
```

cd ~/Desktop
sudo chown <your_username> <filename>
sudo chmod 755 <filename>
rm <filename>

```
Hope this helps

---

### Post by terryq on 2009-04-20
Thank you all. It's gone!

---

