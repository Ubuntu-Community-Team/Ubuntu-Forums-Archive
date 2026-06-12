---
title: "Kubuntu on Ububtu"
date: 2017-01-19
forum: Desktop Environments
---

### Post by sparker781 on 2017-01-19
Trying to install the Kubuntu environment on my Ubuntu install with the following walkthru:

[http://www.tecmint.com/install-kde-plasma-5-in-linux/](http://www.tecmint.com/install-kde-plasma-5-in-linux/)

However when I try the steps in Terminal I am met with the following error:

$: command not found

Not sure what I am doing wrong.  Maybe I should switch to Kubuntu....LOL

Thanks

---

### Post by wildmanne39 on 2017-01-19
Please post which command is failing.

---

### Post by sparker781 on 2017-01-19
Sorry

Here Ya Go:

sudo add-apt-repository ppa:kubuntu-ppa/backports

---

### Post by wildmanne39 on 2017-01-19
Are you copying and pasting the command for accuracy? it worked perfect on my system.

Are you entering your user password after you put that command into the terminal? also you will not see your password as you type just hit enter to execute the command after you enter the password.

It will ask you if you want to add the ppa you will have to confirm that you do.

---

### Post by QIII on 2017-01-19
Could you post the commands you used and the results directly from the terminal?

---

### Post by martemarziano on 2017-01-26
There is a possibility to install Kubuntu DE via Synaptic. Just search for kubuntu desktop in the search box and you will be presented with the options available.

Another alternative is to go to Appgrid. If you don't have it pre-installed, you can install it following instructions here:

[http://www.omgubuntu.co.uk/2014/05/appgrid-ubuntu-software-centre-alternative](http://www.omgubuntu.co.uk/2014/05/appgrid-ubuntu-software-centre-alternative)


[FONT=inherit !important]
[/FONT]

---

### Post by thanuntu on 2017-02-01
Apparently, the add-apt-repository command is not preinstalled with Ubuntu 16.04 (go figure why...).

Try:

```
sudo apt-get install software-properties-common
```

---

