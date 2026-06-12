---
title: "Jmf"
date: 2006-09-11
forum: Desktop Environments
---

### Post by the.grey.lantern on 2006-09-11
Hello,

I need help getting JMF up and running.

I get the message 'Native Libraries Not Found' When I load the JMF Diagnostics Applet: [http://java.sun.com/products/java-media/jmf/2.1.1/jmfdiagnostics.html]("http://java.sun.com/products/java-media/jmf/2.1.1/jmfdiagnostics.html")

I have searched the forums and on Google and none of the solutions suggested work for me.

**Contents of /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/ext**
```

****me@me:/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/ext$ dir
customizer.jar  jmf.jar         mediaplayer.jar  sunjce_provider.jar
dnsns.jar       localedata.jar  multiplayer.jar  sunpkcs11.jar
```

**Contents of /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386**
```

me@me:/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386$ dir
awt_robot      libdeploy.so                 libjava.so          libnio.so
client         libdt_socket.so              libjawt.so          libodbcinst.so
gtkhelper      libfontmanager.so            libJdbcOdbc.so      libodbc.so
headless       libhprof.so                  libjdwp.so          librmi.so
jmfcustomizer  libinstrument.so             libjpeg.so          libsaproc.so
jmfinit        libioser12.so                libjsig.so          libunpack.so
jmfregistry    libj2pkcs11.so               libjsoundalsa.so    libverify.so
jmstudio       libjaas_unix.so              libjsound.so        libzip.so
jvm.cfg        libjava_crw_demo.so          libmanagement.so    motif21
libawt.so      libjavaplugin_jni.so         libmlib_image.so    native_threads
libcmm.so      libjavaplugin_nscp_gcc29.so  libnative_chmod.so  server
libdcpr.so     libjavaplugin_nscp.so        libnet.so           xawt

```

**I have set all the relevant information using the following commands**
```

export JMFHOME=/home/me/JMF-2.1.1e
export CLASSPATH=$JMFHOME/lib/jmf.jar:.:${CLASSPATH}
export LD_LIBRARY_PATH=$JMFHOME/lib:${LD_LIBRARY_PATH}

```

I am a Linux newbie so please bear with me. I don't want to go to Windows XP just so I can use JMF! ](*,) 

Thanks for your help :D

---

