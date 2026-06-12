---
title: "Compiz not working after 11.04 upgrade"
date: 2011-09-16
forum: Desktop Environments
---

### Post by motorcity909 on 2011-09-16
Hi there

So I finally upgraded to 11.04 today.  I knew my machine wouldn't be powerful enough to run Unity as I tried a live CD before.

The upgrade went okay and it duly advised me I couldn't run Unity.  

However, I can't get Compiz to work.  I've disabled the Unity plugin and reenabled my desktop cube etc.  I logged out and back in, this time as Ubuntu Classic but still nothing I do in Compiz is having any effect - no cube, no wobbly windows.

Also I had a nice transparency on my titlebars and that seems to have gone now - I set that using the Config Editor then apps>gwd - screen screengrab.

Any help on getting back my eye candy will be much appreciated.

Thanks
Dave

---

### Post by raja.genupula on 2011-09-16
[http://amazingubuntucube.blogspot.com/2011/06/how-to-get-cube-working-in-ubuntu-1104.html#comments/](http://amazingubuntucube.blogspot.com/2011/06/how-to-get-cube-working-in-ubuntu-1104.html#comments/)


go with this all the best

---

### Post by motorcity909 on 2011-09-16
Thanks Raja.

Unfortunately before I saw your reply, I had a brainwave that the problem was down to Nvida drivers as Ubuntu was showing that Nvida driver 173 was installed but not in use.

So I ran sudo apt-get install nvidia current

This ran and then I rebooted.  Now my PC won't boot up normally.  Instead I have to enter my user name and password on a command line, then go 'sudo reboot' and then select recovery mode and choose 'failsafeX' to get to my normal desktop.

Now if I run the Additional Drivers tool it shows the attached.

Can I simply activate that driver and reboot?

Fixing this is beyond my level of knowledge so any help is really appreciated.  I really should leave things alone and wait for these forums to answer!

(I'm typing this on a friends laptop that I've got at the moment)

---

### Post by motorcity909 on 2011-09-16
Quick update.  When logging into recovery mode I saw there was an option to fix the graphics problem, so I clicked that and it told me a new configuration had been created.  I have since rebooted and it goes straight to my graphical desktop now, no command line, thankfully!

I then looked at the Nvidia settings and it showed the attached screen1.

I then ran Additional Drivers and activated the recommended 173 driver.  Another reboot and the Nvidia settings are now there - see screen2 attached.

So, I *think *I'm back where I was when I started this thread - looking to fix Compiz, so now I'll take a look at the link Raja posted.

---

### Post by motorcity909 on 2011-09-16
Sorry, returning to the Nvida thing.  If I run Additional Drivers, it's still saying that driver 173 is activated but not in use.

Also, I've noticed that if I go into System>Preferences>Appearance, there is no fourth tab anymore for desktop effects.

I really hope someone can help me.

Ever wish you hadn't upgraded on a happy-working-like-clockwork machine?

---

### Post by raja.genupula on 2011-09-16
hey man 
i am not much aware of those drivers.
but i can say one thing that you said after installing those things only you got that problem right ?
then why dont you give a try by removing all those things from software center or synaptic  to get it back to its previous condition

---

### Post by motorcity909 on 2011-09-16
Hi Raja

I only got these problems after upgrading from 10.10 to 11.04.  After that Compiz wasn't working properly.  I then tried to update the Nvidia river and ended up not being able to boot my pc, apart from in recovery mode.

I've fixed that now by activating the Nvidia driver 173 so it boots fine now.

However, Compiz is definitely not working/  I've ven tried to roll back the a previous Compiz as per this - [http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html) - and that hasn't worked.  Nor do the solutions in the link you posted earlier.

I've seen some other threads saying people are having similar issues, some blaming  11.04 and Compiz not playing nice, some blaming Nvidia drivers.  Various solutions are offered then.

One of them was to use Fusion-icon which allows for easier switching between Compiz and Metacity.  Strangely enough if I switched to Metacity, nothing much happened but if  switched to Compiz from within Fusion-icon, all my window decoration (like titlebars) disappeared.

It's like I was using ***both*** Metacity and Compiz for window decoration!  is this even possible?  How did I get there?

Overall. I'm missing my nice transparent titlebars the most, so wonder if I should completely remove Compiz and Emerald, and just use Metacity for window decoration.

Or maybe just roll the whole thing back to 10.10 ;)

