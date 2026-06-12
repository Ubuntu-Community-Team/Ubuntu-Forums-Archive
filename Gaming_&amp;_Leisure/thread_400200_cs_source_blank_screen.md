---
title: "cs source blank screen"
date: 2007-04-03
forum: Gaming &amp; Leisure
---

### Post by g_monkey on 2007-04-03
ok so i got cs source installed on edgy all seemed to go fine, until i go to play it, it starts to load and i see the main screen(with the guy in the background) but the menu doesnt load and then the screen goes blank and nothing happens, is this likely to be because i only have the drivers from the repositary installed and not the official ATI drivers form the site? bear with me this is my first time on linux/ubuntu, although im doin ok and loving it by the way :)

---

### Post by frodon on 2007-04-03
First what are you using to run CS:S ? wine, cedega or crossover

Then tell us what's the version number of the software you use and what you did to install CS:S.

---

### Post by g_monkey on 2007-04-04
sorry i was long i've been busy, ok i have a new problem now, i tried to reinstall wine and cs:s using [_[COLOR="Red"]this[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=304528") guide, all seemed to ok but when i try to run i using this code 

```
cd /home/USER/.wine/drive_c/Program Files/Steam
WINEDEBUG="fixme-all" wine steam.exe
```

i get 'cannot find c:\\...........steam.exe' or words to that effect, so i tried installing, thinking it hadnt worked, with 

```
wine SteamInstall.exe
```

and it goes through the installation process and i have to set my connection etc again and it loads up and starts updating cs, when it finished updating i shut down steam and restarted my computer, more out of habit than anything, anyway when i try to use the first piece of code again to run steam i get the same 'cannot find c:\\......steam.exe, 

so i use the second piece of code again and the same thing happens, it installs like its the first time and when it loads up its already 100% updated so it must be there somewhere just not the right code maybe?

anyway i start up the game change settings etc and when i go to find servers they pop up for a second then disappear, weird? they are still there and updating as i can see the numbers racking up but i cannot see them, i have to hit the refresh button twice quickly to start and stop the refresh before they disappear, giving me about 3-5 servers to choose from, 

and on top of that i hear no sound and when i try to run a sound test, stress test or the actual game i get these errors

[_[COLOR="Red"]pop up box[/COLOR]_]("http://i146.photobucket.com/albums/r264/g_monkey001/Screenshot.png")

[_[COLOR="Red"]on terminal[/COLOR]_]("http://i146.photobucket.com/albums/r264/g_monkey001/Screenshot-1.png")

im thinking maybe a complete uninstall of wine and steam and start again, how would i do that and whats the best way to install cs:s/steam?

---

### Post by frodon on 2007-04-05
What version of wine are you using ?

I advice you the latest 0.34 with which i have really good result and solve many D3D issues, you'll find it here :
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
Then if you still have problems you 'll need to check if you have well installed your graphic drivers and maybe post your xorg.conf here.

---

### Post by g_monkey on 2007-04-05
safe ill try that, what and then re install cs:s? do i need to uninstall it first, pretty sure my gfx drivers are ok, when i do fglrxinfo it says ATI and the correct driver numbers i installed

---

### Post by frodon on 2007-04-05
I don't think you need to re-install CS:S, BTW have a look to the guide on the wine site, it's pretty much the same but you may find usefull information there but don't use GLSL shader with the latest version you may have problems with :
[http://appdb.winehq.org/appview.php?iVersionId=3731](http://appdb.winehq.org/appview.php?iVersionId=3731)

---

### Post by g_monkey on 2007-04-05
safe cheers ill give it a bash and let you know how it goes ;)

---

### Post by g_monkey on 2007-04-05
ok so i decided to uninstall wine before reinstalling following the instructions you provided,perhaps my 1st mistake, so i did that through the packet manager, after this i checked my /home/user/.wine folder and it was still there with everything in it, so i manually deleted the contents, maybe my 2nd mistake

so i rebooted and reinstalled wine following [_[COLOR="Red"]this[/COLOR]_]("http://www.winehq.org/site/download-deb") page as suggested and all seems to install fine, when its finished though it has created this folder called '*wine-0.9.34~winehq0~ubuntu~6.10*' in my /home/user directory and there is nothing in /home/user/.wine, well it is there but there is only 2 files in it, system.reg and user.reg this doesnt seem right?

---

### Post by frodon on 2007-04-05
Strange indeed, and if you try configuring wine with "winecfg" does it work and create something under your .wine directory ?

---

### Post by g_monkey on 2007-04-05
this what i get when i run winecfg [_[COLOR="Red"]screenshot[/COLOR]_]("http://i146.photobucket.com/albums/r264/g_monkey001/Screenshot-3.png")

---

