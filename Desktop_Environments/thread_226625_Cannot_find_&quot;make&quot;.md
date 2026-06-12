---
title: "Cannot find &quot;make&quot;"
date: 2006-07-31
forum: Desktop Environments
---

### Post by elbowgeek on 2006-07-31
I searched the forums and Google, but I haven't found reference to this problem.

I'm trying to install vmware Tools under Dapper which is running in a vmware Server instance on Windows XP.

When it comes to the compilation part of the install process, I get:

```
None of the pre-built vmhgfs modules for VMware Tools is suitable for your
running kernel.  Do you want this program to try to build the vmhgfs module for
your system (you need to have a C compiler installed on your system)? [yes]

Setup is unable to find the "make" program on your machine.  Please make sure
it is installed.  Do you want to specify the location of this program by hand?
[yes]
```

However I've installed gcc and all things around it from the package manager, and even rebooted, but "make" doesn't seem to be in the path.

Any help would be most appreciated.

Cheers

---

### Post by cstudent on 2006-07-31
Did you try installing the build-essential package?

---

### Post by elbowgeek on 2006-07-31
Not sure what the build-essential thingy is, but I'll take a look.  In Synaptic I presume.

Thanks

---

### Post by cstudent on 2006-07-31
> **elbowgeek said:**
> Not sure what the build-essential thingy is, but I'll take a look.  In Synaptic I presume.

Thanks

Yes do a search in Synaptic for build-essential or from a terminal enter:

```

sudo apt-get install build-essential

```

You will probably need to have the extra repositories enabled before you try. Turning those on can be done in Synaptic as well under the repositories menu.

---

### Post by elbowgeek on 2006-07-31
Ok, I found the build-essential and installed it which took me a bit further down the garden path, but I'm now stuck at:
```

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]
```

I've looked all over for some reference to this in the file system, but no luck.  Does this mean I have to download the source code, or is it on the Ubuntu install CD?  I couldn't find it on there either though.

Thanks again

---

### Post by VirtuAlex on 2006-07-31
you'll need to install appropriate linux headers and correct the path accordingly. what you're installing btw?
edit: ah, i see - vmware... anyway

---

### Post by elbowgeek on 2006-07-31
I'm attempting to install vmware Tools, having installed Dapper under vmware Server on an XP Pro machine.

I'll check to see if these header thingies are in Synaptec.

Cheers

---

### Post by VirtuAlex on 2006-07-31
> **elbowgeek said:**
> I'll check to see if these header thingies are in Synaptec.
They are. You need these matching your *user -r*

---

### Post by cstudent on 2006-07-31
Build essential should have installed the linux headers package. It looks like the header files are stored under /usr/include/linux/

[http://packages.ubuntu.com/dapper/devel/build-essential](http://packages.ubuntu.com/dapper/devel/build-essential)

---

### Post by cstudent on 2006-07-31
> **VirtuAlex said:**
> They are. You need these matching your *user -r*

I think that should be

```

uname -r

```

---

### Post by VirtuAlex on 2006-07-31
> **cstudent said:**
> I think that should be uname -r
My bad. Damn alzheimer's. Anyway he needs that matching the kernel. And the worst part - he'd need to do that again whth each kernel update.

---

### Post by elbowgeek on 2006-07-31
With apologies, I feel even more clueless now.  There is nothing in the directory which vmware expects to find it's headers.  And when pointing at the other directory indicated it says they are not the correct headers.

Thanks for everyone's patience.  Can anyone tell me exactly what needs to be installed in order to get these headers?  when I do a uname -r I get:

2.6.15-26-386

Cheers

---

### Post by VirtuAlex on 2006-07-31
> **elbowgeek said:**
> Can anyone tell me exactly what needs to be installed in order to get these headers?  when I do a uname -r I get:

2.6.15-26-386

Cheers
You had to install linux-headers-2.6.15-26-386. Instead of /usr/src/linux/include you have to use /usr/src/linux-headers-2.6.15-26-386/include or whatever it is on your machine. I can't tell for sure cause i'm on amd64. Check if it's there. Check your spelling and if nothing helps then search for vmware howto in this forums.

---

### Post by cstudent on 2006-07-31
Information on the package:

[http://packages.ubuntu.com/dapper/devel/linux-headers-2.6.15-26-386](http://packages.ubuntu.com/dapper/devel/linux-headers-2.6.15-26-386)

---

### Post by elbowgeek on 2006-07-31
Thanks everyone - finally found the headers in Synaptic, all is working fine.  Finally the mouse is more responsive as well.

Cheers

---

