---
title: "Web server installed into wrong place"
date: 2008-12-20
forum: Desktop Environments
---

### Post by andrewjlloyd on 2008-12-20
Hi all - hope you are all well, this is my first visite here.  

I am a web developer fed up with windows & am not even going to mention Vista.  I have installed Ubuntu & skinned it up with kiba dock & compiz- it looks cool..  

The problem i am having is when i try to set up a web server using the packet manager - Apache\php\mysql\phpmyadmin installs in the wrong place. So when i go into firefox and type localhost i get the message saying it works but i need the holl set up in anouther file called var or witch other else the file is called so i can load up phpmyadmin by simply typeing  [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)   i am convinced that the install from the packet manager has installed php/mysql & appache in the wrong directory is there anyway of moving the files to the write directory or how do i install a working webserver were it needs to go??

Take care...   Andy.:o

---

### Post by pytheas22 on 2008-12-20
What's the output of this command:
```

ls -lR /var/www
```

And what happens if you try to visit just 'localhost' in your web browser?  Do you get an error?

---