### Post by frodon on 2007-04-05
Hum, ok i think the quickest way would be to reinstall the package from the ubuntu repositories, open synaptic then search your wine package and force the ubuntu edgy version, detail on how to force a version here :
[https://help.ubuntu.com/community/SynapticHowto?highlight=%28synaptic%29#head-ec06ac55f7b20957887c4b9cfdea6efd07727415](https://help.ubuntu.com/community/SynapticHowto?highlight=%28synaptic%29#head-ec06ac55f7b20957887c4b9cfdea6efd07727415)

Then check your wine directory and maybe try winecfg again to check that all is fine. Then if all is fine upgrade your wine version to the 0.34 from the winehq repository again.

---

### Post by g_monkey on 2007-04-05
ok i tried this and is doesn't seem to do anything i still get the exact same problem, when i go to drives in winecfg i get [_[COLOR="Red"]this[/COLOR]_]("http://i146.photobucket.com/albums/r264/g_monkey001/Screenshot-7.png") error and [_[COLOR="Red"]this[/COLOR]_]("http://i146.photobucket.com/albums/r264/g_monkey001/Screenshot-6.png") is in the terminal when i try to add the c drive

---

### Post by g_monkey on 2007-04-05
sorry this is whats in the terminal [_[COLOR="Red"]this[/COLOR]_]("http://i146.photobucket.com/albums/r264/g_monkey001/Screenshot-8.png")

---

### Post by frodon on 2007-04-05
Strange, for the moment i don't really understand why the reinstall of the edgy package don''t solve the situation. Try to reinstall it again (i mean the edgy package) and watch the synaptic output log during the re-install, if there's some error they will appear there.
Maybe just paste the log here if you are not sure.

---

### Post by g_monkey on 2007-04-05
heres what i did 

forced version [[COLOR="Red"]_screen_[/COLOR]]("http://i146.photobucket.com/albums/r264/g_monkey001/Screenshot-9.png")

installed wine [_[COLOR="Red"]screen[/COLOR]_]("http://i146.photobucket.com/albums/r264/g_monkey001/Screenshot-10.png")

updated wine [_[COLOR="Red"]screen[/COLOR]_]("http://i146.photobucket.com/albums/r264/g_monkey001/Screenshot-11.png")

all seems to go well but still no /.wine directory :(

---

### Post by g_monkey on 2007-04-05
so i got really annoyed and thought f$%k it, formatted my hdd and started over, not the ideal solution i know but im impatient, anywho so im all up and firing got everything working i think

[_[COLOR="Red"]graphics[/COLOR]_]("http://i146.photobucket.com/albums/r264/g_monkey001/Screenshot-12.png")

[_[COLOR="Red"]wine directories[/COLOR]_]("http://i146.photobucket.com/albums/r264/g_monkey001/Screenshot-1-1.png")

[_[COLOR="Red"]winecfg[/COLOR]_]("http://i146.photobucket.com/albums/r264/g_monkey001/Screenshot-2-1.png")

so can you point me to the best way to install steam and cs:s

*also what audio settings should i have setup in winecfg?

ok scrap that i have installed it and its ok so far, its all properly there and in the applications list, just updating it, ill let u know how it goes

oh and it made a shortcut file and a 'Steam.Ink' file on my desktop, can i delete the 'Steam.Ink' file safely?

---

### Post by g_monkey on 2007-04-05
ok im back to the original problem when i load up the game the screen goes blank and it freezes :confused:

---

### Post by frodon on 2007-04-06
Ok so at least you are at the same step than at the beginning, just add the wine repository and update wine without uninstalling t previously or deleting the .wine repository.

---

### Post by g_monkey on 2007-04-06
> **frodon said:**
> Ok so at least you are at the same step than at the beginning, just add the wine repository and update wine without uninstalling t previously or deleting the .wine repository.

im pretty sure its updated to the max, will this really make any difference

[_[COLOR="Red"]wine version[/COLOR]_]("http://i146.photobucket.com/albums/r264/g_monkey001/Screenshot-3-1.png")

---

### Post by frodon on 2007-04-06
Ok, I guess you didn't added GLSL shader support so it shouldn'd be the problem.

While steam opened right click on CS:S and choose property then click on launch option or something like that then add these options "-gl -dxlevel 70" then start the game and tell me if something has changed.

---

### Post by g_monkey on 2007-04-06
> **frodon said:**
> Ok, I guess you didn't added GLSL shader support so it shouldn'd be the problem.

While steam opened right click on CS:S and choose property then click on launch option or something like that then add these options "-gl -dxlevel 70" then start the game and tell me if something has changed.

genius:KS  this has done it i can run the game get 94fps in stress test too

one more problem i seem to have no sound this is what i have set in winecfg

[_[COLOR="Red"]audio settings[/COLOR]_]("http://i146.photobucket.com/albums/r264/g_monkey001/Screenshot-4-1.png")

any suggestions?

---

### Post by frodon on 2007-04-06
Your sound setting is good, but because CS:S will use OSS driver and that OSS allows only one apps to use the sound device you will need to close the apps using the sound card before playing (e.g. your music player).
If you don't find the apps which use the sound device this command will tell you :
```
lsof /dev/dsp
```

About the command i asked you to pass in the steam interface :
-gl : tells to send the graphic infos to opengl before the display
-dxlevel : set the directx level used. For example -dxlevel 70 tells to run the game with dirextx 7.0.

If you wish better rendering you can try -dxlevel 80 and even -dxlevel 90, you may have better performances with -dxlevel 70 however (i use -dxlevel 80 in my case).

---

### Post by g_monkey on 2007-04-06
> **frodon said:**
> Your sound setting is good, but because CS:S will use OSS driver and that OSS allows only one apps to use the sound device you will need to close the apps using the sound card before playing (e.g. your music player).
If you don't find the apps which use the sound device this command will tell you :
```
lsof /dev/dsp
```

About the command i asked you to pass in the steam interface :
-gl : tells to send the graphic infos to opengl before the display
-dxlevel : set the directx level used. For example -dxlevel 70 tells to run the game with dirextx 7.0.

If you wish better rendering you can try -dxlevel 80 and even -dxlevel 90, you may have better performances with -dxlevel 70 however (i use -dxlevel 80 in my case).

i tried the code to see what device was using audio and it showed nothing?

by the way cheers for all the help appreciate it

---

### Post by frodon on 2007-04-06
If it shows nothing then your sound device is free an it is ok to launch the game with sound. If you still have  problems remove the driver emulation in your winecfg audio setting.

Hope you will be good at counter strike and make many head shots now ;)

---

