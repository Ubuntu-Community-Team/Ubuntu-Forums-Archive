---
title: "Screen Resolution problem"
date: 2006-06-05
forum: Desktop Environments
---

### Post by abyssspecter on 2006-06-05
Well, recently i redid my computer. wiped my hard drive (which had breezy) and installed Dapper.

Now, I like Dapper and all, but I have been trying to fix my resolution, and followed several guides on here. But no progress. i edited my xorg.conf, and restarted, and till, it stays in the large resolution. if anyone can help, please do.

---

### Post by Chickenmonger on 2006-06-05
What graphics card do you have?
What is the 'large resolution', and what resolution do you want to change it to?
Does the Preferences, Screen Resolution menu option in Gnome work?

---

### Post by abyssspecter on 2006-06-05
[QUOTE=Chickenmonger]What graphics card do you have?
What is the 'large resolution', and what resolution do you want to change it to?
Does the Preferences, Screen Resolution menu option in Gnome work?[/QUOTE]

an ATI something. Default with the computer, as far as i know. 
The resolution is 640X480, which is far too large for me, maybe 1280x1024.
And all it does is show my 640 reso.

---

### Post by halfvolle melk on 2006-06-05
What output do you get from **lspci | grep ATI** and **fglrxinfo**?

---

### Post by abyssspecter on 2006-06-05
```
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]
```

and 

```
bash: fglrxinfo: command not found

```

---

### Post by halfvolle melk on 2006-06-05
edit: oops, sorry. The stuff below will probably not work since you have a Radeon 7500, not supported by the driver I suggested.

I think you need to install the ATi driver. Here's a good how-to:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

If method 1 doesn't work and you try method 2, don't use this 32bit installer:
[http://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.25.18-x86.run](http://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.25.18-x86.run)

make sure to use this one:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run)

---

### Post by abyssspecter on 2006-06-05
i found out what to do. i restarted X

---

