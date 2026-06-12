---
title: "hello"
date: 2007-06-27
forum: Dell  Ubuntu Support
---

### Post by a_kalash on 2007-06-27
I am using Linux (Ubuntu7.04 Desktop Edition) as an operating system and i did the installation of apache2.2.4 to create a web server and it's running but i want to know the steps to upload the files into my local web server??

In other words, akk the data <files> exicted in a directory on the desktop, how can i let the apache share the files from this directory so that i can see the files in my local web server?

Thanks

---

### Post by DoctorMO on 2007-06-27
you need to be able to set up the apache web server such that the directory you want your files to go in is in the configuration. you should also know where the default directories are; see:

```

/etc/apache2/apache2.conf

```

and

```

man apache2.conf
man apache2ctl

```

---

### Post by a_kalash on 2007-06-27
So can u list all the things that must be change it in the configuration file>> if you can give me an example about directory change that's will be great!!

---

