---
title: "setclasspath does not see JAVA_HOME"
date: 2009-01-02
forum: General Help
---

### Post by rduncan on 2009-01-02
When starting a shell as superuser, it doesn't see the environment variables.

Here is a very simple shell:
rduncan@Antec:~$ cat testagain
#!/bin/sh
echo $JAVA_HOME

Here is running it as a normal user:
rduncan@Antec:~$ ./testagain
/usr/local/jdk1.6.0

Here is running it as superuser:
rduncan@Antec:~$ sudo ./testagain

Here is simply echo-ing the variable as superuser:
rduncan@Antec:~$ sudo echo $JAVA_HOME
/usr/local/jdk1.6.0

Any ideas?




I have apache-tomcat 5.5 installed on my ubuntu system but I only use it occasionally to test applications before uploading them. 

Today when I went to startup tomcat I got this message:

Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program

But I can echo $JAVA_HOME:

rduncan@Antec:/usr/local/apache-tomcat-5.5.20/bin$ echo $JAVA_HOME
/usr/local/jdk1.6.0

I can also cd to $JAVA_HOME and it looks like all the files are there.

The last change I made to the system was upgrading to the latest ubuntu. The upgrade installed a new sysctl.conf, but I compared it to the old one and don't see any difference that seems like it would cause this problem.

I haven't made any changes to my tomcat or java installations.

I was defining JAVA_HOME in /etc/profile. I also tried putting it in /etc/environment. That didn't help.

Does anybody know what's going on here?

Thanks.

Apparently it has to do with the fact that I have to start tomcat as superuser.

I made it simple little script:

rduncan@Antec:~$ more testit
#!/bin/sh

if [ -z "$JAVA_HOME" -a -z "$JRE_HOME" ]; then
  echo "They were zero bytes";
else
  echo "Something had data";
fi

Then run as normal user:

rduncan@Antec:~$ ./testit
Something had data

Then run as superuser:

rduncan@Antec:~$ sudo ./testit
They were zero bytes

So what do I have to do to get superuser to see $JAVA_HOME.

I've got it set in /etc/profile and /etc/environment.

---

