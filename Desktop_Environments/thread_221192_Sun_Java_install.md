---
title: "Sun Java install?"
date: 2006-07-22
forum: Desktop Environments
---

### Post by Luthy on 2006-07-22
Cant seem to install Sun Java...how do i install it? I'm using ubuntu dapper.:-k

---

### Post by arkangel on 2006-07-22
do it  by Synaptics 

or
[http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)
 download what applies 

install as sudo  (if you have downloaded this file for instances  )  

# chmod +x     	jdk-1_5_0_07-nb-5_0-linux-ml.bin 
# sudo    jdk-1_5_0_07-nb-5_0-linux-ml.bin


then you can add  this line to your .bashrc  
#gedit  /home/MYUSER/.bashrc

export JAVA_HOME=/opt/jdk1.5.0_07/
export PATH=$PATH:/opt/jdk1.5.0_07/bin/

if you have installed in this  directories (this wil apply only for your account )

---

### Post by mlind on 2006-07-22
```

sudo aptitude install sun-java5-jre

```

You must enable **multiverse** repository for this.

---

### Post by Jeff250 on 2006-07-22
edit: Same as above. :)
sudo apt-get install sun-java5-jre for user tools
sudo apt-get install sun-java5-plugin for the mozilla plugin for Java applets
sudo apt-get install sun-java5-jdk for the developer kit (for compiling java classes, etc.)
Make sure that the multiverse repository is enabled first though.

---

### Post by Luthy on 2006-07-24
I think i did enable the multi-verse. but in case i was doing something stupid, can u please tell me how to do that?

---

### Post by mlind on 2006-07-24
> **Luthy said:**
> I think i did enable the multi-verse. but in case i was doing something stupid, can u please tell me how to do that?

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Luthy on 2006-07-24
It works. I didnt do the multiverse thing lol. but working fine now. i love you guys thank you! <3

---

