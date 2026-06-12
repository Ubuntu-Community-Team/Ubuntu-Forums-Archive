---
title: "How to install pSX, ePSXe, PCSX Reloaded on Ubuntu 10.10 x86"
date: 2010-12-16
forum: Emulators
---

### Post by Buttink on 2010-12-16
First of all if you notice any mistakes please tell me. I wrote this so that no one has to go thought the massive pain of finding all the solutions for these emulators.

[SIZE="4"]**How To Use**[/SIZE]

[INDENT]
This guide is set up in the format of explaining how to manually perform each step and then providing command line instructions to do them automatically. Some commands require you to have a specific file structure. Also, every blue word is a link to a website or download.
[/INDENT]



[SIZE="4"]**PCSX Reloaded - Recommended**[/SIZE]

[INDENT]
There are multiple ways to get pcsxr. You can download from there [[COLOR="Blue"]site[/COLOR]]("http://pcsxr.codeplex.com/"), or get it from [[COLOR="Blue"]playdeb[/COLOR]]("http://www.playdeb.net/welcome/"). Playdeb does not contain the OpenGL plugin that the site does. So basically if you need fullscreen and more resolutions, download from the site [[COLOR="Blue"]here[/COLOR]]("http://pcsxr.codeplex.com/"). If you want the PlayDeb version simply run these commands.

```
wget http://archive.getdeb.net/install_deb/playdeb_0.3-1~getdeb1_all.deb
sudo dpkg -i playdeb_0.3-1~getdeb1_all.deb
sudo apt-get update
sudo apt-get install pcsxr
```

pscxr can simulate a bios file. However if you need to use a bios, just move the bios file into  "~/.pcsx/bios/".

```
cp scph1001.bin ~/.pcsx/bios/
```

