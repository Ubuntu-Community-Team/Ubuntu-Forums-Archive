---
title: "Openoffice.org headless and jodconverter problem in ubuntu Jaunty"
date: 2009-05-07
forum: General Help
---

### Post by reza.adinata on 2009-05-07
Hi all, 
I am trying to install JODConverter in Ubuntu Jaunty Server. I have already installed the openoffice.org-headless (it points out to openoffice.org-core) and set the java_home
> 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.13/"


and the openoffice seems to work just fine :

> root@ubuntu:~# netstat -nap | grep office
tcp        0      0 127.0.0.1:8100          0.0.0.0:*               LISTEN                                                                                   2249/soffice.bin

But the result after I execute below 

**root@ubuntu**:/home/ubuntu/jodconverter-2.2.1/jodconverter-2.2.1/lib# java -jar jodconverter-cli-2.2.1.jar /home/ubuntu/sample.ppt /home/test.swf

> 
May 8, 2009 9:33:52 AM com.artofsolving.jodconverter.openoffice.connection.AbstractOpenOfficeConnection connect
INFO: connected
May 8, 2009 9:33:53 AM com.artofsolving.jodconverter.openoffice.connection.AbstractOpenOfficeConnection disposing
INFO: disconnected
Exception in thread "main" com.artofsolving.jodconverter.openoffice.connection.OpenOfficeException: conversion failed: could not load input document
        at com.artofsolving.jodconverter.openoffice.converter.OpenOfficeDocumentConverter.loadAndExport(OpenOfficeDocumentConverter.java:131)
        at com.artofsolving.jodconverter.openoffice.converter.OpenOfficeDocumentConverter.convertInternal(OpenOfficeDocumentConverter.java:120)
        at com.artofsolving.jodconverter.openoffice.converter.AbstractOpenOfficeDocumentConverter.convert(AbstractOpenOfficeDocumentConverter.java:104)
        at com.artofsolving.jodconverter.openoffice.converter.AbstractOpenOfficeDocumentConverter.convert(AbstractOpenOfficeDocumentConverter.java:74)
        at com.artofsolving.jodconverter.openoffice.converter.AbstractOpenOfficeDocumentConverter.convert(AbstractOpenOfficeDocumentConverter.java:70)
        at com.artofsolving.jodconverter.cli.ConvertDocument.convertOne(ConvertDocument.java:134)
        at com.artofsolving.jodconverter.cli.ConvertDocument.main(ConvertDocument.java:113)
Caused by: com.sun.star.lang.IllegalArgumentException: URL seems to be an unsupported one.
        at com.sun.star.lib.uno.environments.remote.Job.remoteUnoRequestRaisedException(Job.java:187)
        at com.sun.star.lib.uno.environments.remote.Job.execute(Job.java:153)
        at com.sun.star.lib.uno.environments.remote.JobQueue.enter(JobQueue.java:349)
        at com.sun.star.lib.uno.environments.remote.JobQueue.enter(JobQueue.java:318)
        at com.sun.star.lib.uno.environments.remote.JavaThreadPool.enter(JavaThreadPool.java:106)
        at com.sun.star.lib.uno.bridges.java_remote.java_remote_bridge.sendRequest(java_remote_bridge.java:657)
        at com.sun.star.lib.uno.bridges.java_remote.ProxyFactory$Handler.request(ProxyFactory.java:159)
        at com.sun.star.lib.uno.bridges.java_remote.ProxyFactory$Handler.invoke(ProxyFactory.java:141)
        at $Proxy5.loadComponentFromURL(Unknown Source)
        at com.artofsolving.jodconverter.openoffice.converter.OpenOfficeDocumentConverter.loadDocument(OpenOfficeDocumentConverter.java:150)
        at com.artofsolving.jodconverter.openoffice.converter.OpenOfficeDocumentConverter.loadAndExport(OpenOfficeDocumentConverter.java:127)
        ... 6 more


Please point out what I probably do wrong? I need an automated converter server :(

Thank you so much

---

### Post by reza.adinata on 2009-05-07
Still don't know how to implement it in Ubuntu Server. 

I tried to install a headless server in Xubuntu and Ubuntu Desktop  with an extra ooo headless server and tried to remote via the terminal.. It works just fine in converting, and the ooo did not load its GUI on the Desktop (just as I want it to be). 

hope to discuss with any of you who have managed to install it in Ubuntu Server.. 

cheers
R.A

---

### Post by briantatl on 2009-08-14
You need to install the openoffice.org package as well as the openoffice.org-headless and openoffice.org-java-common . This one caught me for a while too.

---

