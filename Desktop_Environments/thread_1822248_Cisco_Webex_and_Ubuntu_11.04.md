---
title: "Cisco Webex and Ubuntu 11.04"
date: 2011-08-10
forum: Desktop Environments
---

### Post by metallica1973 on 2011-08-10
I had my laptop working great with Ubuntu 10.04 and decided to go with the latest and greatest and upgrade to 11.04. After doing that I cannot use Cisco Webex. I can create a session, I pass the control to the user as presenter and when they share they desktop, my screens just blinks. This is what is showing up in my logs after the screen blinks and I cannot see the remote desktop:

```

Aug 10 10:33:44 pegasus kernel: [ 3609.752592] atasjni[9044]: segfault at 3e84 ip b648db8d sp bfc2c0d8 error 4 in atascli.so[b63f4000+11e000]

```

I have installed the lastest jdk from java.com and create all the symbolic links and read several posts. 
Could it be this unity garbage?

---

### Post by mgieparda on 2011-08-29
I have exactly the same when somebody starts sharing the desktop. I see only blink and this error in syslog.
Fresh installation of 11.04 with all latest updates and java from sun.


atasjni[10445]: segfault at 3e84 ip b64d7b8d sp bfa7b758 error 4 in atascli.so[b643e000+11e000]

---

### Post by SagarDoke on 2011-09-07
I also facing the same issue.
I'm using Dell Latitude E6420 laptop.
Using Sun Java 6 Plugins.

Thanks,
Sagar

---

### Post by jamesgthang on 2011-09-07
I am also seeing this very same problem and I am on the 11.04 Ubuntu Classic mode.  All I get is a quick flash of the green background and the same segfault message in /var/log/syslog

I am able to share my desktop and control with others, but cannot view when others are sharing with me.

I tried removing webex (rm -rf ~/.webex) re-installing but that didn't work.  Removing and re-installing java via synaptic did not help either.

Any other ideas?

---

### Post by jamesgthang on 2011-09-07
Also tried editing the ~/.webex/client.cfg file to point to other java versions with no success:[INDENT]JVMLocation=/home/Downloads/jre1.7.0/bin
[/INDENT]Java versions I tried:[INDENT]java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)

java version "1.6.0_27"
Java(TM) SE Runtime Environment (build 1.6.0_27-b07)

java version "1.7.0"
Java(TM) SE Runtime Environment (build 1.7.0-b147)
[/INDENT]

---

### Post by metallica1973 on 2011-09-15
I created a ticket with Cisco and this is there response 

Hello Metallica1973,

Thank you for contacting Cisco WebEx Technical Support.

I am sorry to hear that you are experiencing issues with viewing the user's shared desktop.

I understand the difficulty experienced and apologize for the inconvenience caused.

The reason for the issue could be due to compatibility issue.

Currently, Ubuntu 11.04 OS version is yet to be supported for WebEx services. 

We apologize for this inconvenience.

WebEx supports the following Linux distributions: 

Ubuntu 10x, Red Hat 5, 6, Open SuSE 11.2, 11.3, Fedora 13, 14 (all 32-bit)
Kernel: 2.6 or later 
X Lib: X11R6 or later compatible 
 C++ Lib: libstdc++ 6 
Desktop Environment: XFce 4.0 or later, KDE, Ximian, Gnome 
GDK/GTK+ version: 2.0 or later 
Glib: 2.0 or later 
Sun Java 1.5 or later 

Hence, please use a supported Ubuntu version and check if you able to view the user's shared desktop properly during the meeting.

If you need any further clarifications in this regard, please reply and I will be glad to assist you.

