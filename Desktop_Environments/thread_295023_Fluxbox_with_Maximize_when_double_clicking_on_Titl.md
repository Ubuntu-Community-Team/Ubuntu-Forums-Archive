---
title: "Fluxbox with Maximize when double clicking on Title bar : Has someone made a deb"
date: 2006-11-07
forum: Desktop Environments
---

### Post by patrick295767 on 2006-11-07
Fluxbox with maximize when double clicking on Windows Title Bar : Has someone made a deb ?

I am actually lazy to make the changes into the source, configure make checkinstall...
By chance, has someone made the little work already?
(please indicate too lsb_release -a it concerns)

HowTo Link: [http://fluxbox-wiki.org/index.php/Howto_Make_dblclick_titlebar_maximize](http://fluxbox-wiki.org/index.php/Howto_Make_dblclick_titlebar_maximize)

Thank you,

Greetings;

Patrick

---

### Post by patrick295767 on 2006-11-12
Ok;
 
I could not wait for someone. 
I made the deb with the double clicking on Title bar.

You can download the deb there: [here]("http://patrick295767.sitesled.com/miniram/dblclickfluxbox_1.0rc2-1_i386.deb")

then,  

```
rm -rf  /usr/bin/fluxbox   #to make sure you have it right
dpkg -i dblclickfluxbox_1.0rc2-1_i386.deb
cp -a /usr/local/share/fluxbox/ /usr/share/
ln -s /usr/local/bin/fluxbox /usr/bin/fluxbox
cd /tmp
wget http://patrick295767.sitesled.com/miniram/startfluxbox 
mv /tmp/startfluxbox   /usr/bin/startfluxbox
chmod uog=rx  /usr/bin/startfluxbox

```

and create: /usr/share/xsessions/dcfluxbox.desktop 
```
[Desktop Entry]
Encoding=UTF-8
Name=Fluxbox
Comment=Highly configurable and low resource X11 Window manager
Exec=/usr/bin/startfluxbox
Terminal=False
TryExec=/usr/bin/startfluxbox
Type=Application

[Window Manager]
SessionManaged=true

```

Enjoy !!

Double click on the title bar, makes the window un-/ maximized

:KS 
 
--
I have still a small prob with the styles.

---------
my lsb_release:
[I]lsb_release -a
Distributor ID: Ubuntu
Description:    Ubuntu 6.06.1 LTS
Release:        6.06
Codename:       dapper[/I]

---

