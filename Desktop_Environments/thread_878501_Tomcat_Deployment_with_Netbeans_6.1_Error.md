---
title: "Tomcat Deployment with Netbeans 6.1 Error"
date: 2008-08-03
forum: Desktop Environments
---

### Post by theblang on 2008-08-03
I am having an issue deploying the bundled tomcat with Netbeans 6.1.  I downloaded the Netbeans 6.1 installer.sh from the official site and left everything default during installation (tomcat and netbeans both installed to home directory).  If I try running a jsp I receive the following error (pasted below).  Any help would be greatly appreciated.

init:
deps-module-jar:
deps-ear-jar:
deps-jar:
Created dir: /home/theblang/NetBeansProjects/WebApplication1/build/web/WEB-INF/classes
Created dir: /home/theblang/NetBeansProjects/WebApplication1/build/web/META-INF
Copying 1 file to /home/theblang/NetBeansProjects/WebApplication1/build/web/META-INF
Copying 3 files to /home/theblang/NetBeansProjects/WebApplication1/build/web
library-inclusion-in-archive:
library-inclusion-in-manifest:
compile:
compile-jsps:
Created dir: /home/theblang/NetBeansProjects/WebApplication1/build/generated/src
Created dir: /home/theblang/NetBeansProjects/WebApplication1/build/generated/classes
Compiling 1 source file to /home/theblang/NetBeansProjects/WebApplication1/build/generated/classes
In-place deployment at /home/theblang/NetBeansProjects/WebApplication1/build/web
Deployment is in progress...
deploy?config=file:/tmp/context29974.xml&path=/WebApplication1
[http://localhost:8180/manager/deploy?config=file:/tmp/context29974.xml&path=/WebApplication1](http://localhost:8180/manager/deploy?config=file:/tmp/context29974.xml&path=/WebApplication1)
Deployment error:
The module has not been deployed.
See the server log for details.
        at org.netbeans.modules.j2ee.deployment.devmodules.api.Deployment.deploy(Deployment.java:166)
        at org.netbeans.modules.j2ee.ant.Deploy.execute(Deploy.java:104)
        at org.apache.tools.ant.UnknownElement.execute(UnknownElement.java:288)
        at sun.reflect.GeneratedMethodAccessor46.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:597)
        at org.apache.tools.ant.dispatch.DispatchUtils.execute(DispatchUtils.java:105)
        at org.apache.tools.ant.Task.perform(Task.java:348)
        at org.apache.tools.ant.Target.execute(Target.java:357)
        at org.apache.tools.ant.Target.performTasks(Target.java:385)
        at org.apache.tools.ant.Project.executeSortedTargets(Project.java:1329)
        at org.apache.tools.ant.Project.executeTarget(Project.java:1298)
        at org.apache.tools.ant.helper.DefaultExecutor.executeTargets(DefaultExecutor.java:41)
        at org.apache.tools.ant.Project.executeTargets(Project.java:1181)
        at org.apache.tools.ant.module.bridge.impl.BridgeImpl.run(BridgeImpl.java:277)
        at org.apache.tools.ant.module.run.TargetExecutor.run(TargetExecutor.java:460)
        at org.netbeans.core.execution.RunClassThread.run(RunClassThread.java:151)
Caused by: The module has not been deployed.
        at org.netbeans.modules.j2ee.deployment.devmodules.api.Deployment.deploy(Deployment.java:160)
        ... 16 more
BUILD FAILED (total time: 39 seconds)

---

### Post by theblang on 2008-08-03
So I wasn't using the bundled Tomcat I was using the Tomcat 5.5 package I had installed in the past.  I am still curious what the error is though.

---

