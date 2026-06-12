---
title: "epsxe and libcrypto problem"
date: 2020-04-25
forum: Gaming &amp; Leisure
---

### Post by trickyy on 2020-04-25
Hi
I am having problems with the 64 bit version of epsxe and Ubuntu 20.04
I have downloaded it from the official site but when I start it from the terminal I get
```

./epsxe_x64: error while loading shared libraries: libcrypto.so.1.0.0

$ locate libcrypto.so.1.0.0
/opt/google/earth/pro/libcrypto.so.1.0.0
/opt/[COLOR=#ff0000]pia[/COLOR]/ruby/32/libcrypto.so.1.0.0
/opt/[COLOR=#ff0000]pia[/COLOR]/ruby/64/libcrypto.so.1.0.0

$ echo $PATH
/opt/pia/ruby/64/
```

Pia is private internet access and I have added this directory to my PATH but still get the error. I know there is a different emulator in the repos but its not as good as epsxe

---

### Post by Holger_Gehrke on 2020-04-26
PATH is for finding programs not libraries. Setting PATH like you have done is a very bad idea since it would only search for programs in that directory and would therefore find almost no programs. PATH is a colon separated list of directories. To add a directory to the PATH you would use something like 'PATH=$PATH:/opt/pia/ruby/64/' or 'PATH=/opt/pia/ruby/64/:$PATH'.

libcrypto.so.1.0.0 is part of the package libssl on older versions of Ubuntu but 20.04 has a newer version of libssl which has libcrypto.so.1.1.0. The two copies you have found were installed for their own use by the two programs in whose directories in opt they are found. You can try to make epsxe_x64 use one of those by calling it with 'LD_LIBRARY_PATH=/opt/google/earth/pro/ epsxe_64' or 'LD_LIBRARY_PATH=/opt/pia/ruby/64/ epsxe_64', but they might be different from the standard libcrypto.so.1.0.0 and might not work because of this. Libraries are normally found through the configuration in /etc/ld.so.conf and /etc/ld.so.conf.d/ but the variable LD_LIBRARY_PATH can be used to override this configuration or add to it.

Edit: And while epsxe is slightly faster I find mednafen has better compatibility. It does not have the ability to run without a dump of the PSX-BIOS and is somewhat picky about those BIOS-files but once everything is configured right it works great. Using the front-end mednaffe is highly recommended, configuring mednafen without it can be ... interesting ... to say the least. The higher compatibility is probably the reason why retroarch uses the beetlepsx core from mednafen for Playstation emulation.

Holger

---

### Post by trickyy on 2020-04-27
HI Holger 				

Thanks for the reply I had added a few lines in home/bash.rc to add to the path so I have now deleted them and its back to normal. I tried your suggestion about adding a path when calling epsxe but it kept on wanting more and more libs until it wanted one that was 32bit.

At which time I gave up and tried mednafen and its brilliant.

Thanks

---

