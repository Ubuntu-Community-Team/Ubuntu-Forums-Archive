---
title: "Root access for program"
date: 2009-03-21
forum: General Help
---

### Post by Toady00 on 2009-03-21
I have installed xampp and netbeans. The default location of xampp is /opt/lampp so everytime I try to add a page to the /opt/lampp/htdocs/ directory I have to use the terminal with sudo. Also trying to make the project directory for netbeans in the xampp install wont work because netbeans doesn't have write access. Is there a way to make a linked shortcut on my desktop that isn't protected that would put the files in the proper /opt/lampp/ directory? Thanks

---

### Post by skydiver|goose on 2009-03-21
could you just chmod the directories so that you own them?

---

### Post by Toady00 on 2009-03-21
> **skydiver|goose said:**
> could you just chmod the directories so that you own them?

I tried to chown and chmod rwx and I still can't access it without using sudo.

---

### Post by jrela2000 on 2009-03-21
:popcorn:

Gonna wait for an answer for this as I am having trouble not having permission adding a joomla folder to /opt/lampp/htdocs

---

### Post by taurus on 2009-03-21
> **Toady00 said:**
> I tried to chown and chmod rwx and I still can't access it without using sudo.

Which directory?  Was it /opt/lampp only?

```
ls -la /opt/lampp
```

---

### Post by gali98 on 2009-03-21
You need to chmod recursively...
Something like
chmod -R 777 /opt/lampp/
should fix it... (You may need to change the 777 to fit your needs...)
Kory

---

### Post by gali98 on 2009-03-21
Woops.. didn't see the rest...
for the shortcut, just open the terminal and 
cd Desktop
ln -s /opt/lampp/ lampp

This would put a shortcut to the folder /opt/lampp on your desktop named lampp.
You could always also browse to the folder in nautilus and right click and create a link... then drag it to your desktop. Either way :)
Kory

---

