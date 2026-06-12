---
title: "DOSEmu crashes when running UFO:XCOM"
date: 2006-10-24
forum: Gaming &amp; Leisure
---

### Post by mbant on 2006-10-24
I had some real trouble with dosemu and ubuntu. This is what I've gone through:

First of all, I discovered the ubuntu package didn't have X support compiled in (100 minus points for ubuntu) so I got the ubuntu source package and compiled it myself (no fancy switches or anything, X support is default setting and 'apt-get source -b dosemu' was enough, in fact).

Next, I had to use a debian package for freedos because the package that comes with ubuntu seems to be broken.

So far everything seems all right. xdosemu fires up, but when I start playing xcom I get the following error:
```

   You do not have the DOSEMU vga font installed and are running
   remote X. You need to install the vga font on your _local_ Xserver.
   Look at the readme for details. For now we start with an fixed font,
   which does not display all national characters correctly.
   ... be warned

ERROR: ES selector invalid: 0x0001, type=0 np=1

```

Both errors really don't tell me anything. The first is very confusing: I am using a vga font (I set it up myself in dosemu.conf and it works) and I'm certainly not using X remotely, it's all here on my laptop. All special characters work fine, too. However, I get the first error all the time. The second one is XCOM specific. At first, I thought it's because xcom uses DOS/4GW, but other apps using that work fine.

Any ideas?

My data:
```

$ dpkg -l | grep dosemu
ii  dosemu                                 1.2.2-3build1                          The Linux DOS Emulator
ii  dosemu-freedos                         0.0.b9r5a-3                            FreeDOS package for DOSEMU
ii  xfonts-dosemu                          1.2.2-3build1                          VGA font for the DOS Emulator

```
Running Dapper Drake.

---

### Post by king20878 on 2006-10-24
I'm afraid I don't know how to help you, but I am **very **interested in getting XCOM up and running.  If you could turn this into a howto once you get the bugs ironed out, I'm sure it would be a very appreciated in the community.

I will give your instructions a try tonight to see if I run into the same errors.

---

### Post by minisori on 2006-10-24
Both UFO and XCOM should work with dosbox without any problems. And  it's in the repos.

Long time ago i got it running on dosemu also, I think was crashing cause the sound in my case.. but i'm talking about 3 or 4 years ago...

---

### Post by mbant on 2006-10-31
Thanks for the advice, but dosbox doesn't really run well on my old machine. dosbox is incredibly slow compared to dosemu, anyway.

---

