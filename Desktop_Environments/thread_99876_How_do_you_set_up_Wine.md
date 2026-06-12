---
title: "How do you set up Wine ?"
date: 2005-12-06
forum: Desktop Environments
---

### Post by dw5437 on 2005-12-06
I ran automatix and it said that I needed to run wine.cfg after completion. I didnt write it down but I could have sworn that is what it said. When I go into a terminal and type wine.cfg it says no such command. So how do you set up Wine

---

### Post by linbetwin on 2005-12-06
It's **winecfg**, without the dot.

---

### Post by lhtown on 2005-12-06
I don't use wine, but wine.cfg looks like a configuration file and not a program to me. You might try searching for it in the /etc directory.

If you are not familiar with them, configuration files are simply text files that you can edit with a text editor such as nano or gedit. Generally they have documentation written into them (you will see it when you open the text file) so you can figure out what options to change.

---

### Post by dw5437 on 2005-12-06
When I tried winecfg I still got command not found.

---

### Post by rem on 2005-12-06
Hi,

Winecfg it's some extra stuff you'll have to install. Just sudo apt-get install winecfg and when you'll run Wine you'll notice something like a configuration window that will popup. It'll ask you where to set your Windows virtual folder and stuff like that... This is what worked for me at least. Good luck!

---

### Post by dw5437 on 2005-12-06
dw5437@ubuntu2:~$ sudo apt-get install winecfg
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package winecfg
dw5437@ubuntu2:~$

---

### Post by rem on 2005-12-06
Then i think it should be something with your repositories list... just a sec, I'll look into my list and get back to you with the right one.

---

### Post by pizzach on 2005-12-06
If you aren't sure of a name you guys could always just go to Synaptic Package Manager...maybe search something like "wine" and have everything wine pop up.

---

### Post by Joe_CoT on 2005-12-06
there is no such "wineconfig" package

what you *most probably* need to do is install wine 
```
sudo apt-get install wine
```

 and then just run wine once from the command line.

```
wine
```

the program probably meant you need the *file* wine.cfg, which is generated the first time you run wine.

---

### Post by polpak on 2005-12-06
[QUOTE=dw5437]I ran automatix and it said that I needed to run wine.cfg after completion. I didnt write it down but I could have sworn that is what it said. When I go into a terminal and type wine.cfg it says no such command. So how do you set up Wine[/QUOTE]


Try just reading the howto..

