---
title: "Frustrated with Java"
date: 2009-04-22
forum: General Help
---

### Post by gspawn69 on 2009-04-22
Hi,

I'm trying to install the latest version (1.6.0u13) of Java from the sun website, and I can't get it to work. Whenever I run a java applet, it's still using an older version, despite me following the instructions on the java site, and firefox refuses to acknowledge the new version of the plugin, even though I've created the symbolic link. Can somebody please post a step-by-step guide for installing this? Or better yet, has someone made a .deb for it? The version in the repos is still only version 1.6.0u07, so it hasn't been updated in a while.

Also, i'm running Ubuntu Studio 8.04, if that makes a difference.

---

### Post by johannes_h on 2009-04-22
Search for jdk in the synaptic package manager

---

### Post by rickbeton on 2009-04-22
I often install JDKs manually because I need to switch between several versions, and also because I add extensions to them such as JAI (I don't like meddling with the packages that have been installed and managed by Apt).

So I download the .sh installer from the Sun website and run it in /opt via 'sudo'. This happily unpacks the JDK there, but to use it you also need to set some shell variables manually.

```
export JAVA_HOME=/opt/jdk1.6.0u12
PATH=$JAVA_HOME/bin:$PATH
```

These are best added to ~/.bashrc or one of the config files in /etc.

You might also find functions useful, e.g

```
function useJava5()
{
    export JAVA_HOME=/opt/jdk1.5
    export PATH=$JAVA_HOME/bin:$PATH
}
```

Note that Firefox will itself depend on the shell variables defined when it is started. So you might need to log out/in again to get the new JDK used by Firefox (or just lauching from a command terminal).

Rick

---

