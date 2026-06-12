---
title: "Cant install php5-curl package"
date: 2009-03-03
forum: General Help
---

### Post by marknt15 on 2009-03-03
Hi all,

I have trouble installing curl in Ubuntu 8.04. It tells me there is a broken package. How do I fix it? thanks

I have read a similar [thread]("http://ubuntuforums.org/showthread.php?t=743999") but I don't understand this instruction:

1. paste the contents of your /etc/apt/sources.list and all files in /etc/apt/sources.list.d .
2. paste the output of
Code:

apt-cache policy php5-curl libcurl3 libc6

3. Have you installed any .deb files manually or used repositories not currently in your sources.list?


Here is the terminal result

```

sudo apt-get install php5-curl

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5-curl: Depends: php5-common (= 5.2.4-2ubuntu5) but 5.2.4-2ubuntu5.5 is to be installed
E: Broken packages

```

---

### Post by kilroy423 on 2009-03-03
1. paste the contents of your /etc/apt/sources.list and all files in /etc/apt/sources.list.d .

```
cat /etc/apt/sources
```
```
ls -lha /etc/apt/sources.list.d 
```

copy and paste those into the thread

2. paste the output of

```
apt-cache policy php5-curl libcurl3 libc6
```

type that into the console and paste the outcome

3. Have you installed any .deb files manually or used repositories not currently in your sources.list?

Have you installed anything without using apt-get?

---

### Post by marknt15 on 2009-03-03
Hi kilroy,

Step 1:
```

$ cat /etc/apt/sources
cat: /etc/apt/sources: No such file or directory

```

```

$ ls -lha /etc/apt/sources.list.d
total 60K
drwxr-xr-x 3 marknt15 root     4.0K 2009-03-04 11:01 .
drwxr-xr-x 4 marknt15 root     4.0K 2009-03-02 14:57 ..
drwxr-xr-x 2 marknt15 marknt15 4.0K 2009-03-04 11:01 apt.conf.d
-rw-r--r-- 1 marknt15 root      227 2009-03-02 14:57 medibuntu.list
-rw-r--r-- 1 marknt15 root      227 2009-03-02 14:57 medibuntu.list.save
-rw------- 1 marknt15 marknt15    0 2009-03-04 11:01 secring.gpg
-rw-r--r-- 1 marknt15 marknt15 2.5K 2009-03-04 11:01 sources.list
-rw-r--r-- 1 marknt15 marknt15 3.1K 2009-03-04 11:01 sources.list~
-rw-r--r-- 1 marknt15 marknt15 2.8K 2009-03-04 11:01 sources.list.save
-rw------- 1 marknt15 marknt15 1.2K 2009-03-04 11:01 trustdb.gpg
-rw-r--r-- 1 marknt15 marknt15 8.1K 2009-03-04 11:01 trusted.gpg
-rw-r--r-- 1 marknt15 marknt15 8.1K 2009-03-04 11:01 trusted.gpg~

```

This is the output of step 2:
```

$ apt-cache policy php5-curl libcurl3 libc6

php5-curl:
  Installed: (none)
  Candidate: 5.2.4-2ubuntu5
  Version table:
     5.2.4-2ubuntu5 0
        500 http://ph.archive.ubuntu.com hardy/main Packages
libcurl3:
  Installed: 7.18.0-1ubuntu2
  Candidate: 7.18.0-1ubuntu2
  Version table:
 *** 7.18.0-1ubuntu2 0
        500 http://ph.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
libc6:
  Installed: 2.7-10ubuntu4
  Candidate: 2.7-10ubuntu4
  Version table:
 *** 2.7-10ubuntu4 0
        100 /var/lib/dpkg/status
     2.7-10ubuntu3 0
        500 http://ph.archive.ubuntu.com hardy/main Packages


```

Step 3: I installed the php5-curl using the synaptic but it failed and gave me the error message : broken package.

I tried to install it again using the
```

sudo apt-get install php5-curl

```
but there is still the broken package error.

What am I doing wrong? :(

---

### Post by marknt15 on 2009-03-04
Hello, anybody? I am stuck with step 1. :(

Please help me. Thanks.

---

### Post by kilroy423 on 2009-03-11
Sorry, there was a typo on my response, should be

```
cat /etc/apt/sources.list
```

You can try 

```
sudo apt-get clean
```

and

```
sudo apt-get check
```

---

