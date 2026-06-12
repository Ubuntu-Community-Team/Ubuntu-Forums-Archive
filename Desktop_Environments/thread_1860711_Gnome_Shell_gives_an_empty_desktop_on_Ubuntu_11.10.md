---
title: "Gnome Shell gives an empty desktop on Ubuntu 11.10"
date: 2011-10-15
forum: Desktop Environments
---

### Post by deshmukh on 2011-10-15
After super-happy experience of Gnome 2 on Ubuntu 11.04, I upgraded to Ubuntu 11.10. It has been disastrous since.

Upgrade posted no errors. I now see LightDM and Gnome, Gnome Classic. Gnome Classic (No Effects) and Ubuntu as options.

Of these, Ubuntu works as advertised - Unity interface launches. So does Gnome Classic. But when I select Gnome as an option, all I see is empty desktop - no bars, no menus, nothing.

Taking the mouse to all edges has no effect. Alt-F2 does not work. Hitting Super key has no effect.

Only two things happen - on Alt-Ctl-Del, it allows me to logout and right click on the desktop works.

What is wrong? What is the remedy??

Thanks in advance.

---

### Post by drawkcab on 2011-10-15
I had to reboot a few times before G3 worked on my htpc.  Upgrading left me with several bugs so I did a clean reinstall and now everything's working just fine.

---

### Post by garvinrick4 on 2011-10-15
> What is wrong? What is the remedy??Try a few things:
```
sudo apt-get install gnome-shell
```What does it say?

Below to reinstall
```
sudo apt-get install --reinstall gnome-shell
``````
sudo apt-get install aptitude
``````
aptitude show gnome-shell
```
Does it say installed?
```
sudo dpkg --configure -a
```Above to make sure no broken packages.

```
sudo reboot
```Choose Gnome? What happens?
Still no success.
```
sudo apt-get install gnome-tweak-tool
```
Make sure themes are like this to start and see if works now.

---

### Post by Menti on 2011-10-15
I have exactly the same problem, and I have had it since beta 1.

But in my case, GNOME Shell **actually works**. I have to boot into another desktop (Unity or GNOME Classic), and then launch it manually (gnome-shell --replace in a terminal), and it works like a charm (a lot more fluid than Unity in fact). What fails is just logging in into GNOME Shell.

I have reinstalled everything, checked the config files for session startup... nothing.

Any idea? Thanks.

---

### Post by deshmukh on 2011-10-15
[QUOTE=garvinrick4;11345954]Try a few things:
```
sudo apt-get install gnome-shell
```What does it say?

The packages you mentioned are installed. But I think it is the graphics card drivers that are causing the problem (ATI RS780).

Here is what I have done subsequently:

Deleted the following folders from ~: .compiz, .compiz-1, .config, .gconf, .gconfd, .gnome2, .gnome2_private, .local

Also removed fglrx and fglrx-amdccle and installed fglrx-updates and fglrx-amdccl-updates using Synaptics.

Now, Gnome starts and I see something like a menubar at the top. I can also press Super key to summon a searchbox but the display is a MESS. It continuously flickers.

Moreover, gnome do window says that compositing is not allowed so I can not choose any theme. I can play supertuxcart - however.

When I log into Unity, things work quite well. Gnome do allows me to select any theme I want. So, I assume that compositing is working properly.

Also, Additional Drivers (from system settings) show fglrx and fglrx post update release not activated. When I try activitng them, it gives an error writing to /var/log/jockey.log

Hope I have given useful information and hope I am able to get back to gnome and out of unity-clutch.

Now, how do I get gnome to run on a machine on which Unity worked quite well right out of the box?

Thanks in advance.

---

### Post by garvinrick4 on 2011-10-15
> Now, how do I get gnome to run on a machine on which Unity worked quite well right out of the box?
Sorry I have never had to go any farther and went through alpha's and beta's but with my
intel vanilla cards and drivers, I imagine you read a fix with removing directorys as in
your post above? This will bump it back up to start of Forum, have a nice day deshmukh.

