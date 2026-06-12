---
title: "Xgl not present?"
date: 2007-10-30
forum: Desktop Effects &amp; Customization
---

### Post by madhatter563 on 2007-10-30
Hello, I am trying to get compiz to work, and this is what i get


```
trinity@Trinity:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
```

I INSTALLED the xserver-xgl package as requested, and restarted, it gave the message that it would automatically start, etc, so i know it is installed. Im not sure where to troubleshoot from here. Oh by the way, I am using a thinkpad t23 which uses the _SuperSavage IX/C SDR by IBM_. Perhaps this is just too old to run it correctly. Thanks for any help!

---

### Post by kdawgmfic79 on 2007-10-30
Run in terminal

gksu gedit /usr/bin/compiz

then add your driver to the Driver whitelist section line #54

**_EXAMPLE:_**

# Driver whitelist
WHITELIST="nvidia intel ati radeon i810"

to add fglrx, simply add it  

# Driver whitelist
WHITELIST="nvidia intel ati radeon fglrx i810"

---

### Post by madhatter563 on 2007-10-30
Im a little confused by that.. I followed those instructions, but had the same result.. were those both examples? do i have a different driver, and if so, how do i figure out with one?

---

### Post by Zorael on 2007-10-30
I know it says which driver is loaded in the KDE Control Centre (Appearance -> Monitor & Display -> Hardware), and there's likely some similar GUI way in Gnome, but I don't know it.

Open /etc/X11/xorg.conf with the editor of your choice, and scroll down to the **Section "Device"** which has an Identifier entry that says "Generic Videocard" (or the actual name of your card). There'll be an entry there named Driver with the driver module name after it.

Example:
```
Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce Go 7600]"
    Driver         "nvidia"
EndSection
```

---

### Post by madhatter563 on 2007-10-31
ok tried that.  here is what my driver whitelist looks like.  i commented out some other tries.  but here was my last which fits the last request:

```
# Driver whitelist
# WHITELIST="nvidia intel ati radeon i810"
WHITELIST="savage"
# WHITELIST="S3 Inc. SuperSavage IX/C SDR"
```

I tried enabling the desktop effects after all my attempts, and it still says it cannot be enabled.  I went back and typed compiz in terminal and got the same thing, but it now has more lines to spit out at the end:
```

:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 5333:8c2e (rev 05) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: Not present. 
aborting and using fallback: /usr/bin/metacity 

```
Any idea?

---

