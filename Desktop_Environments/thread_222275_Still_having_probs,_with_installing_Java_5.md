---
title: "Still having probs, with installing Java 5"
date: 2006-07-24
forum: Desktop Environments
---

### Post by Luthy on 2006-07-24
I think ive tried everything! I am still having a hard time installing Java the newest one. can someone please explain this to me step by step? I am  new to Ubuntu, and am using Ubuntu Dapper  I am having sucha hard time with this. Im very sorry if im bothering anyone. I just want my Java installed! :confused: ](*,)

---

### Post by meng on 2006-07-24
What have you tried that hasn't worked? Did you try these instructions?
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by Luthy on 2006-07-24
this is what i get:
luthy@luthy-desktop:~$ sudo aptitude install sun-java5-jre
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "sun-java5-jre"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
luthy@luthy-desktop:~$ sudo apt-get install sun-java5-jre
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-jre

---

### Post by meng on 2006-07-24
Looks like you didn't enable multiverse repositories. It's mentioned in the link I posted above.

---

### Post by Kilz on 2006-07-24
[In case you dont know how to add the repositories.]("http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories")

---

### Post by Luthy on 2006-07-24
I did the multi verse thing :-) thank you guys so much for helping me. omg i felt like a total n00b asking all these q's. Love you guys!

---

### Post by littlespy on 2006-07-24
after you install you may need to do

sudo update-alternatives --config java

to use the correct instance

---

### Post by korny on 2006-07-24
> **littlespy said:**
> after you install you may need to do

sudo update-alternatives --config java

to use the correct instance

You probably want to do this for all the java-related binaries, not just java itself.

Alternatively, run "sudo update-java-alternatives" - this sets all the various binaries; it works for the full JDK, not sure if it works for the JRE though.
basically:
"update-java-alternatives -l" to list the options
"sudo update-java-alternatives -s java-1.5.0-sun" to choose the Sun one.

Some programs will also need you to set JAVA_HOME to point to /usr/lib/jvm/java-1.5.0-sun, which is where the java binaries (probably) are - but see how you go with the above settings first.

---

### Post by beameup on 2006-07-25
You could also have done this with a GUI. 

Go to Applications > Add/Remove > Internet > select "Sun Java Runtime"

---

