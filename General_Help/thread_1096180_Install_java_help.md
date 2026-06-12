---
title: "Install java? help"
date: 2009-03-14
forum: General Help
---

### Post by blaker1994 on 2009-03-14
I downloaded this - jre-6u12-linux-i586.bin - and i have no idea how to make it work. please help, i have looked everywhere. I am trying to play runescape and it wont let me. any suggestiosn?

---

### Post by Rackstar on 2009-03-14
You should give it execute permission:

Type this in your terminal.
```

cd /path/to/file/
sudo chmod u+x jre-6u12-linux-i586.bin
```

Or right-click > permissions > allow executing (or something like that)

Then just running the file should install it.

You could try installing it through the synaptic package manager too.

---

### Post by blaker1994 on 2009-03-14
how do i install it through the synaptic package manager? I can find the file (I am on the synaptic package thing but i can find the jre file)

---

### Post by taurus on 2009-03-14
Does runescape require the latest java plugin?  Would the one from the repos good enough?

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by blaker1994 on 2009-03-14
taurus
 it says this > ubuntu@ubuntu:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


---

### Post by Rackstar on 2009-03-14
This is because your synaptic package manager is still open, close it and the run the command.

On the other hand normally in synaptic if you search for "sun-java6" you'll get the packages. Click the packages indicated above.

---

### Post by blaker1994 on 2009-03-14
now i get this "E: Couldn't find package sun-java6-bin"

But i have it?? help please?

---

### Post by blaker1994 on 2009-03-14
and when i made it an exc. file it tells me this " Could not display "/home/ubuntu/Desktop/jre-6u12-linux-i586.bin"."

---

### Post by taurus on 2009-03-14
Make sure you have enable both universe and multiverse in System -> Administration -> Software Sources.  Save it and close down Software Sources.  Then run those two commands from a terminal again.

---