---

### Post by ioca100 on 2011-10-16
Open a *terminal(unit session)* and enter the following command: gnome-shell --replace.

---

### Post by OzzyFrank on 2011-10-17
Just confirming the when I try to log into Gnome Shell, it just ends up with an empty desktop, no way to do anything. While others report they could log out via Ctrl+Alt+Del, for me the System Monitor did appear, yet I couldn't click on it, then I couldn't do anything more in there and had to hit the reset button on my PC.

I might try again in a couple of reboots, since that seemed to "fix" it for at least one person. Not really keen to use that terminal command when logged into another desktop, just in case.

---

### Post by muralidhar.ch on 2011-10-17
I have the same issue as Deshmukh. When I ran the command as suggested, I see the following warning message: 

$ gnome-shell --replace
Window manager warning: Log level 16: Unable to register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject
Window manager warning: Log level 16: Error registering polkit authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject (polkit-error-quark 0)
      JS LOG: GNOME Shell started at Mon Oct 17 2011 10:31:11 GMT-0700 (PDT)

The gnome shell does get loaded, but its completely broken. The top menubar fonts are distorted and different colored. Hope this helps.

---

### Post by ioca100 on 2011-10-17
> **muralidhar.ch said:**
> I have the same issue as Deshmukh. When I ran the command as suggested, I see the following warning message: 

$ gnome-shell --replace
Window manager warning: Log level 16: Unable to register authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject
Window manager warning: Log level 16: Error registering polkit authentication agent: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: An authentication agent already exists for the given subject (polkit-error-quark 0)
      JS LOG: GNOME Shell started at Mon Oct 17 2011 10:31:11 GMT-0700 (PDT)

The gnome shell does get loaded, but its completely broken. The top menubar fonts are distorted and different colored. Hope this helps.

Did you reinstall gnome-shell?

---

### Post by muralidhar.ch on 2011-10-17
I did. Even, did a re-install of the OS again yesterday. Nothing has helped so far.

---

### Post by robin_s on 2011-10-18
I have more or less the same experience as muralidhar.ch
The only workaround which seems to work is to give the command 
   [COLOR=Red] gnome-shell --replace [/COLOR]
from a terminal window.  However, the resulting system is pretty unstable and freezes easily.  It's difficult to characterise exactly what gets it to freeze.  Almost anything seems to be able to do it :(

Worse still, once the Gnome shell has been activated, lots of the application windows lose their toolbars.  In Ubuntu 11.04 the toolbar for the active window would appear at the top of the screen.  In 11.10, only the name of the application appears.  Very irritating if you need to adjust the preferences or whatever for,
say, Thunderbird.

It looks like a nice combination (better than Unity...), but not yet simple to use.

---

### Post by glaubersm on 2011-10-18
gnome-shell only shows wallpaper here.
gnome-shell --replace command says...

> 
(gnome-shell:2537): Clutter-CRITICAL **: 

