---
title: "Jaunty - Webex not supported"
date: 2009-05-20
forum: General Help
---

### Post by Johnny &quot;V&quot; on 2009-05-20
When I try to run support manager or access anywher  a dialog comes up in webex and states 
 
"Sorry, your OS is not supported by WEBEX"
 
I installed java by doing this
 
[INDENT]sudo apt-get install libstdc++5 sun-java6-plugin
[/INDENT]_Edit your ~/.profile and add these two lines:_
[INDENT]export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.13
export PATH=$JAVA_HOME/bin:$PATH
 
[/INDENT]I logged out logged in and still got the same error. Any ideas?

---

### Post by therblack on 2009-07-29
Were you able to get this working?

I've had little success:

-- tried standard intall of 64bit firefox.  It loads and then hangs
-- tried it with 32 bit firefox, and it doesn't even download the webex applet.  I get:

load: class JDownload not found.
java.lang.ClassNotFoundException: JDownload
	at sun.plugin2.applet.Applet2ClassLoader.findClass(Applet2ClassLoader.java:151)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at sun.plugin2.applet.Plugin2ClassLoader.loadCode(Plugin2ClassLoader.java:429)
	at sun.plugin2.applet.Plugin2Manager.createApplet(Plugin2Manager.java:2866)
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1395)
	at java.lang.Thread.run(Thread.java:619)
Caused by: javax.net.ssl.SSLKeyException: RSA premaster secret error
	at com.sun.net.ssl.internal.ssl.RSAClientKeyExchange.<init>(RSAClientKeyExchange.java:97)
	at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverHelloDone(ClientHandshaker.java:634)
	at com.sun.net.ssl.internal.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:226)
	at com.sun.net.ssl.internal.ssl.Handshaker.processLoop(Handshaker.java:516)
	at com.sun.net.ssl.internal.ssl.Handshaker.process_record(Handshaker.java:454)
	at com.sun.net.ssl.internal.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:884)
	at com.sun.net.ssl.internal.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1112)
	at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1139)
	at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1123)
	at sun.net.[www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:434](www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:434))
	at sun.net.[www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:166](www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:166))
	at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1041](www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1041))
	at java.net.HttpURLConnection.getResponseCode(HttpURLConnection.java:373)
	at sun.net.[www.protocol.https.HttpsURLConnectionImpl.getResponseCode(HttpsURLConnectionImpl.java:318](www.protocol.https.HttpsURLConnectionImpl.getResponseCode(HttpsURLConnectionImpl.java:318))
	at sun.plugin2.applet.Applet2ClassLoader.getBytes(Applet2ClassLoader.java:457)
	at sun.plugin2.applet.Applet2ClassLoader.access$000(Applet2ClassLoader.java:46)
	at sun.plugin2.applet.Applet2ClassLoader$1.run(Applet2ClassLoader.java:126)
	at java.security.AccessController.doPrivileged(Native Method)
	at sun.plugin2.applet.Applet2ClassLoader.findClass(Applet2ClassLoader.java:123)
	... 6 more
Caused by: java.security.NoSuchAlgorithmException: SunTlsRsaPremasterSecret KeyGenerator not available
	at javax.crypto.KeyGenerator.<init>(DashoA13*..)
	at javax.crypto.KeyGenerator.getInstance(DashoA13*..)
	at com.sun.net.ssl.internal.ssl.JsseJce.getKeyGenerator(JsseJce.java:223)
	at com.sun.net.ssl.internal.ssl.RSAClientKeyExchange.<init>(RSAClientKeyExchange.java:89)
	... 24 more
Exception: java.lang.ClassNotFoundException: JDownload

---

### Post by approaching on 2009-07-29
I am fairly certain that this just doesn't work at the moment (or wont). I have had it completely crash my system once.

---

### Post by moataz_mmdh on 2009-10-04
Hello
i got this error 
my OS is not support by WebEX

any solution for this problem?

i saw a lot of posts on the internet saying it works with them and i have followed their steps but also NO LUCK at all

i really confused about this problem , i need both Linux and Webex :):-({|=


Any Solutions or ideas


Ubuntu 9.0.4

---

### Post by JoeRiel on 2009-11-02
I'm having the same problem, sort of.  I am able to connect to a test webex session from the webex site, but not from my company's site.  The webex site uses the 8.5 version of webex, my company uses the 8.0 version.   I just tried installing the 32-bit version of firefox, but have the same problem reported above, the applet is not downloaded and the java console has the error, 

load: class JDownload not found.
java.lang.ClassNotFoundException: JDownload

Followup.  Using java 1.5, rather than java 6, allowed this to work with 32-bit firefox (3.5.4).  I added a link:

 ln -s /usr/lib/jvm/ia32-java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/local/firefox32/plugins

---

### Post by makemylifeeasier on 2009-12-30
I am having a similar issue.   I set up a virtual box to run 32 bit ubuntu 9.10 and followed the instructions on another thread to get java installed.  

I can join the test meeting, but when i try to start a meeting it stops with an error reading the webex downloaded file: libatdv.so  

When accessing the test meeting the files downloaded go to a local directory under .webex/ named '924' but when starting a meeting they go to a directory named '824'.   The libatdv.so file in the 924 directory is larger.  

 I have posted to Webex support and asked if there is a way to create a meeting and have it utilize the 924 files.  If anyone has any thoughts on this i would be interested to know.  I will post again when i hear from webex.

---

### Post by makemylifeeasier on 2010-01-03
I got webex working in the 32 bit version of 9-10.  The important thing is:

1) Run this to install Java

sudo apt-get install ubuntu-restricted-extras

2) Make sure you are using libstdc++5  

This package is not available in 9-10, but it can be installed from here:

[http://packages.debian.org/lenny/i386/libstdc++5/download](http://packages.debian.org/lenny/i386/libstdc++5/download)


> **makemylifeeasier said:**
> I am having a similar issue.   I set up a virtual box to run 32 bit ubuntu 9.10 and followed the instructions on another thread to get java installed.  

I can join the test meeting, but when i try to start a meeting it stops with an error reading the webex downloaded file: libatdv.so  

When accessing the test meeting the files downloaded go to a local directory under .webex/ named '924' but when starting a meeting they go to a directory named '824'.   The libatdv.so file in the 924 directory is larger.  

 I have posted to Webex support and asked if there is a way to create a meeting and have it utilize the 924 files.  If anyone has any thoughts on this i would be interested to know.  I will post again when i hear from webex.

---

### Post by dave100 on 2010-02-23
With Ubuntu 9.10 I have java plugin in place and also libstdc++5. I can join a webes meeting. But I can not see any shared information.
Any ideas?

---

### Post by markdjones82 on 2010-02-23
Dave,
  I have 9.10 and I had the Java plugin enabled, the restricted items installed (sudo apt-get install ubuntu-restricted-extras), and everything I could find on the internet.

I still could not get it to work.

So, I started firefox using command line with sudo firefox & and it worked for me.

Try running it using root permissions

---

### Post by belgianfries on 2012-07-10
I also got the "java.lang.ClassNotFoundException: JDownload" on kubuntu 12.04 64bit with Oracle JDK 6.

I can confirm that it works just fine as root.

Could be nice to know why it has to be run as root but I am already happy that it works!

Cheers,
Torsten

---

### Post by nothingspecial on 2012-07-10
[IMG]http://img845.imageshack.us/img845/6976/necro2.png[/IMG]

---

