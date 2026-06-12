---
title: "consolidated uptime"
date: 2005-10-16
forum: Desktop Environments
---

### Post by MichaëlVD on 2005-10-16
This must be absolutely easy if you know how to do it. Problem is, I don't...

Where can I find logs about how long my desktop has been running in the past month or so? I know I can run 'uptime' to know how long my current session has been running, but I would like to keep that information available after I reboot.

Thanks!

---

### Post by Rxke on 2005-10-25
Not sure this is what you're looking for, but you can install uptimed (either via synaptic or type :  ```
sudo apt-get install uptimed
```  in a terminal window.

then in terminal type: ```
uprecords
```   and you get an overview:

```
rxke@FireClam:~$ uprecords
     #               Uptime | System                                    Boot up
----------------------------+-------------------------------------------------
->   1     8 days, 12:54:31 | Linux 2.6.12-9-powerpc   Sun Oct 16 20:18:24 2005
----------------------------+-------------------------------------------------

```
(I didn't reboot since installing uptimed, so it's a bit sparse, but normally you get a list of your reboots etc.

(Edit: oh: this is a laptop, which 'goes to sleep' when I go to sleep (heh) but as you can see the 'suspend' events are not listed....)

---

### Post by n2j3 on 2008-01-10
```

     #               Uptime | System                                     Boot up
----------------------------+---------------------------------------------------
     1    20 days, 18:09:48 | Linux 2.6.22-1-mepis-smp  Tue Dec 18 00:20:14 2007
->   2     0 days, 07:05:33 | Linux 2.6.22-1-mepis-smp  Thu Jan 10 07:49:06 2008
     3     0 days, 00:11:35 | Linux 2.6.22-1-mepis-smp  Tue Jan  8 16:40:54 2008
     4     0 days, 00:05:14 | Linux 2.6.22-1-mepis-smp  Mon Jan  7 21:44:17 2008
----------------------------+---------------------------------------------------
no1 in    20 days, 11:04:16 | at                        Thu Jan 31 01:58:56 2008


```
^
example

and also a bump to a really old post...

---