Long post I know.  Any help will be much appreciated.

Dave

---

### Post by wildmanne39 on 2011-09-16
Hi, open synaptic and uninstall the nvidia driver you installed then activate the 173 driver it works great for me.

Then reboot. Do not  worry about the message that says it is not in use that is just a bug and if you activated it then it is being used. 

Also use the link my friend Raja gave you to set up the cube and effects, and be sure to revert to the previous version of compiz for classic mode as stated at the link before you setup the cube and effects.

The appearance tab was removed you can set up effects and everything with compiz.
Thank you

---

### Post by motorcity909 on 2011-09-16
Thanks Wildmanne

I seem to have two Nvidia drivers according to Synaptic - see attached.  Do I remove the 270 version?

Thanks
Dave

---

### Post by wildmanne39 on 2011-09-16
Hi, that is what happens when you install from another source you end up with two or more.

Yes uninstall the 270.
Thank you

---

### Post by motorcity909 on 2011-09-16
I've removed the Nvidia 270 driver.  Rebooted.  Followed the Compiz instructions (I'd already rolled back to an older version).  Rebooted.  Still nothing.  No cube, no wobbly windows.

This is v.frustrating and makes me wish I'd never clicked on that upgrade button this morning.

I'll settle for my transparent title bars back over Compiz cubes!

I know it's only eye-candy and I have a functioning machine but it was nice to have it there. :(

---

### Post by wildmanne39 on 2011-09-16
Hi, it may be that your video card is no long supported in natty.

Please run these commands and post the results here:
```
lspci | grep VGA
```
```
/usr/lib/nux/unity_support_test -p
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by motorcity909 on 2011-09-16
Curiouser and curiouser.  Before I saw your reply I'd also run 

```
metacity --replace &
```

which didn't do anything, followed by 

```
compiz --replace &
```

after which the screen flickered and my transparent titlebars were back!!

And Compiz is working again!!!  Spinny cube, wobbly windows, magic lamp - all back.

Oh Happy Day!

Will still run your suggested commands and post the output in a while.

Thanks for all your help
Dave

---

### Post by wildmanne39 on 2011-09-16
Hi, that is great I was going to suggest compiz --replace next.
Thank you

---

### Post by motorcity909 on 2011-09-16
Here for info are the outputs of your three suggested commands - 

```
01:00.0 VGA compatible controller: nVidia Corporation NV36.2 [GeForce FX 5700] (rev a1)
```

```
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce FX 5700/AGP/SSE2/3DNOW!
OpenGL version string:  2.1.2 NVIDIA 173.14.30

