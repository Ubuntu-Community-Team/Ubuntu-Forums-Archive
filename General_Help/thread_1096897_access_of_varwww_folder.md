---
title: "access of /var/www folder"
date: 2009-03-15
forum: General Help
---

### Post by nitinkapoor25 on 2009-03-15
Hi all,

I have recently installed bluefish and create one web page but when I tried to save that file in  "/var/www/" folder. It is not allowing me to save and giving below error message.

"Could not write file"
/var/www/index1.html

Please help me to solve this problem.

Regards
Nitin

---

### Post by taurus on 2009-03-15
You can either change the permissions for /var/www so that everybody can write to it or try to edit /var/www/index1.html with root privilege.

```
gksudo bluefish /var/www/index1.html
```

---

### Post by nitinkapoor25 on 2009-03-15
Thanks buddy.

Now I am getting the message that you are unable to read file.
Can you help to solve this problem.

Regards
Nitin

---

### Post by taurus on 2009-03-15
What's the output of this command?

```
ls -la /var/www/index1.html
```
On the other hand, you can change permissions of /var/www so everybody can write to it.

```
sudo chmod -R 777 /var/www
ls -la /var/www
```

---

### Post by nitinkapoor25 on 2009-03-15
Thanks buddy
It's works.

---

