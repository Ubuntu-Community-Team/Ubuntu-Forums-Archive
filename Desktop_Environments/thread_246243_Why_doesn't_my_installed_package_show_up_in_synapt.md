---
title: "Why doesn't my installed package show up in synaptic package manager?"
date: 2006-08-29
forum: Desktop Environments
---

### Post by johnusa on 2006-08-29
I am new to Linux.
I decided to install the apache server v2.2.3.  I downloaded the source, unpacked it, configured it, make it and make install.  I believe that "httpd" is the resulting executable.  Why doesn't httpd or httpd-2.2.3 show up in the  synaptic package manager when I select All packages?

---

### Post by randell6564 on 2006-08-29
> **johnusa said:**
> I am new to Linux.
I decided to install the apache server v2.2.3.  I downloaded the source, unpacked it, configured it, make it and make install.  I believe that "httpd" is the resulting executable.  Why doesn't httpd or httpd-2.2.3 show up in the  synaptic package manager when I select All packages?

What the hell are you talking about MAN?!  What distro are you using?

---

### Post by johnusa on 2006-08-29
Once again, I AM NEW TO LINUX!  Some advanced linux users may not be able to answer questions from newbies.

I installed Ubuntu 6.06 LTS - the Dapper Drake on my PC. I may be wrong but I am assuming that the synaptic package manager will list all the software packages loaded on my PC during the installation of Ubuntu.  I further assume, that if I download, configure, make and make install a software package, that it too will show up in the synaptic package manager.  My assumptions may be false, but that is what I assume.

I download the source for apache 2.2.3 and installed it on my PC via the ./configure, make and make install commands and expected it to show up in the synaptic package manager but could not find it in the list.

So far, what I have said should be easy to understand even if my assumptions are false.

Why is the apacke 2.2.3 not included in the synaptic package manager?

Please don't reply with what the hell are you talking about.  If I knew enough about what I was doing, then I probably wouldn't be posting this thread.

---

### Post by iTrendsNET on 2006-08-29
johnusa - It's been my experience that if I download a deb file and install with dpkg, use aptitude, apt, or synaptic to install, the package will show up in Synaptic.  A file that you download and install from source will not show up in synaptic.  So, this should be normal.  In conclusion, since this was a custom install from source, Synaptic most likely does not recognize it.  Hope this helps.

---

### Post by randell6564 on 2006-08-29
> **johnusa said:**
> Once again, I AM NEW TO LINUX!  Some advanced linux users may not be able to answer questions from newbies.

I installed Ubuntu 6.06 LTS - the Dapper Drake on my PC. I may be wrong but I am assuming that the synaptic package manager will list all the software packages loaded on my PC during the installation of Ubuntu.  I further assume, that if I download, configure, make and make install a software package, that it too will show up in the synaptic package manager.  My assumptions may be false, but that is what I assume.

I download the source for apache 2.2.3 and installed it on my PC via the ./configure, make and make install commands and expected it to show up in the synaptic package manager but could not find it in the list.

So far, what I have said should be easy to understand even if my assumptions are false.

Why is the apacke 2.2.3 not included in the synaptic package manager?

Please don't reply with what the hell are you talking about.  If I knew enough about what I was doing, then I probably wouldn't be posting this thread.

I'm sorry my friend.  I do not mean to insult you. As for  **"I further assume, that if I download, configure, make and make install a software package, that it too will show up in the synaptic package manager."**

Not if it is not supported.  I am certainly not a pro, but I do know that there are several packages that one can install that will not show up in the package manager!

---

### Post by mcduck on 2006-08-29
Synaptic only list installed .deb packages and packages available in Ubuntu repositories, not anything installed from source, autopackages or anything else.

Apache is available from Ubuntu repositories, so you can install it with Synaptic, no need to compile anything from source. Just find it with Synaptic and select for installation and Synaptic will handle all the work for you.

However if you need something that's not available so you need to compile it yourself you can use 'checkinstall' to make a deb package out of your compiled program and install that instead. So when you normally run 'sudo make install' you'd use 'sudo checkinstall' instead. You'll of course have to install checkinstall before you can do that, but it's in repositories too.

---

### Post by johnusa on 2006-08-29
Thank you **iTrendsNET **& **mcduck **for your replies.  Your comments were very helpful to a ubuntu newbie!

---

