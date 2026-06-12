---
title: "Java Problems"
date: 2006-03-18
forum: Desktop Environments
---

### Post by josh34 on 2006-03-18
I followed this guide to install java: [http://www.ubuntuforums.org/showthread.php?t=76735](http://www.ubuntuforums.org/showthread.php?t=76735) But when I clicked on the link included in the post to check for java, the page told me I didn't have it. I have also tried Sun's official java verification page and it says I don't have it either. I tried starting frostwire from terminal and it gave me this:

josh@ubuntu:~$ frostwire
: command not found:
: No such file or directory
: command not found:
: command not found3:
'unFrost.sh: line 24: syntax error near unexpected token `
'unFrost.sh: line 24: `look_for_java()
josh@ubuntu:~$

How can I fix java?

Thanks,
Josh

---

### Post by knalle on 2006-03-19
which browser did you use to try it? and what is frostwire?

---

### Post by Ramses de Norre on 2006-03-19
Frostwire a an open limewire-like application.
It's totally based on java.

---

### Post by knalle on 2006-03-19
[QUOTE=josh34]josh@ubuntu:~$ frostwire
: command not found:
: No such file or directory
: command not found:
: command not found3:
'unFrost.sh: line 24: syntax error near unexpected token `
'unFrost.sh: line 24: `look_for_java()
josh@ubuntu:~$

How can I fix java?

Thanks,
Josh[/QUOTE]

ok, first of all, you don't start frostwire the right way, read the **read.me** of the app to find out how to launch it

---

### Post by xenmax on 2006-03-19
I had the same problem. Although the how-tos told me that placing a link to java lib file in /usr/lib/mozilla-firefox/plugins dir will enable JRE plugin for ALL users, for some reason, loading java test sites on firefox gave me err that i didn't have JRE.

I tried placing a link in /home/<username>/.mozilla/plugins dir pointing to the link in /usr/lib/mozilla-firefox/plugins and it worked!

---

### Post by josh34 on 2006-03-19
I am using firefox and the only reason I started frostwire that way, was because it wouldn't start the normal way. I have installed java on other Ubuntu machines, and this has never happened to me before. So should I just try to install it again?

Thanks,
Josh

Edit: Could I possibly remove all of the java componets, even the default ones, and then install the Sun version. Also what do I need to edit /etc/jvm to say?

Edit: I removed Sun's Java and I now have the following javas:
/usr/bin/gij-wrapper-4.0
/usr/lib/jvm/java-gcj/bin/java
/usr/lib/j2se/1.4/bin/java
If I could, how can I remove these?

---

### Post by mctavish on 2006-03-20
I've just had the same problem here. 

I got a fix from the frostwire forums. The problem is that the startup script has windows format rather then 'nix. This is courtesy of jojoman02. 

> 
DO THE FOLLOWING AS ROOT (OR SUDO) in a Terminal
=========================================

1) nano /usr/lib/frostwire/runFrost.sh

2) then save in nano CTRL+O

3) here you can hit ALT+D to change the format. Then hit enter to save the file.

Note:
make sure after hitting CTRL+O the filename it doesn't have [DOS Format] before it.

Frostwire should now work

---

