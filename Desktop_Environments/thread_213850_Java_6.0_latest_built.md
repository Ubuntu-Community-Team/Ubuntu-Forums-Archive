---
title: "Java 6.0 latest built"
date: 2006-07-11
forum: Desktop Environments
---

### Post by bardu on 2006-07-11
Hi friends,

for development and testing purpose I need to have the latest snapshot of Java 6.0 as the default Java version on my machine with Ubuntu6.06. Doing as recommended in Ubuntu5.10 I get the following error messages and a deb package isn't created (same is happening with Java 6.0 Beta):

```
fakeroot make-jpkg jdk-6-rc-bin-b90-linux-i586-30_jun_2006.bin
Creating temporary directory: /tmp/make-jpkg.XXXXqziGzV
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)

No matching plugin was found.
Removing temporary directory: done
```

I would highly appreciate if someone could give me advices on how to install the latest snapshot of Java 6.0 correctly as the default Java version.

Thanks in advance.

Stephan

---

### Post by JoWilly on 2006-07-11
GCC seems not to be installed.

Install it , or you could also install build-essential which will install all the necessary default packages (including gcc) for building/compiling.

---

### Post by bardu on 2006-07-11
Thanks, this helped to get the gcc problem solved. Now I get this meesage:

```
fakeroot make-jpkg jdk-6-rc-bin-b90-linux-i586-30_jun_2006.bin
Creating temporary directory: /tmp/make-jpkg.XXXXwMCSIo
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done
```

I can use the snapshot in my IDE if I installed it in my user/dir, so I can't get it why make-jpkg is complaining.

So far I know there are no files in the Java distribution that ends with .sh.

Do I miss here a step?

Thanks.

Stephan

---

### Post by JoWilly on 2006-07-12
> **bardu said:**
> Now I get this meesage:

```
fakeroot make-jpkg jdk-6-rc-bin-b90-linux-i586-30_jun_2006.bin
Creating temporary directory: /tmp/make-jpkg.XXXXwMCSIo
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done
``` 
I can use the snapshot in my IDE if I installed it in my user/dir, so I can't get it why make-jpkg is complaining.

So far I know there are no files in the Java distribution that ends with .sh.

Do I miss here a step?

Thanks.

Stephan

I have not tried this, but I am guessing from what I see:

These plugins look like scripts for specific versions of java. You could look at the .sh file for the java 5 sdk plugin and make a new one for the java 6 sdk (you would probably need to edit some path/directory/locations that may be different in sdk 5 and sdk 6).

But you could also install it directly with "sh jdk-6-rc-bin-b90-linux-i586-30_jun_2006.bin".

---

