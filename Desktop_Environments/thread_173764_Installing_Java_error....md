---
title: "Installing Java error..."
date: 2006-05-10
forum: Desktop Environments
---

### Post by BayGuy27 on 2006-05-10
Note: I am good with windows/dos but a newbie to linux.

**Following the steps at [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) to install Java, running 'fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin' command came up with this:**

dave@linux:~$ fakeroot make-jpkg jre-1_5_0_06-linux-i586.bin
Creating temporary directory: /tmp/make-jpkg.XXXXQtIJwI
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk.sh
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)

No matching plugin was found.
Removing temporary directory: done

**I then ran 'sudo dpkg -i sun-j2re1.5_1.5.0+update06_i386.deb' and got the following result:**

dave@linux:~$ sudo dpkg -i sun-j2re1.5_1.5.0+update06_i386.deb
dpkg: error processing sun-j2re1.5_1.5.0+update06_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 sun-j2re1.5_1.5.0+update06_i386.deb

[B]I have also tried i586 as the site suggested for that last step and recieved the same message. The lead-up commands to installing java worked fine. Something tells me the fakeroot command is deleting this DEB file on me, but I am not sure. Anyone have any ideas? Thanks in advance,

Dave[/B]

---

### Post by Sef on 2006-05-10
Can think of two possiblities.

1) Did you add the repositories?  (Unlikely)

[https://wiki.ubuntu.com/AddingRepositoriesHowto]("https://wiki.ubuntu.com/AddingRepositoriesHowto")

2) Add build-essential

From the terminal (Applications > Accessories > Terminal)

sudo apt-get update

sudo apt-get install build-essential

---

### Post by BayGuy27 on 2006-05-10
**Yes, I replaced sources.list with this one ->**

# Example sources.list for Ubuntu hoary

## All officially supported packages, includingsecurity- and other updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## The source pacakges
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted

## All community supported packages, including security- and other updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates universe multiverse

## The source pacakges
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe multiverse
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates universe multiverse


## Backports - package version from a newer release build to work on the current
## no guarantees on working - not enabled by default 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports universe multiverse

## The source packages
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports universe multiverse

## hoary-extras - the most widely used source for packages not includded in Ubuntu
## no guarantees on working - not enabled by default

[B]I then ran the apt-get update command. It was the first thing I did, under advisement from a friend. Should I have a newer entry in this list perhaps?

Note that I installed mp3 capability fine. Thanks again,

Dave
[/B]

---

### Post by tedk on 2006-06-23
I also had some difficulty following the directions in Restricted formats.

This is how I have java working (but I would very much appreciate if someone could tell me why this is not what people are supposed to do).

I downloaded jdk-1_5_0_06-linux-i586.bin from Sun. It already had execute permissions. I made /usr/local/sunjava (because I didn't want it messing up any other Javas), put the file in that directory, executed it, accepted the license. It made a directory jdk1.5.0.06 in sunjava. This directory has a bin with a java and a javac. I put that bin in my path.

I can make a java file (like Hello.java) in my home, compile with javac and execute with java. Like javac Hello.java, then java Hello.

Now admittedly, I'm an old guy and this is how I did things years (more than I care to admit) ago.

Also, this is just a hello world test and I have yet to start up eclipse with this jdk (although I do have another machine working with eclipse and an older version of java installed this way). 

I have Breezy (I have friends who are struggling with Dapper and I need to get stuff done in the next couple of weeks so I'm holding off on Dapper). Also this new instance of Breezy is running under VMWare, but so far operates as well as for real.

But what bothers me is that I didn't follow the directions in Restricted Formats.  I mean I tried but I got errors. Like yours. So if someone is kind enough to point out why this method I used is wrong, I would be grateful.

 -Ted

---

