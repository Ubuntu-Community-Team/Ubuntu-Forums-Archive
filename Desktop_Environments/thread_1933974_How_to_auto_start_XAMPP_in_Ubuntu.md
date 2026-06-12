---
title: "How to auto start XAMPP in Ubuntu?"
date: 2012-03-01
forum: Desktop Environments
---

### Post by thesufi on 2012-03-01
I am trying to automatically start XAMPP for Linux (LAMPP) after Ubuntu reboot/boot. I have tried lots of solutions available in internet. None worked for me.
Could someone help me please? I am using Ubuntu 11.10

---

### Post by namibian on 2012-03-28
I was struggling with the same thing. This was very useful [http://menatronics.blogspot.com/2012/01/lampp-installation-to-securing-your.html?showComment=1332943543823#c8137946384736629784](http://menatronics.blogspot.com/2012/01/lampp-installation-to-securing-your.html?showComment=1332943543823#c8137946384736629784)
but didn't work for me because the permissions on /etc/init.d/lampp

Here is the complete proccess that worked for me (Ubuntu 11.10, Xampp 1.7.7)

1. Create a script in init.d called lampp
**sudo gedit /etc/init.d/lampp**

2. Paste this code on the script and save
```

#!/bin/bash
/opt/lampp/lampp start

```

3. Give -x permissions to the file
**sudo chmod +x /etc/init.d/lampp**

4. Use update-rc.d to install init scripts to all runlevel by typing 
** sudo update-rc.d lampp defaults **

---

### Post by swiftoid on 2012-04-29
Sorry to dig up an old thread, but I needed to do this too and thought I'd add to it for anyone else who stumbles across it. That file should really be:

file: /etc/init.d/lampp
```
#!/bin/bash
/opt/lampp/lampp $1
```


That way you can run:
```
service lampp stop
``` 
or similar to control it.

You may also find it helpful on ubuntu to add a umask definition in that file if you have set up appache with it's own user/group. E.g.
```
#!/bin/bash
umask 002
/opt/lampp/lampp $1
```

---

