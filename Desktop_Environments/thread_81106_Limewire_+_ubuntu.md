---
title: "Limewire + ubuntu"
date: 2005-10-23
forum: Desktop Environments
---

### Post by Meksw0ll on 2005-10-23
First off, I'm not sure whether or not I'm in the right place to ask this question so if it isn't I apologize sincerely. However I am having a problem getting LimeWire to work on my ubuntu.

I am a very new Linux user and and I've been using Windows for the last 7 years or so but I fancied a change and therefor thought I'd give Linux a go and that's how I got here.

My problem now is that I have followed the steps on [http://ubuntuguide.org/#limewire](http://ubuntuguide.org/#limewire) except for the second step concerning Java because that file isn't available anymore I believe but I managed to install it (after a few bad installs) and then proceeded to the next step which I did and which, I believe, went right. However, when I type *runLime.sh* I get the following:

Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: Onbekend bestand of map
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: Onbekend bestand of map
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)


Obviously I thought I'd check to see my Java version which is this after typing *java -version*

java version "1.4.2"
gcj-4.0 (GCC) 4.0.0 20050301 (prerelease) (Debian 4.0-0pre6ubuntu7)
Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


As you can see my version should support the use of Limewire. I must say that I might have installed some other Java files such as 'j2sdk-1_4_2_09-linux-i586.bin'. But even if my second installation (Version 5 normally) which is named 'jre-1_5_0_05-linux-i586.bin' didn't install properly it should still work...


Thanks in advance,
Thomas

---

### Post by LorenzoD on 2005-10-23
You need to use Sun's Java. It's been explained at other places, but right now I'm too tired to search and give you links, so I'll just quickly explain it:

To do this you need to have java-package installed. Apt-get it if you don't.

First, you've downloaded a jdk*.bin file. In a terminal, type fakeroot make-jpkg <name of bin file>. You'll see some permission denied messages flying by. Don't worry about them. This will give you a .deb file which you install with sudo dpgk -i <name of deb>.

Sorry if the explanation is terse, but I've really got to get some sleep..

---

### Post by Meksw0ll on 2005-10-23
I have a file here called 'j2sdk-1_4_2_09-linux-i586.bin' which I'm guessing is the Sun Java which I need. I then typed the command *fakeroot make-jpkg j2sdk-1_4_2_09-linux-i586.bin* which made a .deb file as you said it would but when I then try to install the .deb file by typing *sudo dpgk -i sun-j2sdk1.4_1.4.2+09_i386.deb* I get the following error message:

sudo: dpgk: command not found


Anyone have any bright ideas?

Ta,
Thomas

---

### Post by LorenzoD on 2005-10-23
Sorry, my bad: dpkg -i <deb file> (That is: dee-pee-kay-gee).

---

### Post by Meksw0ll on 2005-10-23
Thanks, just tried it and works perfecty. Thanks a bunch

---

### Post by bored2k on 2005-10-23
You could just
1. ```
sudo apt-get install alien j2re1.4
```
OR
2. [http://www.ubuntuforums.org/showthread.php?t=70428](http://www.ubuntuforums.org/showthread.php?t=70428)

After that, download the limewire RPM file and do a 
```
sudo alien -d LIMEWIRE_WHATEVER_NAME.RPM
sudo dpkg -i limewhatever.deb
```

---