### Post by theorem_hunter on 2007-11-12
i cant get it right either
$ compiz --replace
Checking for Xgl: not present.
Detected PCI ID for VGA: 05:00.0 0300: 1002:5e4d (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
aborting and using fallback: /usr/bin/metacity
no /usr/bin/metacity found, exiting

$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present.
Detected PCI ID for VGA: 05:00.0 0300: 1002:5e4d (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Starting emerald
/usr/bin/compiz.real (core) - Fatal: No 

$ cat /usr/bin/compiz | grep WHITELIST
WHITELIST="fglrx nvidia intel ati radeon i810"

$ glxinfo | grep direct
direct rendering: Yes

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X700
OpenGL version string: 2.0.6473 (8.37.6)

i do see that i do have a error.

$ cat /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering

anyhelp? thanks

---

### Post by krammer on 2007-11-12
I also have the same problem...

$ compiz
Checking for Xgl: not present.
Detected PCI ID for VGA: 02:00.0 0300: 1002:5e4b (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
aborting and using fallback: /usr/bin/metacity
no /usr/bin/metacity found, exiting



$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X700 PRO
OpenGL version string: 2.0.6334 (8.34.8)

display: :0.0  screen: 1
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X700 PRO
OpenGL version string: 2.0.6334 (8.34.8)

---

### Post by theorem_hunter on 2007-11-13
ok this solved part of my problem...
```
sudo apt-get install xserver-xgl
```

then i logged out & in again & ran
```
compiz --replace
```

which did start compiz but it was not working 100%, i have 4 desktops normally, it put 8, then i couldnt rotate the cube, it was just a 3D version of 1 of the faces of the cube...
none of the other functions of compiz were working...
but the above code snippets should help the rest of you...

---

### Post by Fran89 on 2007-11-21
> **madhatter563 said:**
> Hello, I am trying to get compiz to work, and this is what i get


```
trinity@Trinity:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
```

I INSTALLED the xserver-xgl package as requested, and restarted, it gave the message that it would automatically start, etc, so i know it is installed. Im not sure where to troubleshoot from here. Oh by the way, I am using a thinkpad t23 which uses the _SuperSavage IX/C SDR by IBM_. Perhaps this is just too old to run it correctly. Thanks for any help!

same thing here...
sad really

---

### Post by thecmpguru on 2007-11-21
I have Ubuntu Gutsy with Compiz and an ATI Radeon X1400. I get the 
```

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```

error message also. This is reproducible by running
```

compiz --replace &

``` 

I have installed xserver-xgl and I am running the restricted ATI drivers.

---

### Post by Flashstar on 2007-11-25
I too have the same problem with my T23. I get stuck with the error:

Checking for texture_from_pixmap: present. 
Checking for non power of two support: Not present. 
aborting and using fallback: /usr/bin/metacity

I added the savage driver to the whitelist, installed xserver-xgl, and attempted to turn on compiz. But I got the error that I mentioned previously.

I heard on Thinkwiki that Compiz will run. Does anyone have some suggestions?

---

### Post by lengo on 2008-01-03
I'm completely new to this game, but I just got Compiz-Fusion working on my IBM T42 w/ ATI Radeon 9600 Mobility card. I did everything in this thread and was ready to give up when I took one last look at System > Preferences > Appearance > Visual Effects which was set back to None (though I'm sure I had Custom selected at some point . . . ) I reselected Custom, my screen flickered, *et voila*, I'm in 3D land! I hope this helps someone.

---

### Post by shrinux on 2008-01-04
After following the instruction I end up with the same problem of the others:

$ compiz --replace

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1106:3344 (rev 01) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
```


I'm using a built-in graphics card (in the motherboard)

I don't know what is it !!! ... probably VIA ... I don't know :(

---

### Post by lengo on 2008-01-04
Try the command: fglrxinfo in the terminal to find your display type (cf. posts #6 and 7 on the first page). That may be the best place to begin b/c it seems there are different methods for different display types.

---

### Post by shrinux on 2008-01-06
> **lengo said:**
> Try the command: fglrxinfo in the terminal to find your display type (cf. posts #6 and 7 on the first page). That may be the best place to begin b/c it seems there are different methods for different display types.

this is the result:
```
The program 'fglrxinfo' is currently not installed.
```

I'm installing it now ...
what is 'fglrxinfo' anyway ?

---

### Post by shrinux on 2008-01-06
This is the result of the command [COLOR="Blue"]'fglrxinfo'[/COLOR] :
```
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  14
  Current serial number in output stream:  15
```
[COLOR="Red"]What is my graphics card ?!![/COLOR]

After installing [COLOR="Green"]'xorg-driver-fglrx'[/COLOR]
and running command [COLOR="Blue"]'compiz --replace'[/COLOR]
this is the result :
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1106:3344 (rev 01) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity
```

I'm feeling that [COLOR="Green"]'xgl-server'[/COLOR] is disabled !!!

[COLOR="Red"]How could I enable it ?!![/COLOR]

---

### Post by lengo on 2008-01-06
> **shrinux said:**
> what is 'fglrxinfo' anyway?
'fraid I don't know . . . Kind of scary for a new guy like me to be making suggestions that I don't fully understand--sorry. I should have just stuck to what I knew (cf. post #12). I suggested 'fglrxinfo' because I took it on faith from someone else and it provided me with the info I needed. As for your current issues, I'm at a complete loss . . . Perhaps you could let us know what kind of computer you have which may provide a clue as to your graphics card type.

---

### Post by shrinux on 2008-01-07
**This post could be related to an Ubuntu bug filed at**: about my graphics card chips [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				[COLOR="DarkOrchid"]My PCs motherboard is:[/COLOR]
MSI PM8M3-V

[COLOR="DarkOrchid"]and the graphics chips is:[/COLOR]
VIA P4M800CE

[COLOR="DarkOrchid"]From VIA website, I found this link to install the driver in Ubuntu 7.10:[/COLOR]
(don't tell, I'm also surprised that VIA  provide support for deferent Linux distros)
[COLOR="Blue"][http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=150](http://www.viaarena.com/default.aspx?PageID=420&OSID=45&CatID=3220&SubCatID=150)[/COLOR]

[COLOR="DarkOrchid"]But I'm afraid that 3D accelerator and other stuff are not supported for this chips:[/COLOR]
you can download the compressed file and read the description that is included from this link:
[COLOR="Blue"][http://www.viaarena.com/Driver/via_ubuntu710_unichrome-v40072d-kernel-bin-_v0.80.zip](http://www.viaarena.com/Driver/via_ubuntu710_unichrome-v40072d-kernel-bin-_v0.80.zip)[/COLOR]

[COLOR="Green"]I will post my feedback after installing the driver (as illustrated in the package)[/COLOR]

See you soon

---

### Post by rasty on 2008-01-23
fglrxinfo is used to grep info from ati-amd based video cards,chips whatever. You should use glxinfo to grep the info for your system. You will probably get something like vesa which is the open source....FGLRX are the drivers for ati graphics but closed source or proprietary.As I can see from your logs you don't have the appropriate drivers installed so you can't render 3d content as it is required to run compiz etc. Make sure to first know your video card (perhaps open the case and take a look on your video card or first boot with windows?) and then install appropriate driver

---

### Post by pianist4Him on 2008-04-13
Hi kdawgmfic79,

As I've noticed that you have a video card as I do, which is ATI X1400 on a Insiprion 9400, I'm really a newby in Linux, but I would really like to have it configured properly. I have installed the Kubuntu 7.10 successfully and it's working ok the wireless and sound. What I'd really love to have is the 3D cube desktop effects with compiz. I made it till here by the instructions from another page from the same forum. When I run the 'compiz --replace' command in the terminal I get the following error: 'Checking for Xgl: not present. 
No whitelisted driver found'. I would really appreciate it if you could guide me to make this work. 
Thank you in advanced. God bless.



> **kdawgmfic79 said:**
> Run in terminal

gksu gedit /usr/bin/compiz

then add your driver to the Driver whitelist section line #54

**_EXAMPLE:_**

# Driver whitelist
WHITELIST="nvidia intel ati radeon i810"

to add fglrx, simply add it  

# Driver whitelist
WHITELIST="nvidia intel ati radeon fglrx i810"

---

### Post by kutjara on 2008-04-13
Not a solution, just some extra info for your consideration.

I have Compiz-Fusion up and running beautifully on my Acer laptop. I too get the message that xgl isn't present when I type compiz --replace, but that doesn't matter a bit. All my Compiz features run smoothly. This is on an Intel integrated graphics setup (X3100), so the situation is not directly comparable with yours, but it is indicative that xgl isn't the issue.

I actually tried installing the xgl-xserver package to see if it conferred any benefits but found, when I used glxgears to "benchmark" my card, that the framerate had dropped from (pre xgl-xserver)  800fps to 150fps, so running through that particular xserver was killing my graphics card's performance. Uninstalling xgl-xserver restored my framerate.

---

### Post by observative on 2008-04-13
pianist4him, to install Xgl enter into a terminal ```
sudo apt-get install xserver-xgl
```To uninstall Xgl, type ```
sudo apt-get remove xserver-xgl
```I too experienced a massive frame rate drop and ended up removing xgl. Hope this answers your question.

---

### Post by russo.mic on 2008-04-14
> **observative said:**
> pianist4him, to install Xgl enter into a terminal ```
sudo apt-get install xserver-xgl
```To uninstall Xgl, type ```
sudo apt-get remove xserver-xgl
```I too experienced a massive frame rate drop and ended up removing xgl. Hope this answers your question.

Well,  XGL only helps if you don't have direct rendering capablities.  If you install it on top of AIGLX this is what will happen.  Do you ahve an AIGLX supported card?

kutjara,  if you don't have XGL and your compiz is working, you must have an AIGLX supported card.  The ATI cards, although they now support AIGLX, always seems to me to look worse with AIGLX.  I'm waiting a few driver releases before I try it.

Russo

---

### Post by space_agent on 2008-05-07
I just have to tell you that I am very lucky about finding this thread. Until recently I noticed that I had high CPU Usage and the fan going loud on a Sony 1,6GHz Notebook with a Geforce Go 7600(128MB) while using compiz and firefox. When I ran compiz from the terminal there came the message xgl=not present. After installing xserver-xgl everything runs perfect now thanks to you.

---

### Post by anupmanekar on 2008-05-17
Hi 

  I tried compiz --replace on ubuntu 8.0.4. That gave following error

   Checking for Xgl: present. 
   Checking for nVidia: not present. 
   Checking for Xgl: present. 
   Enabling Xgl with nVidia drivers...
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

   After removing Xgl(I read somewhere that XGL is not needed on ubuntu latest version).. I got this

  Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:12.0 0300: 10de:0531 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

What should I do to move ahead ??

---

### Post by painterh on 2008-07-08
Hi;
I am running Ultimate Edition based on Ubuntu 8.04 64 bit.  I too have the same problem with desktop effects.  I'm currently using the nvidia-glx-new driver for Nvidia 7600GS. When I try to run compiz --replace it reports the following;

harlund@harlund-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0392 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

I tried to install xserver-xgl using apt-get but it reported that it was already installed and was latest version.

I also do not show any restricted drivers available or in use in the restricted drivers manager.  I know they are installed because I have installed them.  I am at wits end with desktop effects.

---

