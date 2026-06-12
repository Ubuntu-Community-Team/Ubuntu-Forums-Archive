---
title: "Kubuntu gets really messed up after dist-upgrade"
date: 2005-10-29
forum: Desktop Environments
---

### Post by tmmuk on 2005-10-29
you can follow whats happened in this thread: [http://ubuntuforums.org/showthread.php?t=82156](http://ubuntuforums.org/showthread.php?t=82156) (about halfway down it starts)

I think that X got screwed up or something. For now im stuck in a terminal :(

any help would be much appreciated

---

### Post by greatshape on 2005-10-29
[QUOTE=tmmuk]you can follow whats happened in this thread: [http://ubuntuforums.org/showthread.php?t=82156](http://ubuntuforums.org/showthread.php?t=82156) (about halfway down it starts)

I think that X got screwed up or something. For now im stuck in a terminal :(

any help would be much appreciated[/QUOTE]
Hi :-) 
Just to be sure, can you post the output of your sources.list here?
```
 cat /etc/apt/sources.list
```

---

### Post by GeneralZod on 2005-10-29
Please post your graphics card model, xorg.conf and xorg.log.  I'm not sure how to post the latter two from a text-mode browser, though :/ Do you have a live CD that can give you a GUI and internet access?

---

### Post by tmmuk on 2005-10-29
do you want me to type it all out? ok here goes:

```

## Uncomment the following two lines to fetch updated software from the network
deb http://gb.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the ' universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive and review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu breezy universe
deb-src http://gb.archive.ubuntu.com/ubuntu breezy universe

deb http://wine.sourceforge.net/apt binary/
deb-src http://wine.sourceforge.net/apt source/

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

```

---

### Post by tmmuk on 2005-10-29
[QUOTE=GeneralZod]Please post your graphics card model, xorg.conf and xorg.log.  I'm not sure how to post the latter two from a text-mode browser, though :/ Do you have a live CD that can give you a GUI and internet access?[/QUOTE]

I would have been able to provide the first request answer a minute ago, but since doing what greatshape said in the other thread (see top of this one for link) I cant find that out anymore.

EDIT: if you tell me where xorg.conf and xorg.log are, (directory) then I might be able to display them with:
cat /path/to/files/xorg.conf 
or
cat /path/to/files/xorg.log

just said that because it worked for displaying sources.list

EDIT2: I managed to output xorg.conf using:
```
cat /etc/X11/xorg.conf
```
but when I tried the same method but with xorg.log it said "no such file or directory"

also, I can only see the bottom part of my xorg.conf file, as it is huge and I dont know how to scroll up the page (view terminal history aka rest of xorg.conf). Anyway, the xorg.conf file is way to long for me to type it all out :(.

---

### Post by tmmuk on 2005-10-29
You might want to check the other thread as well as I have replied in it.

---

### Post by beefsprocket on 2005-10-29
Try ```
cat /var/log/Xorg.0.log |less
``` That should get the information on your card, config, and error message(s). You can use the pipe | with commands (less, more, grep etc.) to allow scrolling, grepping etc.

---

### Post by tmmuk on 2005-10-29
[QUOTE=beefsprocket]Try ```
cat /var/log/Xorg.0.log |less
``` That should get the information on your card, config, and error message(s). You can use the pipe | with commands (less, more, grep etc.) to allow scrolling, grepping etc.[/QUOTE]

ok I did that command. what do you want to know from this log? and how to I quit It and get back to the terminal? also how do I scroll in a terminal?

---

### Post by tmmuk on 2005-10-29
Just to say:
I dont know why any of this should be happening anyway, as I've never had a problem with this xorg stuff before.

---

### Post by tmmuk on 2005-10-29
Is there a way to just get back my old version of hoary? Or is there a way to install Breezy of a CD from scratch, overwriting the current mess but keeping all my files?

---

### Post by beefsprocket on 2005-10-29
From scratch works if you delete everything but your home directory (or back it up). I've done this many a time. Backing up to a separate disc (hdd, cd, dvd etc.) is best but you can just remove all the files on your drive *except* the home directory and reinstall. 

I tend to reinstall using a different user so as to not overwrite or mess up any files in my current home dir. I then paste all files from the backup and chown the whole thing to my new user. Alternatively, you can just create your user again with the useradd command: [(see this post for proper groups etc.)]("http://ubuntuforums.org/showpost.php?p=351313&postcount=2") and then paste all the files back into the directory.

To quit from less, use q. When scrolling through the Xorg log, what errors do you see and what is your hardware (I think someone asked previously which is why I mentioned it).

You could also try apt-get remove "package-name" --purge
To figure out which packages, have a look in the /var/cache/apt/archives directory. Use ls |less if you want to scroll through the output. Look for all the X packages and use apt-get remove --purge on each. Names might be off making this difficult. As such:

One other thing to try is dpkg-reconfigure --all. Try purging your xorg packages first.

---

### Post by greatshape on 2005-10-30
[QUOTE=tmmuk]ok I did that command. what do you want to know from this log? and how to I quit It and get back to the terminal? also how do I scroll in a terminal?[/QUOTE]
```

cat /var/log/Xorg.0.log |more      (or less like suggested b4)

```
lets you scroll down the page by pressing the enter button
You can get back to the terminal by pressing "q" 
You talk about re-installing, do you have a cd-writer or external HD to backup your files? If so, run a bootable linux cd like knoppix or so and write your files to a cd by k3b or copy them to your external HD. You could also write your files to a different partition, but as i notice from your posts you are not familiar with linux at all (no offense!), so maybe a cd or ext. HD is safer. (i don't want you to delete that partition when you re-install kubuntu :) )

Regards, Steve

---

### Post by tmmuk on 2005-10-30
Ok, I think a clean install might be the easiest option for me. I have a dvd-burner and a 40gb external HDD so I should be fine. It's a bit annoying that I will lose all application data (settings, game saves etc) but I guess ill have to give them up to get a working computer. (I dont really understand that --purge stuff above)

It seems that I no longer have Xorg, I think it got deleted when I did some of the things in the other thread.

If I am going to start from scratch, what is the best way to do it? should I back up my home dir and then format the whole hdd? And then install breezy off a CD? If so, how would I go about doing this? (how to format drive etc). I wasnt too sure about that adduser thing and moving users, but will it work anyway if I'm starting from scratch?

Do you have any Idea why this might have happened anyway? I dont remember messing with X before... and my previous version of Hoary worked fine. Maybe it has something to do with the errors I got about language. they were something like: "en_gb:gb not supported/not found or something, reverting to normal en C compiler or something", I cant fully remember.

thanks for all your help so far

---

### Post by tmmuk on 2005-10-30
[QUOTE=beefsprocket]From scratch works if you delete everything but your home directory (or back it up). I've done this many a time. Backing up to a separate disc (hdd, cd, dvd etc.) is best but you can just remove all the files on your drive *except* the home directory and reinstall. 

I tend to reinstall using a different user so as to not overwrite or mess up any files in my current home dir. I then paste all files from the backup and chown the whole thing to my new user. Alternatively, you can just create your user again with the useradd command: [(see this post for proper groups etc.)]("http://ubuntuforums.org/showpost.php?p=351313&postcount=2") and then paste all the files back into the directory.

To quit from less, use q. When scrolling through the Xorg log, what errors do you see and what is your hardware (I think someone asked previously which is why I mentioned it).

You could also try apt-get remove "package-name" --purge
To figure out which packages, have a look in the /var/cache/apt/archives directory. Use ls |less if you want to scroll through the output. Look for all the X packages and use apt-get remove --purge on each. Names might be off making this difficult. As such:

One other thing to try is dpkg-reconfigure --all. Try purging your xorg packages first.[/QUOTE]

I did:
```
ls /var/cache/apt/archives |less
```
and it showed all the packages. I scrolled down to where x stuff starts. theres a lot there. do I need to remove all of the x packages? even things like xclock, xeyes, xcalc etc? There are also the pacakges like Xine, would they be a problem? (probably not seeing as they are for a media player)

I just want to know before I remove tons of stuff. Also, after I have removed them all, how is that going to help me get my X windowing system back? (if it was just removed) or does dpkg-reconfigure --al fix that?

---

### Post by greatshape on 2005-10-30
[QUOTE=tmmuk]Ok, I think a clean install might be the easiest option for me. I have a dvd-burner and a 40gb external HDD so I should be fine. It's a bit annoying that I will lose all application data (settings, game saves etc) but I guess ill have to give them up to get a working computer. (I dont really understand that --purge stuff above)

It seems that I no longer have Xorg, I think it got deleted when I did some of the things in the other thread.

If I am going to start from scratch, what is the best way to do it? should I back up my home dir and then format the whole hdd? And then install breezy off a CD? If so, how would I go about doing this? (how to format drive etc). I wasnt too sure about that adduser thing and moving users, but will it work anyway if I'm starting from scratch?

Do you have any Idea why this might have happened anyway? I dont remember messing with X before... and my previous version of Hoary worked fine. Maybe it has something to do with the errors I got about language. they were something like: "en_gb:gb not supported/not found or something, reverting to normal en C compiler or something", I cant fully remember.

thanks for all your help so far[/QUOTE]

The --purge stuff and so many other things you can learn from the man pages (typ man apt-get in a terminal). English is your native language, that's a big advantage!  Further i think you should read a good book on linux basics. There are many arround, for example try "Running linux from O'reilly" There even are electronic versions of that book arround on the net.

I doubt you have xorg deleted ;)  
  
If you're planning to do a fresh install, the best way depends on the setup of your system. Are you ONLY running linux on that system? or also windows?
Normally the installer will take care of your partitioning in both ways, just be carefull you don't remove your windows partition if there is one arround.
Just use the breezy install cd, follow the steps and you 'll do fine. 
About the settings you lose, don't worry, the installer will set most of the things right, and playing arround with your system to get things the way you like it is the best way to learn about your system. 

I don't know what went wrong with your system. Very hard to find out from here :-) 

Enjoy your learning!
Steve

---

### Post by tmmuk on 2005-10-30
[QUOTE=greatshape]Are you ONLY running linux on that system? or also windows?[/QUOTE]

Just Linux (own-built PC, no windows installed - linux was the first os put on it)

Ok I might try the --purge stuff and if that doesnt work, ill copy my home dir to an external hdd (using a live-cd?) and do a clean install.

So how would I go about wiping the entire hdd?

EDIT: before I do, would you like me to post any errors I find in xorg.conf and xorg.log?

EDIT2: I did that reconfigure stuff (above) and am now going through the system configuration. is there anything specific I need to configure differently to before?

EDIT3: after going through the system configuration thing, it said nothing about display/xorg/xserver etc. Im back at the terminal. startx no longer does anything...

EDIT4: this is too complicated. im gonna do a re-install. will the live cd allow me to get my stuff onto an external hdd? will it also let me wipe the whole (internal) hdd?

EDIT5: after a reboot, the kubuntu splash screen (well loading screen) showed!

EDIT6: It just finished loading, now im back at the terminal (again) :(

EDIT7: should I start a new post by now...

---

### Post by tmmuk on 2005-10-30
Just worked out - my gfx card is an "XFX Geforce fx5200 128mb DDR AGP"

just incase that helps...

EDIT: I tried the live-cd of breezy. just realised some problems though:
- The external hdd that I have is firewire, and I dont have a firewire card for my pc
- I cant burn my stuff onto a cd/dvd, as I only have one drive which is being used to run the live-cd.
- When I open the home folder (and others) it is a new one called "ubuntu". None of my stuff seems to be there??? (how can I access it?)

If I can get access to my actual home folder and other folders, I could back it up over the network onto another computer.

So any ideas on how to get it to show my actual home folder?

---

### Post by beefsprocket on 2005-10-30
Try to reinstall xserver-xorg before anything else. Once installed, tinker with your xorg.conf and try changing the driver from nv or nvidia to vga or to vesa. Just enough to get you into kdm. 

Another thing to try is installing the commercial nvidia driver once you've got xserver-xorg reinstalled. If you can't get kdm you can still use wget and compile the driver from your shell. 

i.e. wget [http://download.nvidia.com/XFree86/Linux-x86/1.0-7676/NVIDIA-Linux-x86-1.0-7676-pkg1.run](http://download.nvidia.com/XFree86/Linux-x86/1.0-7676/NVIDIA-Linux-x86-1.0-7676-pkg1.run)
sh NVIDIA-Linux-x86-1.0-7676-pkg1.run

You'll have to use the same gcc version your kernel uses and may have to install the kernel headers. You can use uname -a to check your kernel version and then use apt-cache search version# (likely 2.6.12-9 will work best). Then apt-get the headers for your kernel and run the nvidia install. You can (once installed) then edit your xorg.conf driver section from whatever you have it at to nvidia and reboot.

---

### Post by tmmuk on 2005-10-30
[QUOTE=beefsprocket]Try to reinstall xserver-xorg before anything else. Once installed, tinker with your xorg.conf and try changing the driver from nv or nvidia to vga or to vesa. Just enough to get you into kdm. 

Another thing to try is installing the commercial nvidia driver once you've got xserver-xorg reinstalled. If you can't get kdm you can still use wget and compile the driver from your shell. 

i.e. wget [http://download.nvidia.com/XFree86/Linux-x86/1.0-7676/NVIDIA-Linux-x86-1.0-7676-pkg1.run](http://download.nvidia.com/XFree86/Linux-x86/1.0-7676/NVIDIA-Linux-x86-1.0-7676-pkg1.run)
sh NVIDIA-Linux-x86-1.0-7676-pkg1.run

You'll have to use the same gcc version your kernel uses and may have to install the kernel headers. You can use uname -a to check your kernel version and then use apt-cache search version# (likely 2.6.12-9 will work best). Then apt-get the headers for your kernel and run the nvidia install. You can (once installed) then edit your xorg.conf driver section from whatever you have it at to nvidia and reboot.[/QUOTE]

so you reckon I should try this before formatting my hdd? I am copying what I want off it onto another pc over the network at the moment. Ill try it anyway and if it doesnt work then ill try a clean install. 

thanks

---

### Post by beefsprocket on 2005-10-30
I'd give it a shot. It may seem convoluted and unnecessary, but it might prove much more satisfying to have fixed the problem than to just wipe it off the map and begin again. Admittedly, it sounds like a frustrating enough problem that a good hard drive wipe might be just the thing.

---

### Post by tmmuk on 2005-10-30
nope, it didnt work. how can I go about wiping the hdd? ( i have backed up my home folder which contains the stuff I want to keep - its on another pc's hdd)

can I do it with a command / from a live-cd or what?

---

### Post by greatshape on 2005-10-30
[QUOTE=tmmuk]nope, it didnt work. how can I go about wiping the hdd? ( i have backed up my home folder which contains the stuff I want to keep - its on another pc's hdd)

can I do it with a command / from a live-cd or what?[/QUOTE]

Just boot from the breezy install cd, it will partition&format your HD

Regards,
Steve

---

### Post by peanut butter on 2005-10-30
for people(like me)who have had to do the same thing you can use puppy linux (live cd that you can takeout) if youdonthave another pc or if you donthave a network.:p :p 


PS.smae thing happened to me you are not alone only it just wouldent bootso i guess you were lucky.

Waiting forbreezy cds

---

### Post by tmmuk on 2005-10-31
[QUOTE=greatshape]Just boot from the breezy install cd, it will partition&format your HD

Regards,
Steve[/QUOTE]

ok thanks

---

### Post by tmmuk on 2005-11-04
Just saying I got it all working now, after starting again from fresh.

I had a few problems with compiling stuff from cvs, but I fixed them by installing automake, autoconf, make and a few other things.

---

### Post by shinygerbil on 2005-11-04
That's good to hear :)

Steve

---

### Post by greatshape on 2005-11-05
[QUOTE=tmmuk]Just saying I got it all working now, after starting again from fresh.

I had a few problems with compiling stuff from cvs, but I fixed them by installing automake, autoconf, make and a few other things.[/QUOTE]

Glad everything worked out fine for you :) 
What for example did you have to compile yourself?
Weren't there packages for it available in the repo's? 
Or did you really need the newest one? Just curious...

Regards, Steve ;)

---

### Post by tmmuk on 2005-11-06
I had to compile ndiswrapper 1.4 to get my wireless card working (the old version in the repos didnt work) and I was trying to get racer working ([www.racer.nl](www.racer.nl)) but no luck so far

---

### Post by greatshape on 2005-11-06
[QUOTE=tmmuk]I had to compile ndiswrapper 1.4 to get my wireless card working (the old version in the repos didnt work) and I was trying to get racer working ([www.racer.nl](www.racer.nl)) but no luck so far[/QUOTE]

Is, indeed it's better to use ndiswrapper from source.
No games 4me :) , sorry...
racer.nl? Where are you from? We might be neighbours talking the same language...

Regards, Steve

---

