---
title: "How to identify potential performance bottlenecks?"
date: 2014-09-18
forum: Desktop Environments
---

### Post by murray3 on 2014-09-18
Hey,

I'm using Ubuntu 14.04.1 LTS x64. I'm running this on the following configuration: Intel(R) Core(TM) i5-3450 CPU @ 3.10GHz with 9G RAM.

The problem is that the whole system is getting sluggish but most importantly my local dev environment is getting really, really slow. I'm using vagrant with virtual box and LAMP (Ubuntu as well) and the loading times between page loads on the local server are ridiculous. First I thought this was due to remote database connections but I've migrated the database locally and got only a marginal improvement. I don't think this is vagrant related as it was almost as bad before using Vagrant.

Chrome is using a lot of memory (6-7G) and I see *some* swapping, for example now I'm at total 6.2G of RAM used and 967MB of swap as per Monitor. I don't know if this is normal or not.

I understand that this is not an easy thing to diagnose over the Internet and also I'd like to know how to go about this in a general sense. So I'm looking for methods / utilities that would allow me to identify what the bottle neck is and further diagnose it.

I'm using atop and couldn't find anything standing out besides memory MEM and sometimes SWP that would sometimes look a bit like below but from what I've read online, it shouldn't be a concern (should it?)

```

SWP | tot     7.9G |  free    6.9G |              |               |              |              |               |              |              |               |              | vmcom  16.9G  | vmlim  12.2G |

```

Thanks,

EDIT: I forgot to mention that I had this install probably since 12.04 or 13 and have updated it each time without a clean install between versions, not really sure if it makes a difference.

---

### Post by lukeiamyourfather on 2014-09-18
Swap typically is not touched until the physical memory is completely full so at some point it sounds like the system is running out of physical memory since there's something in the swap. There are various utilities to track resource usage like top, htop, and a bunch of GUI applications.

---

### Post by tgalati4 on 2014-09-18
Install *htop* and monitor that in a terminal.  Look at your RAM and see how much is actually in use.  I'm not familiar with vagrant development, but it might be a RAM hog.

What is your host operating system?  It's possible that performance under virtualbox is not suitable for running vagrant web development.

```
sudo apt-get install htop
htop
free
```

Depending on the Agony Units involved, you might try kvm or Xen and run your development loops and see if performance improves.

---

