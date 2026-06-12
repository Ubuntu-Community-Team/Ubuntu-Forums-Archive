---
title: "Strange MySQL behavior"
date: 2009-05-20
forum: General Help
---

### Post by WhiteScars on 2009-05-20
Hello guys,

I have a strange mysql problem. I really dont have any idea about how to solve the issue. Oke here it is:

I have a text collection that is stored in mysql database. I have written an application (in java) that extracts words and writes the same database but in different table. There are ~2000 texts in my database. After this process i got ~800000 words and this operation takes like 10 min on my laptop. But when i deploy the same database and application to my desktop computer, this process takes like 2 days.:popcorn: This application uses a single thread to write the words to database. 

The algorithm is simple, i fetch the text and extract the words and in a for loop i sent insert queries to db. 

My laptop has the following configuration:

```
Lenovo SL 500
Dual Core P8600 CPU 2.4 Ghz. 
4 GB of RAM DDR 667
250 GB 5400 RPM disk
GeForce 9300M Video Card
Vista Ultimate 64-bit OS and MySQL is 64 bit also. 
```Operation takes 10 min in this computer

My Desktop:

```
AMD 6400+ X2 3.2 Ghz
2 GB of DDR 800 RAM
2 TB HDD 7200 RPM
GeForce 8600 GTS-O Video Card
Windows XP Pro SP3 32 bit MySQL installed. 
Vista Ultimate 64-Bit 64 bit MYSQL installed.
Ubuntu x32_64 64-Bit MySQL installed.
```Operation takes like 2 days in this computer in each OS

Another Computer:

```
Intel QuadCore CPU 2.4 Ghz
4GB of RAM
1 TB 7200 RPM disk
Windows XP Pro 32 bit mysql installed
```Operation takes like 2 days in this computer..

In Each OS same version mysql, JDK kit and JDBC drivers are installed. 
I have also used the same configuration file in each mysql. And I got the configuration file from my laptop. In ubuntu the result is also same. takes two days... :popcorn:

---

