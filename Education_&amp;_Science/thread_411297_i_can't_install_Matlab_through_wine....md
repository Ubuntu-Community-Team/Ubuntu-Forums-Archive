---
title: "i can't install Matlab through wine..."
date: 2007-04-16
forum: Education &amp; Science
---

### Post by Titi on 2007-04-16
hey,
i have matlab 7 cdroms for windows. i thought i could install them using Wine. but i don't get any further than the first dialog window. that's empty. in my console i get these messages:
```
maarten@maarten-desktop:/media/cdrom0$ wine setup
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:win:EnumDisplayDevicesW ((null),0,0x33e778,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x33e778,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0xa866e28) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0xa8644e0)->((nil),00001008)
err:d3d:state_multisampleaa Multisample antialiasing not supported by gl
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0xa8644e0)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock

```

does anybody know how to fix this? i've searched on google, but i can't seem to find any guide to install matlab through wine. i know there are alternatives for linux, but they are not compatible enough. and i have these windows cds, so it'd be nice not to have to buy the same thing for linux...
and i've seen on the wine website that people succeeded in installing it, and that it works nearly perfectly, so i should be able to do it too. just need a little help...
thanks,

maarten

---

### Post by raja on 2007-04-16
I have previously tried to do this with matlab 6.5 and remember that you can get it working only with the --nojvm option (no java virtual machine). I dont know if you can get it to work perfectly. But remember there are alternatives that are as good or better - Scilab, Octave and Python/scipy.

---

### Post by harishg on 2007-04-21
Check if codeweavers mention about support for matlab.If they do not mention it,you would not be able to install matlab with wine.

---

### Post by roadster.eleven on 2007-04-24
I think that exits a Linux version of Matlab 7. Maybe this is the only way to run the software!

---

### Post by anoir on 2007-04-25
Matlab for Linux works perfectly under Feisty without 3d desktop effects . And I think it is a lot faster than  Windows version. I'm not sure, but IMHO Linux version exploits dual core CPU better than its Windows counterpart.

However, Matlab for Windows should work as well, using wine. See its entry in the wine application DB:

