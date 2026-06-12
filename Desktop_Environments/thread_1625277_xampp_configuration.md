---
title: "xampp configuration"
date: 2010-11-18
forum: Desktop Environments
---

### Post by wenkep3 on 2010-11-18
I just successfully installed xampp on ubuntu.  I'm having trouble configuring it so I have localhost be pointed to another directory.  I've attempted to link htdocs to my portfolio folder but I'm receiving access denied, so I'm not sure I'm doing it correctly. Anyone have some input?

Thanks,
  Paul

---

### Post by asmoore82 on 2010-11-18
I would recommend avoiding xampp at all costs.

You receive better support, stability, and security if you stick with the official Ubuntu packages.

You can install the "LAMP" stack on ubuntu by simply running
```
sudo tasksel
```

Are you sure you really need a database server?
You can also install just the apache web server itself if that's all you need.

---

### Post by lovinglinux on 2010-11-19
> **asmoore82 said:**
> I would recommend avoiding xampp at all costs.

You receive better support, stability, and security if you stick with the official Ubuntu packages.

If you need a sever for developing and testing, but not for deploying, then xampp is an excellent alternative in my opinion. I always use it and I have no issues. Is easy to setup.

See [http://ubuntuforums.org/showthread.php?t=223410](http://ubuntuforums.org/showthread.php?t=223410)

I follow that tutorial every time I need to install and setup xampp. Works like a charm.

---

### Post by mcduck on 2010-11-19
> **asmoore82 said:**
> I would recommend avoiding xampp at all costs.

You receive better support, stability, and security if you stick with the official Ubuntu packages.

You can install the "LAMP" stack on ubuntu by simply running
```
sudo tasksel
```

Are you sure you really need a database server?
You can also install just the apache web server itself if that's all you need.

I agree with this.

Well, maybe not the "at all costs" but the basic point that using Ubuntu's own LAMP stack will give you better integration with the rest of the OS, automatic updates through the package management and quite likely better support as well.

There really is no reason to use any other LAMP stack with Ubuntu. There's nothing to gain from doing that, more of the opposite.

---

### Post by wenkep3 on 2010-11-19
Thanks for the quick responses.  My intentions are to install Apache, MySQL, and PHP for developmental purposes.  I decided to install LAMP and had no problem.  Everything is up and running but I have one last task, which is to switch the working directory to a portfolio folder.  I'm new to linux so I apologize for something which may be obvious.  I've come across two possible ways, changing the documentroot inside the 000-default file or linking to my portfolio folder.  Anyone have some input to which is better/how would I do this?

Thanks,
  Paul

---

### Post by mcduck on 2010-11-19
Both ways work fine for development purposes.

I usually just create a new site that has it's root in my home, and then use the "a2dissite"-command to disable the default site and "a2ensite" to enable the custom site. (Not a big difference to just editing the default site, but this leaves the default settings intact which makes it a bit smoother in my opinion.)

See the "virtual hosts"-section of the LAMP guide for detailed instructions:
[https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts]("https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts")

---

### Post by wenkep3 on 2010-11-19
Thanks for all the help.  I have everything up and running.  The switch from windows was a lot easier then expected.

Thanks again,
  Paul

---

