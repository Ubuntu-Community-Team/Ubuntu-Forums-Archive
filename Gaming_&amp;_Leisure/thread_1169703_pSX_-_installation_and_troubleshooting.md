---
title: "pSX - installation and troubleshooting"
date: 2009-05-25
forum: Gaming &amp; Leisure
---

### Post by sp0tz on 2009-05-25
[SIZE=5]Installing pSX:[/SIZE]
There's a little info around about installing this, but some of it's outdated, and there are a couple (easily fixable) problems they don't mention, so I figured I'd consolidate what I know and put it out here.

     pSX is an emulator that allows you run original playstation games from your PC. It's pretty customizable and appears to have a high compatibility rate, as well as a fairly straightforward install process. The biggest drawback is that it's named pSX, which is also a nickname for the console, so it's nigh impossible to find information on it. Anyways, let's get started.

     pSX has a few dependencies, so let's install them. Open a terminal and enter this:
sudo apt-get install libgtkglext1 libgtkglext1-dev

     pSX is free to use, so let's grab he binaries.
wget [http://psxemulator.gazaxian.com/pSX_linux_1_13.tar.bz2](http://psxemulator.gazaxian.com/pSX_linux_1_13.tar.bz2)
tar xvf pSX_linux_1_13.tar.bz2
(protip: just type tar xvf pSX and then hit the tab key.)

     The resulting folder will have pSX in it, and can be moved anywhere you like. Feel free to remove the pSX_linux_1_13.tar.bz2 file, as it's not useful anymore.

     Now that you've got pSX, you'll need a bios file and a game to run. The bios file will be named scph1001.bin (There are legal issues about that file, so I can't just hand mine out. Go find it.) Find the bios file, then put it in the pSX/bios folder. Now all you need is a game. Again, copyright issues, blah blah blah. You might try using AcetoneISO to rip your disks, but they're encrypted, so I never bothered. Go find some games. And put them somewhere not to far from the pSX folder. Also: I haven't found a disk image format that doesn't work with pSX, but I know for a fact that .bin/cue files work fine, as do the .ccd/img files.

     Whew. Now everything's set up and (maybe) ready to go. In a terminal, navigate to the pSX directory and execute
./pSX
A new window should open up and act just like a playstation. If it doesn't, please skip ahead to the troubleshooting section. If it does, click file, then load CD image. Navigate to the cd image of your game and double click it. The game should load and all should be well. Press alt+enter for fullscreen. Have fun!

---

### Post by sp0tz on 2009-05-25
[SIZE="5"]Troubleshooting:[/SIZE]
pSX is not without problems. It's worth getting through them, though, as it runs better than any other playstation emulator I've used.


**So, I try to run pSX, but it crashes. What's the deal?**
     Check the terminal output. If the words "segmentation fault" appear, then there are a couple of options. First, before you run pSX, run 
```
killall pulseaudio
```
pSX and pulseautio don't play nice sometimes, which is a shame.

     If it still segfaults (crashes with the terminal output segmentation fault), try this: run it as root, as per [this thread]("http://ubuntuforums.org/showthread.php?t=1146830")
```
sudo ./pSX
```
If that runs well, click file, then configuration. get over to the sound tab. If the dropdown box next to the word Device says "default", then change it to something else, then click apply, then click OK. If there's no sound anymore, get back in there and change the dropdown box again until it's /not/ set to default, but there /is/ sound.

     There's a config file that we can edit so you don't have to run the emulator as root, though. First, lets check what pSX is using as the sound device when run as a regular user. run this from the terminal:
```
grep Device= ~/.pSX/psx.ini
```
the output should be the phrase "Device=", which may or may not be followed be some gibberish. If it's followed by some gibberish, like this:
Device=7c2c7ba0
Then running as root may have solved the problem. Try running ./pSX without sudo. If that didn't work, see if running the emulator as root set up a config file for root:
```
grep Device= /root/.pSX/psx.ini
```
If the earlier command just had Device=, but this one had some gibberish after it, copy that gibberish, then run this command
gedit ~/.pSX/psx.ini
then locate "Device=" and paste the gibberish there. That should fix it all up.

After I did all this stuff, I still had trouble getting pSX to run until I started including running it like this:
```
/home/tails/emulation/pSX/pSX /home/tails/emulation/psx_disks/symphony_of_the_night/symphony_of_the_night.bin

```
In simpler terms, like this:
```
path/to/pSX /path/to/cdimage
```
I know, that's kind of sloppy, and no one wants to run programs from the terminal every time, but I've managed to turn it into something clean and sexy. Check a little further down on setting up sexy icons and lanuchers.



references:
note: a couple of these are instructions on getting pSX installed on an AMD64 system. They're pretty solid, but a little old.

[http://ubuntuforums.org/showthread.php?t=1146830](http://ubuntuforums.org/showthread.php?t=1146830)
[http://ubuntuforums.org/showthread.php?t=394097](http://ubuntuforums.org/showthread.php?t=394097)
[http://www.ubuntugeek.com/install-psx-emulator-on-ubuntu-amd64.html](http://www.ubuntugeek.com/install-psx-emulator-on-ubuntu-amd64.html)
[http://psxemulator.gazaxian.com/](http://psxemulator.gazaxian.com/)

---

### Post by sp0tz on 2009-05-25
[size=5]Making pSX Sexy:[/size]
Now, pSX should be up and running, if a bit sloppy. [Check this out, though]("http://img21.imageshack.us/img21/166/screenshotpfo.png").
Nice, no? It's pretty easy to set up.

1. create a folder and some launchers:
     Open the pSX folder and make a folder in it. Call it whatever you like, though you can't go wrong with a name like launchers. Now right click an open spot on a panel and click add to panel. In the window that pops up, choose custom application launcher. For type, set to location. Then click browse and browse to the folder you just made.
     Now, right click somewhere on the desktop and select create launcher. This time, set Type to application. For the command, use the path to the pSX binary (~/pSX/pSX for example) and the path to the disk image (~/pSX/cdimages/symphony_of_the_night.bin for example) seperated by a space. So:
```
~/pSX/pSX ~/pSX/cdimate/symphony_of_the_night.bin
```
could be one of them. Make as many as you have disks and you're just about done.

2.  Give the launchers new icons. 
     I've attached the icon I use. If you'd like to use it, make this folder:
/usr/share/icons/custom/
Then grab the attached icon and drop it in there. If you right click on a launcher and open it's properties, you can click on the icon to change it. Browse to the folder you just created, select the icon and click open. Now the pSX emulator should be up and running, and pretty sexy to boot.




I could use some feedback on this, so feel free to post whatever you'd like.

---

### Post by Mr. Bane on 2009-05-28
Edit: Ah hell, it works! :D

---

### Post by hikaricore on 2009-05-29
I just can't get the damn thing to run no matter what I do.
It never fills in the Device line ever so I can't copy it.  >.>
If there were just a way to disable sound I'd just do that for the time being.

I've been trying to find an alternate to epsxe since updating to Jaunty as it has a few strange issues that I can't resolve.
Pcsx is out of the question as it has a rendering issue that causes floor textures to be white regardless of plugin used.

---

### Post by BoyOfDestiny on 2009-05-29
> **hikaricore said:**
> ...
Pcsx is out of the question as it has a rendering issue that causes floor textures to be white regardless of plugin used.

I don't want to derail the thread, but did you try the latest version of pcsx-df?
[http://pcsx-df.sourceforge.net/](http://pcsx-df.sourceforge.net/)
I posted a 32-bit deb here
[http://ubuntuforums.org/showpost.php?p=7346240&postcount=8](http://ubuntuforums.org/showpost.php?p=7346240&postcount=8)

---

### Post by hikaricore on 2009-05-29
Yups that's the one I'm using.
It's just bizare.. I've tried every single video plugin including software rendering and the floor is still pure white.
Can't for the life of me figure it out as epsxe doesn't do this even with the same plugins.

---

### Post by sp0tz on 2009-05-29
Wait, it won't run even when you run it with sudo? Did you run 
sudo killall pulseaudio
first? Can you copy n paste the terminal output?

If it can run with sudo, but never populates the config file with the new Device=
line, you might try running pSX as root once or twice to see if it edits the config file then. Ubuntu doesn't activate the root account by default, so you'd have to run
sudo passwd root
and give it a password before logging in as root. If you'd like to do that, after you've set up a root account, run 
su
from the terminal, then enter the password you just made for root. Run pSX a few times, change the device through the gui, click apply, etc. Then exit pSX and type in 
exit
as root to get back to a regular terminal.


Was that helpful?

---

### Post by hikaricore on 2009-05-30
I appreciate the advice and I'll keep trying, but I'm quite familiar with troubleshooting steps.  ^_^  I've been here a long long time.
With or without pulse running and reguardless of root pSX will not run.  It crashes with a seg fault EVERY single time no matter what.

I always add a root account to my systems so that's not an issue.
I even logged into my root account and ran an Xsession to test pSX to no avail.

Sorry but I don't think you're going to be able to help in this case.
I'll just need to wait til pSX resolves it's sound issues.

---

### Post by sp0tz on 2009-05-30
That's cool. I may be a software QA tester by trade, but I don't take my job very seriously. ;)


edit: that may have sounded snarky, but I meant it in a lighthearted manner.

---

### Post by sp0tz on 2009-05-30
Addressed to no one in particular:

My install spits this out when I simply run ./pSX from the terminal:

[src/linux/sound.cpp, line 582]: 'snd_pcm_open(&pcm_handle,dev->info->device_fname,SND_PCM_STREAM_PLAYBACK,0)' returned 'Device or resource busy'
pSX: pcm_params.c:2259: snd_pcm_hw_refine: Assertion `pcm && params' failed.
Aborted


But the 
tails@tornado:~$ /path/to/pSX /path/to/game
method works just fine. Not sure what that's all about, but that's why I made the launchers.

---

### Post by tommah04 on 2009-06-09
hey all

I'd really like to get this started, but this is confusing me

tom@tom-desktop:~/pSX$ ./pSX
./pSX: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory


sorry, a lil new and don't know much yet

---

### Post by hikaricore on 2009-06-09
> **tommah04 said:**
> hey all

I'd really like to get this started, but this is confusing me

tom@tom-desktop:~/pSX$ ./pSX
./pSX: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory


sorry, a lil new and don't know much yet

Try:

> sudo apt-get install libgtkglext1

I'm not sure what other dependencies there are but I'd imagine they're mentioned in the documentation or on their forum.

---

### Post by tommah04 on 2009-06-10
that didn't seem to work.  getting same error message

---

### Post by hikaricore on 2009-06-10
**> I'm not sure what other dependencies there are but I'd imagine they're mentioned in the documentation or on their forum.**


^

---

### Post by Ferrat on 2009-06-10
Sounds really odd, going to find the guide I used, I got pSX working under 9.04 without any problems, runs flawless on my netbook

EDIT:
Found it 
[http://maketecheasier.com/guide-to-playstation-emulator-on-ubuntu/2008/03/19](http://maketecheasier.com/guide-to-playstation-emulator-on-ubuntu/2008/03/19)

Just followed that and had to allow frameskipping to avoid sound lag.

Screenshot of pSX running on my Netbook =)

---

### Post by Tested on 2009-06-10
I followed the directions step by step, but when i go to run the emulator, it asks for the language, i pick english, and then it says it cant find the bios file and it needs to be installed in the bios folder. However, i already have one in their. Help? I'm running Ubuntu 9.04

---

### Post by Ferrat on 2009-06-10
is it scph1001.bin? 
pSX looks for a file called that as by default, it should start up otherwise so you can enter options and change the name to look for

---

### Post by Tested on 2009-06-10
Yeah thats the one I'm using, I've read reviews saying thats the one which works best, so now, even though its in the bios folder, it still can't find it, and I wonder why. I'd open it through the terminal, but I don't know the commands =/

---

### Post by Ferrat on 2009-06-11
> **Tested said:**
> Yeah thats the one I'm using, I've read reviews saying thats the one which works best, so now, even though its in the bios folder, it still can't find it, and I wonder why. I'd open it through the terminal, but I don't know the commands =/

open a terminal 
do```

cd .pSX
```
then 
```
gedit psx.ini
```

There you should see this
```
[BIOS]
PS1=bios/scph1001.bin
PS2=bios/scph39001.bin
```

Make sure PS1 says exactly like above, save if you changed it and then try again.

---

### Post by Tested on 2009-06-12
Thanks for the help with the commands, and it does say exactly like you have shown me. So what else could be the issue of that file is correct?

---

### Post by sp0tz on 2009-06-21
It's case sensitive. I had to rename my bios file to match what pSX expected it to be named. If that doesn't work, you might try to get another copy of the bios file from a different source.

---

### Post by jordan80562 on 2009-06-21
[SIZE=4]i need help with my memory im playin ff9 and i have both epsxe 1.5.2 and 1.60 and 1.5.2 is farther than the other but one day i system recovery my computer (because it was running too slow) and all the file on the 1.5.2 memory card is erased but the one on the 1.60 one is still there i know this someone else post but i need help with this how do i get the file to the 1.5.2 epsxe back..[/SIZE]
:mad:

---

### Post by Psyphre on 2009-06-24
> **tommah04 said:**
> hey all

I'd really like to get this started, but this is confusing me

tom@tom-desktop:~/pSX$ ./pSX
./pSX: error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory


sorry, a lil new and don't know much yet

> **hikaricore said:**
> Try:



I'm not sure what other dependencies there are but I'd imagine they're mentioned in the documentation or on their forum.

> **tommah04 said:**
> that didn't seem to work.  getting same error message

> **hikaricore said:**
> ****


^

I'm also getting this error. I have quadruple checked to make sure its installed and it is. Yet it STILL comes up with

```
error while loading shared libraries: libgtkglext-x11-1.0.so.0: cannot open shared object file: No such file or directory
```

Have checked their forums and documentation and I have everything as far as I'm aware. Even if I havent the error specifically states libgtkglext-x11 which I have installed. Even tried using sudo as suggested on another forum. Still nothing.

---

### Post by Saghaulor on 2009-10-09
I'm having the same issue. Also, the file is there.

See my post in this thread for confirmation.

[http://ubuntuforums.org/showpost.php?p=8028623&postcount=20]("http://ubuntuforums.org/showpost.php?p=8028623&postcount=20")

So the file is there, but it doesn't see it. How do I make it see it?

---

