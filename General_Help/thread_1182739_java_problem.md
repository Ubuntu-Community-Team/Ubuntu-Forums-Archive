---
title: "java problem"
date: 2009-06-09
forum: General Help
---

### Post by adelattre on 2009-06-09
I'm trying to install and run gcaldaemon.  One of the first instructions is to confirm java.  I type "java -version" and it returns:



andre@andre-laptop:~$ java -version
The program 'java' can be found in the following packages:
 * gij-4.3
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * cacao
 * gij-4.2
 * jamvm
 * kaffe
Try: sudo apt-get install <selected package>
bash: java: command not found
andre@andre-laptop:~$ 


I've installed sun-java6-bin/jre/plugin via synaptic.  Not sure why it doesn't show java installed.
After installing gcaldaemon and attempting to run the pasword-encoder.sh it returns a java error: 
"./password-encoder.sh: 8: java: not found"

Any ideas where I've gone wrong, or what else to do to determine the source of the problem?

Thanks

---

### Post by zvacet on 2009-06-09
You installed just plugin.Install sun-java6-bin package.Other way is to go to the Applications > Add/Remove > Show: All Available Applications > Search: Restricted > Click on the box next to Ubuntu Restricted Extras (top choice) > Apply changes > apply > Close.

---

### Post by sedawk on 2009-06-09
Is package "sun-java6-bin" properly installed?
```

dpkg -l sun-java6-bin

```
should show
```

ii sun-java6-bin ...

```
The package contains a file "java" in the bin directory:
```

dpkg -L sun-java6-bin |grep bin/java$

```
Running that binary with absolute path should work (/usr/lib/jvm.../bin/java -version).

If that works check if there is a symbolic link in /usr/bin:
```

ls -l /usr/bin/java

```
(I'm not sure who creates this one. On my box it points to /etc/alternatives/java. That one points to java in directory
".../java-6-sun" which (finally) is a symbolic link to the
real directory and the correct java binary.).

(If you do not have /usr/bin/java there are different workarounds,
 e.g. running "sudo dpkg-reconfigure sun-java6-bin" or creating
 the symbolic link yourself, or adding the bin directory of "sun-java6-bin" to your PATH).

---

### Post by adelattre on 2009-06-09
thanks for your help.
I *think* that step one works...
dpkg -l sun-java6-bin   returns:

andre@andre-laptop:~$ dpkg -l sun-java6-bin
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  sun-java6-bin  6-13-1         Sun Java(TM) Runtime Environment (JRE) 6 (ar
andre@andre-laptop:~$ 


then, I'm not sure what it means to "Running that binary with absolute path should work (/usr/lib/jvm.../bin/java -version)." for step two.  Can you clarify?
Thanks

---

### Post by sedawk on 2009-06-09
If you enter "java" at the command line the shell will look for the
program "java" in all directories listed in PATH.
(display with "echo $PATH").

If a program is not located in a directory in that list you have
to append that directory to that list, or start the program giving
the absolute path to that program. In your case something like
```

/usr/lib/jvm/java-6-sun-1.6.0.10/bin/java -version
# appending to PATH
export PATH=$PATH:/usr/lib/jvm/java-6-sun-1.6.0.10/bin
# now this works
java -version

```

On my computer some other trick is used. Because /usr/bin is in
the PATH normally, a symbolic link /usr/bin/java (finally) points
to /usr/lib/jvm/java-6-sun-1.6.0.10/bin/java. I have no clue why
it exists on my computer, but you can create it with
```

ln -s /usr/lib/jvm/java-6-sun-1.6.0.10/bin/java /usr/bin/java

```
Now a simple "java -version" should work even without setting PATH first.

---

### Post by TrakerJon on 2009-06-09
Go to the System menu > select Administration > select Software Sources > Check the first four boxes under the Ubuntu Software and Updates tabs > Close and Reload

From a terminal window:

sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

Then type: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Then type: sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

---

### Post by adelattre on 2009-06-10
thanks again.  that got me one step further.
now, when I do: ls -l /usr/bin/java
it returns:
andre@andre-laptop:~$ ls -l /usr/bin/java
ls: cannot access /usr/bin/java: No such file or directory
andre@andre-laptop:~$ 

I see that you're advice if there is no /usr/bin/java is to do:
(If you do not have /usr/bin/java there are different workarounds,
e.g. running "sudo dpkg-reconfigure sun-java6-bin" or creating
the symbolic link yourself, or adding the bin directory of "sun-java6-bin" to your PATH)

but I'm not quite sure what that means?

---

### Post by adelattre on 2009-06-10
nevermind.  steps one and two have solved my problem.
thanks again for your assistance!

---

### Post by adelattre on 2009-06-10
ok, so I spoke too soon.
steps one and two worked and I could launch gcaldaemon, BUT after restarting, I had to repeat the two steps for gcaldaemon to find java.

I don't seem to have a /usr/local/java directory, as when I do:
ls -l /usr/bin/java
it returns:
andre@andre-laptop:~$ ls -l /usr/bin/java
ls: cannot access /usr/bin/java: No such file or directory
andre@andre-laptop:~$

I see that you're advice if there is no /usr/bin/java is to do:
(If you do not have /usr/bin/java there are different workarounds,
e.g. running "sudo dpkg-reconfigure sun-java6-bin" or creating
the symbolic link yourself, or adding the bin directory of "sun-java6-bin" to your PATH)

but I'm not quite sure what that means?  could you elaborate, OR suggest some other way to make the PATH adjustment permanent?
Thanks

---

### Post by adelattre on 2009-06-11
bump

---

### Post by benow on 2009-06-17
This is similar to a problem which I was having due to an installation error.  Basically, the destination /usr/bin/java points to is not being found. In order to track down why /usr/bin/java is not found, you can try the following:

```
$ ls -lah /usr/bin/java
lrwxrwxrwx 1 root root 22 2009-04-11 18:23 /usr/bin/java -> /etc/alternatives/java
$ ls -lah /etc/alternatives/java
lrwxrwxrwx 1 root root 32 2009-06-17 01:10 /etc/alternatives/java -> /opt/jdk/bin/java

```
For me, it was the case that a startup script failure was occuring with /usr/bin/java not found due to /etc/alternatives/java pointing to a file that did not exist at that time (/opt is mounted with a --bind and is not there at bootup time).  I changed /etc/alternatives/java to point to the real, full, path available at bootup with
```
$ sudo ln -sf /media/storage1/opt/jdk/bin/java /etc/alternatives/
```
Admittedly, your situation is different, but the solution might be similar.

---

### Post by adelattre on 2009-06-17
thank you for the reply.  I gave up on this post and reposted a clearer question and got the following answer, which worked for me:


So all you will need to do is add the following line anywhere in that file using your favorite text editor, and save it. To test it, open up a new terminal and run 'java -version', and see if the output is as you expect.

export PATH=$PATH:/usr/lib/jvm/java-6-sun-1.6.0.13/bin

So your file might look like this...

# my favorite aliases
alias rm='rm -i'
alias cp='cp -i'
alias mv='mv -i'

#export path for gcaldaemon
export PATH=$PATH:/usr/lib/jvm/java-6-sun-1.6.0.13/bin

Make sense? You can use .bashrc for all sorts of other things too: command aliases, setting colors, tab-completion, and more.

---

