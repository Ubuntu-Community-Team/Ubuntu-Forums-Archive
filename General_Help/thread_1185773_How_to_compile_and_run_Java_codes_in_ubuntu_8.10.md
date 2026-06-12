---
title: "How to compile and run Java codes in ubuntu 8.10"
date: 2009-06-12
forum: General Help
---

### Post by NT. on 2009-06-12
Hello everyone.
I am new to linux and would like to know how to compile and run the java codes on linux.
Currently I have installed Ubuntu 8.10 so kindly help me to know what are the different packages required to perform the respective job and how can I continue my programming in java in linux.

---

### Post by michy99 on 2009-06-12
Basically, there ae two ways you can go. You can write your programs in a basic editor and compile them with command-line tools, or you can use a fancy IDE like Netbeans or Eclipse.

---

### Post by NT. on 2009-06-13
> **michy99 said:**
> Basically, there ae two ways you can go. You can write your programs in a basic editor and compile them with command-line tools, or you can use a fancy IDE like Netbeans or Eclipse.

Could you please tell me what are the different command line tools required to compile and run the java programs.

---

### Post by michy99 on 2009-06-13
First, if you have not installed the java development kit, you need to do that first.```
sudo apt-get install sun-java6-jdk
```Then you compile with the javac command. To learn more about it enter this in the terminal:```
man javac
```

---

