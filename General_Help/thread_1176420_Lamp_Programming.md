---
title: "Lamp Programming"
date: 2009-06-02
forum: General Help
---

### Post by rbueno on 2009-06-02
hi guys! how to program php in ubuntu? from creating folders, setting up smarty templates, creating php files & etc, up to complete system?

---

### Post by Mirge on 2009-06-02
[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies)

---

### Post by rbueno on 2009-06-02
i have already installed lamp successfully and it works. problem is how can i write my php script because i can't save using notepad++ in my root folder(var/www/mineleads)
"Error you have no permision to save":(

---

### Post by Tibuda on 2009-06-02
Didnt knew Notepad++ had a Linux version. Forget it, to enable your user to write to /var/www, run this:
```
sudo chown $USER:$USER /var/www
```

---

### Post by rbueno on 2009-06-02
Thanks Dan. i get it..
bdy i installed notepad++ using wine application, still windows version

---

### Post by prem1er on 2009-06-02
Is there are reason for using notepad++ in wine, instead of using a native linux text editor?

---

### Post by rbueno on 2009-06-02
it depends on programmer where he is comfortable.
im just used it because im still newbie in ubuntu 9.04

---

### Post by tgalati4 on 2009-06-02
You may need to change permissions to:

sudo chmod -R www-data:www-data /var/www/yourwebdirectory

Apache2 runs as www-data on ubuntu.  Otherwise apache2 won't have permission to execute php scripts.  .htacess should be root owner for security purposes.

Install sugarcrm and that will give you a year's worth of php to play with.

Notepad++?

---

### Post by Mirge on 2009-06-02
For an editor, I much prefer Geany, native on Linux. Lightweight and fast, plenty of options, syntax highlighting, lotta good stuff.

---

### Post by Tibuda on 2009-06-02
> **Mirge said:**
> For an editor, I much prefer Geany, native on Linux. Lightweight and fast, plenty of options, syntax highlighting, lotta good stuff.

I use Geany when I'm on Windows. I prefer Gedit, but it is only available for Linux.

---

### Post by rbueno on 2009-06-03
hell yes..
*      ** gksudo nautilus***
*then open documents using your favorite editor*
*thanks and best regards:popcorn:*

---

### Post by Tibuda on 2009-06-04
> **rbueno said:**
> hell yes..
*      ** gksudo nautilus***
*then open documents using your favorite editor*
*thanks and best regards:popcorn:*

Hey, why are you doing that? It is not safe to use sudo for daily work like this. If it is a Windows app under Wine, never. You better use **gksudo nautilus** to edit the /var/www folder permissions (Browse to /var, right-click www, and choose properties), and then use your editor without root privileges.

---

### Post by rbueno on 2009-06-04
Thanks dan :p

---

