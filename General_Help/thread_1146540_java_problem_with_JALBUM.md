---
title: "java problem with JALBUM"
date: 2009-05-02
forum: General Help
---

### Post by heitjer on 2009-05-02
All,
I am trying to install JALBUM and I am experiencing a few problems:

1) I downloaded the latest bin file from here:[http://jalbum.net/]("http://jalbum.net/")

2) I placed it in /tmp and then run ```
sh ./Jalbuminstall.bin
```

3) I get the following error in the terminal:

```
root@QuadCore:/tmp# PS1='' sh ./Jalbuminstall.bin
Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.lang.NoClassDefFoundError: Could not initialize class sun.awt.X11GraphicsEnvironment
	at java.lang.Class.forName0(Native Method)
	at java.lang.Class.forName(Class.java:169)
	at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:68)
	at java.awt.Window.init(Window.java:362)
	at java.awt.Window.<init>(Window.java:415)
	at java.awt.Frame.<init>(Frame.java:403)
	at java.awt.Frame.<init>(Frame.java:368)
	at com.zerog.ia.installer.LifeCycleManager.g(DashoA8113)
	at com.zerog.ia.installer.LifeCycleManager.h(DashoA8113)
	at com.zerog.ia.installer.LifeCycleManager.a(DashoA8113)
	at com.zerog.ia.installer.Main.main(DashoA8113)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at com.zerog.lax.LAX.launch(DashoA8113)
	at com.zerog.lax.LAX.main(DashoA8113)
This Application has Unexpectedly Quit: Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

```

So I have been reading up a bit and upgraded my java. 

```
root@QuadCore:~$ java -version
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Server VM (build 11.0-b15, mixed mode)

```


When I do the config I get the following:

```
root@QuadCore:/tmp# update-alternatives --config java

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-6-sun/jre/bin/java
 +        2    /usr/lib/jvm/java-6-openjdk/jre/bin/java

Press enter to keep the default[*], or type selection number: 1
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.

```

And this should be right although on the java website I am showing 6.10 and they recommend to upgrade to 6.13. 

I think the problem lies here where it says:

**Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)**

or 

**java.lang.NoClassDefFoundError: Could not initialize class sun.awt.X11GraphicsEnvironment**

I also tried this:
```
root@QuadCore:/tmp# PS1=''
sh Jalbum.bin

```


Any thoughts?

---

### Post by FluffyElmo on 2009-05-02
It's not finding your screen, which could be a video driver issue or a configuration issue (do you have multiple monitors?). Try the following export statement before launching to see if it works, it will force it to use the primary display.
```
export DISPLAY=:0.0
```

The install script also has lines commented out which let the installer run in console mode. If setting the DISPLAY variable doesn't work you may want to try that. Open the installer file in gedit and go to line 1445 for instructions.

---

### Post by FluffyElmo on 2009-05-02
Another quick thought would be to download the zip version which doesn't use an installer and try that. It's available here: [http://jalbum.net/download/Jalbum8.2.8.zip](http://jalbum.net/download/Jalbum8.2.8.zip)

---

### Post by heitjer on 2009-05-02
Thanks FluffyElmo - yes I have dual monitors but your command did not solve my problem. But I downloaded the zip and extracted it to the desktop. I am not sure what to do with it now.

I think I should copy it to a /usr/jalbum folder - is this correct?
Then how would I start it?

---

### Post by heitjer on 2009-05-02
I guess I outed me as newb....

Alright for all other newb's out there here is what I have done to get it running:

Extract the zip file in a directory of your choice. I copied mine to my **/etc/jalbum** folder.

In Gnome, right click on a **Panel > Add to Panel > Custom Application Launcher**. In the dialogue box which then appears, give your launcher a name and description ("jalbum"), and enter the command which runs your programme ("**java -jar /etc/Jalbum/JAlbum.jar**") the command you use to launch it from the terminal.

---

### Post by davidekholm on 2010-02-19
Hi all Ubuntu users. We're sorry it has been such a hazzle installing and running Jalbum on Ubuntu.
We've now polished Jalbum for Ubuntu and packaged it as a proper .deb package. Please check it out:

[http://jalbum.net/forum/thread.jspa?messageID=216632&#216632](http://jalbum.net/forum/thread.jspa?messageID=216632&#216632)

---

### Post by Don Bowen on 2010-05-25
> **davidekholm said:**
> Hi all Ubuntu users. We're sorry it has been such a hazzle installing and running Jalbum on Ubuntu.
We've now polished Jalbum for Ubuntu and packaged it as a proper .deb package. Please check it out:

[http://jalbum.net/forum/thread.jspa?messageID=216632&#216632](http://jalbum.net/forum/thread.jspa?messageID=216632&#216632)

in a frustrated manner.... well , that's nice of you, but it still doesn't work. Has anyone got Jalbum to install under 10.04?  If so, please detail how you did this.

---

