---
title: "How to install StepMania in Ubuntu 12.04LTS 64-bit"
date: 2013-04-08
forum: Gaming &amp; Leisure
---

### Post by FenrirXIII on 2013-04-08
StepMania - basically Dance Dance Revolution (DDR) in a computer. keyboard, controller and even Dance Pad friendly. Great game for workingout or just unwinding. 

 

 **Prerequisites:**
 

 
[LIST]
[*]Internet Connection 
[*]Meet StepMania system     requirement/s. 
[*]Download the 64-bit binary of     StepMania
[LIST]
[*]In this case,         StepMania-v5.0-beta1a-linux64.tar.bz2 
[/LIST]
  
[/LIST]
 

 **Package Dependencies**
 

 
[LIST]
[*]libpng15.so.15 
[*]libglew1.8 
[/LIST]
 

 **Step 1: Download the files**
 

     **libpng15.so.15**
 

 [TABLE="class: outer_border, width: 100%"]
[TR]
[TD="width: 100%"]             
sudo add-apt-repository ppa:linaro-maintainers/overlay sudo apt-get update sudo apt-get install libpng1.5         [/TD]
[/TR]
[/TABLE]
 

     **libglew1.8**
         [COLOR=#0000ff]_**Although **_[/COLOR][COLOR=#0000ff]_**this package**_[/COLOR][COLOR=#0000ff]_**'s release is for 12.10, libglew1.8 works **_[/COLOR][COLOR=#ff0000]_**perfectly**_[/COLOR][COLOR=#0000ff]_** in 12.04LTS**_[/COLOR]
 

 
[LIST]
[*]64-bit (Click link) 
[/LIST]
 [http://security.ubuntu.com/ubuntu/pool/main/g/glew/libglew1.8_1.8.0-1ubuntu2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/g/glew/libglew1.8_1.8.0-1ubuntu2_amd64.deb)
 

 download the .deb file, locate and install in Ubuntu Software Center.
 

 or
 

 **If the link is broken, search the package in: [www.ubuntuupdates.org]("http://www.ubuntuupdates.org/")**
 

 **Step 2: Installing Stepmania-v5.0**
 

 
[LIST]
[*]_After     downloading_     &#8220;StepMania-v5.0-beta1a-linux64.tar.bz2&#8221;,     _locate the file and     move it on the Desktop_ 
[*]_Double     click and Unzip (extract)_     StepStepMania-v5.0-beta1a-linux64.tar.bz2     to _**Desktop**_
[LIST]
[*]here's         a different variation on how to extract it via Terminal 
[/LIST]
  
[/LIST]
 [TABLE="class: outer_border, width: 100%"]
[TR]
[TD="width: 100%"]             cd Desktop
             tar -jxvf StepMania-v5.0-beta1a-linux64.tar.bz2
                      [/TD]
[/TR]
[/TABLE]
 

 
[LIST]
[*]**Run     the program (via Terminal)** 
[/LIST]
 [TABLE="class: outer_border, width: 100%"]
[TR]
[TD="width: 100%"]             cd Desktop/stepmania
             ./stepmania

                      [/TD]
[/TR]
[/TABLE]
 

 THERE! It's running good... except _maybe you want to clean it up a bit_.
 

 
[LIST=1]
[*]Neat     Setup 
[*]Create     a Launcher 
[/LIST]
 

 **1. Neat Setup**
 

 
[LIST]
[*]Go     to Desktop and open the stepmania folder.
[LIST]
[*]_Select         all, Cut._ 
[/LIST]
           
[*]Go     to home folder and Show Hidden Files **(View     Tab > Show Hidden Files)**
[LIST]
[*]locate         _.stepmania-5.0_         and open folder
[LIST]
[*]_Paste_             files here. 
[/LIST]
     
 
[/LIST]
      
[*]Neat     Setup Compete
[LIST]
[*]You         may delete the stepmania folder on the Desktop. 
[/LIST]
  
[/LIST]
 **2. Create a Launcher**
 
Google "StepMania Icon" and select a suitable icon and save it as "stepmania.png" in home folder /.stepmania-5.0
 
[LIST]
[*]sudo     gedit /usr/share/applications/StepMania.desktop
[LIST]
[*]password         prompt 
[/LIST]
      
[*]Type/Copy     the following: 
[/LIST]
 [TABLE="class: outer_border, width: 100%"]
[TR]
[TD="width: 100%"]             [Desktop Entry]
             Version=5.0beta
             Type=Application
             Terminal=false
             StartupNotify=true
             Icon=/home/(YOUR_USERNAME)/.stepmania-5.0/stepmania.png
             Name=StepMania
             Comment=StepMania
             Exec=/home/YOUR_USERNAME)/.stepmania-5.0/stepmania
             Categories=Application; Games;

         [/TD]
[/TR]
[/TABLE]
 

 
[LIST]
[*]SAVE and Close
[LIST]
[*][COLOR=#ff0000]_**If         for some reason it won't save, click Save as... and save it on:**_[/COLOR]
[LIST]
[*]File System:             _/usr/share/applications_ 
[/LIST]
      
[/LIST]
  
[/LIST]
 

 CONGRATULATIONS! You have successfully, manually installed StepMania
 

 BONUS: ADDING SONGS!!!
 

 
[LIST]
[*]on the home folder, Show Hidden     Folders and  open .stepmania
[LIST]
[*]CREATE a Songs folder 
[/LIST]
      
[*]On [www.stepmania.com]("http://www.stepmania.com/")     download songs on the Download category
[LIST]
[*]extract your downloaded songs and         put them in the Songs folder of the hidden .stepmania-5.0 folder         located in the home folder when Show Hidden File is checked. 
[/LIST]
  
[/LIST]
 

 **ENJOY**
 

 *TIP:*
 

 [I]There are some DDR .smzip out there. Search the web for more info.
With a controller or Dance Pad, Go to Options to configure button/key mapping.
[/I]

---

### Post by MSoles on 2013-07-02
I did some alterations on your tutorial because I have a 32-bit version but it worked out none of the less.

Oh and here's one more tip for adding songs.

[LIST]**If you already have a songs folder somewhere else and you want to add it to SM5, go to the home folder, Show Hidden Folders and open .stepmania and then open Save.**
[/LIST]

There should be a file called Preferences.ini open that with your text editing program (GEdit) and there should be a line saying.

```
AdditionalSongFolders=
```

now locate where your song is and then type it in

```
AdditionalSongFolders=/media/(YOUR HARD DISK DRIVE NAME)/(YOUR SONGS FOLDER)/Songs
```

Save the file and close your text editing program, run the Stepmania program and it'll load your songs that you told to find.

---

### Post by Moses_Moore on 2013-09-11
I just built Stepmania 5.x from source and I came to Ubuntu Forums to describe my pitfalls.

The prereq list is in the opening post is too short.  It wasn't working for me until I found a mention in a Japanese-only mailing list about Stepmania about getting sound drivers working correctly.


[LIST]
[*]Get the tarball from [http://sourceforge.net/settings/mirror_choices?projectname=stepmania&filename=stepmania/5.0%20beta%202a/stepmania-5.0b2a-src.tar.bz2](http://sourceforge.net/settings/mirror_choices?projectname=stepmania&filename=stepmania/5.0%20beta%202a/stepmania-5.0b2a-src.tar.bz2) 
[*]cd $(mktemp -d) 
[*]tar xjf /tmp/stepmania-5.*-src.tar.bz2 
[*]cd stepmania-tip 
[*]apt-get install libpng-dev libxrandr-dev libjpeg-dev libbz2-dev libvorbis-dev libmad0-dev libglew-dev libgtk2.0-dev libpulse-dev 
[*]./configure 
[*]make 
[*]sudo chown /opt $USER 
[*]make install # ye gods why would I have to `sudo make install` ? 
[*]sudo chown /opt root
[*]cd /top/stepmania\ 5/
[*]./stepmania 
[/LIST]
 
If you do not have libpulse-dev installed, ./configure will not error out, but the compiled Stepmania will keep telling you 'device not found: /dev/dsp' and trying it with `padsp` will wedge the pulseaudio daemon something terrible.

It will look in $HOME/.stepmania-5.0/Songs/ for your song&step files.  Without any Song files, some of the main menu settings will just send you to help files, which will want to open a webbrowser... but that doesn't work.  (The stepmania website is down today anyways, some problem with Google Docs since they're using that for hosting?)

I was able to keep using the electro-body-music stuff I made for Stepmania 3.8.

---

### Post by Espionage724 on 2013-12-19
> **Moses_Moore said:**
> I just built Stepmania 5.x from source and I came to Ubuntu Forums to describe my pitfalls.

The prereq list is in the opening post is too short.  It wasn't working for me until I found a mention in a Japanese-only mailing list about Stepmania about getting sound drivers working correctly.
Just wanted to say thanks for this guide :) StepMania 5 seems to work fine for me after following these instructions on 13.10.

As for the **make** command, if my limited understanding is right, you could attach **-j #** onto it to use more cores for a faster compile (so **make -j 4**). Guess the general rule is to use a little less than double the CPU cores you have or something, but I used **-j 6** without problem on a quad core system.

---

