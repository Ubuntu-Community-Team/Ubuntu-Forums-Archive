---
title: "edit text file via a shell or perl script"
date: 2009-05-16
forum: General Help
---

### Post by instantkarma on 2009-05-16
How can I do this?

I want to edit /etc/resolv.conf to change it from ```
nameserver 228.23.501.19
``` to ```
nameserver 75.199.286.4
```. I have to do so every so often (when I'm at home) and want to save myself editing it manually by $sudo nano /etc/resolv.conf.

Is there a way to do this?

Thanks.

---

### Post by zeex on 2009-05-16
> **instantkarma said:**
> How can I do this?

I want to edit /etc/resolv.conf to change it from ```
nameserver 212.33.511.29
``` to ```
nameserver 62.219.186.7
```. I have to do so every so often (when I'm at home) and want to save myself editing it manually by $sudo nano /etc/resolv.conf.

Is there a way to do this?

Thanks.

Hi, 

You can try a simple shell script. 

```
#!/bin/sh

echo "nameserver 62.219.186.7" > /etc/resolv.conf ;
```

save the script say nameserver.sh make it executable 

```
$ chmod +x nameserver.sh
```

you can run it after boot from terminal or you can add it to runlevel so that it updates resolv.conf when system boots up :)

[This link]("http://stringofthoughts.wordpress.com/2009/04/16/adding-removing-shell-scripts-ubuntu-810/") might help you in running script during boot

Good luck :)

---

### Post by kaibob on 2009-05-16
The following command--which can be placed in a shell script--will do what you want:

```
sudo sed -i 's/212.33.511.29/62.219.186.7/' /etc/resolv.conf
```

---

### Post by instantkarma on 2009-05-21
> **zeex said:**
> Hi, 

You can try a simple shell script. 

```
#!/bin/sh

echo "nameserver 62.219.186.7" > /etc/resolv.conf ;
```

save the script say nameserver.sh make it executable 

```
$ chmod +x nameserver.sh
```

you can run it after boot from terminal or you can add it to runlevel so that it updates resolv.conf when system boots up :)

[This link]("http://stringofthoughts.wordpress.com/2009/04/16/adding-removing-shell-scripts-ubuntu-810/") might help you in running script during boot

Good luck :)

Works like a charm. Thanks.

---

