---
title: "PATH question"
date: 2005-10-13
forum: Desktop Environments
---

### Post by dto on 2005-10-13
A couple of days ago I modified the $PATH in /etc/profile to include the Sun JDK that I had installed to /usr/local/. For example:

PATH=**/usr/local/jdk1.5.0_05/bin**:/usr/local/bin:/usr/local/sbin...

Last night I noticed that my $PATH variable didn't include the updated $PATH, though I had logged in/out a number of times since changing it. I looked at .bash_profile and saw that the PATH is changed to prepend /home/<user>/bin to the system PATH, but that still should be including the info specified in /etc/profile, shouldn't it? Is the system PATH actually defined elsewhere?

---

### Post by ngms27 on 2005-10-13
I think you have to do the PATH in the .bashrc file

It works for me.

JonnyT

---