[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

It's pretty straight forward.

Once it's installed you just use winecfg to configure it.

---

### Post by dw5437 on 2005-12-06
Ok sorry about that. I did do a search in synaptic for wine config and it came up with winetools. When I downloaded that then I done the command winecfg and it worked. Thanks for the tremendous help.

---

### Post by Joe_CoT on 2005-12-06
fyi: the wine package is in the universe repository. in order to install it from apt-get, you need to enable the universe repositories.

edit the /etc/apt/sources.list

```
sudo nano /etc/apt/sources.list
```
and remove the #s from the two lines that have the universe repositories.

the run sudo apt-get update to update the database

---

### Post by rem on 2005-12-06
> I don't use wine, but wine.cfg looks like a configuration file and not a program to me. You might try searching for it in the /etc directory.

If you are not familiar with them, configuration files are simply text files that you can edit with a text editor such as nano or gedit. Generally they have documentation written into them (you will see it when you open the text file) so you can figure out what options to change.

Yeap, you maybe right, couldn't find **winecfg** too even though I'm pretty sure I installed it once with Synaptic but [**here's an address where you can get winecfg source**]("http://sf.gds.tuwien.ac.at/w/wi/winecfg/")...

I installed also Wine with Automatix but didn't helped so I removed it and freshly installed again.

Besides the wine install / configuration guide from [www.winehq.com](www.winehq.com), here's another method that always works for me: 

**The right Wine versions working with [Winetools]("http://www.von-thadden.de/Joachim/WineTools/"). **

[**Download the .deb packages for wine & winetools**]("https://sourceforge.net/project/showfiles.php?group_id=118894&package_id=135906&release_id=283484") 

Winetools did all the work for me and installed everything I needed.  
Just download and then install the files in this order and run from console "winetools" (without the quotes). If you still need winecfg, I guess you should be able to install it from source (check out the above winecfg URL).

1. libwine_0.0.20041019-1.3_i386.deb
2. wine_0.0.20041019-1.3_i386.deb
3. win-utils_0.0.20041019-1.3_i386.deb
4. wine-doc_0.0.20041019-1.3_all.deb
5. winetools

```
sudo dpkg -i libwine_0.0.20041019-1.3_i386.deb
``` 
etc ... you know the drill... :)

Hope it helps and you should know that this stuff worked fine for me. I can't tell that it will work for you too. Maybe other people around here and more experienced with Linux, can correct me if I'm wrong with anything.

Good luck!

---

### Post by YokoZar on 2005-12-08
[QUOTE=rem]Hi,

Winecfg it's some extra stuff you'll have to install. Just sudo apt-get install winecfg and when you'll run Wine you'll notice something like a configuration window that will popup. It'll ask you where to set your Windows virtual folder and stuff like that... This is what worked for me at least. Good luck![/QUOTE]
What are you talking about?  Winecfg isn't a separate package, it's included with Wine.

---

### Post by YokoZar on 2005-12-08
[QUOTE=rem]1. libwine_0.0.20041019-1.3_i386.deb
2. wine_0.0.20041019-1.3_i386.deb
3. win-utils_0.0.20041019-1.3_i386.deb
4. wine-doc_0.0.20041019-1.3_all.deb
5. winetools[/QUOTE]Don't do this, all this junk is literally over a year out of date.

Just use the beta release of Wine from the Winehq APT repository.

---

### Post by rem on 2005-12-08
These is the optimal versions of Wine working with the right version of Winetools. I just followed the instructions from the [Winetools]("http://www.von-thadden.de/Joachim/WineTools/index.html#winever") website. If that guy's lying, then I'm lying too... As I said, I'm not a Wine expert, I just shared what's working fine for me, you don't have to be that acid!

----
And the mistery is solved: I specially need Internet Explorer 6 running on my Ubuntu. I'm a web designer / developer and I need it for testing purposes so this is the reason why I'm using Wine after all ... Unfortunately, latest Wine builds doesn't support IE6 installation so that's why I needed Winetools (this one is smoothly installing me the IE6 required applications like DCOM98.exe) who only works with the older versions of Wine I already posted earlier in this thread. So, if you're a web designer and need 
IE6 for testing purposes, you might want to give my version a try. If you need wine to run some other Windows stuff, go ahead and install the latests builds from the repos.

Anyone correct me if I'm wrong. Thanks!

---

### Post by YokoZar on 2005-12-08
[QUOTE=rem]Anyone correct me if I'm wrong. Thanks![/QUOTE]You can install a far newer packaged verion of winetools (that works with the latest Wine) via apt-get.  Just add the winehq apt repository to sources.list.

If your setup is working and you don't need anything new, I wouldn't mess with it, though.  But in general it's easy to get setup using the packages I've made.

---

### Post by rem on 2005-12-08
I couldn't agree more and please believe me that I tried several options until I found this old one. Each time I set up newest Wine versions (this was the first thing I did) it didn't worked at all or messed up bad my IE6.

After the discussion we had earlier, I tried to install latest Wine with [Sidenet Wine Configuration Utility]("http://sidenet.ddo.jp/winetips/config.html"). On [Frank's Corner]("http://frankscorner.org/index.php") I found about it to be pretty usefull and even that's very easy to install IE with Wine 0.9. So I gave it a try and it worked but not as good as my previous configuration. So I removed everything and installed my stuff from the start and everything's cool again...

---

