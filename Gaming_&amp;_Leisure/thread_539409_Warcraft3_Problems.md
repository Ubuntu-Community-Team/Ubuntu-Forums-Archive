---
title: "Warcraft3 Problems"
date: 2007-08-31
forum: Gaming &amp; Leisure
---

### Post by melzanis on 2007-08-31
Ok I have a problem when I try to play Warcraft 3. 
 Every time that I go to run the game it just freezes of me. I can't even close the "wine" window, I'm forced to restart my computer. I really don't know what to do with this, can some one please help me out.

Thanks

---

### Post by cogadh on 2007-08-31
Are you using the terminal to launch the game and if so, is there anything listed in the terminal, such as error messages? What video hardware do you have and do you have the 3D accelerated driver for it installed? What version of Ubuntu and Wine are you using? Did the game install through Wine normally?

You need to provide a lot more detail before anyone can really make any useful suggestions.

EDIT - Almost forgot, did you follow a how-to to get the game installed and running? If not, I suggest you try this one:
[http://appdb.winehq.org/appview.php?iVersionId=1177](http://appdb.winehq.org/appview.php?iVersionId=1177)

---

### Post by melzanis on 2007-08-31
Ok well I do use the terminal and the desktop icon. I do get this one error when I go into "winecfg" and then come out: 

fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
err:winecfg:load_drives GetVolumeInformation() for 'E:\' failed, setting serial to 0

'E:\' is my my cdrom. 

I used all the how-to's to get the lastest version of wine installed and to intall warcraft. I also have WoW installed and that's doing the same thing. They where working fine before I installed beryl from this link:

[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

i'm also using the lastest version of Ubuntu Feisty.

hope that helps a bit.

cheers

---

### Post by cogadh on 2007-08-31
Beryl is your problem. You should not run games through Wine while Beryl is running, it usually leads to problems. Set the window manager to Metacity and the problem _should_ go away.

---

### Post by melzanis on 2007-09-01
Hey cogadh, 
       I want to thank you so far for your help. I had a feeling that it was beryl. I took your advise and I got the fooling error:

fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
err:ole:CoCreateInstance apartment not initialised
fixme:win:EnumDisplayDevicesW ((null),0,0x34f46c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f4a4,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:win:EnumDisplayDevicesW ((null),0,0x34cf3c,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
[email] warlock@warlock-desktop:~/.wine[/email]/dosdevices/c:/Program Files/Warcraft III$ fixme:win:EnumDisplayDevicesW ((null),0,0x34d568,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:win:EnumDisplayDevicesW ((null),0,0x34d5f8,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16

it still freezes when it starts up and tries to run the video. I have the file for the movies renamed.

---

### Post by soxs on 2007-09-01
Do you use the ```
-opengl
``` option?

---

### Post by melzanis on 2007-09-01
yes I do use '-opengl'

---

### Post by cogadh on 2007-09-01
Is 16 BPP a valid setting in your xorg.conf? If so, try setting your desktop to that before you launch the game.

---

### Post by melzanis on 2007-09-02
I'm not to sure what you mean by that... Would I be changing the screen rez then?

edit: this is what I found in that xorg.conf file ->	EndSubSection
	                                                                                  SubSection "Display"
		                                                                                              Depth	16
		                                                                                                    Modes		"1024x768"	"800x600"	"640x480"
and i'm using the "1024x768" mode

---

