---
title: "Packages.gz  404 Not Found"
date: 2009-02-25
forum: General Help
---

### Post by MrBear on 2009-02-25
I just have ubuntu 8_04 installed on my work laptop with VXBOX  I can open yahoo.com and other internet sides.  However, when I tried to update with System->Admi->SoftwareSource->search and select the best server. I got the following error.



ailed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz](http://ubuntu-mirror.cs.colorado.edu/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I tried many different servers and I got the same thing.  I tried to search for solution and answers in this forum and I cannot find any.  I have spent 2-3 days scratching my head to figure this issue out without any success. Here is my source.list

$ cat /etc/apt/sources.list
## See sources.list(5) for more information, especialy
# Remember that you can only use http, ftp or file URIs
deb [http://ubuntu-mirror.cs.colorado.edu/ubuntu/](http://ubuntu-mirror.cs.colorado.edu/ubuntu/) hardy main universe restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main restricted
deb [http://ubuntu-mirror.cs.colorado.edu/ubuntu/](http://ubuntu-mirror.cs.colorado.edu/ubuntu/) hardy-updates universe main restricted
# CDROMs are managed through the apt-cdrom tool.

Can someone help me?

---

### Post by taurus on 2009-02-25
Try using the Main Server and see what happens.

---

### Post by MrBear on 2009-02-25
I did.  Same issue, though!

---

### Post by taurus on 2009-02-25
Does your network have anything to do with proxy?

---

### Post by MrBear on 2009-02-25
Yes.  I did setup the proxy as [http://autoproxy.mycompany.com:9090](http://autoproxy.mycompany.com:9090) as exactly I set in the internet browser.  The Internet browser works perfectly, though!

---

### Post by taurus on 2009-02-25
You need to go into synaptic and then the network tab and configure it for your proxy.

---

### Post by MrBear on 2009-02-25
Already, did!  System->References->NetworkProxy

---

### Post by MrBear on 2009-02-25
One thing to mention that when I selected the path to the missing package and placed it in the Internet browser, I was able to download the package.  So, what does this imply?

---

### Post by MrBear on 2009-02-25
Can anyone help me with this issue????????

---

### Post by taurus on 2009-02-25
> **MrBear said:**
> One thing to mention that when I selected the path to the missing package and placed it in the Internet browser, I was able to download the package.  So, what does this imply?

That implies that you have a proxy problem.

---

### Post by MrBear on 2009-02-26
Then how do I fix it? As I mentioned earlier, my proxy setting is: [http://autoproxy.mycomany.com:9090](http://autoproxy.mycomany.com:9090).  How do I fix it?

---

### Post by MrBear on 2009-02-26
I am stuck.  Can anyone please help?

---

