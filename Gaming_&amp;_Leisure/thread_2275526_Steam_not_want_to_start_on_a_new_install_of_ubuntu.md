---
title: "Steam not want to start on a new install of ubuntu 15.04"
date: 2015-04-26
forum: Gaming &amp; Leisure
---

### Post by Diego_Alberto_Alba on 2015-04-26
I just installed ubuntu 15.04,fresh install, i have installed steam from terminal "sudo apt-get install steam", no problem on the installation,  but after star steam and download the data (210mb), does not start, launching it from terminal says:
```
Running Steam on ubuntu 15.04 64-bitSTEAM_RUNTIME is enabled automatically
[2015-04-26 20:04:03] Startup - updater built Apr 13 2015 15:17:10
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadValue (integer parameter out of range for operation)

```
 I do not know what to do, what data need so you can help me, I am not new using ubuntu, but I generally do not run into these problems, the previous version of ubuntu 14.10 ran smoothly steam.

Sorry if I write with mistakes, English is not my native language, but I thought this forum is where I have more chance of a solution, thx.

---

### Post by oldrocker99 on 2015-04-27
What is your video circuitry? What kind of driver are you using?

Please post the results of:```
lspci | grep VGA
```

This will show whether you're using Intel, ATI, or nVidia graphics, and is pretty essential for further advice.

---

### Post by sejvenables on 2015-04-27
> **Diego_Alberto_Alba said:**
> I just installed ubuntu 15.04,fresh install, i have installed steam from terminal "sudo apt-get install steam", no problem on the installation,  but after star steam and download the data (210mb), does not start, launching it from terminal says:
```
Running Steam on ubuntu 15.04 64-bitSTEAM_RUNTIME is enabled automatically
[2015-04-26 20:04:03] Startup - updater built Apr 13 2015 15:17:10
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadValue (integer parameter out of range for operation)

```
 I do not know what to do, what data need so you can help me, I am not new using ubuntu, but I generally do not run into these problems, the previous version of ubuntu 14.10 ran smoothly steam[INDENT]
[/INDENT]
 Sorry if I write with mistakes, English is not my native language, but I thought this forum is where I have more chance of a solution, thx.

I'm pasting in someone else's answer from another thread, seeing as this is the top result on Google. This fix worked for me. Hope the poster from the other thread is OK with this:

 >  This is a problem with steam and ubuntu 15.04.  Steam bundles old  libs and are colliding with mesa drivers, that is also why closed  drivers aren't seeing this problem.

  There is a [open bug]("https://github.com/ValveSoftware/steam-for-linux/issues/3801") in steam github
  the workaround for now is to remove the old lib version, at least until valve fix the issue in their startup script or similar.
  So enter this folders and do this
  
```
cd $HOME/.steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu
mv libstdc++.so.6 libstdc++.so.6.bak
cd $HOME/.steam/ubuntu12_32/steam-runtime/amd64/usr/lib/x86_64-linux-gnu
mv libstdc++.so.6 libstdc++.so.6.bak
  
```
It worked for me... but please note that if some game required that  old lib from the steam runtime, it may crash (that is why should be  valve fixing this)
     


Original post here: [http://askubuntu.com/questions/614422/problem-with-installing-steam-on-ubuntu-15-04/614458#614458](http://askubuntu.com/questions/614422/problem-with-installing-steam-on-ubuntu-15-04/614458#614458)

---

### Post by Diego_Alberto_Alba on 2015-04-27
Thank you very much both of you for replying ths thread, really thx, the answer that sejvenables shared had solved my problem, anyway, there is the informationn that oldrocker99 requested:
```
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS780L [Radeon 3000]
```

Again thank you very much

---

