---
title: "cant't start administrative applications"
date: 2006-09-22
forum: Desktop Environments
---

### Post by krazed nun on 2006-09-22
Every time i start an administration application, such as the synaptic package mangaer, it closes before i can even put in my password. IT says:
'Opening administrative application' then it dissapears. Please help.

---

### Post by Delkster on 2006-09-22
If you open a terminal and enter, for example, the following command there, what happens? Does something, such as an error, get printed on the terminal?
```
gksudo synaptic
```

---

### Post by krazed nun on 2006-09-22
This is what i got:

```
kingluis@BLEEK:~$ gksudo synaptic
sudo: unable to lookup BLEEK via gethostbyname()

```

---

### Post by ayoli on 2006-09-22
reboot in recovery mode, then
edit:
```
sudo nano /etc/hosts
```
found this line:
```
127.0.0.1 localhost
```
change by this (assuming BLEEK is your hostname):
```
127.0.0.1 localhost BLEEK
```
ctrl + o and ctrl + x to save and exit, then reboot
sudo should work

---

### Post by krazed nun on 2006-09-22
i rebooted, but when i changed the things, and tried to save it, it said permission denied.

---

### Post by ayoli on 2006-09-22
> **krazed nun said:**
> i rebooted, but when i changed the things, and tried to save it, it said permission denied.
have reboot in recovery mode to edit ? i mean hit ESC at the very begining of boot to this menu (image bellow)  where you choose recovery mode.
[IMG]http://psychocats.net/ubuntu/images/sudo1.gif[/IMG]
then when in terminal edit with nano by type in at command prompt:
```
sudo nano /etc/hosts
```
and then as explained above.

edit: you should even not hav to sudo in recovery mode because you ll be logged as root. so
```
nano /etc/hosts
```

---

### Post by krazed nun on 2006-09-22
oh ok thanx. sorry. i am stupid.

---

### Post by krazed nun on 2006-09-23
thanks ayoli. really helped.:D

---

### Post by jdrott1 on 2006-09-27
i'm having the same problem. i've tried these solutions with no luck.  my computer doesn't allow me to sudo nano /etc/hosts in recovery mode.  my hostname is (none).

this is what message i'm getting:

jonathan@(none):~$ gksudo synaptic
sudo: unable to lookup (none) via gethostbyname()

---

### Post by lizajane999 on 2006-09-29
HELP!! 

I erased my host name!! 

So, when I do the above test I get:

lizajane999@:~$ gksudo synaptic
sudo: unable to lookup  via gethostbyname()

I tried working on the /etc/hosts file, but it looks like this:
127.0.0.1 localhost

And I don't know what to add, I tried putting just a space but it didn't work. What do I do now???

---

### Post by Delkster on 2006-10-04
> **lizajane999 said:**
> HELP!! 

I erased my host name!! 

So, when I do the above test I get:

lizajane999@:~$ gksudo synaptic
sudo: unable to lookup  via gethostbyname()

I tried working on the /etc/hosts file, but it looks like this:
127.0.0.1 localhost

And I don't know what to add, I tried putting just a space but it didn't work. What do I do now???

In case this still helps...

1) Boot in recovery mode as [instructed by ayoli](http://ubuntuforums.org/showpost.php?p=1532605&postcount=6) above

2) The hostname is set in the file /etc/hostname. You can check if there's anything by entering:
```
cat /etc/hostname
```
If there's no hostname set, you can set it by entering it in the aforementioned file. A straightforward way of doing that would be:
```
echo <hostname> > /etc/hostname
```
where you would replace <hostname> with your desired name.

3) Edit the /etc/hosts file by entering the following command:
```
nano /etc/hosts
```
As instructed earlier in this thread, add your hostname (as specified in /etc/hostname) to /etc/hosts so that the line beginning with `127.0.0.1' stands for example as follows:
```
127.0.0.1 localhost.localdomain localhost <hostname>
```
where, again, you should replace <hostname> with whatever you set it to.

4) Reboot, for example with the following command:
```
reboot
```

Please note that in recovery mode you should **not** use *sudo* or *gksudo* in front of commands -- you're already running with administrator privileges in recovery mode so you don't need sudo.

Edit: A couple of fixes for clarity

---

### Post by jimnz111 on 2006-11-07
I changed hosts file and it all stopped working as previous posts! Machine was 500km away so couldn't reboot easily... Luckily had already installed webmin and thought it was worth a try to see if I could alter things through webmin, and through this was able to get it running again! Thanks webmin :D

---

### Post by BadDolphin on 2006-12-16
I'm still battling the same thing.  There's definitely something other than those two files that's causing this.  Fixing them both does not fix this issue for me, at least, so there's definitely another factor here. 
I enabled the root account. Here's my latest settings (I've edited those two files in both recovery mode and simply as root, makes no difference:
# hostname
closetbox

# cat /etc/hostname
closetbox

# cat /etc/hosts
127.0.0.1       localhost
127.0.0.1       closetbox

HOWEVER...

# sudo foo
sudo: unable to lookup closetbox via gethostbyname()

Permissions:
# ls -al /etc/hostname
-rw-r--r-- 1 root root 10 2006-12-16 11:15 /etc/hostname
-rw-r--r-- 1 root root 31 2006-12-16 11:15 /etc/hosts

Having a root account enabled doesn't even help much since most apps in GNOME still can't be run.

---

### Post by Delkster on 2006-12-17
> **BadDolphin said:**
> Here's my latest settings
...
# cat /etc/hostname
closetbox

# cat /etc/hosts
127.0.0.1       localhost
127.0.0.1       closetbox


I don't know if it matters but the man page for the hosts file says:
For **each host a single line should be present** with the following information:
IP_address canonical_hostname [aliases...]

(emphasis mine)

Have you tried specifying both localhost and closetbox on the same line, for example this way:

```
127.0.0.1 localhost.localdomain localhost closetbox
```

---

