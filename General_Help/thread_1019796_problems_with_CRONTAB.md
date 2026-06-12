---
title: "problems with CRONTAB"
date: 2008-12-23
forum: General Help
---

### Post by arunprasad13 on 2008-12-23
I am using ubuntu edgy 6.10, i want to schedule a particular program to run on a particular time...i learnt that CRONTAB command could be used to do the same,but i dont know how to configure it for edgy ,besides i m interested in GUI which would help me schedule my programs..i humbly solicit  your guidance on this...
 :confused:

---

### Post by andrew.46 on 2008-12-23
Hi,

I am not aware of a gui interface for crontab but I have been wrong before :-). The good news is that there is a superb exposition on cron and crontab in the Ubuntu Community documentation I would highly recommend that you read it through:

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

Hope this has helped you?

Andrew

---

### Post by arunprasad13 on 2008-12-24
i tried this

$crontab -e 

01 02 * * * root /opt/azureus/azureus 

cntl+o
cntl+x

but it still doesn work..

---

### Post by Titan8990 on 2008-12-24
In crontabs the path needs to start with /.

---

### Post by andrew.46 on 2008-12-24
Hi arunprasad,

> **arunprasad13 said:**
> i tried this

```
$crontab -e 

01 02 * * * root /opt/azureus/azureus 
```

You have created a mix of anacron and crontab syntax here :-). I am not the one to ask about anacron as I do not use it but crontab is pretty straightforward. Do you want to open azureus as superuser? To do this you must use sudo:

```
sudo crontab -e
```

and then place your command line something like:

```
01 02 * * * /opt/azureus/azureus
```

without adding *root* in there. If you wish to open azureus as a normal user simply duplicate this procedure *without* using sudo.

I am not sure about these:

```
cntl+o
cntl+x
```

Are these commands for your editor? Anyway don't forget to check your own crontab and the superuser crontab when you are finished by using:

```
crontab -l
sudo crontab -l
```

All the very best,

 Andrew

---

### Post by dcstar on 2008-12-24
> **arunprasad13 said:**
> i tried this

$crontab -e 

01 02 * * * root /opt/azureus/azureus 

cntl+o
cntl+x

but it still doesn work..

If this is a GUI application then it needs to be told where to output. Do a forum search as this issue has many posts.

---

### Post by andrew.46 on 2008-12-24
Hi dcstar,

> **dcstar said:**
> If this is a GUI application then it needs to be told where to output.

Thanks for that, I was not aware of the extra steps involved with launching a gui program. Some details [here]("http://ubuntuforums.org/showthread.php?t=185993").

Thanks again,

Andrew

---

### Post by arunprasad13 on 2008-12-25
i tried it..

i have copied this from the terminal

arun@arun-desktop:~$ sudo crontab -l
# m h  dom mon dow   command
26 14 * * * /opt/azureus/azureus
arun@arun-desktop:~$ 

but the application doesn run in GUI at at...the screen is as black as a white sheet..nothing happens at 2:26 pm...

do i have to enable sth in order to run crontab...or is that crontab is not supported in edgy

---

### Post by andrew.46 on 2008-12-25
Hi arunprasad,

> **arunprasad13 said:**
> i tried it..

```
arun@arun-desktop:~$ sudo crontab -l
# m h  dom mon dow   command
26 14 * * * /opt/azureus/azureus
arun@arun-desktop:~$ 
```

but the application doesn run in GUI at at...the screen is as black as a white sheet..nothing happens at 2:26 pm...

There is the issue that dcstar has mentioned in a previous post, of which I was unaware, that an extra step is involved when launching a gui program from crontab. I have not tested this but I gather it involves syntax similar to:

```
26 14 * * * export DISPLAY=:0 && /opt/azureus/azureus
```

Some discussion on this can be seen [here]("http://ubuntuforums.org/showthread.php?t=185993"). I will admit to only having launched commandline applications from crontab before and I was unaware of this extra step until dcstar pointed it out.

All the best,

Andrew

---

### Post by arunprasad13 on 2008-12-27
thank you..i have osted my doubt in that forum ..lets see if they acn help..can u tell me how to run a simple CLI command using crontab 

say for example ps -aux or clear

---

