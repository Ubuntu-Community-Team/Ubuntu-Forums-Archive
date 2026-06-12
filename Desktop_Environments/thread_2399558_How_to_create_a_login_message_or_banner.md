---
title: "How to create a login message or banner"
date: 2018-08-27
forum: Desktop Environments
---

### Post by wilsonwx18 on 2018-08-27
Hi,

Does anybody know how to create a login message or banner for ubuntu 18.0.4 LTS.

---

### Post by ajgreeny on 2018-08-27
From your description it's impossible to know what you really want so please give us more details.

What do you want it to look like, do you want it to show for a limited time and disappear, etc etc.

---

### Post by wilsonwx18 on 2018-08-27
Hi,
I will like to create a warning message "Please login only if you are authorised to do so" at the login page or before the user log into his or her account. How do I go about doing this.

---

### Post by deadflowr on 2018-08-27
See: [https://help.gnome.org/admin/system-admin-guide/stable/login-banner.html.en]("https://help.gnome.org/admin/system-admin-guide/stable/login-banner.html.en")

---

### Post by wilsonwx18 on 2018-08-27
Hi,
How do I create a keyfile in /etc/dconf/db/gdm.d

---

### Post by again? on 2018-08-29
You create the gdm keyfile as shown in deadflowr's link.
_**1. Create the gdm profile**_
```
sudo nano /etc/dconf/profile/gdm
```
Copy and paste...
```
user-db:user
system-db:gdm
file-db:/usr/share/gdm/greeter-dconf-defaults

```

In nano to save, press and release ctrl + x, hit y and then Enter.

_**2. Create a gdm keyfile**_
Create the */etc/dconf/db/gdm.d* directory if it doesn't exist.
```
sudo mkdir -p /etc/dconf/db/gdm.d
```

Create keyfile...
```
sudo nano /etc/dconf/db/gdm.d/01-banner-message
```
Copy and paste...
```
[org/gnome/login-screen]
banner-message-enable=true
banner-message-text='[COLOR="#FF0000"]Type the banner message here.[/COLOR]'
```
Using [COLOR="#FF0000"]your message[/COLOR]
Save as before.

**_3. Update database_**
```
sudo dconf update
```
Reboot.

---

