---
title: "Chaning folder permissions for www folder under var"
date: 2009-01-21
forum: Desktop Environments
---

### Post by raunhar on 2009-01-21
I tried changing the folder permissions using:
sudo chown -R www-data:ww-data /var/www
and
sudo chmod 777 /var/www -R

but nothing happened. It gave a error variable missing

---

### Post by taurus on 2009-01-21
> **raunhar said:**
> I tried changing the folder permissions using:
sudo chown -R www-data:**[COLOR="Red"]ww-data[/COLOR]** /var/www
and
sudo chmod 777 /var/www -R

but nothing happened. It gave a error variable missing

Could it be because you are missing a **w** in there?

Open a terminal and post the outputs of these commands here.

```
ls -la /var/www
grep www-data /etc/group
```

---

### Post by raunhar on 2009-01-22
thanks solved

---

