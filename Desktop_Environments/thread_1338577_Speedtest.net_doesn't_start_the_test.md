---
title: "Speedtest.net doesn't start the test"
date: 2009-11-26
forum: Desktop Environments
---

### Post by darkod on 2009-11-26
Hello. I am new to Ubuntu and there is probably something I missed.
When trying to test my internet speed on [www.speedtest.net](www.speedtest.net) I can not run the test. The map with the test servers shows up as normal, you point the cursor to some location and it shows the city. So far so good.
You click on the city and nothing happens. :(

As far as I know, I have installed flashplugin-nonfree and java plugin (don't remember the exact package name). My Ubuntu is 64bit but I have also installed the 32bit java plugin and I thought it actually helped. I remember once I was able to run the test.
Then without any changes to firefox, it doesn't want to start same as before installing java plugin.
Are there more packages to install?
In System -> Preferences I can see control panel for both Java and Java 32bit, opened both and under Java tab in View it shows the plugin as enabled. Also firefox preferences show JavaScript and Java enabled, haven't touched those.

Thanks in advance.

---

### Post by smilingralph on 2009-11-27
Darkod. I had the exact same problem although I'm using 32 bit Xubuntu 9.10. In my case the problem was a conflict with kdocker. Starting firefox without kdocker solved the problem.
Ralph

---

### Post by darkod on 2009-11-28
Thanks for the reply. I will look into it but it seems it's not the same problem. Judging by the name kdocker is used in KDE or Kubunu, while I am running Ubuntu with gnome.
But you made a valid point, I am also starting firefox from the shortcut on the top bar, I will try from the App menu to see what happens.

---

### Post by darkod on 2009-11-28
I have tried anything I could think of with my limited Ubuntu experience. I think the problem is the java applet not executing but don't know how to check.

I have removed all java packages with --purge option, inclusing sun-java6-bin, sun-java6-plugin and sun-java6-fonts. After that I installed them again. I also installed ia32-sun-java6-plugin which should be the 32bit plugin.

I have tried with the 64bit plugin disabled and enabled, no change.

I looked in firefox in about:plugins and all java plugins seem to be working and are enabled.

My system is Desktop 64bit, can that be the problem? What am I missing?

---

### Post by smilingralph on 2009-11-28
Have you tried the 64 bit Adobe Flash Plugin?
Ralph

---

### Post by darkod on 2009-11-29
I don't think the problem is flash, but I removed it anyway and made sure I install the 64bit version. Didn't help.
If flash is the problem then the sppedtest.net would not open at all, not the part with the server locations. After that I think java takes over for the actual speed test and that's the hiccup. Even though all java plugins seem installed and enabled, it doesn't work.

---

### Post by smilingralph on 2009-11-29
Sorry I couldn't have been more help. As I said in my first post my problem was a conflict with Kdocker, a dock to tray program similar to Alltray or the Firetray Firefox extension. As far as I know these programs have nothing to do with Java or Flash. You might try checking for conflicts with other running programs or Firefox extensions.

Ralph

---

### Post by darkod on 2009-11-30
Got it sorted. It was a problem with the flash plugin. It seems that test does not even use java. For 64bit Ubuntu you have to make sure you get the 64bit flash plugin, it turned out just downloading a library and copying it to plugins folder does the trick.

---

### Post by timothydonohue on 2010-04-19
hmmm...i wish that's all there was to it.  i put the 64 bit libflashplayer.so into ~/.mozilla/plugins, and still no dice for me...

---

### Post by Rodney9 on 2010-04-20
> **timothydonohue said:**
> hmmm...i wish that's all there was to it.  i put the 64 bit libflashplayer.so into ~/.mozilla/plugins, and still no dice for me...

I put mine in  ```
/usr/lib/mozilla/plugins
```

---

### Post by Linuxforall on 2010-04-20
Apart from Flash, speedtest needs Java, try with Open Java and if it don't work, install latest Sun Java.

---

### Post by markhorrocks on 2010-06-09
I fixed this with the following commands in the terminal.

sudo add-apt-repository ppa:sevenmachines/flash && sudo apt-get update && sudo apt-get install flashplugin64-installer

downloading the flash plugin (64 bit) from the adobe website and copying it to the mozilla/plugins directory did not work.

---

### Post by stanito33 on 2012-04-16
> **darkod said:**
> Got it sorted. It was a problem with the flash plugin. It seems that test does not even use java. For 64bit Ubuntu you have to make sure you get the 64bit flash plugin, it turned out just downloading a library and copying it to plugins folder does the trick.

I have the same problem but i'm on WinXP 32bit. How to fix this problem? Please help me :( :sad:

---

### Post by coffeecat on 2012-04-16
Old thread closed.

@stanito33, this is the Ubuntu forums, Ubuntu being a Linux-based operating system. If you are an Ubuntu user and you need help with a Windows problem, you may post in the [Other OS section]("http://ubuntuforums.org/forumdisplay.php?f=401") here. However, you will be much better off asking about Windows problems on a Windows forum.

---

