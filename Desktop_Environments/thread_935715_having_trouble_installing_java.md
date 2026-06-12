---
title: "having trouble installing java"
date: 2008-10-02
forum: Desktop Environments
---

### Post by meomike2000 on 2008-10-02
i have version 8.04.1 desktop. i am trying to install java for the firefox web browser. can anybody help me with that please. 

i have went to java and downloaded the self extracting file and tried to install it per the directions on java site.

tia.....

---

### Post by blingo on 2008-10-02
You can use the package manager.

Take a look at

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

I've chooesed to use the Sun version,
Note there's a special package for browser support in the package manager.

After

update-java-alternatives -l

I got to see both Sun and something else,
than I've uninstalled the other thing, so when I write 

update-java-alternatives -l
I only see:

java-6-sun 63 /usr/lib/jvm/java-6-sun

---

### Post by maruthi_s@infosys.com on 2008-10-02
[COLOR="Blue"]
Try installing using this command

sudo apt-get install sun-java6-jdk
[/COLOR]

---

### Post by joey-elijah on 2008-10-02
that helped me upgrade my java! thanks!

---

### Post by meomike2000 on 2008-10-03
thank you. i did it from the site instructions and i was able to get it to work.....

i did not know that there was more than one firefox directory and was puting the plugin in the wrong one.

but thank u for the shortcut. that will help in the future.

---

