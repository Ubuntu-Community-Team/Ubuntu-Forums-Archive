---
title: "Runescape not working."
date: 2007-10-21
forum: Gaming &amp; Leisure
---

### Post by meesekiller on 2007-10-21
Okay, so ya I've looked through the other topics and I haven't seen my question answered. I've seen it asked once, but it was imbedded in another thread and no one answered.

So, I've tried just about everything to get Runescape to load. What I do is I go to Runescape.com click on existing player. It takes me to the screen to choose high or low detail. I click low detail(I've tried it once with high detail) and it takes me to the world select. So I select some random free to play world. Then I am taken to the loading screen. Okay, it tells me additional plugs needed. Synaptic manager pops up and gives me four choices Java SE 6, Java SE 5.0, GCJ web browser plug in, and GCJ 7 with (Ice tea) or something like that, the last two are a bit sketchy in my memory. So I have tried loading all 4 of them. The java ones and the Icetea ones do nothing...the plug in symbol just sits there saying I need to load one then pops up and gives me the four options again, GCJ gives me an actually choice to accept the applet, but then gives me a loading error...every time. So I'm at a loss. I when into the synaptic package manager and loaded everything related to java I could find...no cigar (that includes the JR2E 1.4 mozilla plug in which I originally thought was the problem). 

So, I'm at a loss. I'm using the new 7.10 32 bit edition as no other version even came close to loading. Any help with my predicament would be appreciated. Thanks in advance.

Meese

P.S. This is my first experience with Ubuntu and linux in general...so ya, I may be missing something pretty fundamental.

---

### Post by TidusBlade on 2007-10-21
I have the Sun Java 5.0 Plugin and Sun Java 5.0 Runtime and it works perfectly, try uninstalling all javas and leaving those two on, maybe it will work? Im using Feisty repos so it might be diffrent.
On a side note, you might wanna find another game to play ;)

---

### Post by meesekiller on 2007-10-21
Ya, that didn't work...could it be the browser. I just upgraded to mozilla firefox 2.0.0.8.

Oh and I tried the whole onslaught, unistalled everything and loaded just the 5.0 plugin. When I checked the synaptic manager it had installed the runtime environment as well. Still same thing, not recognized...frustration overtakes me...:confused:

---

### Post by TidusBlade on 2007-10-21
If I remember correctly, you can download the client and play from there, try that.

---

### Post by meesekiller on 2007-10-21
> **TidusBlade said:**
> If I remember correctly, you can download the client and play from there, try that.

Ya, not working either...it says it requires I.E. 6 or higher to use...plus it is an .exe file...so I'm not sure if that is compatible with ubuntu.

But ya I downloaded it, tried it and it gave me an error message.

Any other ideas...anyone?

---

### Post by TidusBlade on 2007-10-21
Have you tried other browsers? Opera? Galeon?

---

### Post by lnxnut on 2007-10-26
if ur running the 64-bit firefox I used the icedtea java, click and install it from the browser when it tells you your missing the plugins.  After icedtea installs then open your terminal copy and paste this instruction:

sudo gedit /etc/apt/sources.list

copy and paste these three lines to the bottom of that file and save it.

# iced-tea updates
deb [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/
deb-src [http://people.ubuntu.com/~doko/ubuntu/](http://people.ubuntu.com/~doko/ubuntu/) gutsy/

make sure your system updates afterwards.

when you go to runescape.com and your at the high detail / low detail page ... look on down the page, it will ask which java to use.  choose the bottom one "unsigned". If I knew how to make a /rscache directory with write permissions it would work normally. If you figure out how to do this please post it.  Thanks.

---

### Post by mig5 on 2007-11-02
After you've installed a Java version type this into the firefox address bar:
```
about:plugins
```
Look on that page and see if the java plugin is showing up.

> **lnxnut said:**
> ...
when you go to runescape.com and your at the high detail / low detail page ... look on down the page, it will ask which java to use.  choose the bottom one "unsigned". If I knew how to make a /rscache directory with write permissions it would work normally. If you figure out how to do this please post it.  Thanks.


To get runescape to cache properly (stop it loading from scratch every time), make a folder in /home/[username]/ called .file_store_32 and another called .jagex_cache_32 .  Once you've done that you can select 'signed applet with default java' on the detail select screen.

---

