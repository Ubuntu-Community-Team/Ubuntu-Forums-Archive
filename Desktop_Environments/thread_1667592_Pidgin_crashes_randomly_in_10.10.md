---
title: "Pidgin crashes randomly in 10.10"
date: 2011-01-15
forum: Desktop Environments
---

### Post by jfet on 2011-01-15
Hi,

After upgrading to Ubuntu 10.10 Pidgin seems to crash randomly.
Dmesg shows me segmentation faults in various libraries, but the most common is: libpurple.so.0.7.3

Here it is:
```
$ dmesg |grep pidgin
[39837.965939] pidgin[16074]: segfault at 766c6f68 ip 005ab655 sp bfd376a0 error 4 in libpurple.so.0.7.3[51b000+f3000]
[43849.174005] pidgin[19601]: segfault at 27 ip 02db549d sp bfd61db0 error 4 in ssl-nss.so[2db3000+4000]
[44632.564359] pidgin[19724]: segfault at 67206d7d ip 00928655 sp bf84d0c0 error 4 in libpurple.so.0.7.3[898000+f3000]
[52967.877599] pidgin[20646]: segfault at 2d503264 ip 00445655 sp bfaf9100 error 4 in libpurple.so.0.7.3[3b5000+f3000]

```

My pkgs:
```
$ dpkg -l |grep purp
ii  gpp                                    2.24-2                                                     a general-purpose preprocessor with customizable syntax
ii  libpurple-bin                          1:2.7.3-1ubuntu3.2                                         multi-protocol instant messaging library - extra utilities
ii  libpurple0                             1:2.7.3-1ubuntu3.2                                         multi-protocol instant messaging library
ii  telepathy-haze                         0.4.0-1ubuntu0.1                                           A telepathy connection manager that use libpurple
$ dpkg -l |grep pidgi
ii  pidgin                                 1:2.7.3-1ubuntu3.2                                         multi-protocol instant messaging client
ii  pidgin-awayonlock                      0.5.2-1                                                    pidgin plugin to set as away on screensaver activation
ii  pidgin-data                            1:2.7.3-1ubuntu3.2                                         multi-protocol instant messaging client - data files
ii  pidgin-libnotify                       0.14-4ubuntu1                                              display notification bubbles in pidgin
ii  pidgin-plugin-pack                     2.6.3-1ubuntu1                                             Collection of Pidgin plugins

```

```

$ uname -a
Linux dome-laptop 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU/Linux

```

Do you have any ideas what is wrong here?

---

### Post by jcer93705 on 2011-01-16
> **jfet said:**
> Hi,

After upgrading to Ubuntu 10.10 Pidgin seems to crash randomly.
Dmesg shows me segmentation faults in various libraries, but the most common is: libpurple.so.0.7.3

Here it is:
```
$ dmesg |grep pidgin
[39837.965939] pidgin[16074]: segfault at 766c6f68 ip 005ab655 sp bfd376a0 error 4 in libpurple.so.0.7.3[51b000+f3000]
[43849.174005] pidgin[19601]: segfault at 27 ip 02db549d sp bfd61db0 error 4 in ssl-nss.so[2db3000+4000]
[44632.564359] pidgin[19724]: segfault at 67206d7d ip 00928655 sp bf84d0c0 error 4 in libpurple.so.0.7.3[898000+f3000]
[52967.877599] pidgin[20646]: segfault at 2d503264 ip 00445655 sp bfaf9100 error 4 in libpurple.so.0.7.3[3b5000+f3000]

```

My pkgs:
```
$ dpkg -l |grep purp
ii  gpp                                    2.24-2                                                     a general-purpose preprocessor with customizable syntax
ii  libpurple-bin                          1:2.7.3-1ubuntu3.2                                         multi-protocol instant messaging library - extra utilities
ii  libpurple0                             1:2.7.3-1ubuntu3.2                                         multi-protocol instant messaging library
ii  telepathy-haze                         0.4.0-1ubuntu0.1                                           A telepathy connection manager that use libpurple
$ dpkg -l |grep pidgi
ii  pidgin                                 1:2.7.3-1ubuntu3.2                                         multi-protocol instant messaging client
ii  pidgin-awayonlock                      0.5.2-1                                                    pidgin plugin to set as away on screensaver activation
ii  pidgin-data                            1:2.7.3-1ubuntu3.2                                         multi-protocol instant messaging client - data files
ii  pidgin-libnotify                       0.14-4ubuntu1                                              display notification bubbles in pidgin
ii  pidgin-plugin-pack                     2.6.3-1ubuntu1                                             Collection of Pidgin plugins

```


Do you have any ideas what is wrong here?

My crashes too in ubuntu 10.10 x64 and we're also on 2.7.3 i wunder if 2.7.9 will fix the problem??

---

### Post by zdesigner on 2011-01-17
I have almost the same problem. The only difference is that the segfault occurs in pidgin instead of libpurple.so.0.7.3 - or I misunderstood the output of dmesg.

```
$ dmesg | grep pidgin
[ 2232.460266] pidgin[2102]: segfault at 58 ip 000000000045d5bd sp 00007fff9f132f80 error 4 in pidgin[400000+e4000]
```

```
$ dpkg -l | grep purp
ii  libpurple-bin                             1:2.7.3-1ubuntu3.2                                multi-protocol instant messaging library - extra utilities
ii  libpurple0                                1:2.7.3-1ubuntu3.2                                multi-protocol instant messaging library
ii  pidgin-skype                              20100302+dfsg-1                                   Skype plugin for libpurple messengers
ii  telepathy-haze                            0.4.0-1ubuntu0.1                                  A telepathy connection manager that use libpurple
```

