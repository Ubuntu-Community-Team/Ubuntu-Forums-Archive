---
title: "Auto-login not working."
date: 2009-01-29
forum: General Help
---

### Post by sceo on 2009-01-29
I have auto-login enabled in System->Administration->Login Window->Security, but I still just get the login screen when I reboot.

I *think* this happened when I installed the server kernels to get PAE (and the full 4GB of RAM recognized), but I can't be 100% sure.

I read one post that "preload" may have interfered, so I uninstalled preload (but it did not help).

---

### Post by zika on 2009-01-29
> **sceo said:**
> I have auto-login enabled in System->Administration->Login Window->Security, but I still just get the login screen when I reboot.

I *think* this happened when I installed the server kernels to get PAE (and the full 4GB of RAM recognized), but I can't be 100% sure.

I read one post that "preload" may have interfered, so I uninstalled preload (but it did not help).
do You have readahed tweak running? it can also, beside preload, mess with autologin.

---

### Post by sceo on 2009-01-29
Thanks for the reply.  I do not have readahead running (as far as I can tell from this post: [http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651)).

---

### Post by zika on 2009-01-29
> **sceo said:**
> Thanks for the reply.  I do not have readahead running (as far as I can tell from this post: [http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651)).
check the file /etc/gdm/gdm.conf-custom

---

### Post by sceo on 2009-01-29
My gdm.conf-custom (comments and extraneous whitespace removed for readability):

[daemon]
AutomaticLogin=******
DefaultSession=gnome.desktop
AutomaticLoginEnable=true

[security]

[xdmcp]

[gui]

[greeter]
Use24Clock=no
DefaultWelcome=false
DefaultFace=
GlobalFaceDir=//

[chooser]

[debug]

[servers]

---

### Post by zika on 2009-01-29
> **sceo said:**
> My gdm.conf-custom (comments and extraneous whitespace removed for readability):

[daemon]
AutomaticLogin=*****
DefaultSession=gnome.desktop
AutomaticLoginEnable=true

[security]

[xdmcp]

[gui]

[greeter]
Use24Clock=no
DefaultWelcome=false
DefaultFace=
GlobalFaceDir=//

[chooser]

[debug]

[servers]
it looks pretty OK. (You might want to edit Your post to delete Your user name, especially if You are going to enable autologin ... ;))
try timed autologin ...

---

### Post by zika on 2009-01-30
do You have any stuff in /etc/rc.local ? I can not remember now but there was a time when some innocently looking stuff in that file was making autologin impossible for me ... I think some killing of Network manager or pulseaudio ... in themeantime I've learned better ways to deal with them and got used to pulseaudio ... ;)

---

### Post by sceo on 2009-01-30
Timed auto-login works, but then I get a gnome-keyring password prompt (network-manager-applet).  I know that's a separate issue.

There's nothing in rc.local (just "exit 0").

I do hate pulseaudio and tried to remove it, but I think ultimately I'm living with it installed but just setting my sound settings to use ALSA.  So I haven't really messed with the config.

I tried initially to start my network without nm-applet, but now like you said I'm just living with it.  Auto-login was actually what I did to "live with it" tho.

If I can get the network-manager-applet to stop prompting for my password, timed autologin is an acceptable solution for me (but of course leaves me wondering what I've done to upset the normal auto-login :) ).

---

### Post by zika on 2009-01-30
> **sceo said:**
> Timed auto-login works, but then I get a gnome-keyring password prompt (network-manager-applet).  I know that's a separate issue.

There's nothing in rc.local (just "exit 0").

I do hate pulseaudio and tried to remove it, but I think ultimately I'm living with it installed but just setting my sound settings to use ALSA.  So I haven't really messed with the config.

I tried initially to start my network without nm-applet, but now like you said I'm just living with it.  Auto-login was actually what I did to "live with it" tho.

If I can get the network-manager-applet to stop prompting for my password, timed autologin is an acceptable solution for me (but of course leaves me wondering what I've done to upset the normal auto-login :) ).
I've managed to exclude NetworkManager totally from my loop. it's installed but totally dormant on disk not entering memory ... :) to be clear, I use on my desktop only wired connection and static (local) address with willful excursions into dhcp just for fun ... :)
pulse audio was in that state of hibernation also but I figured that it is not so big problem so it was rehabilitated recently.
I'll roam through my installation-log-notebook to see what could help You ...

---

### Post by sceo on 2009-01-30
I have to admit, I've got something workable, but head-scratchable.  I just installed wicd (which seemed to be what most people did to stop network-manager-applet from bugging them), and it's pretty B.A.  I played with it before once, but it seems a lot more polished now.

Between timed login wicd, I now know that if I have a power outage, my BIOS will set my computer to 'last state' (which is always on), boot Ubuntu--after 10 seconds I will log in as me, and the network will be up and running.  I should be good!

---

### Post by campaigner444 on 2009-01-31
Will this method work in Xubuntu?

---

