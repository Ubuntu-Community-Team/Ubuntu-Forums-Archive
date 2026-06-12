---
title: "Need help with 8.10 server"
date: 2009-03-16
forum: General Help
---

### Post by Utemetsu on 2009-03-16
Alright, I'm a linux n00b. I admit it.

Regardless, I wanted to start my own home file server using a linux server build, the whole thing is a learning experience for me, so bear with me while I explain my problem.

Right, I've been using this guide here: [http://www.howtoforge.com/ubuntu-home-fileserver-p3](http://www.howtoforge.com/ubuntu-home-fileserver-p3)

Anyway, I want to connect to the server from my windows desktop: Using Putty -- which is where my problem lies. I cannot connect to the server with putty for a few reasons: A) I cannot check the external IP of my server, I don't know how and have been having problems doing so.

B) when I try to run ssh localhost I get, "ssh: connect to host localhost port 22: connection refused"

Is this a router problem? What is it? It's becoming tiresome constantly hitting the input switch on my monitor.

Any help would be greatly apprieciated.

---

### Post by jerome1232 on 2009-03-16
From what you've posted I'm assuming that...

Your Ubuntu Server is on your LAN (it's in the same building as the windows computer and they are both connected to the same router, whether via ethernet or wifi it doesn't matter)


If you run ssh localhost on the server and your getting connection refeused, sounds like you haven't installed an ssh server yet. So install one.

```
sudo apt-get install openssh-server
```

sudo -- run the following command with root user privilages
apt-get -- an easy to use package manager
install -- this tells apt-get we want to install a package
openssh-server -- this is a package that provides everything you need to run an ssh server

After installing openssh-server it should auto start, if you want to start/stop/restart that service this is what you do

```

sudo service ssh start
sudo service ssh stop
sudo service ssh restart
```

The address you need to ssh to is the internal ip address of the server, to find that just run this, it'll be the one that says "inet addr:" and isn't 127.0.0.1.

```
ifconfig | grep "inet addr"
```

I hope that helps.

---

### Post by Utemetsu on 2009-03-16
Right, did what you said. Here's the response:

"Package openssh-server is not available, but is refferred to by another package. This may mean that the package is missing, has be obseleted or is only available from another source. 

E: Package openssh-server has not installation candidate."


Could this be an internet connectivity issue? How do I know that the server is connected to the internet?


As to the setup, both machines are on a "sub-router"; that is to say that, they are connected to a router which is connected to another router which is connected to the internet.


Fun Fact: I chose to install the openssh thing during the install process as per the instructions of the aforementioned guide.

---

### Post by jerome1232 on 2009-03-17
Well if you can't ssh to localhost than the way you followed on that guide either failed or the server isn't started. I took a look at that guide and it was way to long for me to read through it to follow what steps you've taken.

What happens when you do a sudo apt-get update? If there are errors post them, if no errors retry installing openssh-server.

Use the "ifconfig" command to figure out your ip address, it's roughly the equivalent to the windows ipconfig command.

---

### Post by crokett on 2009-03-17
Step 6 in that guide you posted says to update your sources.list file and refresh the package list before installing openssh.  Did you do this?

---

### Post by Saghaulor on 2009-03-17
Also, I'm not sure if the server is set up with a static IP address, but I believe having one will help in the future so you're not trying to discover the address constantly. 

Correct me if I'm wrong.

Upon reviewing the tutorial linked above, the address is statically assigned.

---

### Post by Utemetsu on 2009-03-17
Let me start this off by saying thanks. I'm glad there are people willing to help me.

Right, I haven't gotten to step 6 yet in the guide. The author says that you should be able to connect to the ssh on the server [I'm assuming] Immediately upon the installation. I'll jump to 6, run the updates, then run the ssh installer again. Thanks again, guys.

---

### Post by Utemetsu on 2009-03-18
I hate to be such a bother, but I think the problem lies with internet connectivity.

I did a fresh install of the OS to be sure I didn't miss any steps in the install process.

I've changed all of my IPs to those listed in the tutorial:
(the file is /etc/network/interfaces)

```
#The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
 address 192.168.0.100
 netmask 255.255.255.0
 network 192.168.0.0
 broadcast 162.168.0.255
 gateway 192.168.0.1
```

I did indeed restart the network after these changes were made.

Next up was to edit the /etc/hosts ...

```
127.0.0.1     localhost.localdomain     localhost
192.168.0.100     server1.example.com     server1

# The following lines are desireable for IPv6 capable hosts

::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6allhosts#
```


Few questions:

1) My hostname is different than the one provided. Do I need to own the domain name (i.e., should my server be called 'Mummserver', do I need to own 'mummserver.com'?

2) What should my IP addresses be in the /interfaces file? I have no idea what these numbers mean in this context.

3) Running ifdown eth0 and ifup eth0 prints nothing to screen. Is this normal?



As to the updating of the linux distribution, I cannot as I am not connected to the internet on that machine!


Thanks again for all the help.

~Utemetsu

---

### Post by Utemetsu on 2009-03-19
I've made some changes:

I've registered mummserv.erikmumm.homelinux.com as a domain name using DynDNS -- I needed a hostname that was free so I took that one.


How do I connect to the internet on Intrepid Ibex 8.10? It's plugged in, and I've got (I hope) a static IP set up. (see earlier post); but, when I test it with ```
sudo apt-get update
```, It's not fetching Index files and thus not updating. Once I know it's online, I think my other problems will fall into place.


Thanks again all,
Utemetsu

---

### Post by Utemetsu on 2009-03-20
I fixed the problem. Thanks for the help, everyone!

---

