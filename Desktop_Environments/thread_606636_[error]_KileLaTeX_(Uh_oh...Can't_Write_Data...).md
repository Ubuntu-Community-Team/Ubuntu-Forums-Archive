---
title: "[error] Kile/LaTeX (Uh oh...Can't Write Data...)"
date: 2007-11-08
forum: Desktop Environments
---

### Post by KillerJoe on 2007-11-08
Hi people,

I have some problems with my Kile (LaTeX editor).

I am running Ubuntu 6.06 LTS (@ university) and have now encountered some problems with it.

From time to time (kinda random) Kile freezes and doesn't save the last additions to the text written. I have not been able to pinpoint the cause yet, but am still working on that.

Now when starting up Kile also displays some error message:

```
<user>@<machine>:~/<dir>$ kile
kbuildsycoca running...
Uh oh.. can't write data..
```

:confused:

I don't know what to do with that error - any suggestions?

Oh yes: I am running Kile 1.8.1 (using KDE 3.5.2).

As I am writing my master's thesis I REALLY like them changes to get saved ;)

I am looking forward to hearing from you!

Cheers,
KJ

---

### Post by eldragon on 2007-11-08
how are the following?

[LIST]
[*]disk space: is it full?
[*]folder write permissions
[*]/tmp write permissions
[/LIST]

these are the ones i can think of..

if you are so hard pressed on your thesis, i suggest switching editors just to be safe.
i use vim for my latex editing :)

---

### Post by KillerJoe on 2007-11-08
> **eldragon said:**
> 
[LIST]
[*]disk space: is it full?
[/LIST]

No: ```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             5,8G  3,7G  1,9G  67% /
varrun                248M  104K  248M   1% /var/run
varlock               248M  4,0K  248M   1% /var/lock
udev                  248M  100K  248M   1% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   19M  230M   8% /lib/modules/2.6.15-29-386/volatile
/dev/sda6             104G   58G   41G  60% /home
```
> **eldragon said:**
> 
[LIST]
[*]folder write permissions
[/LIST]

It's my own folder and I'm also administrator on the machine.
> **eldragon said:**
> 
[LIST]
[*]/tmp write permissions
[/LIST]

```
drwxrwxrwt  12 root root 16384 2007-11-08 12:14 tmp
```
> **eldragon said:**
> 
if you are so hard pressed on your thesis, i suggest switching editors just to be safe.
i use vim for my latex editing :)
Yeah I know - but Kile is just so convenient to use - I could also use Emacs or VIM or PICO, but I'd really like to use Kile (and can't see why it shouldn't work ;))

Thanks for your reply, but unfortunately it didn't help me a lot.

Any other good ideas?

---

### Post by lexxonnet on 2007-11-08
Hmm... it definitely sounds like a permissions issue. Are you running AS root? or are you a user with sudo privileges?

Also, check the permissions of "~/.kde", since thats where kde config settings are stored

---

### Post by KillerJoe on 2007-11-13
Hi lexxonnet,

I am not running AS root - I'm running as a user with administrator privileges. (also sudo privileges).

The permissions of ~/.kde are as following:
```
<user>@<machine>:/$ ll ~/.kde
total 4
lrwxrwxrwx 1 <user> users   25 2007-06-08 15:06 cache-<machine> -> /var/tmp/kdecache-<user>
drwx------ 8 <user> users 4096 2007-06-08 15:06 share
lrwxrwxrwx 1 <user> users   20 2007-06-08 15:06 socket-<machine> -> /tmp/ksocket-<user>
lrwxrwxrwx 1 <user> users   16 2007-06-08 15:06 tmp-<machine> -> /tmp/kde-<user>
```

So it seems as if these folders are in fact mine (as I am <user> ;))

---

### Post by KillerJoe on 2007-11-23
*bump*

Any other good ideas? :)

---

