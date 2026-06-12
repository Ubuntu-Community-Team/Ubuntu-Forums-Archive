---
title: "Rox filter - Xubuntu"
date: 2008-03-19
forum: Desktop Effects &amp; Customization
---

### Post by namespace std on 2008-03-19
Thunar doesn't allow icons on the desktop (home folder, trash, etc), so I wanna install Rox filter. But where can I find it and how do I install it ? 

I have Xubuntu 6.06 LTS. 

Thanks in advance. :)

---

### Post by kerry_s on 2008-03-19
you must have desktop icons turned off.

for rox, open a terminal
sudo apt-get update
sudo apt-get install rox-filer
or
you can use the gui synaptic to find and install it.

---

### Post by namespace std on 2008-03-19
I can't find it in Synaptic. :(

Also:

```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package rox-filter

```

---

### Post by kerry_s on 2008-03-19
> **namespace std said:**
> I can't find it in Synaptic. :(

Also:

```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package rox-filter

```

it's **rox-filer**, there's no "t"

---

### Post by namespace std on 2008-03-19
```
~$ sudo apt-get install rox-filer
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package rox-filer
```

Could be something wrong with the repositories ?

---

### Post by p_quarles on 2008-03-19
No, it's definitely there:
[http://packages.ubuntu.com/dapper/rox-filer](http://packages.ubuntu.com/dapper/rox-filer)

You will need to make sure that the "universe" repository is enabled, though.

---

### Post by namespace std on 2008-03-19
These are the unchecked ones. Which one is the right one ? 

[[img]http://www.postimage.org/aV1n1mh9.jpg[/img]](http://www.postimage.org/image.php?v=aV1n1mh9)

---

### Post by p_quarles on 2008-03-19
That screenshot isn't very helpful, since it doesn't show all of the ones that are unchecked. 

Here's a command that will add the repository for you:
```
echo "deb http://archive.ubuntu.com/Ubuntu/ dapper universe" >> /etc/apt/sources.list
```
Then, update the repository cache:
```
sudo apt-get update
```
and you're set.

---

### Post by namespace std on 2008-03-19
```
~$ echo "deb http://archive.ubuntu.com/ubuntu/ dapper universe" >> /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied

```

---

### Post by p_quarles on 2008-03-19
Oh, sorry, writing to the sources.list file requires root permissions. Just put "sudo" at the beginning of the command.

---

### Post by namespace std on 2008-03-19
```
~$ sudo echo "deb http://archive.ubuntu.com/ubuntu/ dapper universe" >> /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
```


Same thing :(

What if I enable all the unchecked repositories ? Could that affect something ?

---

### Post by p_quarles on 2008-03-19
Odd. Anyway, just do this. Copy this line:
```
deb http://archive.ubuntu.com/ubuntu/ dapper universe
```
Run this:
```
sudo nano /etc/apt/sources.list
```
And paste that line in there.

---

### Post by namespace std on 2008-03-19
Ok, thanks, I added the line. Is it ok ? And how can I save it ?



>   GNU nano 1.3.10          File: /etc/apt/sources.list                Modified

**deb [B][http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) **dapper universe[/B]
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

---

### Post by p_quarles on 2008-03-19
Yes, it's good. Just hit the exit key chord (ctrl-x, I believe), and it will ask you want to save it.

---

### Post by namespace std on 2008-03-19
Thanks a lot. It worked perfectly. :)

One more question: How do I install the mp3 codecs in Xubuntu ? What are their names in Synaptic ?

---

