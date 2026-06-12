---
title: "Jalbum, photo album maker"
date: 2008-12-24
forum: General Help
---

### Post by Wobblybob on 2008-12-24
I have been using the Jalbum application since before I started out on Ubuntu and was glad to find out it has a Linux version that work on Ubuntu too. The program lets you create and upload your photos as a web album, see mine here [COLOR="red"][http://www.sofabedz.co.uk/]("http://www.sofabedz.co.uk/")[/COLOR] as an example. I have just downloaded Jalbum v8.1.4 and installed it on Intrepid and had some problems getting it up and running so here is how I did it.

First download Jalbum from [COLOR="Red"][http://jalbum.net/]("http://jalbum.net/")[/COLOR] to your home folder then you need to add a java Vm so in a Terminal type;

**sudo apt-get install -y sun-java6-jre**

then in the same Terminal, type;

**sh ./Jalbuminstall.bin**

this should start the Jalbum installer which should find your java VM and install Jalbum. In my case this did not happen as it could not find the java VM so if you have the same problem, in a terminal type;

**sudo update-alternatives --config java**

this will allow you to select your default java, select java6-sun and note down the path to it, mine is /usr/lib/jvm/java-6-sun/jre/bin/java

now start the install again with;
[B]
sh ./Jalbuminstall.bin[/B]

and when the installer fails to find java, select the (Choose Another) option, navigate to the java you have selected above, in my case;
/usr/lib/jvm/java-6-sun/jre/bin/java

then click on (Next) and all should install correctly. There will be no automatic program launcher created but you can navigate to the folder you have installed Jalbum in and double click on the Jalbum file or type Jalbum in the Terminal or create your own launcher.

If you need a more detailed description or help creating a Launcher, please visit my web site at [here]("http://sofabedz.co.uk/linux/")

Good Luck

---

### Post by washakie on 2009-03-08
I had some problems installing Jalbum, so I thought I would make an addition to this post.

1) Download and unpack Jalbum from the site.

2) When running the Jalbum.bin file, if you encounter problems with Java, it is likely due to a malformated PS1 string... do the following:

```

sudo PS1=''
/bin/sh Jalbum.bin

```

Now the installer should run, select the Java_vm as mentioned above. Here's a trick I did for running it. Once you've installed the software, do the following to create a link to it from /usr/bin that you can run using ALT-F2:

```

cd /usr/bin
sudo vi Jalbum

```

Enter the following lines to the file:
```
#!/bin/bash
PS1='' /opt/Jalbum/Jalbum &

```

Exit & save (ZZ), Now one more step:
```
chmod 0755 Jalbum

```

That should do it! Now any user can type 'Jalbum' at the prompt and launch the application.

Good luck, happy photoing!

---

### Post by davidekholm on 2010-02-19
Hi all Ubuntu users. We've now polished Jalbum for Ubuntu and packaged it as a proper .deb package. Please check it out:

[http://jalbum.net/forum/thread.jspa?messageID=216632&#216632](http://jalbum.net/forum/thread.jspa?messageID=216632&#216632)

---

### Post by Don Bowen on 2010-05-25
> **davidekholm said:**
> Hi all Ubuntu users. We've now polished Jalbum for Ubuntu and packaged it as a proper .deb package. Please check it out:

[http://jalbum.net/forum/thread.jspa?messageID=216632&#216632](http://jalbum.net/forum/thread.jspa?messageID=216632&#216632)

Yes, but it still doesn't work under 10.04.  The installation complains that it can't find some JRE file it needs... Has anyone got JAlbum to install correctly uner 10.04.  I've been reading all sorts of posts, but so far nothing has worked.

---

### Post by Wobblybob on 2010-11-30
bit late coming back to this but yes I have had this working in 10.04 and now 10.10 you still need to add java

install sun-java6-jre or later, from the listed packages and install it.We then need to make sure it is the default Java VM running on your PC.

Open a [Terminal] type or copy and paste;

sudo update-alternatives --config java

which should give you an output like this;

There are 2 alternatives which provide `java’.
Selection Alternative
———————————————–
* 1 /usr/lib/jvm/java-6-sun/jre/bin/java
+ 2 /usr/lib/jvm/java-6-openjdk/jre/bin/java<
Press enter to keep the default[*], or type selection number:

Select java-6-sun by typing the number next to the correct version.

now install the jalbum .bed file

my blog full post [[COLOR="Navy"]http://myubuntublog.wordpress.com/2010/10/24/jalbum-create-photo-web-albums/[/COLOR]]("http://myubuntublog.wordpress.com/2010/10/24/jalbum-create-photo-web-albums/")

Good Luck

---

