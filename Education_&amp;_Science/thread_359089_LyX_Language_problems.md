---
title: "LyX Language problems"
date: 2007-02-11
forum: Education &amp; Science
---

### Post by Blueshift on 2007-02-11
Hi!

I have just installed LyX and it seems like a cool program. I just have one major bug that I would like to resolve. The letters in the task bar are automatically set to Danish when I install it via the Ubuntu repository. Unfortunately something strange happens when the program tries to do this and the letters are all screwed up.. think it has something to do with the libraries. Here is what I get if I run the program from the terminal:

X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Locale da_DK could not be set

Found some help on this at [http://wiki.lyx.org/LyX/Troubleshooting](http://wiki.lyx.org/LyX/Troubleshooting)

Write the following command from Terminal:

export LC_ALL=en; lyx

It seems to work, as it changes the locale from Danish to English :)

---

### Post by Blueshift on 2007-02-11
^^

---

### Post by dakhan on 2007-02-15
Hi!

I had similar problem with Polish localization - it is because LyX assumes ISO-8859-x coding system, while Ubuntu uses UTF-8 by default. The problem hopefully will disappear when LyX 1.5 will be released - it is to be recoded unicode as well.

For now the solution is to enable appropriate coding system in Ubuntu. I have done it for myself editing (as superuser) the file:
/var/lib/locales/supported.d/pl

It contained by default only:
```
pl_PL.UTF-8 UTF-8
```

and I have added:
```
pl_PL ISO-8859-2
```

I hope you know what should be ISO variant for Danish :)
Then you have to generate the locales in new coding system running in terminal:
```
sudo dpkg-reconfigure locales
```

Then menu and dialog boxes in Danish should be displayed properly.

The next problem that I haven't found solution for is making Aspell under LyX respect the coding system... For now it is unusable, cause it applies dictionaries coded in UTF-8 to the Polish diacritical marks - for which LyX does allow only ISO-8859-2.

Best regards,
Andrzej

---

### Post by wgrant on 2007-02-16
LyX's bad handling of non-Latin locales is [bug #61698]("https://launchpad.net/ubuntu/+source/lyx/+bug/61698"). I believe it will be fixed in the next version.

---

