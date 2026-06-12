---
title: "MATLAB GUI is very slow"
date: 2007-11-25
forum: Education &amp; Science
---

### Post by leeping on 2007-11-25
Dear community,

I just did a fresh install of Gutsy, and I'm finding the MATLAB GUI just as slow as it was when I was using Dapper.  Is there something I can do to speed it up?  The GUI is beyond slow - e.g. in the Array Editor, it takes me several seconds to type entries into a matrix.

Can it have anything to do with the Java Runtime Environment?

Thanks everyone,

- Lee-Ping

---

### Post by Aniongap on 2007-11-27
Hi,

one of problems may be that processor spends a lot of its time in processing. You can  watch kernel max threads.

take a look at 

sudo sysctl -a | sort | more

You can change kernel.threads-max for testing:

sudo sysctl -w kernel.threads-max="number"
try double times less number than shows kernel.threads-max

also how much ram you use?
somentimes adding ram is the best solution.

---

### Post by kevmitch on 2008-07-06
I also found matlab GUI to be excruciating. This seems to be exacerbated (though not entirely caused by) running it over XDMCP. I'm pretty sure this is not a threads issue since I strongly doubt matlab is trying to spawn more than 147456 threads (what I get from sysctrl -a | grep threads-max). And even if it was, I don't see how increasing that number could possibly increase performance even on my 8 processor machine. It is also not a ram issue since I've go 8GB of it. 

I'm pretty sure Java Virtual Machine #vomit# is indeed the cuplrit as running with -nojvm eliminates all problems. I would recommend running matlab like this as a habit:

```
echo "alias matlab='matlab -nojvm -nosplash'" >> ~/.bashrc
```

However, since I have users that are likely attached to the GUI, I decided to install the x86 version along side the x86_64 version and found the GUI to be an order of magnitude more tolerable. I would consider this either a bug in matlab or a bug in Java. Well, actually I consider it a bug in matlab for using Java Virtual Machine in the first place.

---

### Post by kevmitch on 2008-07-06
Oh, something else you might try, though it didn't seem to solve the problem for me is use your system Java Virtual Machine (which will likely be more up to date):

Assuming you have sun-java6-jre installed

```
MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.06/jre/ matlab
```

This also fixes a problem that matlab seems to have with the new xserver.

---

### Post by kevmitch on 2008-07-06
By the way, to run the x86 version when you also have the x86_64 version installed, 

```
matlab -glnx86
```

---

### Post by shabbychef on 2009-01-23
we solved this problem under ubuntu 8.0 as suggested on this link:
[https://bugs.launchpad.net/ubuntu/+bug/241063](https://bugs.launchpad.net/ubuntu/+bug/241063)

1 copy /usr/lib64/libX11.so.6.2.0 from a gentoo distribution to the machine in question; put it in /opt/lib
2 make symlinks: 
$ cd /opt/lib && ln -s libX11.so.6.2.0 libX11.so.6
$ cd /opt/lib && ln -s libX11.so.6.2.0 libX11.so
3 do the export
$ export LD_LIBRARY_PATH=/opt/lib:$LD_LIBRARY_PATH
4 call matlab. worked for us!

hth,

-shabby

---

### Post by JPLGuy on 2009-03-11
I have this problem with MATLAB R2009a, and tried shabbychef's solution, sadly it failed to work for me. I recompiled the libX11.so.6.2.0 from X11 version 7.2.1.1.1 source code (the earliest I could easily compile, the earlier versions had dependencies I couldn't fill with Synaptic). I imagine there are probably a lot of different ways this can be compiled, so I am not surprised. Maybe gentoo has some optimization flags that are relevant, or something. 

What version of gentoo did you use shabbychef? I thought I'd install it in a VM and grab the file that way... (and try out gentoo while I am at it).

I also tried to use the latest JVM (1.6.0.10 I think) available in the repo for intrepid, without luck. 

I should note I am using the 32bit version, not 64 bit as in the example. (At least, I presume lib64 is for 64 bit, since mine is empty).

My symptoms are that typing code into long M files is very slow, and it will frequently interrupt my music (played with Rythmbox)! MATLAB itself is very fast, including start up. The -nojvm or -nodesktop are not options for me, sadly.

I have also noticed that Xorg CPU usage shoots upward (in top) when typing, scrolling, etc in MATLAB, while MATLAB's use is pretty minimal. 

I also just tried version 5 of Sun's JRE, and the Open version as well, neither resolved the problem, and the open version version generated additional errors and some graphical oddness in MATLAB. 

I suppose the problem really is in XOrg, so shabbychef's solution makes sense to me. I don't know how to determine what the specific issue is, maybe somebody else does.

> **shabbychef said:**
> we solved this problem under ubuntu 8.0 as suggested on this link
[https://bugs.launchpad.net/ubuntu/+bug/241063](https://bugs.launchpad.net/ubuntu/+bug/241063)

1 copy /usr/lib64/libX11.so.6.2.0 from a gentoo distribution to the machine in question; put it in /opt/lib
2 make symlinks: 
$ cd /opt/lib && ln -s libX11.so.6.2.0 libX11.so.6
$ cd /opt/lib && ln -s libX11.so.6.2.0 libX11.so
3 do the export
$ export LD_LIBRARY_PATH=/opt/lib:$LD_LIBRARY_PATH
4 call matlab. worked for us!

hth,

-shabby

---

### Post by JPLGuy on 2009-03-13
Hello,

Try the directions at (repeated below)
[http://www.mathworks.com/matlabcentral/newsreader/view_thread/160387](http://www.mathworks.com/matlabcentral/newsreader/view_thread/160387)

It worked for me. A few notes (as I posted there), I had to make the "system" directory as well, and had to start MATLAB from that directory. Starting it normally with this java.opts file did not work.

> 
maybe I found a resolution for this problem! Just put a file called "java.opts" containing the Java option "-Dsun.java2d.pmoffscreen=false" into the directory *matlabroot*/bin/*system*/


---

