---
title: "Quake III 3ever. Install with"
date: 2010-10-17
forum: Gaming &amp; Leisure
---

### Post by getphuture on 2010-10-17
I tried to install the quake3 demo on my ubuntu 10.04 but got some troubles. I didn't find the appropriate answers on the forums for my case so here how I did. It should work for everyone and cover most of the cases. The issue is that the script is a little bit older, so you have to take care while installing and running to get everything fine.

I cover the official Quake 3 Demo first and then the official release but you should consider buying the game, really !

**About SDL output solution, please scroll to the bottom**

**Quake 3 DEMO**

[LIST=1]
[*]Download the linux version from the [Id Software]("http://www.idsoftware.com/games/quake/quake3-arena/index.php?game_section=demo").
[*]Running the installer as super-user gave more troubles. The best way I found is to create a temporary directory with full permission. Open a terminal and type for example
```
mkdir ~/tmp
chmod 777 ~/tmp
```
Don't forget to delete it after you finished installing quake
[*]First issue: the script is probably using an older syntax for the "tail" command. So you have to set the compatibility mode like this:```
export _POSIX2_VERSION=199209
```
[*]Then Extract the files like this:
```
./linuxq3ademo-1.11-6.x86.gz.sh -target ~/tmp/quake3
```
No need to sudo as I kind of explained. If it worked, you should read at the end:
> (...)
Error: no such file "Uncompressing Quake III Arena Demo"
./setup.sh: 9: function: not found
x86
The installer has exited normally - removing temporary files...
Press Return to close this window ...

[*]No the installation was not completed ( the x86 error ). Files were extracted but the wizard didn't run.
So go the repository
```
cd ~/tmp/quake3
```
Make two scripts writable:
```
chmod u+w ./setup.sh ./setup.data/postinstall.sh
```
Replace #!/usr/bin/sh by #!/usr/bin/bash. Yeap, was just a shell dispute.
And run as super-user the setup script to install the game ```
sudo ./setup.sh
```
[/LIST]

Issue with video
q3demo is calling by default /etc/ld.conf to retrieve the location of libGL.so. On most recent distros, it's a little bit different. The fallback is looking to the current repository. To resume, as you read on the forums, you have to use that and create a symlink to libGL.so from where you start the game. For example
```
cd ~/bin/quake3
ln -s /usr/lib/mesa/libGL.so.1.2 ./libGL.so
```
Then you can start the game by
```
cd ~/bin/quake3
./q3demo
```

Issue with audio
With recent ubuntu / debian distros, it's possible but a pain to get the audio working.
If you are not using the latest version of ubuntu, and arts is available, the easiest way is:
```
artsdsp -m quake3
```
The best unpainfully way is to use the SDL output, but the faster is about the official release only, not the demo.So instead of spending hours to make the demo working, please buy the game and install the release version :-) And you remember the old days ? Some servers started to check for the key and in less than a few weeks the Europe was kind of "out of stock" for quake 3 lol



**Quake 3 Release**

