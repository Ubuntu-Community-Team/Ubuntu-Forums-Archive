---
title: "SUDO APT-GET INSTALL command taking wrong IP address"
date: 2009-12-28
forum: Desktop Environments
---

### Post by anirudhtomer on 2009-12-28
I am trying to install the JDK for my linux ubuntu 9.10 using the command

sudo apt-get install openjdk-6-jdk

it asks me for a my password & then starts installing & then hangs at 
0%[Connecting to 10.1.25.3] 

the 10.1.25.3 is the PROXY SERVER's IP address at ma office
I use a dial up connection at my home.

I HAVE TRIED EVERYTHING TO MAKE IT WORK but it hangs at 0% 

Please help me out

---

### Post by ubhi on 2009-12-28
This will help you surelly..

either you have to enter you network settings in synaptic
settings-> preference -> network

enter you proxy detail

or from command line use for apt-get

follow this

If you&#8217;re using command-line apt-get

Edit your /etc/bash.bashrc file as root.

Put these line at the end of your /etc/bash.bashrc file :

export http_proxy=http://username:password@proxyserver.net:port/
export ftp_proxy=http://username:password@proxyserver.netport/


or open mentioned page, this help u

[http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html](http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html)

---

### Post by anirudhtomer on 2009-12-28
thanks for the reply UBHI but at home I am not using a proxy connection

& this thing automatically takes the PROXY CONNECTION's IP (of my office 10.1.25.3)
but I want it to update my system properly at home without proxy

My ubuntu system is somehow remembering the PROXY address & trying to download from there

ONE SOLUTION I see is to somehow make the system take new IP of my home which is not PROXY ofcourse...

CAN U SUGGEST ME more solutions

---

### Post by erenay on 2012-11-27
please check  /etc/apt/apt.conf and if there is an entry like 

```
acquire::http:: proxy "http://<user>:<pass>@<ip>:<port>";
```

replace it with 

```
acquire::http:: proxy "false";
```

---

### Post by overdrank on 2012-11-27
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