clutter_actor_set_text_direction: assertion `text_dir != CLUTTER_TEXT_DIRECTION_DEFAULT' failed

JS ERROR: !!! 
 Exception was: 
 Error: Failed to convert UTF-8 string to JS string: Sequência de bytes inválida na entrada de conversão

 JS ERROR: !!! 
 lineNumber = '0'

 JS ERROR: !!! 
 fileName = '"gjs_throw"'

 JS ERROR: !!! 
 stack = '"("Failed to convert UTF-8 string to JS string: Sequ\xEAncia de bytes inv\xE1lida na entrada de convers\xE3o")@gjs_throw:0
 ("%a %e de 

 %b, %R")@/usr/share/gnome-shell/js/ui/environment.js:75
 ()@/usr/share/gnome-shell/js/ui/dateMenu.js:208
 ([object Object])@/usr/share/gnome-

 shell/js/ui/dateMenu.js:167
 DateMenuButton([object Object])@/usr/share/gnome-shell/js/ui/dateMenu.js:44
 ()@/usr/share/gnome-

 shell/js/ui/panel.js:948
 Panel()@/usr/share/gnome-shell/js/ui/panel.js:887
 start()@/usr/share/gnome-shell/js/ui/main.js:215
 @<main>:1
 "'

 JS ERROR: !!! 
 message = '"Failed to convert UTF-8 string to JS string: Sequência de bytes inválida na entrada de conversão"'
 Aviso do gerenciador de janelas: Log level 32: Execution of main.js threw exception: Error: Failed to convert UTF-8 string to JS string: Sequência de bytes inválida da entrada de conversão

Any solution?

---

### Post by jander on 2011-11-01
Hello everybody.

I've found this workaround in [http://fossplanet.com/f13/%5Bfedora-i18n-bugs%5D-%5Bbug-682141%5D-gnome-shell-failed-start-whenchanging-user-language-chinese-china-113072/](http://fossplanet.com/f13/%5Bfedora-i18n-bugs%5D-%5Bbug-682141%5D-gnome-shell-failed-start-whenchanging-user-language-chinese-china-113072/).

I just have the suggested line commented out and gnome-shell worked again. So far, no collateral effects noticed.

[INDENT]
        File: /usr/share/gnome-shell/js/ui/dateMenu.js

        214:  /* this._date.set_text(displayDate.toLocaleFormat(dateFormat)); */[/INDENT]

Jander

---

### Post by loray on 2011-11-19
> **jander said:**
> Hello everybody.

I've found this workaround in [http://fossplanet.com/f13/%5Bfedora-i18n-bugs%5D-%5Bbug-682141%5D-gnome-shell-failed-start-whenchanging-user-language-chinese-china-113072/](http://fossplanet.com/f13/%5Bfedora-i18n-bugs%5D-%5Bbug-682141%5D-gnome-shell-failed-start-whenchanging-user-language-chinese-china-113072/).

I just have the suggested line commented out and gnome-shell worked again. So far, no collateral effects noticed.

[INDENT]
        File: /usr/share/gnome-shell/js/ui/dateMenu.js

        214:  /* this._date.set_text(displayDate.toLocaleFormat(dateFormat)); */[/INDENT]

Jander
 This workaround didn't worked for me. Same empty desktop.

---

### Post by md2406 on 2011-12-06
Hi,
I am having the same problem when I run gnome-shell with effects but no effects is working just fine. It happens when I upgraded nvidia to "recommended" via additional drivers. I have tried whatever you guys said in here but no luck. If anybody has different idea or solution, I am willing to try.

---

### Post by wxnker on 2011-12-09
I've had an empty gnome-shell also. In both cases it was related to the graphics card driver.

On a nVidia laptop I had the same problem after a kernel update, iirc. I don't remember exactly what I did. I think I installed a newer nVidia driver (from a ppa perhaps) with newer kernel support. 

On my Ati desktop I now use the newest Catalyst driver from the Ati site. It works, with glitches. From my experience (hd5xxx), don't enable "tear free desktop" in the Ati Catalyst app though. It made my screen flicker.

---

### Post by md2406 on 2011-12-09
> **loray said:**
> This workaround didn't worked for me. Same empty desktop.


I have tried this one too but nothing changed.

---

### Post by md2406 on 2011-12-09
> **wxnker said:**
> I've had an empty gnome-shell also. In both cases it was related to the graphics card driver.

On a nVidia laptop I had the same problem after a kernel update, iirc. I don't remember exactly what I did. I think I installed a newer nVidia driver (from a ppa perhaps) with newer kernel support. 

On my Ati desktop I now use the newest Catalyst driver from the Ati site. It works, with glitches. From my experience (hd5xxx), don't enable "tear free desktop" in the Ati Catalyst app though. It made my screen flicker.

can you tell which PPA u used in installing nVidia driver with new kernel support?

---

