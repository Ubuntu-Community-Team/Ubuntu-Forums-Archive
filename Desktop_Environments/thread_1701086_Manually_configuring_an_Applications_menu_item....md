---
title: "Manually configuring an Applications menu item..."
date: 2011-03-06
forum: Desktop Environments
---

### Post by karlkras on 2011-03-06
Seems a sophomoric question, but I've installed an application manually that requires execution via su to properly use.
I've tried to create a menu shortcut to start the application by using various commands:

sudo /usr/local/netbeans-6.9.1/bin/netbeans

and I also created a sh script that essentially attempts to execute the above command in a bash script so the command line states:

/home/myaccount/startnetbeans.sh
(startnetbeans.sh is defined as exectuable, also tried "sh "/home/myaccount/startnetbeans.sh"') and in all cases when this menu item is select it does absolutely nothing.

If I try any of these options from a terminal windows they work fine. Why the difference?

~Karl

---

### Post by realzippy on 2011-03-06
So if you type in terminal

```
sh "./startnetbeans.sh"
```

script works without password?


And welcome to the forum...

---

### Post by karlkras on 2011-03-06
> **realzippy said:**
> So if you type in terminal

```
sh "./startnetbeans.sh"
```script works without password?


Well, actually no. I'm challenged for my password as I'm forced to using sudo for the execution of the script. Do I need to pipe the password in?

> **realzippy said:**
> And welcome to the forum...

Thanks! Glad I found you. Nice to be back using Linux again.

---

### Post by grizzler on 2011-03-06
Have you tried 'graphical sudo' i.e.

**gksudo /usr/local/netbeans-6.9.1/bin/netbeans**

in the menu shortcut?

---

### Post by karlkras on 2011-03-06
> **grizzler said:**
> Have you tried 'graphical sudo' i.e.

**gksudo /usr/local/netbeans-6.9.1/bin/netbeans**

in the menu shortcut?

Hey, now there's an option. Until I figure out how to configure Netbeans to run properly without running as root this is a viable stopgap.
Thanks grizzler,
K2

---

### Post by realzippy on 2011-03-07
Sorry for stupid question,but have you run

```
chmod a+x
``` to your file to make it executable to all users?
I.e.:

```
sudo chmod a+x /usr/local/netbeans-6.9.1/bin/netbeans
```

---

### Post by spet on 2011-03-07
Since the version of Netbeans in the (Lucid and Maverick) repositories is 6.9, I suspect you could dissect the package identify the patches and workarounds used to make Netbeans run without root privileges.

There's a bug on launchpad for [packaging Netbeans 6.9.1]("https://bugs.launchpad.net/ubuntu/+source/netbeans/+bug/620744"). You could note, that it affects you.

---

