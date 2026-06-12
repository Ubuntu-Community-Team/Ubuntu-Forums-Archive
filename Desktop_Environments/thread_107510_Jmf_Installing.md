---
title: "Jmf Installing"
date: 2005-12-23
forum: Desktop Environments
---

### Post by Cybercool on 2005-12-23
Hello,

i am installing JMF because i am making a application with JMF support.

IN linux you can download a packages for it and install it.

But now i must configure it, with the next steps but it doesn't work:
Installing JMF 2.1.1 with Solaris or Linux Performance Pack

The Solaris and Linux install packages contain an exectuable installation program. Run the installation program to extract JMF and then set your class path to reference the JMF directory. For example:

    setenv JMFHOME /home/someuser/JMF2.1.1
    setenv CLASSPATH $JMFHOME/lib/jmf.jar:$JMFHOME/lib/sound.jar:.:${CLASSPATH} 

You'll also need to set your LD_LIBRARY_PATH (shared libraries path) to point to the JMF libraries. For example:

    setenv LD_LIBRARY_PATH $JMFHOME/lib:${LD_LIBRARY_PATH} 

What is setenv???

---

### Post by darth_vector on 2005-12-23
have a read of this:

[http://unlser1.unl.csi.cuny.edu/tutorials/viunix/subsubsection3_3_5_20.html](http://unlser1.unl.csi.cuny.edu/tutorials/viunix/subsubsection3_3_5_20.html)

---

### Post by mustang on 2006-01-10
Hi Cybercool,

I'm not sure you're still following this thread but I found out how to install JMF after a lot of googling.

[http://lists.debian.org/debian-user-french/2004/11/msg01899.html](http://lists.debian.org/debian-user-french/2004/11/msg01899.html)

That's a french mail list but the guy basically says that since we're using the bash shell, we use different commands, namely

```

export JMFHOME=/home/someuser/JMF-2.1.1e
export CLASSPATH=$JMFHOME/lib/jmf.jar:.:$CLASSPATH
export LD_LIBRARY_PATH=$JMFHOME/lib:$LD_LIBRARY_PATH

```

Unlike what is on sun's website which are instructions for the CSH shell. 

Now I don't remember fully if those commands worked for me or if I did

```
export -x declare JMFHOME....
```

and so on for the other commands. Sorry about this!

So try what I pasted first and then try my suggestion if it doesn't work out.

---

### Post by Dave Davidson on 2006-02-27
Hi, I also am having trouble setting the CLASSPATH for JMF under unubtu.

Should the above export commands be typed into the terminal and not appended to any files?

Having tried the commands in the terminal (ammending the path to the JMF as appropriate) and then checking Sun's diagnostics applet, it still cannot find the JMF Classes. 

Any ideas anyone?

---

### Post by kaamos on 2006-02-27
Hello!

After entering those commands in a terminal, you must launch the program that uses those paths from the same terminal. If it works fine like that, you can then make it permanent by adding the commands to /home/username/.bashrc and /home/username/bash_profile

Hope this helps.

---

### Post by Dave Davidson on 2006-02-27
Hi, thnks for responding.

still no luck. I'm fairly certain I've got the paths pointing to the correct locations- yet I can't get Sun's web app to find the JMF classes!

Any other ideas where I'm going wrong?

---

### Post by hawk88 on 2006-03-13
[QUOTE=Dave Davidson]Hi, thnks for responding.

still no luck. I'm fairly certain I've got the paths pointing to the correct locations- yet I can't get Sun's web app to find the JMF classes!

Any other ideas where I'm going wrong?[/QUOTE]

I've the same problem, paths set right ant still it doesn't work :-?

---

### Post by niC666 on 2006-04-11
Hi

I'm pretty much in the same place with this, has anyone out there had any luck?
I've done pretty much everything i can think of with those jar files and my classpath, copied all the .so 's around used ldconfig to try link them dynamically, all to no avail.

The java diagnostics program still cant find the classes. Also when i try run JMStudio i get a NullPointeRexception. Did anyone manage to get JMStudio to run?

I would really like to get this working.
Thanks

niC

---

### Post by mrmcd on 2006-06-18
Yet another ubuntu user (6.06) with the same problem.  This is an issue because if I don't get this working correctly in ubuntu I will have to be code an entire project in WinXP.

I've exported the classpaths for bash, set up the exports in my .bashrc, etc. but the sun JMF diagnostics page still fails to detect the classpaths, this appears to be everybody's problem.

However, I am wondering if it is related to my key problem - I have pwc drivers installed via EasyCam, and it detects my webcam fine with programs like Canorama.
The JMF registry also detects my webcam.  The PWC drivers must be working.

However, when I run personally authored programs in eclipse, it does not detect any "capture devices" (i.e. the webcam).  

Most of the posts on JMF not working on this forum are back from 2005/Breezy.
No one has figured this out by now?
I don't want to abandon ubuntu/linux for my projects, but I'm running out of options.

---

### Post by scottpreston on 2006-06-27
I am also having problems. I have working code in Windows and want to Migrate to Linux, but the MediaLocator of v4l://0 does not work. I get the error:

Error instantiating class: com.sun.media.protocol.v4l.DataSource : 
java.io.IOException: java.lang.Error: No such capture device 

I was able to get my ENV vars set by updating /etc/environment.

Cheers,
Scott

---

### Post by vidak on 2006-07-04
the same problem here... jmstudio gives an output:
```

Exception in thread "main" java.lang.NullPointerException
        at sun.awt.X11.XMenuPeer.repaintMenuItem(Unknown Source)
        at sun.awt.X11.XMenuItemPeer.setEnabled(Unknown Source)
        at sun.awt.X11.XMenuItemPeer.disable(Unknown Source)
        at java.awt.MenuItem.disable(Unknown Source)
        at java.awt.MenuItem.enable(Unknown Source)
        at java.awt.MenuItem.setEnabled(Unknown Source)
        at JMStudio.updateMenu(JMStudio.java:1274)
        at JMStudio.<init>(JMStudio.java:119)
        at JMStudio.createNewFrame(JMStudio.java:1412)
        at JMStudio.main(JMStudio.java:1401)

```

then nothing happens... :(
somebody help, pls!

---

### Post by cortomaltes84 on 2006-07-25
Have you tried?

java -Dawt.toolkit=sun.awt.motif.MToolkit JMStudio

I assume that jmf jar files are in the classpath

bye

---

### Post by moser on 2006-09-03
It's no wonder eclipse says: com.sun.media.protocol.v4l.* not found.
Have a look into the jar, there's no subfolder v4l in media/protocol!
It's in the sources, but not in the 2.1.1e Jar/binary.
F* piece of s*

---

### Post by rockprincess on 2006-12-14
hello all,

i've got the same problem as everyone else...downloaded and install the JMF from the sun website, but still the sun diagnostics applet keeps saying

```

Java 1.1 compliant browser.....Maybe
JMF classes.....Not Found

```

my .bashrc reads as followed:

```

export JMFHOME=/home/theresa/Daten/Programmieren/JMF-2.1.1e
export CLASSPATH=$JMFHOME/lib/jmf.jar:.:$CLASSPATH
export LD_LIBRARY_PATH=$JMFHOME/lib:$LD_LIBRARY_PATH

```

---

### Post by cail on 2007-01-15
same here,
**Exception in thread "main" java.lang.NullPointerException**

I am in edgy, with sun-jdk

---

### Post by Qui on 2007-08-26
fast forware  >> 08/2007 + Feisty + firefox == updated system.  i am curious, have you found a solution to this problem.  same error. sleepess, little luck!
 
development of application halted,
qui

---

### Post by tiato on 2008-01-25
I posted a fix that worked for me using Ubuntu 7.10 & JMF 2.1.1e:

[http://ubuntuforums.org/showthread.php?p=4203390#post4203390](http://ubuntuforums.org/showthread.php?p=4203390#post4203390)

Java and JMF is working great for me on Ubuntu. 
I really hope this helps!

---

### Post by rhea112 on 2008-02-17
> **cortomaltes84 said:**
> Have you tried?

java -Dawt.toolkit=sun.awt.motif.MToolkit JMStudio

I assume that jmf jar files are in the classpath

bye

Can you explain what you mean???? may be you can give an example, or screenshoot

Please answer me..you can send your answer to [email]blackhorse20032001@yahoo.com[/email] with subject "JMF Solution"

Thanks advance

---

### Post by rhea112 on 2008-02-17
I've try to run "jmstudio" and "jmfinit" like in this bellow:

--> jmstudio 

> 
root@andromeda:~# /opt/JMF-2.1.1e/bin/jmstudio 
Exception in thread "main" java.awt.HeadlessException: 
No X11 DISPLAY variable was set, but this program performed an operation which requires it.
        at java.awt.GraphicsEnvironment.checkHeadless(GraphicsEnvironment.java:159)
        at java.awt.Window.<init>(Window.java:318)
        at java.awt.Frame.<init>(Frame.java:419)
        at jmapps.ui.JMFrame.<init>(JMFrame.java:34)
        at jmapps.ui.PlayerFrame.<init>(PlayerFrame.java:40)
        at JMStudio.<init>(JMStudio.java:118)
        at JMStudio.createNewFrame(JMStudio.java:1412)
        at JMStudio.main(JMStudio.java:1401)


--> jmfinit
> 
root@andromeda:~# /opt/JMF-2.1.1e/bin/jmfinit 
Exception in thread "main" java.awt.HeadlessException: 
No X11 DISPLAY variable was set, but this program performed an operation which requires it.
        at java.awt.GraphicsEnvironment.checkHeadless(GraphicsEnvironment.java:159)
        at java.awt.Window.<init>(Window.java:318)
        at java.awt.Frame.<init>(Frame.java:419)
        at JMFInit.<init>(JMFInit.java:23)
        at JMFInit.main(JMFInit.java:248)


And i also run 

> 
root@andromeda:/# java -Dawt.toolkit=sun.awt.motif.MToolkit JMStudio
Exception in thread "main" java.lang.NoClassDefFoundError: JMStudio
root@andromeda:/#


Any body help???please...

What is the problem??? and how to solve it??? Please send the answer to [email][COLOR="Blue"]blackhorse20032001@yahoo.com[/COLOR][/email] with subject is "JMF solution"

Thanks so much to people who has answered my question

---

### Post by alasdair.mccall on 2008-03-04
For those still battling with JMF and Ubuntu. Here is my solution (taken from tiato's post [here]("http://ubuntuforums.org/showthread.php?t=210053") which he/she solved using Sun's forum [here]("http://forum.java.sun.com/thread.jspa?threadID=741521&messageID=4255204"))

Step1. Download the JMF cross-platform Java from [http://java.sun.com]("http://java.sun.com/products/java-media/jmf/2.1.1/download.html")

Step2. Unzip the downloaded zip file anywhere, for this example let's say we unzipped the downloaded file at ```
/home/some-user/JMF-2.1.1e
```

Step3. Locate your current JRE home directory. For Ubuntu 7.10 this is installed in ```
/usr/lib/jvm/java-6-sun/jre
``` 

Step4. Copy the jar files located in ```
/home/some-user/JMF-2.1.1e/lib
``` to ```
/usr/lib/jvm/java-6-sun/jre/lib/ext
```. Note: Obviously you need to be super-user (sudo) to do this.  

Step5. Copy the file ```
/home/some-user/JMF-2.1.1e/lib/jmf.properties
``` to ```
/usr/lib/jvm/java-6-sun/jre/lib
```. Again you'll need to be super-user to do this.

Step6. Add these lines to the end of your ```
.bashrc
``` file located in your $HOME directoy.

```
export JMFHOME=/usr/lib/jvm/java-6-sun/jre/lib
export CLASSPATH=$JMFHOME/ext/jmf.jar:.:$CLASSPATH
export LD_LIBRARY_PATH=$JMFHOME/ext:$LD_LIBRARY_PATH
```

Step7. Restart GDM. Either do this by logging out and logging back in, pressing CRT+ALT+BKSPC or by restart the gdm. Either way, your enviroment settings, (Step6) won't take effect until you do.

Step8. Go to the Sun's JMF diagnostic's [webpage]("http://java.sun.com/products/java-media/jmf/2.1.1/jmfdiagnostics.html") to test if your JMF setup is working correctly.

Things to note:

i. I've only tested this for the cross-platform JMF download.
ii. You probably only need to copy across the jmf.jar file to the ../jre/lib/ext directory. But I did them all anyway
iii. The last line in the .bashrc file is probably only necessary if you want to install the performance JMF files since this is where the native library code is located.

Good Luck

---

### Post by SpookyET on 2008-04-20
It's still not working. The libraries are detected, but video and audio are not working. jmfinit fails.

sudo jmfinit
Password: 
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7efb767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb7efb8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb53d4a8d]
#3 /opt/java/jre/lib/i386/xawt/libmawt.so [0xb54d68ce]
#4 /opt/java/jre/lib/i386/xawt/libmawt.so [0xb54b3067]
#5 /opt/java/jre/lib/i386/xawt/libmawt.so [0xb54b3318]
#6 /opt/java/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x2f) [0xb54b361f]
#7 [0xb5cb2e9d]
#8 [0xb5cabedd]
#9 [0xb5cabedd]
#10 [0xb5ca9249]
#11 /opt/java/jre/lib/i386/client/libjvm.so [0x621c40d]
#12 /opt/java/jre/lib/i386/client/libjvm.so [0x6310378]
#13 /opt/java/jre/lib/i386/client/libjvm.so [0x621c2a0]
#14 /opt/java/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x363) [0x6272153]
#15 /opt/java/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb7cc496d]
#16 [0xb5cb2e9d]
#17 [0xb5cabd77]
#18 [0xb5ca9249]
#19 /opt/java/jre/lib/i386/client/libjvm.so [0x621c40d]
java: xcb_xlib.c:82: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.
zsh: abort      sudo jmfinit

---