### Post by bardu on 2006-07-12
The missing shell scripts are in the /usr/share/java-package folder and seem to be part of the Debian packaging system for Java(I'm not familier with this system).

Before I mess around I would like to ask for some advice on how to modify this scripts to package and install a Java 6.0 snapshot.

Thanks.
Stephan

---

### Post by JoWilly on 2006-07-12
> **bardu said:**
> The missing shell scripts are in the /usr/share/java-package folder and seem to be part of the Debian packaging system for Java(I'm not familier with this system).

Before I mess around I would like to ask for some advice on how to modify this scripts to package and install a Java 6.0 snapshot.

Thanks.
Stephan

Deb packaging is the best thing as it is easy to maintain/unistall the software. If you have the oportunity this is the way to chose.

But don't forget that, as I have already said, you can install jdk 6 with "**sudo** sh jdk-6-rc-bin-b90-linux-i586-30_jun_2006.bin" (If forgot sudo previously).

jdk-6-rc-bin-b90-linux-i586-30_jun_2006.bin is actually a "package" of its own that is already made to install the jdk. If it gets too complicated for you or if do not want to waste time in searching for how to make a deb package out of it you can just install it...

---

### Post by panurge77 on 2006-07-12
When I last tried it, I had to use something like 
```
$JAVA_PATH=path/to/jdk
```
after extracting the .bin

---

### Post by bardu on 2006-07-12
> But don't forget that, as I have already said, you can install jdk 6 with "sudo sh jdk-6-rc-bin-b90-linux-i586-30_jun_2006.bin" (If forgot sudo previously).

jdk-6-rc-bin-b90-linux-i586-30_jun_2006.bin is actually a "package" of its own that is already made to install the jdk. If it gets too complicated for you or if do not want to waste time in searching for how to make a deb package out of it you can just install it...

What you recommand is simply extrating the Java SDK in a location of your choise, but this makes it not your system wide default Java version. As I have already said, I have Java 6.0 snapshots on my machine( an installation in my home directory ) for quit a while to use it in my IDE. 

Maybe I can reduce the problem to the Firefox plugin. For testing my application I need Firefox to use the Java 6.0 plugin. From a Linux distro I used before switching to Ubuntu I remember that I could use a symbolic link to let Firefox use a certain Java version. But at /usr/lib/firefox/plugin I can't even find a link or the plugin file for the current Java 5.0 plugin.

Can you eventually give me a hint on how to let Firefox use the plugin from my Java 6.0 snapshot?

Thanks.
Stephan

---

### Post by JoWilly on 2006-07-13
Also check /usr/lib/mozilla/plugins and /usr/lib/mozilla-firefox/plugins.

Are you sure that the firefox plugin is already included in java 6 ? I am asking because i.ex the firefox plugin is still not included for java 5 on amd64; so as java 6 still is in development it may not be there yet...

To make java 6 your default java check the ubuntu wiki. There is a script that does this for the actual versions of java, you will probably need to edit it manually to add java6.

---

### Post by JoWilly on 2006-07-13
Here you'll get about everything you need, including the location of the web plugin:

[https://help.ubuntu.com/community/Java?highlight=%28java%29](https://help.ubuntu.com/community/Java?highlight=%28java%29)

---

### Post by bardu on 2006-07-13
Thanks for the time you have invested to help me out.

Yes, the plugin is shiped with the Java 6.0 snapshot and I also know the document you linked to.

You just can change the default Java by selceting a .deb package already installed on your machine.

Building a .deb package is far behind my Linux knowledge and I even haven't the time to dig deeper into it.

I found the email address of the Debian Java maintainers and asked for a how to... but didn't get an answer yet.(Maybe I shouldn't mention that I run Ubuntu!!!)

If more people would ask for a how to install a non offical Sun Java release or that they provide a package for the current Java 6.0 snapshot we might get an response.
Here is the email address:

          **pgk-java-maintainers@lists.alioth.debian.org**

Thanks again,

Stephan

---

### Post by bardu on 2006-07-14
Just before leaving for a canoe trip with my sons I found this thread:

[http://www.mail-archive.com/debian-java@lists.debian.org/msg10870.html]("http://www.mail-archive.com/debian-java@lists.debian.org/msg10870.html")

I will try the recommanded steps out as soon I'm back.

Cheers,
Stephan

---

### Post by bardu on 2006-07-27
Following this recommendations I could successfully create and install a j2sdk6.0-sun package and it is definitely in the /usr/lib folder.

But ```
java -version
``` is still my 1.5.07 version and if I do 

	```
sudo update-alternatives -- config java
```

the new package is not even listed.

I'm wondering what the /etc/jvm and /usr/lib/jvm/ have for a purpose. Is it legacy stuff?
In the /usr/lib/jvm is not even a link to my java-1.5.0-sun and it is the default version.

The instruction to select the default Java version here
           [https://help.ubuntu.com/community/Java?highlight=%28java%29]("https://help.ubuntu.com/community/Java?highlight=%28java%29")
didn't help a bit.

Does someone know how ```
update-alternatives --config java
``` get's is versions from?

Thanks in advance.

Stephan

---

### Post by bardu on 2006-07-27
Finally I got it to work:
Here are the steps I have performed:

[HTML][SIZE="3"]cd /usr/share/java-package
sudo cp -ax sun-j2sdk1.5 sun-j2sdk6.0
sudo cp -ax sun-j2sdk1.5-doc sun-j2sdk6.0-doc

After that I edited the following scripts:

/usr/share/java-package/sun-j2sdk6.0/install

	changed line suffix=j2sdk1.5-sun
                  to suffix=j2sdk6.0-sun

/usr/share/java-package/sun-j2sdk6.0/remove

	changed line suffix=j2sdk1.5-sun
                  to suffix=j2sdk6.0-sun

/usr/share/java-package/sun-j2sdk6.0-doc/install

	changed line j2se_base="/usr/share/doc/j2sdk1.5-sun-doc
                  to j2se_base="/usr/share/doc/j2sdk6.0-sun-doc

	changed line install-docs -i /usr/share/doc-base/sun-j2sdk1.5-doc
                  to install-docs -i /usr/share/doc-base/sun-j2sdk6.0-doc

/usr/share/java-package/sun-j2sdk6.0-doc/remove

	changed line j2se_base="/usr/share/doc/j2sdk1.5-sun-doc
                  to j2se_base="/usr/share/doc/j2sdk6.0-sun-doc

/usr/share/java-package/sun-j2sdk.sh

	added  "jdk-6-rc-bin-b92-linux-i586-20_jul_2006.bin") # UNOFFICIAL
	    	   j2se_version=6.0.0+rc
            	   j2se_expected_min_size=130
	    	   found=true
            	   ;;  

	(Please note: jdk-6-rc-bin-b92-linux-i586-20_jul_2006.bin is the current
                      snapshot binary)


After that I created the .deb package and installed it:

	I went to the directory where I downloaded the snapshot

	fakeroot make-jpkg jdk-6-rc-bin-b92-linux-i586-20_jul_2006.bin

	sudo dpkg -i sun-j2sdk6.0_6.0.0+rc_i386.deb

Now I had to manually change the versions:

	sudo update-alternatives --config java

	and selected  /usr/lib/j2sdk6.0-sun/bin/java from the list

	checked it:  java -version
			java version "1.6.0-rc"
			Java(TM) SE Runtime Environment (build 1.6.0-rc-b92)
			Java HotSpot(TM) Client VM (build 1.6.0-rc-b92, mixed mode, sharing)

Now the browser plugin:

	sudo update-alternatives --config firefox-javaplugin.so

		selected the Java6.0 plugin from the list

        checked it by opening the browser and typed 

		about:plugins
	
	and the Java6.0 plugin is listed as the current version.

If you need the following apps you have to repeat the update-alternatives for each one:

	appletviewer
	apt
	ControlPanel
	extcheck
	HtmlConverter
	idlj
	jar
	jarsigner
	java
	javac
	javadoc
	javah
	javap
	java-rmi.cgi
	javaws
	jconsole
	jdb
	jinfo
	jmap
	jps
	jsadebugd
	jstack
	jstat
	jstatd
	keytool
	native2ascii
	orbd
	pack200
	policytool
	rmic
	rmid
	rmiregistry
	serialver
	servertool
	tnameserv
	unpack200[/SIZE][/HTML]

---

### Post by -DarkMind- on 2006-07-29
> **bardu said:**
> Finally I got it to work:
Here are the steps I have performed:

[HTML][SIZE="3"]cd /usr/share/java-package
sudo cp -ax sun-j2sdk1.5 sun-j2sdk6.0
sudo cp -ax sun-j2sdk1.5-doc sun-j2sdk6.0-doc

After that I edited the following scripts:

/usr/share/java-package/sun-j2sdk6.0/install

	changed line suffix=j2sdk1.5-sun
                  to suffix=j2sdk6.0-sun

/usr/share/java-package/sun-j2sdk6.0/remove

	changed line suffix=j2sdk1.5-sun
                  to suffix=j2sdk6.0-sun

/usr/share/java-package/sun-j2sdk6.0-doc/install

	changed line j2se_base="/usr/share/doc/j2sdk1.5-sun-doc
                  to j2se_base="/usr/share/doc/j2sdk6.0-sun-doc

	changed line install-docs -i /usr/share/doc-base/sun-j2sdk1.5-doc
                  to install-docs -i /usr/share/doc-base/sun-j2sdk6.0-doc

/usr/share/java-package/sun-j2sdk6.0-doc/remove

	changed line j2se_base="/usr/share/doc/j2sdk1.5-sun-doc
                  to j2se_base="/usr/share/doc/j2sdk6.0-sun-doc

/usr/share/java-package/sun-j2sdk.sh

	added  "jdk-6-rc-bin-b92-linux-i586-20_jul_2006.bin") # UNOFFICIAL
	    	   j2se_version=6.0.0+rc
            	   j2se_expected_min_size=130
	    	   found=true
            	   ;;  

	(Please note: jdk-6-rc-bin-b92-linux-i586-20_jul_2006.bin is the current
                      snapshot binary)


After that I created the .deb package and installed it:

	I went to the directory where I downloaded the snapshot

	fakeroot make-jpkg jdk-6-rc-bin-b92-linux-i586-20_jul_2006.bin

	sudo dpkg -i sun-j2sdk6.0_6.0.0+rc_i386.deb

Now I had to manually change the versions:

	sudo update-alternatives --config java

	and selected  /usr/lib/j2sdk6.0-sun/bin/java from the list

	checked it:  java -version
			java version "1.6.0-rc"
			Java(TM) SE Runtime Environment (build 1.6.0-rc-b92)
			Java HotSpot(TM) Client VM (build 1.6.0-rc-b92, mixed mode, sharing)

Now the browser plugin:

	sudo update-alternatives --config firefox-javaplugin.so

		selected the Java6.0 plugin from the list

        checked it by opening the browser and typed 

		about:plugins
	
	and the Java6.0 plugin is listed as the current version.

If you need the following apps you have to repeat the update-alternatives for each one:

	appletviewer
	apt
	ControlPanel
	extcheck
	HtmlConverter
	idlj
	jar
	jarsigner
	java
	javac
	javadoc
	javah
	javap
	java-rmi.cgi
	javaws
	jconsole
	jdb
	jinfo
	jmap
	jps
	jsadebugd
	jstack
	jstat
	jstatd
	keytool
	native2ascii
	orbd
	pack200
	policytool
	rmic
	rmid
	rmiregistry
	serialver
	servertool
	tnameserv
	unpack200[/SIZE][/HTML]

thx, works fine here :D

---

### Post by randu on 2006-12-22
thanks, nice job

---

