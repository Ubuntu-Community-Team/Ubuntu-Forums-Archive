---
title: "JAVA_HOME env. variable - JDK"
date: 2006-01-02
forum: General Help
---

### Post by zambizzi on 2006-01-02
I followed these instructions to install the JDK...and it's installed...yet I have no JAVA_HOME env. variable (which really screws me up when trying to run an app server such as Tomcat or JBoss.)

[https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca](https://wiki.ubuntu.com/RestrictedFormats#head-e2ebd70ede0e3eb2117ffbd618d2295dd1540dca)

When I look here:

```

me@mybox$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
 +    2        /usr/lib/jvm/java-gcj/bin/java
*     3        /usr/lib/j2sdk1.5-sun/bin/java

Press enter to keep the default[*], or type selection number:

```

Obviously the setup in the instructions in the link I posted above worked correctly...except for the missing JAVA_HOME variable.  I'm able to run Netbeans using the newly installed JDK but that's because it didn't require the  JAVA_HOME variable during setup.

Why would it not set this automatically?  It's a vital piece of using the JDK after all! :confused: 

Anyhow...I can't figure out the proper place to set it manually.  I've been using Gentoo for years and I would have just created a file defining the env. variable in /etc/conf.d/java but there is no such thing in Ubuntu, so far as I can tell.

Any ideas?  Thanks!

---

### Post by ape on 2006-01-02
Actually, JAVA_HOME is never set by any JDK.  This is a requirement of the program that is needing this set.  It is there to allow you to configure Tomcat or JBoss against different Java runtimes.

If you need to set JAVA_HOME, you should do this within your .bash_profile yourself.

---

### Post by zambizzi on 2006-01-02
[QUOTE=ape]Actually, JAVA_HOME is never set by any JDK.[/QUOTE]

Well yeah, I realize that...if it appeard I was implying that...then I apologize.  What I meant was...during the whole process of installing the JDK it would have been very handy to have that set for me automatically somewhere in the system.

Thanks for the info, I'll work on it.

---

### Post by zambizzi on 2006-01-02
So I put the variable in my .bash_profile like so (entire contents):

```

# ~/.bash_profile: executed by bash(1) for login shells.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/login.defs
#umask 022

# include .bashrc if it exists
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

JAVA_HOME="/usr/lib/j2sdk1.5-sun/"

```

I've since rebooted and when I "echo $JAVA_HOME" there is still no value.

Did I do something wrong?  I do not have /usr/share/doc/bash/examples/startup-files or I would have looked there for examples.

---

### Post by roncrump on 2006-01-02
[QUOTE=zambizzi]So I put the variable in my .bash_profile like so (entire contents):

```


<snipped>

JAVA_HOME="/usr/lib/j2sdk1.5-sun/"

```

I've since rebooted and when I "echo $JAVA_HOME" there is still no value.

Did I do something wrong?  I do not have /usr/share/doc/bash/examples/startup-files or I would have looked there for examples.[/QUOTE]

I think you need to export the value.
That is, add:
```

export JAVA_HOME

```
on a line after the variable has been set.

HTH,
Ron.

---

### Post by zambizzi on 2006-01-03
I can't believe I forgot that...but no...that didn't do the trick either.

Here's what I've got:

```

# ~/.bash_profile: executed by bash(1) for login shells.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/login.defs
#umask 022

# include .bashrc if it exists
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

JAVA_HOME="/usr/lib/j2sdk1.5-sun/"
export JAVA_HOME

```

Obviously, I can set JAVA_HOME by doing those same two lines manually but where do I put it to set it automatically? :-k

---

### Post by ape on 2006-01-03
Hmm... just checking, but you are using bash as your shell, correct?  If so, do you still not see the JAVA_HOME variable if you run `xterm -ls` (which forces a login shell which will read .bash_profile).  If this does work, you may try removing the JAVA_HOME config from the .bash_profile and instead add it to your .bashrc.

If you are not using bash, what shell are you using?

---

### Post by mattsouth on 2006-01-03
I have the same problem.  I have added the suggested entry to .bash_profile and in the terminal raised by `xterm -ls` I can successfully "echo $JAVA_HOME" and see it in the list of environment variables if I type "export", however I cant do either in a normal terminal window.

---

### Post by zambizzi on 2006-01-03
[QUOTE=mattsouth]I have the same problem.  I have added the suggested entry to .bash_profile and in the terminal raised by `xterm -ls` I can successfully "echo $JAVA_HOME" and see it in the list of environment variables if I type "export", however I cant do either in a normal terminal window.[/QUOTE]

Hmm, same here.  So what does this mean?

And yes, I'm using bash.

---

### Post by zambizzi on 2006-01-03
[QUOTE=ape]...you may try removing the JAVA_HOME config from the .bash_profile and instead add it to your .bashrc[/QUOTE]

This did the trick...thanks!

---

### Post by mattsouth on 2006-01-04
Adding the two lines to .bashrc works for me too.  Now I just need to work out how to start tomcat on startup and check that JAVA_HOME is set before tomcat is started.  In the meantime I can start it manually.

---

### Post by steve.horsley on 2006-01-04
Here is the contents of my file /etc/init.d/tomcat:
> export JAVA_HOME=/opt/jdk1.5.0_03/jre
case "$1" in
  start)
    /opt/jakarta-tomcat-5.5.9/bin/startup.sh
  ;;

  stop)
    /opt/jakarta-tomcat-5.5.9/bin/shutdown.sh
  ;;

  restart)
    /opt/jakarta-tomcat-5.5.9/bin/shutdown.sh
    /opt/jakarta-tomcat-5.5.9/bin/startup.sh
  ;;

  *)
    echo $"Usage: $0 {start|stop}"
    exit 1
esac



After installing this file, you can start tomcat with **sudo /etc/init.d/tomcat start**. The neat thing is that now you can make it start on boot-up just by creating a symbolic link to it from /etc/rc3.d like this:
> sudo ln -s /etc/init.d/tomcat /etc/rc2.d/S20tomcat
I believe that this is the "proper" way to start services. rc2.d, rc3.d etc are a folder full of the services to start/stop at each of Linux's different run levels. Ubuntu defaults to using runlevel 2. You can stop the service from auto-starting by deleting the S20tomcat symbolic link to the real script. The S20 (Start 20) provides a way of controlling the order in which services are started. 

Once the script is in place, a GUI tool called bum (Boot Up Manager, in Synaptic) helps maintaining all the symlinks.

---

### Post by gltonn on 2006-01-26
Where did you get TomCat and what were the steps that you used to install it?

Thanks

---