Not software rendered:    yes
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no
```

and 

```
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
vboxnetadp             13348  0 
ppdev                  12849  0 
vboxnetflt             27855  0 
vboxdrv               238410  2 vboxnetadp,vboxnetflt
rfcomm                 38125  12 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
sco                    17827  2 
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
bnep                   17785  2 
snd_seq_midi           13132  0 
l2cap                  48656  16 rfcomm,bnep
nvidia               7098106  44 
snd_rawmidi            25269  1 snd_seq_midi
btusb                  18160  2 
snd_seq_midi_event     14475  1 snd_seq_midi
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                 12872  0 
soundcore              12600  1 snd
shpchp                 32345  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
i2c_nforce2            12906  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
usb_storage            43946  1 
crc_itu_t              12627  1 firewire_core
sata_nv                23176  0 
floppy                 60032  0 
uas                    17676  0 
forcedeth              58190  0 
pata_amd               13762  2 
```

I knew my modest machine with it's old-ish graphic cards wouldn;t support Unity - not too bothered, am happy with Classic Gnome.

I'm just pleased to have my eye-candy back!

Thanks for all your help, have a great weekend.

Dave

---

### Post by wildmanne39 on 2011-09-16
Hi, it looks good, you have a great weekend too.
Thank you

---

### Post by motorcity909 on 2011-09-16
Back again.  Just did a reboot to ensure all was okay....all gone again, no transparent titlebars, no Compiz effects.

How do I ensure it remains on reboot/startup?

---

### Post by wildmanne39 on 2011-09-16
Hi, give me a few minutes to research it and hopefully I will find the answer.
Thank you

---

### Post by wildmanne39 on 2011-09-16
Hi, open ccsm and make sure session management is enabled it has to be to save settings.
Thank you

---

### Post by motorcity909 on 2011-09-16
Hi

Just had a look and it is enabled.  Should I do the 

metacity --replace & 

followed by 

compiz --replace &

again and check session management is still enabled after that?

Thanks
Dave

---

### Post by wildmanne39 on 2011-09-16
Hi, you can give it a try and I will do more research.
Thank you

---

### Post by motorcity909 on 2011-09-16
Just ran the two commands and all the eye candy is back, including one element that hadn't returned before, which was a picture I had as a background behind my spinning cube.

Opening CCSM, the sssion management is enabled - see screengrab.

Dare I try a reboot???

---

### Post by wildmanne39 on 2011-09-16
Hi, if you continue to have trouble you can run this command but I am not sure it will fix the problem.

These commands to reset all the settings in compiz.
```
gconftool-2 --recursive-unset /apps/compiz
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
```
it will reset your compiz settings but in the process it might make you able to retain your settings, but I just do not know that for a fact.
Thank you

---

### Post by motorcity909 on 2011-09-16
I'm going to see what happens on a reboot first then if no luck will try those three commands.

If that doesn't work is there anyway I could run a script (say from a desktop icon) to run those two commands (metacity --replace & *and *compiz --replace &) quickly without having to type/paste them in a terminal every day?

---

### Post by motorcity909 on 2011-09-16
So, I did a reboot and the eye candy was gone again, so I restored it with metacity --replace & *and *compiz --replace &.

The I ran your three suggested commands.  Eye candy still there albeit without my particular settings.

Next I rebooted and again the eye candy was gone.

Hey ho!  Not sure this is going to be fixed.  Guess I'll just have to get used to running ```
metacity --replace &
``` [I]
and 

[/I]```
*compiz --replace &*
```each day.  Doesn't take long I suppose and this Compiz problem doesn't prevent me doing 'real stuff' with the machine!

Hopefully I'll be getting a new PC in the next 6 months which will be more powerful but I'll have to think about whether I stick with Ubuntu 11.04/11.10/12.04 given that I don't think I'd like Unity but do love my Compiz.  Maybe Mint beckons??  We shall see.

Wildmann, I want to thank you for all your help today, I've really appreciated it and hope you get your membership.

---

### Post by wildmanne39 on 2011-09-16
Hi, your very welcome! I believe those commands can be put into a little script to make it do it at boot but I am not good with scripts so I can not advise on it.
Thank you

---

### Post by wildmanne39 on 2011-09-16
Hi, you can have a look at this link and see if it applies.
[http://ubuntuforums.org/showthread.php?t=1787391](http://ubuntuforums.org/showthread.php?t=1787391)
Thank you

---

### Post by gwi on 2011-09-18
I am still on 10.10, and as of today am having the same problem. The problem only occurs on one of the three user accounts on my system. The other two are not affected.

Running metacity --replace &, followed by compiz --replace & makes the window decorations return, until I log off and log on again.
I checked CCSM. Session management is enabled.

Any ideas (or better: solutions) are welcome. This is very annoying. Even alt-tab isn't working when the window decorations are gone.

---

### Post by wildmanne39 on 2011-09-18
Hi, it sounds like your configuration files got messed up with that one user account but I am not sure how to fix it, I will ask someone with more experience to take a look, also you might consider creating a new user account for that person as a last resort.

Also did you try what was mentioned in post 27 at the link provided?
Thank you

---

### Post by Copper Bezel on 2011-09-18
> Ever wish you hadn't upgraded on a happy-working-like-clockwork machine?
Yes. = )

You should be able to set Compiz as the default window manager by running gconf-editor and setting it in desktop/gnome/session/required_components. Although it's messier this way, you can also create a Startup Application from System > Preferences in the main menu and simply make it compiz --replace.

Edit: gwi, I don't remember the exact location of the key in 10.10, as it's changed in 11.04, but it's possible that you have the same problem, with the default window manager set incorrectly. Check in gconf-editor, and if nothing else works, just create a Startup Applications entry as well.

---

### Post by wildmanne39 on 2011-09-18
Hi, sorry I am so late getting back to you, I was in the hospital 3 days last week and I am still recovering, so I am having to take breaks and take medicine and such that requires my time.

Copper Bezel is correct, Krytarik told me the same thing and I was going to post it here, just a little slow.
Thank you

---

### Post by gwi on 2011-09-18
> **wildmanne39 said:**
> Hi, it sounds like your configuration files got messed up with that one user account but I am not sure how to fix it, I will ask someone with more experience to take a look, also you might consider creating a new user account for that person as a last resort.

Also did you try what was mentioned in post 27 at the link provided?
Thank you
I didn't try that, because it looks like another situation. I never used or installed Unity. I am still on 10.10.
Looking at the configuration files, once we know where they are, looks like the way to go.

> **Copper Bezel said:**
> Yes. = )

You should be able to set Compiz as the default window manager by running gconf-editor and setting it in desktop/gnome/session/required_components. Although it's messier this way, you can also create a Startup Application from System > Preferences in the main menu and simply make it compiz --replace.

Edit: gwi, I don't remember the exact location of the key in 10.10, as it's changed in 11.04, but it's possible that you have the same problem, with the default window manager set incorrectly. Check in gconf-editor, and if nothing else works, just create a Startup Applications entry as well.
Creating a startup application is just a workaround, I am hoping for a solution.
The key desktop/gnome/session/required_components contains the setting windowmanager=gnome-wm.
This is the same value as for one of the unaffected accounts.

---

### Post by Copper Bezel on 2011-09-18
Right, but gnome-wm refers to Gnome's default window manager. There's a separate key to set that in 10.10, but I'm not using 10.10, so I can't check it. You can either change gnome-wm to compiz or find that other key.

Edit: Here we go; gnome-wm's man page.

> DESCRIPTION
       The  gnome-wm program starts the window manager configured by
       the user. If the user has not chosen a window manager it will
       launch a GNOME compliant window manager.

       The  user  [B]can  define  his preferred window manager with the
       /desktop/gnome/session/required_components/windowmanager
       GConf  key. [/B] The  value of this key should be the name of the
       desktop file of  the  desired  window  manager,  without  its
       .desktop  extension.  If  this  key  is set to gnome-wm, then
       gnome-wm will simply look for an appropriate window  manager.
       The  user can also override the selection of a window manager
       by setting the WINDOW_MANAGER environment variable.

       If the --default-wm option is used, gnome-wm will use WINDOW&#8208;
       MANAGER  as  window manager if the WINDOW_MANAGER environment
       variable  is  not  set   and   if   the   /desktop/gnome/ses&#8208;
       sion/required_components/windowmanager  GConf  key  does  not
       define a specific window manager, or if the configured window
       manager cannot be found.

       The  --sm-client-id  option  is  translated to an appropriate
       option depending on which window manager will be started.

---

### Post by gwi on 2011-09-19
I removed the directory .gconf/compiz, and restored from a backup (made when everything was ok). Doesn't solve the problem.
Besides running "compiz --replace &" (or metacity --replace &) changing the display preferences also restores the window decoration ... until the next logon. So the problem is also there if compiz is disabled.

And the other two user accounts are still not affected.

BTW: the value of gconf/desktop/gnome/session/required_components/windowmanager is now "compiz", but that also doesn't change a thing.

---

### Post by Copper Bezel on 2011-09-19
Oh - I missed that you'd said that the window decorations are completely absent; it's definitely a different problem from the OP's and nothing to do with the default WM, and something is causing Compiz to crash on startup. 

Since you have a backup of your profile, could you try resetting Compiz completely to defaults in gconf? (Check that this is the right folder name in gconf-editor - again, I'm not running 10.10, and the locations have changed.)

```
gconftool-2 --recursive-unset /apps/compiz
```

---

### Post by gwi on 2011-09-20
The compiz settings are in /apps/compiz.

But again ... no changes.

---