[LIST=1]
[*]Download the released 1.32 from the [ID Software website](http://www.idsoftware.com/games/quake/quake3-arena/index.php?game_section=updates)
[*]Again ```
export _POSIX2_VERSION=199209
```
[*]Then ./linuxq3apoint-1.32.x86.run and this time it's a graphical wizard. Yeah that was sick at this time !
[*]Remember to copy the PAK0.PK3 from your CD to baseq3 or the game won't work
[*]Then download the 1.32c update from [quakeworld](http://www.quake3world.com/forum/viewtopic.php?f=19&t=21699) Decompress and copy-paste the linux files to quake (Overriding)
[/LIST]

Video Issue
None to my mind, at least with the default mesa gl driver.

Audio issue: switch to SDL output
Everything with oss (even quake3) is greatly explained here:
[Configuring Applications for OSSv4](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4)
[LIST=1]
[*]First install the sdl-oss bridge:
```
sudo apt-get install libsdl1.2debian-oss
```
It will remove the sdl-pulseaudio and a ubuntu-desktop package but you won't die. If you already use an other, like sdl-alsa or ... well have to choose one for all of your games.
[*]Now a script is available. You can get it by pasting in terminal:
```
cd ~/bin
wget -q -O - http://nullkey.ath.cx/~stuff/et-sdl-sound/quake3-sdl-sound.gz | gzip -d > quake3-sdl-sound && chmod a+x quake3-sdl-sound
```
Edit quake3-sdl-sound and set the GAME_PATH and SDL_AUDIODRIVER environment variable.
For example
GAME_PATH="/home/user/quake3" ( Remove the # and specify the path to quake 3 repository )
SDL_AUDIODRIVER="dsp" ( Remove the # and specify dsp as the driver )
[/LIST]

That's all ! You can run ./quake-sdl-sound and enjoy the full version of Quake 3.

Hope it will work for you !

---

### Post by jcer93705 on 2010-10-22
> **getphuture said:**
> I tried to install the quake3 demo on my ubuntu 10.04 but got some troubles. I didn't find the appropriate answers on the forums for my case so here how I did. It should work for everyone and cover most of the cases. The issue is that the script is a little bit older, so you have to take care while installing and running to get everything fine.

I cover the official Quake 3 Demo first and then the official release but you should consider buying the game, really !

**About SDL output solution, please scroll to the bottom**

**Quake 3 DEMO**

[LIST=1]
[*]Download the linux version from the [Id Software]("http://www.idsoftware.com/games/quake/quake3-arena/index.php?game_section=demo").
[*]Running the installer as super-user gave more troubles. The best way I found is to create a temporary directory with full permission. Open a terminal and type for example
```
mkdir ~/tmp
chmod 777 ~/tmp
```
Don't forget to delete it after you finished installing quake
[*]First issue: the script is probably using an older syntax for the "tail" command. So you have to set the compatibility mode like this:```
export _POSIX2_VERSION=199209
```
[*]Then Extract the files like this:
```
./linuxq3ademo-1.11-6.x86.gz.sh -target ~/tmp/quake3
```
No need to sudo as I kind of explained. If it worked, you should read at the end:

[*]No the installation was not completed ( the x86 error ). Files were extracted but the wizard didn't run.
So go the repository
```
cd ~/tmp/quake3
```
Make two scripts writable:
```
chmod u+w ./setup.sh ./setup.data/postinstall.sh
```
Replace #!/usr/bin/sh by #!/usr/bin/bash. Yeap, was just a shell dispute.
And run as super-user the setup script to install the game ```
sudo ./setup.sh
```
[/LIST]

Issue with video
q3demo is calling by default /etc/ld.conf to retrieve the location of libGL.so. On most recent distros, it's a little bit different. The fallback is looking to the current repository. To resume, as you read on the forums, you have to use that and create a symlink to libGL.so from where you start the game. For example
```
cd ~/bin/quake3
ln -s /usr/lib/mesa/libGL.so.1.2 ./libGL.so
```
Then you can start the game by
```
cd ~/bin/quake3
./q3demo
```

Issue with audio
With recent ubuntu / debian distros, it's possible but a pain to get the audio working.
If you are not using the latest version of ubuntu, and arts is available, the easiest way is:
```
artsdsp -m quake3
```
The best unpainfully way is to use the SDL output, but the faster is about the official release only, not the demo.So instead of spending hours to make the demo working, please buy the game and install the release version :-) And you remember the old days ? Some servers started to check for the key and in less than a few weeks the Europe was kind of "out of stock" for quake 3 lol



**Quake 3 Release**

[LIST=1]
[*]Download the released 1.32 from the [ID Software website](http://www.idsoftware.com/games/quake/quake3-arena/index.php?game_section=updates)
[*]Again ```
export _POSIX2_VERSION=199209
```
[*]Then ./linuxq3apoint-1.32.x86.run and this time it's a graphical wizard. Yeah that was sick at this time !
[*]Remember to copy the PAK0.PK3 from your CD to baseq3 or the game won't work
[*]Then download the 1.32c update from [quakeworld](http://www.quake3world.com/forum/viewtopic.php?f=19&t=21699) Decompress and copy-paste the linux files to quake (Overriding)
[/LIST]

Video Issue
None to my mind, at least with the default mesa gl driver.

Audio issue: switch to SDL output
Everything with oss (even quake3) is greatly explained here:
[Configuring Applications for OSSv4](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4)
[LIST=1]
[*]First install the sdl-oss bridge:
```
sudo apt-get install libsdl1.2debian-oss
```
It will remove the sdl-pulseaudio and a ubuntu-desktop package but you won't die. If you already use an other, like sdl-alsa or ... well have to choose one for all of your games.
[*]Now a script is available. You can get it by pasting in terminal:
```
cd ~/bin
wget -q -O - http://nullkey.ath.cx/~stuff/et-sdl-sound/quake3-sdl-sound.gz | gzip -d > quake3-sdl-sound && chmod a+x quake3-sdl-sound
```
Edit quake3-sdl-sound and set the GAME_PATH and SDL_AUDIODRIVER environment variable.
For example
GAME_PATH="/home/user/quake3" ( Remove the # and specify the path to quake 3 repository )
SDL_AUDIODRIVER="dsp" ( Remove the # and specify dsp as the driver )
[/LIST]

That's all ! You can run ./quake-sdl-sound and enjoy the full version of Quake 3.

Hope it will work for you !

Sorry i don't get you how to do 
*]Now a script is available. You can get it by pasting in terminal:
```
cd ~/bin
wget -q -O - http://nullkey.ath.cx/~stuff/et-sdl-sound/quake3-sdl-sound.gz | gzip -d > quake3-sdl-sound && chmod a+x quake3-sdl-sound
```
Edit quake3-sdl-sound and set the GAME_PATH and SDL_AUDIODRIVER environment variable.
For example
GAME_PATH="/home/user/quake3" ( Remove the # and specify the path to quake 3 repository )
SDL_AUDIODRIVER="dsp" ( Remove the # and specify dsp as the driver )
[/LIST]

and cd bin wont work too. Can you help me but make things easier for me. Thanks.

---

### Post by getphuture on 2010-10-23
Of course :)
Let's explain in a easier way: this step is a to create a launcher script for quake3 to use sdl as the output for the sound.

The command ```
cd ~/bin
``` is just a shortcut to /home/user/bin. Actually you can use the repository you want. This repository is nice for using your own binary. Just select the location you want.

The second command ```
wget -q -O - http://nullkey.ath.cx/~stuff/et-sdl-sound/quake3-sdl-sound.gz | gzip -d > quake3-sdl-sound && chmod a+x quake3-sdl-sound
``` will actually:
[LIST=1]
[*]Download the script quake3-sdl-sound.gz
[*]Extract it as quake3-sdl-sound
[*]And make it executable
[/LIST]

If you're not familiar with the terminal, you can just do it manually by
[LIST=1]
[*][Download it]("http://nullkey.ath.cx/~stuff/et-sdl-sound/quake3-sdl-sound.gz") with your browser
[*]Then with nautilus do a right click on "quake3-sdl-sound.gz" and select "Extract Here". The script will be extracted as quake3-sdl-sound.
[*]Then do a right click on the file "quake3-sdl-sound", select "Properties". It will display a dialog panel. Go to the tab "Permissions" and check the checkbox "Allow file executing as program
[/LIST]

Now you are able to run the script. But you need to change some settings.
So open quake3-sdl-sound with your favorite editor ( geany or kate or kwrite or gedit ... )

First search for the keyword GAME_PATH. You should get a line which looks like this: ```
# GAME_PATH=""
```. You should change it to ```
GAME_PATH="/home/user/quake3"
```. Removing the # character (it means comment ) and replace /home/user/quake3 by your own location, where you installed quake3.

Then search for the keyword SDL_AUDIODRIVER. You should read something like:
```
# SDL_AUDIODRIVER=""
``` You should change it to ```
SDL_AUDIODRIVER="dsp"
```

The end. You can double-click on quake3-sdl-sound and select "Run in Terminal". If everything's fine quake3 should be launched and you should hear the sounds.

Keep in touch 8-)

---

### Post by jcer93705 on 2010-10-24
> **getphuture said:**
> Of course :)
Let's explain in a easier way: this step is a to create a launcher script for quake3 to use sdl as the output for the sound.

The command ```
cd ~/bin
``` is just a shortcut to /home/user/bin. Actually you can use the repository you want. This repository is nice for using your own binary. Just select the location you want.

The second command ```
wget -q -O - http://nullkey.ath.cx/~stuff/et-sdl-sound/quake3-sdl-sound.gz | gzip -d > quake3-sdl-sound && chmod a+x quake3-sdl-sound
``` will actually:
[LIST=1]
[*]Download the script quake3-sdl-sound.gz
[*]Extract it as quake3-sdl-sound
[*]And make it executable
[/LIST]

If you're not familiar with the terminal, you can just do it manually by
[LIST=1]
[*][Download it]("http://nullkey.ath.cx/~stuff/et-sdl-sound/quake3-sdl-sound.gz") with your browser
[*]Then with nautilus do a right click on "quake3-sdl-sound.gz" and select "Extract Here". The script will be extracted as quake3-sdl-sound.
[*]Then do a right click on the file "quake3-sdl-sound", select "Properties". It will display a dialog panel. Go to the tab "Permissions" and check the checkbox "Allow file executing as program
[/LIST]

Now you are able to run the script. But you need to change some settings.
So open quake3-sdl-sound with your favorite editor ( geany or kate or kwrite or gedit ... )

First search for the keyword GAME_PATH. You should get a line which looks like this: ```
# GAME_PATH=""
```. You should change it to ```
GAME_PATH="/home/user/quake3"
```. Removing the # character (it means comment ) and replace /home/user/quake3 by your own location, where you installed quake3.

Then search for the keyword SDL_AUDIODRIVER. You should read something like:
```
# SDL_AUDIODRIVER=""
``` You should change it to ```
SDL_AUDIODRIVER="dsp"
```

The end. You can double-click on quake3-sdl-sound and select "Run in Terminal". If everything's fine quake3 should be launched and you should hear the sounds.

Keep in touch 8-)

Nope didn't work out. 

------- sound initialization -------
/dev/dsp: No such file or directory
Could not open /dev/dsp

I did everything what you told me

# You can set this in GAME_PATH environment variable
 GAME_PATH="/home/jaime/quake3"

# SDL audio driver
SDL_AUDIODRIVER="dsp"

Also selected so it could execute it. Then i did 

jaime@jaime-Satellite-L505D:~$ sudo '/home/jaime/quake3/quake3-sdl-sound' 

I also did '/home/jaime/quake3/quake3-sdl-sound' 
also clicked on the file and executed from there. Nope isn't working out. :( Am i doing something wrong?

---

### Post by getphuture on 2010-10-24
Ok jcer93705. So it seems your sound configuration is not the default I expected. So could you give me the ouput of ```
ls -l /dev
``` and more about your current settings ( Ubuntu 10.04, pulse audio, etc... ? )

First if you read /dev/dspXX where XX is a number, you should try it first ;) If you installed successfully libsdl1.2debian-oss, we should only find where to redirect the sound output.

Second /dev/dsp seems to be not available and i don't know the reasons. So if you don't use pulseaudio for example, you may have to install an additional package like alsa-oss ( or the adequate [wrapper]-oss )

Third, check your default mixer too, like output or pcm or etc... are not "mute".

I still keep in touch. Hope I can get it work for you.

Cheers

PS: no you didn't do anything wrong

---

### Post by getphuture on 2010-10-24
I forgot to tell you: my current audio settings are using at least the following packages:
```
alsa-base alsa-utils libesd-alsa0 linux-sound-base libsdl1.2debian-oss libasound2-plugins libpt2.6.5-plugins pulseaudio pulseaudio-plugins
```

As the default ouput sound for quake3 is not available or busy, instead of hacking or changing manually the sound settings, with the script we redirect the expected oss output to sdl. But with your current error, it means the expected oss output doesn't even exist.

I don't know your level but there is an interesting post here about what is Pulse Audio and sound in linux:
[http://www.linux.com/news/hardware/drivers/8100-why-you-should-care-about-pulseaudio-and-how-to-start-doing-it]("http://www.linux.com/news/hardware/drivers/8100-why-you-should-care-about-pulseaudio-and-how-to-start-doing-it")

To resume Pulseaudio is a kind of "sound router". So often alsa is configured to be used with Pulseaudio. Everything's fine.

About oss we often install a kind of bridge - router - wrapper so everything can communicate each other without conflicts. So instead of installing the full oss libraries or lots of sounds server with a complicated pulseaudio settings, we only install the adequate wrapper.

So in the upper level Pulseaudio is a kind of switch between two or three libraries, in the lower level the sound is just bumping to one of those main libraries. It's an image.

So for gaming you should not start editing your sound settings or add processes as I read on the forums, but just playing and adding bridges. That's simple and nice like quake3 when you can't modify the games.

We have just to find the libraries you're missing, and then that's OK.
That will be really useful for other games or softwares in your near future too !

Regards

---

### Post by Sanek on 2010-10-24
Good howto, only one exception for my configuration,

# SDL audio driver
SDL_AUDIODRIVER="alsa"

did the trick :guitar:

I'm running 10.04 64bit and I have all the packages you've listed, except pulseaudio-plugins.

---