For additional assistance, you may also log on to our extensive knowledgebase with thousands of solutions available at [http://kb.webex.com](http://kb.webex.com)

I look forward to assisting you further.

Regards,
Nash,
Cisco WebEx Technical Support

---

### Post by jamesgthang on 2011-09-15
metallica, thanks for the update.  I'm downloading 10.10, will install into VirtualBox and check to see if WebEx is still working like they say.  I remember it working fine for me in 10.10, but that was a while ago.

If that runs fine under the virtual machine, then we should try to pinpoint the differences, such as Java version etc and see if we can get it going in 11.04.

---

### Post by metallica1973 on 2011-09-15
Great Point. Good Luck. I have a feeling that is has something to do with Unity and something on the backend.

---

### Post by Newbify2 on 2011-09-30
> **SagarDoke said:**
> I also facing the same issue.
I'm using Dell Latitude E6420 laptop.
Using Sun Java 6 Plugins.

Thanks,
Sagar

I'm running the same configuration (with 11.04) and I am able to share and view shared desktops by running firefox as root to kick off the webex.

---

### Post by Yanti on 2011-10-03
Hi Newbify2!

I tried to run Firefox with sudo and that really did the trick! Webex seems to work with 11.04 (I can see presentations now).

(And gksudo should be preferred instead of sudo in this case)

Apparently this problem is related to user privileges somehow, perhaps Firefox, Java or Webex client etc. etc. I try to dig this further. 

Thanks!
Yanti

---

### Post by chelusly on 2011-10-03
Did anyone try enabling Java through the Firefox Java Plugin via home directory?

Firefox Java Plugin:

mkdir ~/.mozilla/plugins
cd ~/.mozilla/plugins
ln -s /usr/lib/jvm/java-6-sun-1.6.0.26/jre/lib/amd64/libnpjp2.so

--Chelusly

--------------------

See:
[http://www.linuxintro.org/wiki/Webex](http://www.linuxintro.org/wiki/Webex)

[http://www.oracle.com/technetwork/java/javase/manual-plugin-install-linux-136395.html](http://www.oracle.com/technetwork/java/javase/manual-plugin-install-linux-136395.html)

---

### Post by 243kof on 2011-10-17
Hi, Yanti,

Have you reached any conclusions about why webex needs firefox to run with sudo? I had this problem at work with Kubuntu 11.04 and it drove me crazy until I came across this thread. The strange thing is that webex works out of the box (without using sudo) in my home laptop, where I also use Kubuntu 11.04. I even don't need to use sun-java, it works fine with openjdk and icedtea-plugin.

> **Yanti said:**
> Hi Newbify2!

I tried to run Firefox with sudo and that really did the trick! Webex seems to work with 11.04 (I can see presentations now).

(And gksudo should be preferred instead of sudo in this case)

Apparently this problem is related to user privileges somehow, perhaps Firefox, Java or Webex client etc. etc. I try to dig this further. 

Thanks!
Yanti

---

### Post by jamesgthang on 2011-10-17
It seems to be working fine as a regular user in Ubuntu 11.10 now.  

All I did was the automatic distribution upgrade tool (to upgrade from 11.04 to 11.10) and I can view presentations with no problems.

---

### Post by Yanti on 2011-11-03
Hi 243kof,

unfortunately I have not found any solution in this case. I run Ubuntu 11.10 now and same symptoms continue. Sun-Java is in use and no matter what I do, I just can't get the damn Webex work without gksudo. :(

I have not tried clean install though, all my Ubuntu systems are upgraded from previous versions and they all show same problem.

Cheers: Yanti

---

### Post by dannew on 2012-02-07
> **Yanti said:**
> Hi Newbify2!

I tried to run Firefox with sudo and that really did the trick! Webex seems to work with 11.04 (I can see presentations now).


This workaround works for me on 11.10, thanks.

---

### Post by babarhaq on 2012-05-26
same problem on 11.10. Haven't tried the workaround yet. Can some one confirm if this issue is no more in 12.04.

[Babar]("http://babarhaq.blogspot.com")

---

### Post by cybergalvez on 2012-05-28
> **dannew said:**
> This workaround works for me on 11.10, thanks.

Wow I would never run a browser as sudo! Anyone run the brouwser session in a terminal window to see is there are any errors that pop up

---

### Post by sergeykoch on 2012-08-30
Ubuntu 12.04, JDK7, still has the same issue:
[12065.300926] atasjni[4965]: segfault at 3e80 ip b4f4ba79 sp bfdca378 error 4 in atascli.so[b4eb3000+11b000]

---

