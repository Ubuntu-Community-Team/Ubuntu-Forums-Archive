---
title: "Question on using Cinelerra"
date: 2005-12-25
forum: General Help
---

### Post by faisalK on 2005-12-25
Hi,

trying to install Cinelerra for video editing. 
I am wondering if there is a line I can insirt into my soures.list file wich will make the cinelerra package and all its dependancies available through the package manager.

Cause I am still a newbie and not very versed in the unpacking and installation of software, but if some has an easy way...please suggest.

Thanks

---

### Post by sciurus on 2005-12-26
[This]("http://www.braindead.nu/pppblog/static.php?page=Gettingstarted") may or may not work.

deb [http://www.kiberpipa.org/~minmax/cinelerra/builds/sid/](http://www.kiberpipa.org/~minmax/cinelerra/builds/sid/) ./

or

deb [http://developer.skolelinux.no/~doudou/cinelerra](http://developer.skolelinux.no/~doudou/cinelerra) ./

---

### Post by faisalK on 2005-12-26
OK so it works I have cinelerra in the package manager. 
But now it is giving me all these dependancy issues...I am going around in circles. everytime I upgrade something it asks me to downagrade another or uninstall this or that. ...Libc6 or linux-kernel-headers........or libfaad or this or that.......does it end??

---

### Post by faisalK on 2005-12-27
Any ideas on the above anyone??

---

### Post by faisalK on 2005-12-28
please help woth above issue

---

### Post by rhipwell on 2006-01-03
I'm attempting to get this to work as well...I am using apt source: [http://www.kiberpipa.org/~gandalf/ubuntu/](http://www.kiberpipa.org/~gandalf/ubuntu/) ./ 

I am currently running into a dependancy issue with mjpegtools. I will update if I get this resolved...

---

### Post by TheOtherShoe on 2006-01-04
You can get the dependencies you need from Debian Sid. To do this, add the following line to your sources list:
```
deb ftp://ftp.nerim.net/debian-marillat/ sid main
```
This is in addition to the Cinelerra repository. After you install Cinelerra, I STRONGLY RECCOMEND that you remove the above line from your sources list and re-run apt-get update before you install any new software.

---

### Post by rhipwell on 2006-01-04
That did it! Thanks a bunch :D

---