```
$ dpkg -l | grep pidgi
ii  pidgin                                    1:2.7.3-1ubuntu3.2                                multi-protocol instant messaging client
ii  pidgin-data                               1:2.7.3-1ubuntu3.2                                multi-protocol instant messaging client - data files
ii  pidgin-encryption                         3.1-1                                             pidgin plugin that provides transparent encryption
ii  pidgin-libnotify                          0.14-4ubuntu1                                     display notification bubbles in pidgin
ii  pidgin-microblog                          0.3.0-1                                           Microblogging plugins for Pidgin
ii  pidgin-otr                                3.2.0-5                                           Off-the-Record Messaging plugin for pidgin
ii  pidgin-plugin-pack                        2.6.3-1ubuntu1                                    Collection of Pidgin plugins
ii  pidgin-screenlet                          0.3.5~maverick1                                   A Screenlet to show the Pidgin contactlist
ii  pidgin-skype                              20100302+dfsg-1                                   Skype plugin for libpurple messengers

```

```
$ uname -a
Linux latitude 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux
```

---

### Post by jcer93705 on 2011-01-17
My problem is the app doesn't responde, its either turn white or black the window and then suck up 100 percent one of my cores. Then I
had to open up system monitor to kill the app. It's scary its a new computer and I don't want to bust a core.

---

### Post by Krytarik on 2011-01-18
Try upgrading to the current version using their own PPA, maybe it helps:
[https://launchpad.net/~pidgin-developers/+archive/ppa/](https://launchpad.net/~pidgin-developers/+archive/ppa/)
```
sudo add-apt-repository ppa:pidgin-developers/ppa
sudo apt-get update
sudo apt-get upgrade
```
Greetings.

---

### Post by mustang on 2011-01-22
> **Krytarik said:**
> Try upgrading to the current version using their own PPA, maybe it helps:
[https://launchpad.net/~pidgin-developers/+archive/ppa/](https://launchpad.net/~pidgin-developers/+archive/ppa/)
```
sudo add-apt-repository ppa:pidgin-developers/ppa
sudo apt-get update
sudo apt-get upgrade
```
Greetings.

I'm also getting lots of random crashes. Running x86_64 10.10. 

Thanks for posting this Krytarik. Will try it out.

---

### Post by jfet on 2011-01-25
> **Krytarik said:**
> Try upgrading to the current version using their own PPA, maybe it helps:
[https://launchpad.net/~pidgin-developers/+archive/ppa/](https://launchpad.net/~pidgin-developers/+archive/ppa/)
```
sudo add-apt-repository ppa:pidgin-developers/ppa
sudo apt-get update
sudo apt-get upgrade
```
Greetings.

It seems that the crashes are not so frequent, and now it have no trace in dmesg either.
But pidgin still gets closed/terminated/crashed time to time.
But this state is much better, thank you!

---

### Post by rrsn on 2011-03-08
> **jfet said:**
> It seems that the crashes are not so frequent, and now it have no trace in dmesg either.
But pidgin still gets closed/terminated/crashed time to time.
But this state is much better, thank you!

I have the same problem, pidgin 2.7.9 crash random time in my Ubuntu 10.10.
There is a solution for this?

---

### Post by Krytarik on 2011-03-08
> **rrsn said:**
> I have the same problem, pidgin 2.7.9 crash random time in my Ubuntu 10.10.
There is a solution for this?
I did check its website just yet, version 2.7.10 is out since a month now, but they still didn't update their PPA. If you need a quick fix, I'm afraid you have to compile it yourself:
[http://www.pidgin.im/download/source/](http://www.pidgin.im/download/source/)
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by rrsn on 2011-03-08
> **Krytarik said:**
> I did check its website just yet, version 2.7.10 is out since a month now, but they still didn't update their PPA. If you need a quick fix, I'm afraid you have to compile it yourself:
[http://www.pidgin.im/download/source/](http://www.pidgin.im/download/source/)
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

I cant compile this version of pidgin, too many dependencies are required, I have installed many "dev" resources but din't work.

aggggggrrrhhhhh Empathy sucks!!!!! I need my pidgin back! huahuahuhua

---

### Post by Krytarik on 2011-03-08
> **rrsn said:**
> I cant compile this version of pidgin, too many dependencies are required, I have installed many "dev" resources but din't work.

aggggggrrrhhhhh Empathy sucks!!!!! I need my pidgin back! huahuahuhua
 LOL, Empathy didn't work at all for me, I tried it once.

Actually I successfully compiled it a couple of times a while ago back in Gutsy 7.10.
What error are you currently getting when doing "configure"?

---

### Post by rrsn on 2011-03-08
> **Krytarik said:**
> LOL, Empathy didn't work at all for me, I tried it once.

Actually I successfully compiled it a couple of times a while ago back in Gutsy 7.10.
What error are you currently getting when doing "configure"?

I'm running a build-dep now, maybe work to compile last version of pidgin kakakakakka

---

### Post by paqueteuy on 2011-03-09
> **Krytarik said:**
> Try upgrading to the current version using their own PPA, maybe it helps:
[https://launchpad.net/~pidgin-developers/+archive/ppa/]("https://launchpad.net/%7Epidgin-developers/+archive/ppa/")
```
sudo add-apt-repository ppa:pidgin-developers/ppa
sudo apt-get update
sudo apt-get upgrade
```Greetings.

This seems to work for me, Pidgin 2.7.9 has not crashed after an hour of use, which largely exceeds the average 5 minutes until a crash in Pidgin 2.7.3.

I was having random segfaults in pidgin 2.7.3, according to the log .
No extra information was gathered if executed from a terminal in debug mode.
Just this:
```
pidgin[7543]: segfault at 2f82 ip b6e87655 sp bffbcc90 error 4 in libpurple.so.0.7.3[b6df7000+f3000]
```

---