If you are using the PlayDeb version and really want an opengl driver you can get one from [[COLOR="Blue"]Pete's Domain[/COLOR]]("http://www.pbernert.com/index.htm"). Note however that this plugin config uses GTK+1.2. So you must install GTK+1.2 or edit the setting in the .cfg file. [See ePSXe on how to get GTK+1.2].

```
tar xzvf gpupeopsmesagl178.tar.gz
mv peops_psx_mesagl_gpu/*PeopsMesaGL* ~/.pcsx/plugins/
rm -r peops_psx_mesagl_gpu/
```

Now, you should be all set.
[/INDENT]



[SIZE="4"]**ePSXe via Wine - Best Compatibility**[/SIZE]

[INDENT]
First, you will need Wine. Which version of wine you install is up to you. Ubuntu by default comes with Wine 1.2.x. You can install it with your package manager. You can also add a more up to date PPA to get Wine 1.3.x. Wine places everything it needs in a ".wine" folder. Wine will not create its ".wine" folder unless a program that uses Wine has been ran. So after you install Wine, run "winecfg".

```
sudo apt-get install wine1.2
winecfg

or

sudo apt-add-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine1.3
winecfg
```

Now, you have to download ePSXe from there [[COLOR="Blue"]site[/COLOR]]("http://www.epsxe.com/"). You need to place it in your wine's drive_c folder. You can put it anywhere you like, but I place it in a folder called "Emulators".

```
wget http://www.epsxe.com/files/epsxe170.zip
unzip epsxe107.zip -d ePSXe
mkdir -p ~/.wine/drive_c/Emulators
mv ePSXe ~/.wine/drive_c/Emulators
rm epsxe107.zip
```

This will make a Emulators folder in your wine's drive_c and place ePSXe in it. It is assumed this is how your file structure is for the rest of the guide.

ePSXe uses plugins to handle things like graphics and sound. A very good site for plugins is [[COLOR="blue"]http://www.pbernert.com/index.htm[/COLOR]]("http://www.pbernert.com/index.htm"). Some plugins might work better for your system, but in general you only need this plugin - [[COLOR="Blue"]graphics[/COLOR]]("http://www.pbernert.com/gpupeopsopengl178.zip"). I found that a sound plugin was not nessisary for my system. However, if needed just go to [[COLOR="blue"]http://www.pbernert.com/html/spu.htm[/COLOR]]("http://www.pbernert.com/html/spu.htm") and select a sound plugin. Now, we need to place the plugin in the correct spot so ePSXe can find and use them. Extract the *.dll files and place them in "~/.wine/drive_c/Emulators/ePSXe/plugins" folder.

```
wget http://www.pbernert.com/gpupeopsopengl178.zip
unzip gpupeopsopengl178.zip -d PeteGPU
mv PeteGPU/*.dll ~/.wine/drive_c/Emulators/ePSXe/plugins/
rm -r PeteGPU/
```

Now all you need is a bios file. Just move the bios file into  "~/.wine/drive_c/Emulators/ePSXe/bios/".

```
cp scph1001.bin ~/.wine/drive_c/Emulators/ePSXe/bios/
```

You can now run ePSXe.

```
cd ~/.wine/drive_c/Emulators/ePSXe
wine epsxe.exe
```

Now you just have to configure ePSXe to your liking.
[/INDENT]


[SIZE="4"]**ePSXe Native**[/SIZE]

[INDENT]
As far as I know, there is no package for ePSXe. So, you have to download it from there [[COLOR="Blue"]site[/COLOR]]("http://www.epsxe.com/").

```
wget http://www.epsxe.com/files/epsxe160lin.zip
unzip epsxe160lin.zip -d ePSXe
mkdir ~/Emulators
mv ePSXe ~/Emulators
```

This will make a Emulators folder in your home and place ePSXe in it. It is assumed this is how your file structure is for the rest of the guide.

ePSXe uses plugins to handle things like graphics and sound. A very good site for plugins is [[COLOR="blue"]http://www.pbernert.com/index.htm[/COLOR]]("http://www.pbernert.com/index.htm"). Some plugins might work better for your system, but in general you want to get these plugins -  [[COLOR="Blue"]graphics[/COLOR]]("http://www.pbernert.com/gpupeopsmesagl178.tar.gz"), [[COLOR="Blue"]sound[/COLOR]]("http://www.pbernert.com/spupeopsoss109.tar.gz").

```
wget http://www.pbernert.com/gpupeopsmesagl178.tar.gz
wget http://www.pbernert.com/spupeopsoss109.tar.gz
```

Unforcunitly, the plugins use GTK+1.2. This is a problem because it has been depreciated and is no long available. To get it, we need to add a PPA. The PPA we need to add is [[COLOR="Blue"]this one[/COLOR]]("https://launchpad.net/~adamkoczur/+archive/gtk1.2") from Adam Koczur. You can open your package manager then edit sources. However, you also have to add the key. This is one situation where you should just use the command line.

```
sudo apt-add-repository ppa:adamkoczur/gtk1.2
sudo apt-get update
sudo apt-get install libgtk1.2
```

This should install all the GTK+1.2 library files we need for the emulators.

Now we need to place the plugins in the correct spot so ePSXe can find and use them. The executable cfg* and the *.cfg need to go into the cfg folder. An example would be "cfgPeopsOSS" and "spuPeopsOSS.cfg". They need to go in "~/Emulators/ePSXe/cfg/". The library file, *.so.* must go into the plugins folder, "~/Emulators/ePSXe/plugins/". An example would be "libspuPeopsOSS.so.1.0.9".

```
tar xzvf gpupeopsmesagl178.tar.gz
mv peops_psx_mesagl_gpu/libgpuPeopsMesaGL.so.1.0.78 ~/Emulators/ePSXe/plugins/
mv peops_psx_mesagl_gpu/gpuPeopsMesaGL.cfg ~/Emulators/ePSXe/cfg/
mv peops_psx_mesagl_gpu/cfgPeopsMesaGL ~/Emulators/ePSXe/cfg/
rm -r peops_psx_mesagl_gpu/
tar zxvf spupeopsoss109.tar.gz
mv libspuPeopsOSS.so.1.0.9 ~/Emulators/ePSXe/plugins/
mv cfgPeopsOSS ~/Emulators/ePSXe/cfg/
mv spuPeopsOSS.cfg ~/Emulators/ePSXe/cfg/
rm version_1_9.txt readme_1_9.txt
```

Now all you need is a bios file. Just move the bios file into  "~/Emulators/ePSXe/bios/".

```
cp scph1001.bin ~/Emulators/ePSXe/bios/
```

You can now run ePSXe. There might not be audio which can be fixed by using the pulseaudio OSS wrapper.

```
padsp ./epsxe
```

Now you just have to configure ePSXe to your liking.
[/INDENT]



[SIZE="4"]**pSX**[/SIZE]

[INDENT]
I have heard that there is a package for pSX, but I can't find it. Its probably for an older version of Ubuntu. Anyway, you can download pSX from there [[COLOR="Blue"]site[/COLOR]]("http://psxemulator.gazaxian.com/").

```
wget http://psxemulator.gazaxian.com/pSX_linux_1_13.tar.bz2
tar xzvf pSX_linux_1_13.tar.bz2
mkdir ~/Emulators
mv pSX ~/Emulators
```

pSX requires no plugins! However, pSX does require an extra gtk library, specificaly "libgtkglext1".

```
sudo apt-get install libgtkglext1
```

pSX needs a bios. Place the bios in "pSX/bios/".

```
cp scph1001.bin ~/Emulators/pSX/bios/
```

pSX has a huge problem. The sound plugin does not like pusleaudio. Basically, we have to shutdown pulse audio to change the sound device in pSX. pSX defaults to "Default". This causes it to crash. All we have to do it set it to an actual audio device. Then everything will work fine. These steps are quite involved so the command line is perfered. When pSX starts change the audio device and quit.

**MANUALLY**
First, we have to do is shut down pulseaudio. If your Ubuntu is set up like mine, it will auto start right after you close it. This can be fixed by making a "client.conf" in your ".pulse" folder located in your home folder. Inside of "client.conf", you need to enter "autospawn=no". Save and exit. Then, kill pulseaudio with "pulseaudio --kill" or "killall pulseaudio". You may have to run this twice because pulseaudio hasn't used your client.conf wasn't loaded the first time you killed pulseaudio. Then, run pSX with "./pSX". Make sure you are in the correct folder when you do "./pSX" or it will tell you it cannot find the file. Go to configuration -> sound. Select anything besides "Default". "Default" is the whole reason it crashes with pulseaudio. Exit pSX. Move or Delete the client.conf. Start pulseaudio with "pulseaudio --start". Then see if pSX works with pulse "./pSX".

**SEMI MANUALLY**
```
cd ~/.pulse/
echo "autospawn=no" >> client.conf
service pulseaudio restart
pulseaudio --kill
cd ~/Emulators/pSX/
echo "Set your audio device to anything BUT \"Default\""
./pSX

mv ~/.pulse/client.conf ~/.pulse/client.conf.backup
pulseaudio --start
```

Now pSX should start and have sound.
[/INDENT]

[SIZE="4"]**External Links**[/SIZE]

Adam Koczur GTK+1.2 PPA - [[COLOR="Blue"]link[/COLOR]]("https://launchpad.net/~adamkoczur/+archive/gtk1.2")
Pete's Domain PCSX Plugins - [[COLOR="Blue"]link[/COLOR]]("http://www.pbernert.com/index.htm")
PCSX Reloaded - [[COLOR="Blue"]link[/COLOR]]("http://pcsxr.codeplex.com/")
ePSXe - [[COLOR="Blue"]link[/COLOR]]("http://www.epsxe.com/")
pSX - [[COLOR="Blue"]link[/COLOR]]("http://psxemulator.gazaxian.com/")

---

### Post by thatguruguy on 2010-12-16
You're covering ground which has been well-traveled already.  However, I would like to point out that the version of pcsx-r hoted by playdeb is significantly out-of-date.  It is a much better idea to simply download and install the version from the pcsx-r website, particularly since he was kind enough to provide a .deb for both i386 and amd64 users.  

All the rest of the instructions you give for pcsx-r are either 1) unnecessary or 2) wrong.  If anyone wants that package, all the need to do is download and install the appropriate .deb, and they should be good to go.

---

### Post by Buttink on 2010-12-16
> **thatguruguy said:**
> You're covering ground which has been well-traveled already.  However, I would like to point out that the version of pcsx-r hoted by playdeb is significantly out-of-date.  It is a much better idea to simply download and install the version from the pcsx-r website, particularly since he was kind enough to provide a .deb for both i386 and amd64 users.  

All the rest of the instructions you give for pcsx-r are either 1) unnecessary or 2) wrong.  If anyone wants that package, all the need to do is download and install the appropriate .deb, and they should be good to go.

