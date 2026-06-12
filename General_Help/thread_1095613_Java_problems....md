---
title: "Java problems..."
date: 2009-03-13
forum: General Help
---

### Post by Shiv4m on 2009-03-13
Okay first Java was working for me but then I got his JDK error so I removed Java from synaptic and reinstalled everything successfully. I then try to play a java powered game and it tells me no Java is installed or enabled, help please!

---

### Post by ScatterINC on 2009-03-13
Sorry man to be posting stuff on your question but i dont know where to post or how to post. Is there a portable Ubuntu that can be run from my jump drive?

---

### Post by Shiv4m on 2009-03-13
> **ScatterINC said:**
> Sorry man to be posting stuff on your question but i dont know where to post or how to post. Is there a portable Ubuntu that can be run from my jump drive?

[http://www.google.com/search?hl=en&safe=off&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=46e&ei=Wh67ScXIM9eJtgeGoPz5Cw&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=ubuntu+run+off+flash+drive&spell=1](http://www.google.com/search?hl=en&safe=off&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=46e&ei=Wh67ScXIM9eJtgeGoPz5Cw&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=ubuntu+run+off+flash+drive&spell=1)

---

### Post by doas777 on 2009-03-13
> **Shiv4m said:**
> Okay first Java was working for me but then I got his JDK error so I removed Java from synaptic and reinstalled everything successfully. I then try to play a java powered game and it tells me no Java is installed or enabled, help please!

does synaptic still show a jre installed?
what flavor/version are you talkin?

what is the output of 
```
java --version
javac --version

```

---

### Post by Shiv4m on 2009-03-13
Yes it shows as it is installed and what do you mean what is the output? How can I check that out?

---

### Post by doas777 on 2009-03-14
ahhh. welcome to online linux support. usually you will find people giving instructions in terms of terminal commands, because everyones desktop is different and its a lot easier to just work in text.

so all you have to do, is go to Applications -> Accessories -> Terminal
and paste in the commands in my previous post/. you can paste into a terminal by Right Clicking -> paste, or with Ctrl + Shift + V, if your into key commands.

just to clarify, you show both an JDK and a JRE installed?

---

### Post by Shiv4m on 2009-03-14
Yes I was trying to get JDK I think, it is for a program called "RsBot."

[IMG]http://img16.imageshack.us/img16/2346/screenshotdaj.png[/IMG]

[http://img16.imageshack.us/img16/2346/screenshotdaj.png](http://img16.imageshack.us/img16/2346/screenshotdaj.png)

---

### Post by doas777 on 2009-03-14
ok, try this one:
```

java -version
javac -version

```\

---

### Post by Shiv4m on 2009-03-14
Same thing happened...

[IMG]http://img515.imageshack.us/img515/4645/screenshotshivamshivaml.png[/IMG]

[IMG]http://img209.imageshack.us/img209/4645/screenshotshivamshivaml.png[/IMG]

I could try installing it from [http://java.com/en/download/linux_manual.jsp?host=java.com&returnPage=http%3A%2F%2Fworld90.runescape.com%2Fj1_o0_a0_m1](http://java.com/en/download/linux_manual.jsp?host=java.com&returnPage=http%3A%2F%2Fworld90.runescape.com%2Fj1_o0_a0_m1) but I don't know how to install .bin. Could anyone help me with that?

---

### Post by taurus on 2009-03-14
Didn't you already have a few threads regarding this issue?

```
sudo apt-get update
sudo apt-get install sun-java6-jdk
```

---

### Post by Shiv4m on 2009-03-14
Still doesn't work :(

And no I don't think I posted another thread about this, as this happened for the first time.

---

### Post by taurus on 2009-03-14
> **Shiv4m said:**
> Still doesn't work :(

And no I don't think I posted another thread about this, as this happened for the first time.

What are the outputs of these two commands?

```
sudo apt-get update
sudo apt-get install sun-java6-jdk
```

---

### Post by jespdj on 2009-03-14
You are using GNU Java (gij), which is a slow and incompatible version of Java.

Install Sun Java 6:
```
sudo apt-get install sun-java6-plugin
```
Then make sure that Sun Java 6 is the default version of Java that's being used on your system:
```
sudo update-alternatives --config java
```

---

### Post by Shiv4m on 2009-03-14
> **taurus said:**
> What are the outputs of these two commands?

```
sudo apt-get update
sudo apt-get install sun-java6-jdk
```
For sudo apt-get update it doesn't complete:
[IMG]http://img205.imageshack.us/img205/4645/screenshotshivamshivaml.png[/IMG]

And for the installation, it says I already have it:
[IMG]http://img523.imageshack.us/img523/4645/screenshotshivamshivaml.png[/IMG]

---

### Post by taurus on 2009-03-14
You are running dapper but how come you have hardy repos in there?  Although some people will tell you it's okay to mix repos but it is _not_ a good idea.  Mixing repos will only bring you headache.

---

### Post by doas777 on 2009-03-14
this is just an aside, but are you actually writing code in java, or are you just trying to run programs?

the Java Development Kit (JDK) is for developers who write programs in java. 

the Java Runtime Environment (JRE) is for people that use programs written in java. 

Taurus is right, your system state is likely quite a mess, and you prolly want to backup and rebuild from scratch in the near future.

when you do run
```
sudo apt-get install ubuntu-restricted-extras
``` and you will get the sun java runtime environment, and everything you need to run java programs, along with flash, and a host of useful codecs.

good luck
franklin

---

### Post by Shiv4m on 2009-03-15
Yes I need JDK for the program I want to use and I'm currently using the code above.

How can I clean up my repo?

EDIT: Java still does not work for me...

If I use the code:
> sudo apt-get install sun-java6-plugin

[IMG]http://img11.imageshack.us/img11/4645/screenshotshivamshivaml.png[/IMG]

---

### Post by taurus on 2009-03-15
```
gksudo gedit /etc/apt/sources.list
```
and put a # in front of lines that have hardy in it.  Save it then run

```
sudo apt-get update
```

---

### Post by Shiv4m on 2009-03-15
> **taurus said:**
> ```
gksudo gedit /etc/apt/sources.list
```
and put a # in front of lines that have hardy in it.  Save it then run

```
sudo apt-get update
```

Okay thanks, now with this annoying Java problem...

---

### Post by Shiv4m on 2009-03-15
Okay it is still telling me I have Java installed but when I try to play Runescape it tells me I need to install Java...

I don't know what else to do with this but post on this thread for real help, Is there any way I can just clean up Java and reinstall everything so it's fresh?

[IMG]http://img8.imageshack.us/img8/4645/screenshotshivamshivaml.png[/IMG]

---

### Post by taurus on 2009-03-15
Reboot!

---

### Post by Shiv4m on 2009-03-15
> **taurus said:**
> Reboot!

Uhh no, something like this isn't serious enough to reboot and lose everything.

---

### Post by taurus on 2009-03-15
What do you mean lose everything?  I guess eventually you have to reboot unless you plan to keep your machine running 24/7/365, connecting to a UPS.

---

### Post by Shiv4m on 2009-03-15
Ahh, I thought you ment to reboot the OS and I have done like over 10+ times now since I made this thread.

---

### Post by Shiv4m on 2009-03-16
Ok I am posting all the screen shots about Java:

java -version:

[IMG]http://img23.imageshack.us/img23/5215/screenshotokc.png[/IMG]

javac -version: as you can see here it says it has no source files

[IMG]http://img23.imageshack.us/img23/4645/screenshotshivamshivaml.png[/IMG]

What it tells me when I try to play the game:

[IMG]http://img25.imageshack.us/img25/5127/screenshotshivamshivamlp.png[/IMG]

If none of this works can anyone tell me on how to install "jre-6u12-linux-x64.bin"? i have no idea on how to install .bin files.

---

### Post by taurus on 2009-03-16
Okay, here it is.  You are running x86_64.  There is no java plugin in the repos so you need to download java from Sun and install it.  Then, create a link to /usr/lib/mozilla/plugins.  You don't need to install JDK version to run runescape; all you need is a java plugin for your browser.

Open a terminal and change to the directory that you have saved jre-6u12-linux-x64.bin to your machine.  Then, change the permissions and move it to /opt because that is where you will unpack it.

```
chmod +x jre-6u12-linux-x64.bin
sudo mv jre-6u12-linux-x64.bin /opt
cd /opt
sudo ./jre-6u12-linux-x64.bin
```
Now, there should be a new directory, probably something like jre1.6.12 so you need to change to that new directory.

---

### Post by Shiv4m on 2009-03-16
Okay I did what you said:

```
chmod +x jre-6u12-linux-x64.bin
sudo mv jre-6u12-linux-x64.bin /opt
cd /opt
sudo ./jre-6u12-linux-x64.bin
```

What should I do now? I don't get what your trying to say here: 
> Now, there should be a new directory, probably something like jre1.6.12 so you need to change to that new directory.

---

### Post by taurus on 2009-03-16
What's the output of the second command?

```
cd /opt
ls -la
```

---

### Post by Shiv4m on 2009-03-17
Oh my god still doesn't work :(

I don't know what else to do! Is there any other way to get my Java back, PLEASE!

Can't anyone just view my computer files to see what is wrong instead of guessing?

---

### Post by doas777 on 2009-03-17
I'm noticing that your jre version is 1.6 but your jdk is 1.5

this is what i get:
```

alpha10@21of2:~$ java -version
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6.1) Runtime Environment (build 1.6.0_0-b12)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b12, mixed mode)
alpha10@21of2:~$ javac -version
javac 1.6.0_0-internal
alpha10@21of2:~$ 

```

my recomendation: 
1) uninstall java via synaptic
2) install the ubuntu-restricted-extras package (not just restricted codecs)

have fun,
franklin

---

### Post by jimbola on 2009-03-17
I picked this thread up because of an error message I get when starting up oracle sqldeveloper "Java 6.0 release 16.0_04 is not supported. Upgrade to Java 6.0 release 16.0_04 or later". Yet after doing apt-gets I'm still on version 1.6.0_0.

jimbo@jimbo-laptop:~$ sudo apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jdk is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
jimbo@jimbo-laptop:~$ java -version
java version "1.6.0_0"
OpenJDK  Runtime Environment (build 1.6.0_0-b11)
OpenJDK Client VM (build 1.6.0_0-b11, mixed mode, sharing)
jimbo@jimbo-laptop:~$

---

### Post by Shiv4m on 2009-03-17
> **doas777 said:**
> I'm noticing that your jre version is 1.6 but your jdk is 1.5

this is what i get:
```

alpha10@21of2:~$ java -version
java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6.1) Runtime Environment (build 1.6.0_0-b12)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b12, mixed mode)
alpha10@21of2:~$ javac -version
javac 1.6.0_0-internal
alpha10@21of2:~$ 

```

my recomendation: 
1) uninstall java via synaptic
2) install the ubuntu-restricted-extras package (not just restricted codecs)

have fun,
franklin

This is what I got as of right now:

```
shivam@shivam-laptop:~$ java -version
java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) 64-Bit Server VM (build 10.0-b22, mixed mode)
shivam@shivam-laptop:~$ javac -version
javac 1.6.0_06
shivam@shivam-laptop:~$ 

```

Should I still try what your asking me to do or...?

---

### Post by doas777 on 2009-03-17
it looks like you got that worked out. excelent!
now, does your game work? you may have to redo the changes Taurus had suggested to install the plugin you need.

---

### Post by Shiv4m on 2009-03-18
No my game still does not work, is it possible I would have to redirect the link in FireFox to the new Java folder?Free Users - Click here to play Members - Click here to play

---

### Post by Shiv4m on 2009-03-20
Still nothing, I tried everything...

What is the default folder for the Java files?

---

### Post by doas777 on 2009-03-20
> **Shiv4m said:**
> 
What is the default folder for the Java files?

mine's in /usr/lib/jvm/

---

### Post by Shiv4m on 2009-03-22
> **doas777 said:**
> mine's in /usr/lib/jvm/

How can I change the default folder on FireFox?

---

