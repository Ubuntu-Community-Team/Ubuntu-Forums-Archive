---
title: "Ruuning commands at boot"
date: 2005-10-02
forum: Desktop Environments
---

### Post by ishtvan222 on 2005-10-02
Hi,

I am trying to set up a GiantDisc server ([www.giantdisc.org](www.giantdisc.org)) on ubuntu.
I need to run some commands to get it going.
What file should I put these commands in so they are run at boot?

<to be run as root>
sudo chmod a+rw /dev/ttyS0
sudo chmod a+rw /dev/dsp/

<to be run as user music>
gdd.pl --commmode 1 --serialdevice /dev/ttyS0

Thanks in advance.

---

### Post by adwait on 2005-10-02
Put it in a text file. Change it to make it executable by using
```
sudo chmod +x <filename>
```

Now put this file in the /etc/init.d/ directory using
```
sudo mv <filename> /etc/init.d/
```

Now open rcconf using
```
sudo rcconf
```

Find you filename in the list their and check the box against it, using the space bar. 

Done.

---

### Post by ishtvan222 on 2005-10-02
Wow, thanks alot. That was suprisingly easy.

I did that for the two commands that need to be run as root, but how can I run this as user music? ( music is a user to clarify. )

gdd.pl --commmode 1 --serialdevice /dev/ttyS0

Thanks

---

### Post by adwait on 2005-10-02
Umm....In the same place, same way......just change the command to
```
su music <command>
```

---

### Post by ishtvan222 on 2005-10-02
So I put in 

su music -c "/home/music/gdd.pl --commmode 1 --serialdevice /dev/ttyS0"

and it started gdd.pl fine, but now the problem is that gdd.pl refers to other .pl files that need to be run and it cannot run them using this way of starting it. Is there any other way to start gdd.pl so that gdd.pl can execute the other pl files in the bin directory?

Thanks

---

### Post by ishtvan222 on 2005-10-03
Thanks for all the help. I found out I needed to run gdd-wrapper.sh

Everything is working

---

### Post by Titus A Duxass on 2006-01-02
@ishtvan222

Sorry if this is off topic.

What install did you use to get GiantDisc working (i.e. - normal install, minimal install)?
Do you have a guide or can you remember how you did it.

Do you think it would be better to do a fresh install and make music as the original user?

Thanks
Titus

---

