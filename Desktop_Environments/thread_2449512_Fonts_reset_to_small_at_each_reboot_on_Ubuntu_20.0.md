---
title: "Fonts reset to small at each reboot on Ubuntu 20.04"
date: 2020-08-28
forum: Desktop Environments
---

### Post by nico16 on 2020-08-28
Hi, 

I'm using Tweaks to increase fonts on my desktop. It has been working well and kept the configuration from one boot to the next. However for the last week or so, fonts get back to a small size every time I reboot my laptop. 

I think the problem appeared after I had to use this command trying to sort out a networking issue:
"[COLOR=#242729][FONT=Consolas]sudo dpkg-reconfigure linux-image-$(uname -r)"[/FONT][/COLOR]
So it is probably related (although not 100% sure). 

Would anyone know how to get my desktop environment to remember the font settings set through Tweaks from one boot to the next ?

Thanks for your help.

---

### Post by TheFu on 2020-08-28
[https://www.omgubuntu.co.uk/2016/03/how-to-change-ubuntu-desktop-font](https://www.omgubuntu.co.uk/2016/03/how-to-change-ubuntu-desktop-font) isn't working?

---

### Post by nico16 on 2020-08-30
Interesting workaround, thanks a lot for suggesting. It helps a bit but it's not really big enough for my liking and it doesn't impact the size of the top bar, which I find too small with the default settings. 
Interestingly, Tweaks remembers the change of font but not the change of scaling from one boot to the next. 

Is there any way to "neutralise" this command, assuming it is what caused the problem (which might be a long stretch) ?
[COLOR=#000000]"[/COLOR][COLOR=#242729][FONT=Consolas]sudo dpkg-reconfigure linux-image-$(uname -r)"[/FONT][/COLOR]

Has anyone else had that issue of scaling factor in Tweaks not being remembered from one boot to the next ? 

Thanks for your help.

---

### Post by TheFu on 2020-08-30
I haven't used gnome3 ... ever ... so really can't help more if that is a requirement.  

OTOH, if you want complete control over windows, borders, window titles, button locations and which buttons are on every window, then going old-school with a long-proven WM and no DE will certainly work.  People seem to like fvwm-crystal.  I find the default font for window titles to be too large, but everyone has different needs.

```
sudo apt install fvwm
```
Then add the "crystal" theme.
Because fvwm doesn't use any gnome or kde settings, having it installed has ZERO danger to your existing settings.  To try it out, just logout, before logging in click the "gear" and choose "fvwm" from the choices. Login as normal.  Right click anywhere on the desktop. See if you like that.  There are a number of fvwm "helpers". All settings are controlled via text files in ~/.fvwm/. No GUI to make setting changes, but we have complete control.

[http://fvwm-themes.sourceforge.net/](http://fvwm-themes.sourceforge.net/)  It is amazing how very different the exact same WM can appear by applying different themes:
fvwm 2.6.8 is what ships in the 20.04 repos.
fvwm 2.6.5 is what ships in the 16.04 repos.
This means that pretty much any pre-designed theme you'll find online will be compatible.
[http://fvwm-themes.sourceforge.net/windowdecors/](http://fvwm-themes.sourceforge.net/windowdecors/) has about 20 "window decoration" examples.

The great thing about fvwm is the program has been stable for a long time. My same config from 2010 has been working all this time regardless of what Canonical ships. No need to fumble around with some new GUI every release when I just want to be productive on a desktop.

But if you like having the GUI completely changed every 2 yrs, stick with Gnome.

---

### Post by Dennis N on 2020-08-30
Instead of changing the scaling factor, did you try changing the Interface Text size at the top? That might be more persistent.

The size of the font in the top bar is set by the gnome-shell theme you are using. Look for the file gnome-shell.css in the theme's folder.

```
dmn@Sydney-VM:/usr/share/themes/Flat-Remix-Dark/gnome-shell$ tree -L 1
.
&#9500;&#9472;&#9472; assets
&#9492;&#9472;&#9472;[COLOR="#FF0000"] gnome-shell.css[/COLOR]

```

---

### Post by nico16 on 2020-08-31
Thanks for the suggestion. Sounds interesting. Gnome has its limitations and bugs but I guess I got used to it and rather like the look of the latest instalment. I will look into fvwm  at some point though, thanks for suggesting !

---

### Post by nico16 on 2020-08-31
Ok, thanks for the advice about changing the text size in the gnome shell file. I tried to edit it from the terminal but got this error message: 
> (gedit:26126): Tepl-WARNING **: 16:18:46.755: GVfs metadata is not supported. Fallback to TeplMetadataManager. Either GVfs is not correctly installed or GVfs metadata are not supported on this platform. In the latter case, you should configure Tepl with --disable-gvfs-metadata.

Tried same command with "sudo -H" but still get the same error message. If anyone has advice on how to take it further I'd be grateful.

Thanks !

---

### Post by Dennis N on 2020-08-31
I would use an editor that runs in the terminal, the easiest (in my opinion) being **nano**. That's what I always use when editing system files that need admin privileges. I'm sure that's what I used to edit mine. 

If nano is new to you, here's some usage help:
[https://linuxize.com/post/how-to-use-nano-text-editor/](https://linuxize.com/post/how-to-use-nano-text-editor/)

---

### Post by nico16 on 2020-08-31
Ok, thanks a lot for that. I managed to edit the file with nano, however, whatever I did doesn't make a difference. 

I followed the instructions found on this webpage: [https://www.omgubuntu.co.uk/2017/04/change-gnome-shell-font](https://www.omgubuntu.co.uk/2017/04/change-gnome-shell-font), which suggests that the information to change is where the code says "*stage*" in the file. But it didn't work when I changed the font in that section (I restarted gnome shell but didn't reboot). Maybe the section for the top bar is different in the latest gnome version ? 

Looking into the css file I can see there is a "*Top bar*" section. The fourth line says "*height: 1.86em;*".
Is this the line I need to change?? If not which one is it ?

Thanks a lot for your help.

---

### Post by Dennis N on 2020-08-31
I can give you what I did in Ubuntu 18.04:
Theme Information:
Theme: Flat Remix Dark. 
Archive File: 03-Flat-Remix-Dark_20191027.tar.xz 

I made two changes. The font, and the size:

```
stage {
  font-family: Cantarell, Sans-Serif;
  font-size: 10pt;
  color: #FFF; }

TO:

stage {
  font-family: Liberation, Cantarell, Sans-Serif;
  font-size: 12pt;
  color: #FFF; }

AND

#panel {
  font-feature-settings: "tnum";
  text-shadow: 0px 1px 2px rgba(0, 0, 0, 0.9);
  border-radius: 6px;
  font-weight: normal;
  font-size: .9em;

TO:

#panel {
  font-feature-settings: "tnum";
  text-shadow: 0px 1px 2px rgba(0, 0, 0, 0.9);
  border-radius: 6px;
  font-weight: normal;
  font-size: 1em;


```
These are the only changes made from the original, and panel font size increased.

---

### Post by nico16 on 2020-09-06
Thanks a lot for that. I tried your solution but to no avail. It didn't seem to make any difference somehow. 

I then tried uninstalling and reinstalling Gnome Tweaks a couple of times as suggested [here]("https://ubuntuforums.org/showthread.php?t=2449249") but it didn't work either. 

I can see that others have been having the same issue as me though (see t[his thread]("https://ubuntuforums.org/showthread.php?t=2449371")) so I guess this is a bug with gnome / tweaks and hopefully there will be a fix at some point. 

For what it's worth, in the end I used a combination of solutions / extensions to make things kind of ok:
- Im using the gnome extension "Taskbar 2020" to adjust the size of the top panel
- Im using the gnome extension "Desktop Icons" to adjust the size of the folders on the desktop
- And Im using the gnome extension "Font Scaler" to increase the size of the fonts on the desktop and windows. I still need to double click on the extension icon every time my laptop boots up to activate the larger fonts so it's not a completely satisfactory solution but it's basically ok.

If someone has a better solution, let us know. 

Thanks.

---

