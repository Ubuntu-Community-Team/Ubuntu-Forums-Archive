---
title: "java installation and java plugin"
date: 2005-10-19
forum: Desktop Environments
---

### Post by joplass on 2005-10-19
Someone had a nice Warty guide with repository on the forum for java installation.  That was then.
With Breezy I can't install java.  I have tried all I know including instructions at java.com.
Can someone please steer me to the right direction?
Thank you,

---

### Post by No6 on 2005-10-19
[quote=joplass]Someone had a nice Warty guide with repository on the forum for java installation.  That was then.
With Breezy I can't install java.  I have tried all I know including instructions at java.com.
Can someone please steer me to the right direction?
Thank you,[/quote]

Do you need 1.5? 'cause 1.4.2 is in the repos.

---

### Post by paddyg on 2005-10-19
As I said somewhere else, that's what I did with Breezy:

I Just got jdk-1_5_0_05-linux-i586.bin from java.sun.com.
As root I made a /usr/java dir, saved the file there and unpacked it.
Then manually I made the symlink for firefox (on my sys /usr/java/jdk1.5.0_04/jre/plugin/i386/ns7) and moved it to firefox plugin dir (/usr/lib/mozilla-firefox/plugins)

Hope it helps

---

### Post by joplass on 2005-10-19
That should do it.
Thanks

---

### Post by GoA on 2005-10-19
[QUOTE=No6]Do you need 1.5? 'cause 1.4.2 is in the repos.[/QUOTE]

For example, Azureus won't work with old java.

---

### Post by unexpected on 2005-10-19
Actually, it does work, it just gives you a lil' note saying "upgrade your java." When i installed Breezy, I used azureus for several days before i  installed Java 1.5

---

### Post by lakcaj on 2005-10-19
Why not use java-package that has the make-jpkg utility?  It creates a .deb that you can then install with dpkg, and should automagically setup the browser plugin too.

---

