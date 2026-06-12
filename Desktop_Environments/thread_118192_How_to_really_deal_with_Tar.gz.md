---
title: "How to really deal with Tar.gz"
date: 2006-01-16
forum: Desktop Environments
---

### Post by zimele on 2006-01-16
Hey i need help with Installation of Tools
 
i've gotten the hang of Unziping the tool and placing it in a folder
the problem is after Unzipping i've been to other places and they offer me the support that i must go to the folder that was created after Unzipping and i must use this command **./configure** and after 
checking gcc....no
checking cc.....no
checking cl......no
configure error: no acceptable C compliler found in $path (what does this mean)

whenever i try to use the Make it says **Make command not found** please can you give me a step by step guide on how to tacle my problem

---

### Post by lutrafobic on 2006-01-16
Check your "Synaptic package manger" for packages named:   gcc4.0  (c compiler) and package called:  make

---

### Post by frodon on 2006-01-16
First if you wish to compile some softwares you need the package **build-essential**, it contains all the needed tools to compile a software (including gcc).
Install this package and tell us if you still have problems.

To install from source, in most of the case you have to untar the source first and then run these commands : ```
./configure
make
sudo make install
```
you can install checkinstall, it's a tool wich create a .deb when you compile from source and it also create all the needed debian entries so you're able to see your software in synaptic. To use it, replace "sudo make install" by : ```
sudo checkinstall -D
```

---

### Post by GeneralZod on 2006-01-16
[QUOTE=lutrafobic]Check your "Synaptic package manger" for packages named:   gcc4.0  (c compiler) and package called:  make[/QUOTE]

Easier to just do 

```

sudo apt-get install build-essential

```

To the OP - installing from source should really be used as an absolute last resort as it is a tricky business.  What package are you trying to install?

---

### Post by mcduck on 2006-01-16
Run 'sudo apt-get install build-essential checkinstall', and then follow the instructions hopefully provided in the tar.gz file, except when you are told to 'sudo make install' use 'sudo checkinstall' instead.

Buildessential provides all basic tools needed for compiling programs, and checkinstall will instead of just installing the program create a .deb package and install that. This way you can easily uninstall compiled programs with apt-get/synaptic.

Here's a ice guide about different ways of installing things in Ubuntu: [http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php")

---

### Post by zimele on 2006-01-17
My biggest problem with downloading software right now is that \

1. I have a ADSL connection that i use on My Windows Based Machine, (I wanna Stop Using XP) and it works fine right now i'm using PPPoE, I want to be able to use this connection on my Ubuntu Machine, but whenever i try to connect to a Website it fails, The strangest thing is that i am able to Traceroute and use all the other tools that are fopund within network tools i found out that i should use pppoeconf to configure the pppoe connection and it does the scan and comes back with this

:confused:   [B]Sorry, I scanned 2 interfaces, but the Access            &#9474;
        &#9474; Concentrator of your provider did not respond. Please    &#9474;
        &#9474; check your network and modem cables. Another reason      &#9474;
        &#9474; for the scan failure may also be another running pppoe   &#9474;
        &#9474; process which controls the modem.:confused:[/B]    

and everything is connected fine can you guys offer me assistance as i'm, in dyer need to learn about Ubuntu

---

### Post by Neo- on 2006-01-17
[QUOTE=zimele]Hey i need help with Installation of Tools
 
i've gotten the hang of Unziping the tool and placing it in a folder
the problem is after Unzipping i've been to other places and they offer me the support that i must go to the folder that was created after Unzipping and i must use this command **./configure** and after 
checking gcc....no
checking cc.....no
checking cl......no
configure error: no acceptable C compliler found in $path (what does this mean)

whenever i try to use the Make it says **Make command not found** please can you give me a step by step guide on how to tacle my problem[/QUOTE]
sudo apt-get install gcc g++ make
and you must type make in litle.. it doesnt work if you write Make..
it goes like:
./configure
make
make install

ALLWAYS read the install.txt or readme.txt.. theres usually step by step guide to installing!
Good Luck

---

### Post by zimele on 2006-01-17
I've downloaded the following tools off the Ubuntu software packages website cause as i said my Connection is not running under Ubuntu make_3.80.orig.tar.gz build essential_11.1.tar.gz and gcc-3.3_3.3.5.orig.tar.gz now my question is how do i go by installing these tools and making everything accessible.

---

### Post by GeneralZod on 2006-01-17
Did you run 

```

sudo apt-get install build-essential

```

as suggested? As I recall, it's actually contained on the CD so you shouldn't need an internet connection.  Also, getting your internet connection fixed should be the no.1 priority here, as then a lot of your program installation programs should go away.

---

### Post by zimele on 2006-01-17
Hey everybody thanks for all your help Much appreciated i've finally been able to sort out my I-net issue the problem was my page timeout this is what i did
# Read General Notes
# Applications -> Internet -> Firefox Web Browser
# Mozilla Firefox

Address Bar -> about:config

Filter: ->
network.dns.disableIPv6 -> true
network.http.pipelining -> true
network.http.pipelining.maxrequests -> 8
network.http.proxy.pipelining -> true

:smile: got this from the Ubuntu-Guide!:smile: 

:smile: Now for the next problem!:smile: 

:D Now i don't need to revert all the time:D

---

