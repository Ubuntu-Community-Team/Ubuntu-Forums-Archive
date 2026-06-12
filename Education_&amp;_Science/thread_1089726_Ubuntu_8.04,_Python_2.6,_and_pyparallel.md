---
title: "Ubuntu 8.04, Python 2.6, and pyparallel"
date: 2009-03-07
forum: Education &amp; Science
---

### Post by Wild_Doogy on 2009-03-07
Hello, I am doing a project in school with a computer running Ubuntu 8.04 and python 2.5. we would like to control a circuit board via the computer's parallel port.
On windows with python and pyparallel installed typing
```
p = parallel.Parallel()
```
will let us write to the parallel port. In ubuntu however I am having some trouble. first I was getting an error about permission denied so I ran my script as sudo but now I get this error:

```
>>>p = parallel.Parallel()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.5/site-packages/parallel/parallelppdev.py", line 186, in __init__
    self._fd = os.open(self.device, os.O_RDWR)
OSError: [Errno 2] No such file or directory: '/dev/parport0'
```


In google I found that I should type:

```
sudo rmmod lp
sudo modprobe ppdev
```

But I still get the error about it not existing.

In other treads they say to use "/dev/lp0" or a range of other things in "/dev/" but that isn't working either.

My question is:

Is there something that needs to be modded in Ubuntu? and how?
And, how do you specify a port?  
p = parallel.Parallel("/dev/otherport")  or something different?

---