Edited the entire PCSX Reloaded section.

The version of the playdeb is 2:1.9.92-1~getdeb1 vs 2:1.9.92-1 on pcsxr site. I'm not arguing that the one from the site isn't newer. But, I personally don't like to have to redownload for each new version. I'v got a package manager I like to use it. However, The one from the site does include a OpenGL plugin (didn't know that). The new version also includes a SDL sound driver which would simplify a lot of these instructions.

---

### Post by Buttink on 2010-12-17
Anyone know if there is any Community Documentation for these Emulators? If not, we should add it. I'v looked but the GamesEmulators sections is kinda small.

---

### Post by muzikayise on 2010-12-18
> **Buttink said:**
> First of all if you notice any mistakes please tell me. I wrote this so that no one has to go thought the massive pain of finding all the solutions for these emulators.

[SIZE="4"]**How To Use**[/SIZE]

[INDENT]
This guide is set up in the format of explaining how to manually perform each step and then providing command line instructions to do them automatically. Some commands require you to have a specific file structure. Also, every blue word is a link to a website or download. First perform the actions in General and then move on to the emulator of your choice.
[/INDENT]



[SIZE="4"]**PCSX Reloaded**[/SIZE]

[INDENT]
There are multiple ways to get pcsxr. You can download from there [[COLOR="Blue"]site[/COLOR]]("http://pcsxr.codeplex.com/"), or get it from [[COLOR="Blue"]playdeb[/COLOR]]("http://www.playdeb.net/welcome/"). Playdeb does not contain the OpenGL plugin that the site does. So basically if you need fullscreen and more resolutions, download from the site [[COLOR="Blue"]here[/COLOR]]("http://pcsxr.codeplex.com/"). If you want the PlayDeb version simply run these commands.

```
wget http://archive.getdeb.net/install_deb/playdeb_0.3-1~getdeb1_all.deb
sudo dpkg -i playdeb_0.3-1~getdeb1_all.deb
sudo apt-get update
sudo apt-get install pcsxr
```

pscxr can simulate a bios file. However if you need to use a bios, just move the bios file into  "~/.pcsx/bios/".

```
cp scph1001.bin ~/.pcsx/bios/
```

If you are using the PlayDeb version and really want an opengl driver you can get one from [[COLOR="Blue"]Pete's Domain[/COLOR]]("http://www.pbernert.com/index.htm"). Note however that this plugin config uses GTK+1.2. So you must install GTK+1.2 or edit the setting in the .cfg file. [See ePSXe on how to get GTK+1.2].

```
tar xzvf gpupeopsmesagl178.tar.gz
mv peops_psx_mesagl_gpu/*PeopsMesaGL* ~/.pcsx/plugins/
rm -r peops_psx_mesagl_gpu/
```

Now, you should be all set.
[/INDENT]


hi if i may just advise ppl that PCSX-Reloaded is probably the best one to install on ubuntu 10.10. 
- i tried ePSXe but my sound didn't work  
- i couldnt get pSX to work at all
- PCSX Reloaded was simple and easy but i recommend trying to ePSXe via command line especially if you're new to Ubuntu just like me because you'll learn some commands that you might need for other stuff plus its fun getting your hands dirty. but once you have had enough just download PCSX Reloaded from code [http://pcsxr.codeplex.com/releases/view/50048](http://pcsxr.codeplex.com/releases/view/50048) and select this: pcsxr_1.9.92-1_i386.deb file it will install everything for you. all you need is bios.

therefore PCSX Reloaded (pcsxr_1.9.92-1_i386.deb) from [http://pcsxr.codeplex.com/releases/view/50048](http://pcsxr.codeplex.com/releases/view/50048) is the one to get.

[IMG]http://img696.imageshack.us/img696/52/screenshotpcsx.png[/IMG]
By [muzikayise](http://profile.imageshack.us/user/muzikayise)

good luck

---

### Post by thatguruguy on 2010-12-18
> **Buttink said:**
> Edited the entire PCSX Reloaded section.

The version of the playdeb is 2:1.9.92-1~getdeb1 vs 2:1.9.92-1 on pcsxr site. I'm not arguing that the one from the site isn't newer. But, I personally don't like to have to redownload for each new version. I'v got a package manager I like to use it. However, The one from the site does include a OpenGL plugin (didn't know that). The new version also includes a SDL sound driver which would simplify a lot of these instructions.

I see that playdeb updated the .deb for Maverick as of December 13, 2010.  They still have the out-of-date one for Lucid.  Given the fact that they lag behind the pcsx-r site, and the fact that the guy who puts pcsx-r is kind enough to package .debs for Debian-based distros (like ubuntu), I still recommend getting the package from his site rather than playdeb.  Playdeb is a great resource, generally, but they lag behind in the case of this particular package.

---

### Post by Buttink on 2010-12-18
> **thatguruguy said:**
> I see that playdeb updated the .deb for Maverick as of December 13, 2010.  They still have the out-of-date one for Lucid.  Given the fact that they lag behind the pcsx-r site, and the fact that the guy who puts pcsx-r is kind enough to package .debs for Debian-based distros (like ubuntu), I still recommend getting the package from his site rather than playdeb.  Playdeb is a great resource, generally, but they lag behind in the case of this particular package.

It would be sweet if i could set up some sort of commands to auto install PCSX-R from command line from the web site. The only problem is I don't know if there is a newest link or where to find it. If you have an idea, that would be amazing.

---

### Post by Buttink on 2010-12-24
Added ePSXe via Wine because the native one sucks >.> and PCSX-R wouldn't play Megaman Legends 2 :)

---

### Post by Buttink on 2010-12-25
Fixed how to run epsxe from wine (got all stupid when i typed and inserted the linux native method >.>)

---

### Post by SuperMau on 2012-03-16
Sorry to ask but I can not find the answer anywhere. Is there any way to play compressed iso files on PCSX in order to save some disk space?

---