[http://appdb.winehq.org/appview.php?iAppId=49](http://appdb.winehq.org/appview.php?iAppId=49)

At least, the instruction on the page whose link is given below worked under Edgy without -no-jvm option.

[http://appdb.winehq.org/appview.php?iVersionId=5959](http://appdb.winehq.org/appview.php?iVersionId=5959)

Honestly, I really want to switch to other free alternatives...if the situation permits.

---

### Post by zgornel on 2007-04-25
> **anoir said:**
> Matlab for Linux works perfectly under Feisty without 3d desktop effects . And I think it is a lot faster than  Windows version. I'm not sure, but IMHO Linux version exploits dual core CPU better than its Windows counterpart.

However, Matlab for Windows should work as well, using wine. See its entry in the wine application DB:

[http://appdb.winehq.org/appview.php?iAppId=49](http://appdb.winehq.org/appview.php?iAppId=49)

At least, the instruction on the page whose link is given below worked under Edgy without -no-jvm option.

[http://appdb.winehq.org/appview.php?iVersionId=5959](http://appdb.winehq.org/appview.php?iVersionId=5959)

Honestly, I really want to switch to other free alternatives...if the situation permits.

It works with 3D effects too, you have to export something ... the answer is on the net, works with both beryl and compiz perfectly (you can always run it in text mode :D :D)
Matlab is slow enough on it's own, it the native environment, with wine would be higly unusable, regardless on what winedb says, unfortunately.
Thirdly, it is far more advanced than any open source alternative. Octave is catching up and growing intensively but Matlab has a level of quality and speed that are unmatched. If oyu are using Matlab for billions of calculations you'll realize that octave is simply not up to it :( ... Yet!
I suggest using Matlab for Linux, preferably the latest version possible, old ones are unstable.

---

### Post by dubrict on 2007-04-26
My matlab CD comes with the linux version on it.  And it's the student version.
I remember it being a pain to get it working under fedora, but I haven't tried it in ubuntu.  I do remember there being issues with java, like that other guy said though.

---

### Post by anoir on 2007-04-26
[QUOTE=zgornel]It works with 3D effects too, you have to export something ... the answer is on the net, works with both beryl and compiz perfectly (you can always run it in text mode  )[/QUOTE]

Yeah, I tried that, but haven't succeeded yet. Maybe I have to do more research, but, plainly put, I don't need those 3d desktops so much :) 

3 things prevent me from migrating to other options. First, I have to work with other people who prefer matlab. Second, some toolboxes are just indispensable (unfortunately, I have no ability to write one on my own). Third, I sometimes do rather heavy number crunching. First two seem to be common reason why one cannot ditch proprietary softwares in general :(

[QUOTE=dubrict]
My matlab CD comes with the linux version on it. And it's the student version.
I remember it being a pain to get it working under fedora, but I haven't tried it in ubuntu. I do remember there being issues with java, like that other guy said though.[/QUOTE]

The latest one comes in DVD! Installation in Ubuntu is really without hassle:

```

sudo mkdir /opt/matlab
cd /opt/matlab
sudo /media/cdrom/install
paste licence file into the window - DONE
```

Detail might be different.

---

### Post by zgornel on 2007-04-26
Ok, found the compiz solution, it worked for me: [http://www.suckless.org/pipermail/dwm/2006-December/001349.html](http://www.suckless.org/pipermail/dwm/2006-December/001349.html)

---

### Post by Titi on 2007-04-26
thanks for the information. i guess it'll try the linux version then. i suppose i should get it very cheap somewhere on the uni.

---

### Post by anoir on 2007-04-26
> **zgornel said:**
> Ok, found the compiz solution, it worked for me: [http://www.suckless.org/pipermail/dwm/2006-December/001349.html](http://www.suckless.org/pipermail/dwm/2006-December/001349.html)

Oh, I found that I mistyped as MTookKit before. It works!! Thank you.

---

### Post by turbod33 on 2007-04-27
I'm running fiesty 7.04, and I installed my Uni copy of Matlab R14SP3 with no problem. I love open source, but some closed stuff is just fantastic, and I love me some Matlab. 

I just spent the last 3 days coding up in Matlab with Beryl, and i feel that I was a lot more productive in the Ubuntu environment with fast virtual desktops and the window-switching capabilities. 

If you need any help getting your license manager set up, let us know.

---

### Post by Kent84 on 2007-05-02
Recently got Matlab 7 going on my Ubuntu Fiesty laptop... wasn't easy getting the license manager going. Anyway, I am having problems copy & pasting matlab figures into openoffice documents; I get an error "Clipboard format not supported". Any ideas? I am having to take screen shots....

---

### Post by anoir on 2007-05-02
How about just saving figures as eps or whatever file type you like? A lot better than taking screen shots.

---

### Post by Kent84 on 2007-05-02
Yea I can save as *.eps in matlab then insert the picture in my openoffice image, but that's a lot of work since I have to repeat this for 40+ images. alt+printscreen then ctrl-v works a bit faster but it is definitely not a neat work around. In windows I use to be able ctrl-c and then ctrl-v straight into openoffice. Anyone know if I can reproduce this behavior with matlab & openoffice in gnome?

---

### Post by anoir on 2007-05-03
I see. I also can't do that. I have not noticed it, because I always export plots as eps for LaTeX/LyX. I tried to use -dmeta option for print function with no success. Probably the option itself is not available in UNIX version. I'm curious to know how to get aroud this issue as well. Does anyone know a solution?

---

### Post by ahmatti on 2007-05-03
> **Kent84 said:**
> Yea I can save as *.eps in matlab then insert the picture in my openoffice image, but that's a lot of work since I have to repeat this for 40+ images. alt+printscreen then ctrl-v works a bit faster but it is definitely not a neat work around. In windows I use to be able ctrl-c and then ctrl-v straight into openoffice. Anyone know if I can reproduce this behavior with matlab & openoffice in gnome?

Can I ask why you need to do this? I guess not for anything high quality...

---

### Post by zgornel on 2007-05-03
> **Kent84 said:**
> Recently got Matlab 7 going on my Ubuntu Fiesty laptop... wasn't easy getting the license manager going. Anyway, I am having problems copy & pasting matlab figures into openoffice documents; I get an error "Clipboard format not supported". Any ideas? I am having to take screen shots....
Save the figures as JPEG. :)

---

### Post by Kent84 on 2007-05-04
> **ahmatti said:**
> Can I ask why you need to do this? I guess not for anything high quality...

I do it for speed and convenience. I keep an "electronic" lab journal so I want to be able to put in figures quickly without the need of them being high quality.

My current workaround is taking screenshots of a section of the screen (so I don't get the window menu bars) using the screen capture shortcut in Beryl or DDM.

In the version of matlab in Windows, under "copy options", I can choose whether the figure I copy (using ctrl-C) is in the BMP file format or the windows meta file format. No such option seems to exist in the UNIX version. I'm guessing the default format is something obscure and unsupported by openoffice.

---

### Post by anoir on 2007-05-05
> **Kent84 said:**
> 
In the version of matlab in Windows, under "copy options", I can choose whether the figure I copy (using ctrl-C) is in the BMP file format or the windows meta file format. No such option seems to exist in the UNIX version. I'm guessing the default format is something obscure and unsupported by openoffice.

It seems that UNIX version does lack that capability. Go for help. It only refers clipboard feature in Windows.

---

### Post by greg_gm on 2008-10-13
I was able to install matlab 2007b using wine 1.15.  The basic instructions are provided here:

[http://appdb.winehq.org/appview.php?iVersionId=5385&iTestingId=5290](http://appdb.winehq.org/appview.php?iVersionId=5385&iTestingId=5290)

Follow all the steps:  including changing your drive serial number in wine, and installing java.

Matlab seems to works perfectly except for the "current directory" window which seems to have various java errors.  I can live without it.  If your display initially looks garbled try to close that window.  Or select "all tabs" under:  Desktop|Desktop Layout|All Tabbed.  Once your display cleans up close the "current directory" window by clicking the X in the upper right hand corner.

---

