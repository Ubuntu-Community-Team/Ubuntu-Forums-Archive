---
title: "JDownloader"
date: 2009-04-23
forum: General Help
---

### Post by nukem170 on 2009-04-23
So I installed JDownloader([http://jdownloader.org/](http://jdownloader.org/)) this morning to help download from rapidshare easily. After installing the program started up on it's own and seemed to run perfectly. Now the issue is that after I closed it I can figure out how to launch it again. I couldnt find a help file or anything and the website didnt really have much help for linux either. So if anyone know about this program can you please tell me how to launch it again? Either the console command or how to create a shortcut.

---

### Post by michy99 on 2009-04-23
Try this:

```
cd ~/.jd
java -jar JDownloader.jar
```

---

### Post by nukem170 on 2009-04-24
Wow that worked. Thanks a lot.

---

### Post by Find on 2009-05-19
You can also add a launcher on Applications menu, if you already dont have it!

Make a menu item for JDownloader:
[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**nano**[/COLOR] [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]share[COLOR=#000000]**/**[/COLOR]applications[COLOR=#000000]**/**[/COLOR]JDownloader.desktop

[FONT=Verdana]Then paste the following[/FONT]

[COLOR=#7A0874]**[**[/COLOR]Desktop Entry[COLOR=#7A0874]**]**[/COLOR]
[COLOR=#007800]Encoding[/COLOR]=UTF-[COLOR=#000000]8[/COLOR]
[COLOR=#007800]Name[/COLOR]=JDownloader
[COLOR=#007800]Comment[/COLOR]=Download Manager
[COLOR=#007800]Exec[/COLOR]=java [COLOR=#660033]-jar[/COLOR] [COLOR=#000000]**/**[/COLOR]opt[COLOR=#000000]**/**[/COLOR]JDownloader[COLOR=#000000]**/**[/COLOR]JDownloader.jar
[COLOR=#007800]Icon[/COLOR]=[COLOR=#000000]**/**[/COLOR]opt[COLOR=#000000]**/**[/COLOR]JDownloader[COLOR=#000000]**/**[/COLOR]JDownloader.png
[COLOR=#007800]Terminal[/COLOR]=[COLOR=#C20CB9]**false**[/COLOR]
[COLOR=#007800]Type[/COLOR]=Application
[COLOR=#007800]Categories[/COLOR]=GNOME;Network;
[COLOR=#007800]StartupNotify[/COLOR]=True
[FONT=Verdana]
save the file using ctrl+o
You now have it in your Application > Internet[/FONT]

---

### Post by SentientFluid on 2009-05-19
Could also add a launcher to the Desktop, panel, or by Edit Menu (via right-clicking the Main Menu icon). Use [I]java -jar /opt/JDownloader/JDownloader.jar
[/I] for the command, and manually browse to the icon.

---

### Post by crystaldart on 2009-08-02
> **Find said:**
> You can also add a launcher on Applications menu, if you already dont have it!

Make a menu item for JDownloader:
[COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**nano**[/COLOR] [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]share[COLOR=#000000]**/**[/COLOR]applications[COLOR=#000000]**/**[/COLOR]JDownloader.desktop

[FONT=Verdana]Then paste the following[/FONT]

[COLOR=#7a0874]**[**[/COLOR]Desktop Entry[COLOR=#7a0874]**]**[/COLOR]
[COLOR=#007800]Encoding[/COLOR]=UTF-[COLOR=#000000]8[/COLOR]
[COLOR=#007800]Name[/COLOR]=JDownloader
[COLOR=#007800]Comment[/COLOR]=Download Manager
[COLOR=#007800]Exec[/COLOR]=java [COLOR=#660033]-jar[/COLOR] [COLOR=#000000]**/**[/COLOR]opt[COLOR=#000000]**/**[/COLOR]JDownloader[COLOR=#000000]**/**[/COLOR]JDownloader.jar
[COLOR=#007800]Icon[/COLOR]=[COLOR=#000000]**/**[/COLOR]opt[COLOR=#000000]**/**[/COLOR]JDownloader[COLOR=#000000]**/**[/COLOR]JDownloader.png
[COLOR=#007800]Terminal[/COLOR]=[COLOR=#c20cb9]**false**[/COLOR]
[COLOR=#007800]Type[/COLOR]=Application
[COLOR=#007800]Categories[/COLOR]=GNOME;Network;
[COLOR=#007800]StartupNotify[/COLOR]=True
[FONT=Verdana]
save the file using ctrl+o
You now have it in your Application > Internet[/FONT]

Done it. But it shows the running icon and then nothing :(
It had run on the first time on installation.

No what shall i do ?

---

### Post by t-vercetti on 2009-08-13
hey guys, i need your help!

i tried to install jdownloader 2 ways.

1.) downloaded the zip file, extraxted it and entered this in the terminal:
java -jar JDownloader.jar
this did not start the installation/startup process (and yes, i am in the right folder).

2.) i tried the alternative method mentioned on the jdownloader homepage using the jd.sh file.
i typed "sh jd.sh" in the terminal after downloading the file which then started the installation/startup process just fine and i can start the program every time by entering "sh jd.sh". 
just fyi: typing "start jd.sh" (mentioned on the jdownloader site) does not work for me either, the terminal gives me this error: "start: Unknown job: jd.sh". 
i got the command "sh jd.sh" off another forum.

ok, so far so good. here's my real problem:

i just wish i could a make a shortcut to the desktop now.
i read this should do the trick, but it doesn't for me:
right click on desktop, "create launcher...", enter the following under command:
"java -jar /home/*my_username*/.jd/JDownloader.jar"

openig the jd.sh file told me the location of the installation, which -as you can see above- is in the hidden folder ".jd"
still, hitting the icon on the desktop won't open jdownloader.

please help!
what's going on here? method 1 doesn't work, "start jd.sh" doesn't work, and the shortcut won't start the prog!

thanx in advance,
vercetti.

---

### Post by michy99 on 2009-08-13
Here's the command from my launcher:```
java -Xmx512m -jar  /opt/JDownloader/JDownloader.jar jiaz jd-team
```Of course, you have to change the /opt/JDownloader/JDownloader.jar part to wherever your JDownloader.jar is.

---

### Post by t-vercetti on 2009-08-13
hey michy99!

this really worked! incredible! i can't believe it, hehe!

i read that the 512 in the command stand for the 512mb that are used for jdownloader. does this mean that jdownloader will use 512mb always, or is the just the maximum entry and it will in fact use less most of the time?

and how did you get to this command line? 
thx,
vercetti.

---

### Post by minxie on 2009-08-14
i've tried all of these suggestions and none of them worked... i installed JDownloader both ways (through the zipped file and then again using jd.sh, also having to use sh jd.sh)... the program comes up fine the first time, and i can get it all configured and working, but when i go to start it up again, nothing works... i'm using ubuntu 9.04

if anyone has any other suggestions, i'd appreciate it a lot... just remember that i'm a complete newbie to linux and ubuntu altho not afraid to use the terminal

thanks!

---

### Post by t-vercetti on 2009-08-16
@minxie:

so you can only start jd once with the "sj. jd.sh" command?
if you close it and then try to start it again with the same command it won't start anymore?

greetz,
vercetti.

---

### Post by merlin666 on 2009-08-19
Thanks for the instructions, this is a nice application. The only "problem" I have is that it loads slow as molasses. Not sure if it's java or plugins or just slow by nature. Is there a way how the loading time could be improved?

---

### Post by __ShaM__ on 2009-12-26
AttentioN Ubuntu GuRus:
Another Thing In My MinD Teasing Me Since LasT Night Is That How To Launch JDownloader Automatically @ SysTem Startup, One Good Example is IDM in Windows :(....
n One Thing More Im UsinG Linux Mint 8 :guitar:.
Despretly W8ing For The Reply...

---

### Post by ok_dr on 2009-12-26
Now I'm no Ubuntu guru, but can't you do it simply by adding it to the startup applications. I installed it using the jd.sh method, in the launcher command field simply put "pathtojd.shfolder/jd.sh" and it's done.

---

### Post by vinan on 2010-03-03
**[COLOR=DarkRed]Solved [/COLOR]**

For those who still bump thier heads in JD in Ubuntu do this

First Java
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk sun-java6-plugin
sudo update-java-alternatives -s java-6-sun

and Jdownloader
wget -c [http://212.117.163.148/jd.sh](http://212.117.163.148/jd.sh)
chmod +x jd.sh
./jd.sh


after install 
make a shor cut in you panel rightclick -> add to panel-> Custom app Launcher->add-> _Type:_ **Apps in Terminal** _Name:_** JD**,  _CMD:_ **sudo ./jd.sh** , _Coments:_what ever u like. -> and OK

next time hit this shortcut and enter your root pass

Jd run smoothly

:D
Cheers

---

### Post by Keith1212 on 2010-03-03
> **vinan said:**
> Solved 

For those who still bump thier head in JD in Ubuntu do this


sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-jdk sun-java6-plugin
sudo update-java-alternatives -s java-6-sun


wget -c [http://212.117.163.148/jd.sh](http://212.117.163.148/jd.sh)
chmod +x jd.sh
./jd.sh


after install 
make a shor cut in you panel rightclick -> add to panel-> make a shortcut->add-> _Type:_ **Program in Termilnal** _Name:_** JD**,  _CMD:_ **sudo ./jd.sh** , _Coments:_what ever u like. -> and OK

next time hit this shortcut and enter your root pass

Jd run smoothly

:D
Cheers

I just insalled Ubuntu yesterday and was gonna get Jdownloader going today cause i can't live without it. Anyways this worked for me perfectly. Thank You very much.

---

### Post by vinan on 2010-03-04
> **Keith1212 said:**
> I just insalled Ubuntu yesterday and was gonna get Jdownloader going today cause i can't live without it. Anyways this worked for me perfectly. Thank You very much.



you are welcome

---

