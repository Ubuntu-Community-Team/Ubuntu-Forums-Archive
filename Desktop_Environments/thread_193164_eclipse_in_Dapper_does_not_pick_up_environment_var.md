---
title: "eclipse in Dapper does not pick up environment vars"
date: 2006-06-09
forum: Desktop Environments
---

### Post by tfandango on 2006-06-09
Hi-

I've installed eclipse 3.2RC7 on a new Dapper install.  I have noticed that it doesn't seem to know anything about the environment I've set up in my local .bashrc file.  For instance, it does not know where the maven executable is even though I've specified it as part of the PATH variable and verified that it works in a terminal.  This isn't that big of a del except that I'd like to create some exteral tasks in eclipse to call maven, and maven requires a JAVA_HOME variable set.

Does anyone knoe how to tell eclipse to pick up the user's environment?

Thanks!
troy

---

### Post by grigpi on 2006-06-09
Try setting JAVA_HOME in /etc/environment.

---

### Post by jvictor on 2006-06-10
Eclipse uses its own CLASSPATH and env variables. IMHO they do this to avoid interfering with other applications. The only mandatory thing that is needed for eclipse is JAVA_HOME. and it needs to be set in ~/.bashrc and exported too.

I hope you've installed the SUN JDK and are sure that JAVA_HOME is set properly. 

Coming to maven, one reason why I chose ANT over it is because of this Integration issues with IDEs. There are some plugins that help u do some maven stuff in Eclipse, but the real 'integration' you find for ANT is missing in Maven. So as for now maven sux for IDE based development. PERIOD

---

### Post by tfandango on 2006-06-12
thanks.  Yea, everything is set up and works fine via command line, and it's not a big deal to switch to a terminal to set call maven commads.  We are pretty much stuck using it here because of the way our build environment is set up at work.  

Thanks for your help!

-troy

---

### Post by cowmix on 2006-06-23
Shouldn't you be able to set JAVA_HOME via your .bashrc though?   

[QUOTE=grigpi]Try setting JAVA_HOME in /etc/environment.[/QUOTE]

---

