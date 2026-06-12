---
title: "error is 4shared desktop"
date: 2012-06-14
forum: Desktop Environments
---

### Post by forsubhi on 2012-06-14
I have this error 
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

### Post by air22 on 2012-07-09
i have the same error , anybody can help us?

---

### Post by Breno Cesar on 2012-07-14
yo man !!!

I have this same problem.
The log i got here is just the same that appears to me.....
I send an email for the support of 4shared and for the maintainer of the package...but it's been one month and a half....and...no answer... :(
If anyone get any clue about this, please help....

Seeya !!

---

### Post by Zorael on 2012-07-15
Simply looking at the backtrace, it looks like there's a binary incompatibility with groovy. With some extra linebreaks;
```
java.lang.IncompatibleClassChangeError: the number of constructors
during runtime and compile time for groovy.util.FactoryBuilderSupport
do not match. **Expected 3 but got 2**
```

Some quick Googling reveals [http://jira.codehaus.org/browse/GROOVY-4802](http://jira.codehaus.org/browse/GROOVY-4802);
[quote=Guillame Laforge][...] this [third] constructor was already deprecated in Groovy 1.6 (in some 1.5.x release).
We kept the deprecation of that constructor in two major releases.
It's indeed only in Groovy 1.8 that we removed that deprecation, and this happened already in June 2010!
I'm not sure we should follow the JDK approach that keeps all the deprecated things forever [/quote]

You don't mention what Kubuntu release you're running, but the precise repository version of groovy is **2.0.0~beta2+_isreally1.8.6-0ubuntu1_**.

What you want to do is to downgrade it to an earlier (< 1.8) version, such as 1.7 that was released with 11.10 oneiric. The easiest way is to [download that package from packages.ubuntu.com](http://packages.ubuntu.com/oneiric/all/groovy/download) and manually install the deb file. (Admittedly you could instead add some oneiric repositories to your apt sources, if you prefer that approach.)

Apologies if this is a bit basic and obvious, but for Googlers who don't know the dance; download the .deb, find it in Dolphin, and double-click it to open up QApt for installation. Or do it from a terminal;
```
$ sudo dpkg -i */path/to/***groovy_1.7.10-2_all.deb**
```

At this point your desktop4shared should work properly -- or at the very least, crash with some other error. ; 3

The next big hurdle is getting package managers to not upgrade the package; there is an update in the precise repositories, after all. They don't always listen to eachothers' settings but the following should be enough;
```
$ printf '**Package: groovy\nPin: version 1.7*\nPin-Priority: 1001\n**' | sudo tee **/etc/apt/preferences.d/groovy**
$ echo **groovy hold** | sudo dpkg --set-selections
$ sudo aptitude **hold groovy**  *# you may not have aptitude installed, in which case this won't work -- ignore if so*
```

If you're using some other exotic package manager (such as smartd), look to its documentation for hints on how to pin/hold packages. Hopefully it should then stay at 1.7 at package upgrades.

---

### Post by Breno Cesar on 2012-07-17
Yo Zorael !!!!

Thanks for your help man....
I make the downgrade as you sugest and its realy works !!

thanks a lot man !!!..=)...:D

---

### Post by felipemartim on 2012-08-11
Worked for me too, thanks a bunch!

---

### Post by judgeg on 2012-10-09
Groovy!!!  thanks its worked here too.  Why don't 4Shared update their app to work?  Surely there's enough Ubuntu users to comapign for a change?

Cheers

---

### Post by Zorael on 2012-10-10
Reasons could be that they outsourced the linux tweaks and don't have the knowhow in-house to update it -- or they simply don't care to spend the effort on a minority userbase when they could spend the manhours on their Win/Mac versions.

I'm inclined to think that whatwith the program being written in Java it would be a trivial thing to do, but I'm not an authority on the language. That's assuming they own the source of said linux-specific modifications and are not bound by license to keep their hands off of it.

---

### Post by Sepero on 2012-10-17
Excellent stuff Zorael. The growth of Linux really depends on intelligent individuals like yourself. This problem affects everyone using Ubuntu 12.04 (and probably 12.10 too). I made a blog post referencing the fix you listed here, in the hopes that it will gain a little more attention and help a few more people. Any further suggestions/corrections are welcome. Cheers
[http://seperohacker.blogspot.com/2012/10/solved-4shared-desktop-crashes-on-linux.html](http://seperohacker.blogspot.com/2012/10/solved-4shared-desktop-crashes-on-linux.html)

---

### Post by wladypauly on 2012-12-19
I sent a mail to the devs as far back as September, but no reply came back. I think they just let the matter drop...

---

### Post by cvnmjs on 2013-10-13
just today i tried out desktop4shared 1.3_1 deb pkg on raring.:| the only different thing i did was search thru "muon" for groovy.:-k i decided to install ```
libgroovy1.7.2-java
``` in addition to the groovy 2 pkg:confused:. 
this time, after fixing the missing deps, the application launched! :grin:

if i get some free time i will try removing the above-mentioned pkg & see what effect this has.

also it could be that 4shared updated their application since the last time i tried it.

hope this helps!

cheers.

---

