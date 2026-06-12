---
title: "Java Response Time"
date: 2006-08-01
forum: Desktop Environments
---

### Post by SRTS on 2006-08-01
I'm using CGoban2 (kgs.kiseido.com) to play a 3000 year old asian boardgame called 'Go' over the internet. The program is a JAR file.

Problem: When I click to place a stone, it will take about 4 seconds until the program reacts and actually places the stone, during that time, the program will freeze.
The same JAR file on Windows 2000 will react almost instantly, like it is supposed to.

I talked to the admins of the server, did some more tests, and also tried blackdown java 1.4 instead of sun java 1.5 but it didn't help.
For no reason at all the java applet that runs at normal speed on win2k (sun java 1.5 and 1.4) is terribly slow on Ubuntu, unusable really (when reviewing a game you just played, you want to zap through the moves at max speed, just believe me that 4 s is totally unusable).
Sometimes I even get 'lag' spikes (although the internet connection is totally fine and has low roundtrip times and no packet loss) of up to 10 seconds, that also doesn't occur on win2k.

Anyone have an idea how to fix Java/Ubuntu to make it work at normal speed instead of this crawling? I'm a hobby Go player, and I dont want to boot win2k each time I want to play really.
Thanks in advance.

---

### Post by SRTS on 2006-08-02
Please, isn't there ANY known solution to get a fast and responsive Java that doesn't lag for 4 seconds? It's really important. I can't use this system if there's no working Java on it! :(

---

### Post by bardu on 2006-08-02
Are you running Ubuntu and win2k on the same machine or are similar hardware?

I can assure you that Java is not responding slower on Ubuntu than on any MSWindows version, in fact it is responding much faster. I'm using Java on  four different OS ( the other two are Mac OS X 10.4.6 and Solaris 10) and the performance is almost equal on similar hardware, except on Windows. And this fact has even nothing to do with Java, we all know that.

---

### Post by SRTS on 2006-08-03
Yes same machine.

Win2k -> normal
KUbuntu -> crazy delays when placing stones in an online game, but no delays when placing stones in offline-mode.

It can't be a programming bug, since it's the same JAR file for both OS. So I guess it's either a Java or a Kubuntu problem?

It's not the internet connection, I have outstanding latency and no packet loss to the server, as I can observe when playing the game on windows, and I also did some pings to be sure.

---

### Post by 3rdalbum on 2006-08-03
Trust me: Anything that goes wrong with a Java applet or application is a bug in Java.

Although Java is theoretically completely cross-platform, there are massive differences in the ways that each platform's Java implementation actually behaves. I've even found that two almost identical computers can exhibit different behaviour with Java apps - in that particular test, one machine couldn't connect to a server and the other was registering keystrokes twice, in the same applet with the same JRE and the same operating system.

---

### Post by SRTS on 2006-08-04
Is there a way to turn the JAR file into a native binary? Maybe then it'd run fine.

---

