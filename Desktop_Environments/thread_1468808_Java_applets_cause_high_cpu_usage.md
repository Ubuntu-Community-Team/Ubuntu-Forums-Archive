---
title: "Java applets cause high cpu usage"
date: 2010-05-01
forum: Desktop Environments
---

### Post by mitk0o0o0 on 2010-05-01
Hello, yesterday when 10.04 got released i decided i'd install it and try it out, when i tried to run a java applet on it (runescape for example) the CPU usage got really high (around 100%), is that normal?

Info about my processor if you need:
AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ 2,61 GHz

This is my first time ever using ubuntu.

---

### Post by infamous-online on 2010-05-01
> **mitk0o0o0 said:**
> Hello, yesterday when 10.04 got released i decided i'd install it and try it out, when i tried to run a java applet on it (runescape for example) the CPU usage got really high (around 100%), is that normal?

Info about my processor if you need:
AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ 2,61 GHz

This is my first time ever using ubuntu.

Sadly, this isn't an issue with an operating system, I think it's a memory leak in the program itself. I have this very issue whenever I visit sites with flash or whenever I go to yahoo to play dominoes my Quad Core Phenom jumps to %60 just like that. However I haven't suffered from it, but I always keep my task manager open and keep an eye on my CPU temp. Speaking of which I need to install the CPU temp monitor on my Ubuntu box. :guitar:

---

### Post by mitk0o0o0 on 2010-05-02
> **infamous-online said:**
> Sadly, this isn't an issue with an operating system, I think it's a memory leak in the program itself. I have this very issue whenever I visit sites with flash or whenever I go to yahoo to play dominoes my Quad Core Phenom jumps to %60 just like that. However I haven't suffered from it, but I always keep my task manager open and keep an eye on my CPU temp. Speaking of which I need to install the CPU temp monitor on my Ubuntu box. :guitar:So there is no fix?

---

### Post by dogafin on 2010-05-13
the only solution i have when java eats up my cpu is going to system monitor and killing the java process. ive never had a problem until my latest update to lucid. im also trying to figure out a fix for this.

---

### Post by pedrogl on 2010-05-14
try installing sun's jre:
```
sudo apt-get install sun-java6-jre sun-java6-plugin
sudo update-java-alternatives -s java-6-sun
```

---

### Post by chiwi on 2010-05-14
That's right, when 10.04 was installed, OpenJDK was installed as well (instead of Sun's), and the high-cpu-usage-issue appeared for me.

I'll try switching back as pedrogl suggested.

---

### Post by chiwi on 2010-05-14
hmmm...it's not available any more.....ideas?

```

chiwi@Brunette:~$ sudo apt-get install sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate
chiwi@Brunette:~$

```

---

### Post by pedrogl on 2010-05-14
Hi,

according to [this]("http://www.ubuntu.com/getubuntu/releasenotes/1004"), sun's jre has moved to the canonical partners repository:
```
add-apt-repository "deb http://archive.canonical.com/ lucid partner"
```
i added that repo when installing, that's why i didn't notice the change

---

### Post by madmax75 on 2010-05-14
I upgraded from Karmic to Lucid, ending up somehow losing the existing Sun Java package. 

It was replaced by the IcedTea package, which does not work properly. It hogs up all the CPU cycles, heats the CPU up and makes the OS unresponsive. So using that is just out of the question for now.

The problem is, I don't have the option to install Sun Java anywhere. It is not in ANY repositories as far as I can tell. The only entries I have in the Software Center Partner repositories are Adobe Flash and Adobe Acrobat. No Sun Java anywhere.

So, how can I add the correct repository?

I have tried the Sun's own manual, text-based installer option from their website. t is just awful crap, it has never worked for me without hours of work and several failed attempts. Not a choice, either.

EDIT: I tried pedrogl's termina command above, didn't do any good. There is no option for Sun Java, still only Adobe stuff.

---

### Post by chiwi on 2010-05-14
let me ask...have you tried pedrogl's command from the post above?

---

### Post by madmax75 on 2010-05-14
Found this guide:

[http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html)

Seems to be working, it's donwloading the Sun Java packages right now.

First time I just copy-pasted the command from the pedrogl post above, the second time I just wrote it straight into the terminal window. Maybe the hyphens were wrong or something like that.

So now it's doing at least something... :)

EDIT: Still nothing. I got to this phase:

"you&#8217;ll get a screen that contains the Sun Operating System Distributor  License for Java and hit Enter to continue."

But, when I hit Enter, nothing happens. All I have is a unresponsive screen full with license text nobody ever reads. Can't get forward from there.

And I can't even retry now, because some process is locking the apt up. *sigh* Probably have to restart to make it go away.

Ubuntu + Sun Java = bad news. Same goes with ANY Java installation, apparently.

All I need is a freakin' .deb package that I could download from the Sun Java website and install manually. But noooo, that would apparently be just TOO easy for Ubuntu users!

---

### Post by 2hot6ft2 on 2010-05-14
Try the third post on this page if you've already enabled the partner repo., start at the first post if you haven't.
[http://ultimateeditionoz.com/forum/viewtopic.php?f=73&t=1080&start=40](http://ultimateeditionoz.com/forum/viewtopic.php?f=73&t=1080&start=40)
:guitar:

---

### Post by madmax75 on 2010-05-15
> **2hot6ft2 said:**
> Try the third post on this page if you've already enabled the partner repo., start at the first post if you haven't.
[http://ultimateeditionoz.com/forum/viewtopic.php?f=73&t=1080&start=40](http://ultimateeditionoz.com/forum/viewtopic.php?f=73&t=1080&start=40)
:guitar:

So, uninstall everything labeled "openjdk" and then try again the Sun Java?

I have to reboot first, becauser I can't even get apt-get or Synaptic to open anymore. There is some process blocking access to them.

Great, now the bloody Sun Java installation crap is destroying even my package manager as well. Oh the joy.

I hate Java.:mad: I've had nothing but trouble with the thing. In both Windows and Linux, Java gives me nothing but constant troubles. I think there something seriously wrong with the whole concept. All Java code that I've bumped into has been bulky, buggy, laggy and generally just full of crap. I even had to change my bank because of the Java problems my old bank had with their online service.

Java sucks.

---

### Post by madmax75 on 2010-05-15
Ok, I rebooted the computer, I was prompted to make a "partial upgrade", did that, it installed Sun Java (lo and behold!).

Then I fired up Synaptic, uninstalled openjdk and IcedTea, then reinstalled Sun Java components once more.

After giving "sudo update-java-alternatives -l" in the terminal I get:

java-6-sun 63 /usr/lib/jvm/java-6-sun

And "java -version" gives me:

java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) Server VM (build 16.3-b01, mixed mode)

This is right, right?

But Java won't still work in the Mozilla Firefox. It only prompts me to install the IcedTea Java plugin, when I go to some page with a Java applet.

So how do I fix this?

EDIT: Oh wait, I apparently forgot to install the java-6 plugin for the browser :-)

The Sun Java is now up, running and working on my system. Yee!

BTW, I hate Java. I. just. hate.it. It is just crap. The worst thing invented by mankind. An abomination from the Underworld. Devil's work, that's what it is!

---

### Post by chiwi on 2010-05-15
People who don't understand Java, tend to hate it.

The problem is clearly not Java, nor Ubuntu, it's just pebsac.

---

