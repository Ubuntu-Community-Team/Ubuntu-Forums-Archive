---
title: "package need to be reinstalled, but its not installed"
date: 2009-11-13
forum: Desktop Environments
---

### Post by DeaD SouL on 2009-11-13
Hello guys..

I'm using LAMPP server installed on "/opt/lampp/"

and I needed to install [PHP/JAVA Bridge]("http://php-java-bridge.sourceforge.net")

so I've installed tomcat6 "sudo apt-get install tomcat6"
then downloaded & installed "php-java-bridge_5.4.4.2-3_i386.deb"

but it didn't work

thats why i wanted to remove the php-java-bridge and tomcate to reinstall them again from source, so that i can install tomcat next to lampp, then install php-java-bridge

but i could not remove them.. 

error notification:
[[img]http://uppix.net/4/f/6/297232ba84fa7566c022b85c0c4abtt.jpg[/img]](http://uppix.net/4/f/6/297232ba84fa7566c022b85c0c4ab.png)

synaptic manager says:
[IMG]http://uppix.net/4/1/9/cb9a34723a96f219c8daed0c47527.png[/IMG]

update manager:
[IMG]http://uppix.net/b/e/b/5ea509925458f7b750d07a6259c3b.png[/IMG]
I've selected: Partial Upgrade
[IMG]http://uppix.net/d/1/c/7c2057c57dce174cb6a20d448bc0f.png[/IMG]
I've selected: yes
[IMG]http://uppix.net/d/9/b/d59b82ca8d89550d385f16b320a03.png[/IMG]
but:
[IMG]http://uppix.net/8/5/b/d66ae3f89ae9d7b2f09311e2518ec.png[/IMG]

tried to upgrade:
[IMG]http://uppix.net/d/1/a/d4284c0524579800b656d04dac9ef.png[/IMG]

---

### Post by DeaD SouL on 2009-11-13
tried to remove the package:
[IMG]http://uppix.net/3/6/b/1d6dcc65eaa7e2d4c4aab94f1c08a.png[/IMG]
[IMG]http://uppix.net/3/8/6/43dabdfcb7f6f94d17a93f970b3da.png[/IMG]

tried to re-install the package:
[IMG]http://uppix.net/d/b/0/77ba94f60add4f34e7ada2b59862c.png[/IMG]

found php-java-bridge in: "/var/lib/dpkg/info/"
[IMG]http://uppix.net/1/2/b/932b655571d196cb16a48f7af73ff.png[/IMG]

sorry about the images.. i just wanted to clear the problem as much as possible

any help would be greatly appreciated

thanks in advance

---

### Post by DeaD SouL on 2009-11-14
any ideas..

---

### Post by DeaD SouL on 2009-11-14
thank God, I found it :D

while I was reading the dpkg's manual
```
man dpkg
```

i found
> remove-reinstreq: Remove a package, even if it's broken and marked to require reinstallation. This may, for example, cause parts of  the  package  to
              remain on the system, which will then be forgotten by dpkg.

so I tried it:
```
sudo dpkg --force-remove-reinstreq --remove php-java-bridge
```

and BINGO.. IT WORKED ;)

hope it will be useful to someone, someday :)

regards

---

