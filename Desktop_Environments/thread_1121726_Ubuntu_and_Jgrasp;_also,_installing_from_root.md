---
title: "Ubuntu and Jgrasp; also, installing from root"
date: 2009-04-10
forum: Desktop Environments
---

### Post by FailureToLoad on 2009-04-10
Hello, I've recently intalled eeebuntu (wasn't available on prefix drop-down) and am trying to get jgrasp to work on it. 

The error I get when compiling my code is 
    "cannot find javac"

It appears as though the eeebuntu distro has the JDK installed so I'm not sure why it can't find the compiler. How would I go about finding it and adding it to the path?

Its also occurred to me to simple be sure of things and install the JRE, just in case. The SUN site gives me a .bin file but its instructions for installing from the root terminal don't seem to work for ubuntu. Any suggestions on this front?

---

### Post by taurus on 2009-04-10
You want to install the sun-java6-jdk version, not the openJDK.

```
sudo apt-get update
sudo apt-get install sun-java6-jdk
```

---

### Post by FailureToLoad on 2009-04-10
> **taurus said:**
> You want to install the sun-java6-jdk version, not the openJDK.

```
sudo apt-get update
sudo apt-get install sun-java6-jdk
```

You're a lifesaver, I'm SOL for a wireless connection right now (posting from work terminal) but I will try this first thing once home.

---

### Post by Vinnie V on 2009-05-19
New to Ubunbtu, and new to Java Programming...
I just followed the instructions to update my JDK, but it looks like it only updates to update 10. The sun website shows that they are up to update 13. Is there a large difference between these? Also, how exactly do I accept the user agreement? It says <OK> at the bottom, but hitting Enter or clicking on it do not accept. Is there something that I am missing?

Thanks!

---

### Post by taurus on 2009-05-19
> **Vinnie V said:**
> New to Ubunbtu, and new to Java Programming...
I just followed the instructions to update my JDK, but it looks like it only updates to update 10. The sun website shows that they are up to update 13. Is there a large difference between these? Also, how exactly do I accept the user agreement? It says <OK> at the bottom, but hitting Enter or clicking on it do not accept. Is there something that I am missing?

Thanks!

Use the Tab key to highlight the <OK> and Return to accept it.

---

### Post by Vinnie V on 2009-05-19
> **taurus said:**
> Use the Tab key to highlight the <OK> and Return to accept it.

Thank you! 

I ended up using the lower tech approach, and went into synaptic to check on the status of my update. It told me that I had a broken package, so I initiated the JDK installation from there, and got a screen with a click-able OK. Turns out that my original issue was that I had JRE installed, and it was interfering. Once I removed it, the JDK worked appropriately.

Thanks for the help!

---

