---
title: "I lost my &quot;Ubuntu' unity choice ..please help me to get it back."
date: 2012-03-06
forum: Desktop Environments
---

### Post by maizuddin35 on 2012-03-06
Hello everyone.
I hope you can help me with this one, problem because of my own mistakes.

based on the title above...I did something to the unity .
I try to install/upgrade to unity 5.0 from here [http://techhamlet.com/2012/01/unity-5-on-ubuntu-11-10/](http://techhamlet.com/2012/01/unity-5-on-ubuntu-11-10/)

after all installation completed,
I restarted my laptop.
and when I want to login,
there is no "Ubuntu" anymore.
There is only "Ubuntu 2D" and I don't like it at all.

I tried to install unity back 
but this appear :
```
utm@utm:~$ sudo apt-get install unity
[sudo] password for utm: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 unity : Depends: unity-common (= 4.24.0-0ubuntu2b1) but 5.4.0+bzr2052ubuntu0+654 is to be installed
         Depends: compiz-core-abiversion-20110828
E: Unable to correct problems, you have held broken packages.

```

some dependencies is missing I presume?

anyone here for the help :)
thanks in advanved

---

### Post by maizuddin35 on 2012-03-06
I think I found my way back to the old unity back 

```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:unity-team/staging
```

well, now waiting for the process to finish , hope it'll work :)

---

### Post by maizuddin35 on 2012-03-06
now I still can't install unity back. there is still only Ubuntu2D. 
```
utm@utm:~$ sudo apt-get install unity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 unity : Depends: compiz-core-abiversion-20110828
E: Unable to correct problems, you have held broken packages.
```

anyone help

---

