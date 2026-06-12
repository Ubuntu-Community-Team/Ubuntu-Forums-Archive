---
title: "program like 4shared desktop"
date: 2012-04-30
forum: Desktop Environments
---

### Post by forsubhi on 2012-04-30
I need program like 4shared desktop  suitable for uploading files to 4shared , do you now any one

---

### Post by kev77 on 2012-04-30
Why not use 4shared desktop? There is a Linux version ! 

[http://www.4shared.com/desktop/]("http://www.4shared.com/desktop/")

---

### Post by forsubhi on 2012-04-30
thank you kev77
I think it is new version , isn't it ?

---

### Post by forsubhi on 2012-06-14
when I run 4shared desktop , it worked and tell me to enter my account , after I entered my account , 4shared desktop **disappear **

what is the problem ?

---

### Post by forsubhi on 2012-06-14
I think this is related to error 
```

subhi@subhi-pc:~$ desktop4shared 
Guessing JAVA_HOME...
Assuming JAVA_HOME=/usr/lib/jvm/java-6-openjdk-amd64
Starting desktop4shared...
19:59:43 [AWT-EventQueue-0] INFO  Initialize - UI Initialized in 215
19:59:49 [main] ERROR common.GlobalExceptionHandler - Uncaught exception in thread [main] : the number of constructors during runtime and compile time for groovy.util.FactoryBuilderSupport do not match. Expected 3 but got 2
java.lang.IncompatibleClassChangeError: the number of constructors during runtime and compile time for groovy.util.FactoryBuilderSupport do not match. Expected 3 but got 2
        at griffon.app.ApplicationBuilder.<init>(ApplicationBuilder.groovy:26) ~[griffon-rt-0.9.jar:0.9]
        at griffon.app.ApplicationBuilder.<init>(ApplicationBuilder.groovy) ~[griffon-rt-0.9.jar:0.9]
        at griffon.builder.UberBuilder.uberInit(UberBuilder.groovy:73) ~[griffon-rt-0.9.jar:0.9]
        at org.codehaus.griffon.runtime.util.CompositeBuilderHelper.handleLocalBuilder(CompositeBuilderHelper.groovy:86) ~[griffon-rt-0.9.jar:0.9]
        at org.codehaus.griffon.runtime.util.CompositeBuilderHelper$handleLocalBuilder.callStatic(Unknown Source) ~[na:na]
        at org.codehaus.griffon.runtime.util.CompositeBuilderHelper$_createBuilder_closure1.doCall(CompositeBuilderHelper.groovy:51) ~[griffon-rt-0.9.jar:0.9]
        at org.codehaus.griffon.runtime.util.CompositeBuilderHelper.createBuilder(CompositeBuilderHelper.groovy:50) ~[griffon-rt-0.9.jar:0.9]
        at org.codehaus.griffon.runtime.util.CompositeBuilderHelper$createBuilder.call(Unknown Source) ~[na:na]
        at org.codehaus.griffon.runtime.util.GriffonApplicationHelper.buildMVCGroup(GriffonApplicationHelper.groovy:233) ~[griffon-rt-0.9.jar:0.9]
        at org.codehaus.griffon.runtime.util.GriffonApplicationHelper$buildMVCGroup.callStatic(Unknown Source) ~[na:na]
        at org.codehaus.griffon.runtime.util.GriffonApplicationHelper.createMVCGroup(GriffonApplicationHelper.groovy:191) ~[griffon-rt-0.9.jar:0.9]
        at org.codehaus.griffon.runtime.util.GriffonApplicationHelper$createMVCGroup$0.callStatic(Unknown Source) ~[na:na]
        at org.codehaus.griffon.runtime.util.GriffonApplicationHelper.createMVCGroup(GriffonApplicationHelper.groovy:171) ~[griffon-rt-0.9.jar:0.9]
        at org.codehaus.griffon.runtime.util.GriffonApplicationHelper$createMVCGroup.call(Unknown Source) ~[na:na]
        at griffon.core.BaseGriffonApplication$_startup_closure2.doCall(BaseGriffonApplication.groovy:178) ~[griffon-rt-0.9.jar:0.9]
        at griffon.core.BaseGriffonApplication.startup(BaseGriffonApplication.groovy:177) ~[griffon-rt-0.9.jar:0.9]
        at griffon.core.GriffonApplication$startup.call(Unknown Source) ~[na:na]
        at griffon.swing.SwingApplication.startup(SwingApplication.groovy) ~[griffon-rt-0.9.jar:0.9]
        at griffon.core.GriffonApplication$startup.callCurrent(Unknown Source) ~[na:na]
        at griffon.swing.SwingApplication.realize(SwingApplication.groovy:61) ~[griffon-rt-0.9.jar:0.9]
        at griffon.application.StandaloneGriffonApplication$realize.call(Unknown Source) ~[na:na]
        at griffon.swing.SwingApplication.main(SwingApplication.groovy:107) ~[griffon-rt-0.9.jar:0.9]
```

---

### Post by Breno Cesar on 2012-07-14
Hi guys !!!!

I have this same problem.
The log i got here is just the same that appears to me.....
I send an email for the support of 4shared and for the maintainer of the package...but it's been one month and a half.... :(
If anyone get any clue about this, pease help....

Seeya !!

---

### Post by Zorael on 2012-07-16
Have you tried the suggestions I posted in the other thread?

[http://ubuntuforums.org/showthread.php?p=12104449#post12104449](http://ubuntuforums.org/showthread.php?p=12104449#post12104449)

---

