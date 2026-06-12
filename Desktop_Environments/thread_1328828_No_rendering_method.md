---
title: "No rendering method?"
date: 2009-11-16
forum: Desktop Environments
---

### Post by dirtlamb5 on 2009-11-16
Hey I've been using Karmic 32-bit since early November and compiz and everything was working fine. But yesterday something went wrong so I restarted X and now compiz doesn't work at all. I can't even enable desktop effects. I downloaded compiz-check and this is the result:

```

billy@billy-desktop:~$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

```Here's some info about my graphics card:

```

billy@billy-desktop:~$ lspci -v | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)

```Is there any way I can reinstall Xgl without having to completely reinstall Ubuntu?

---

### Post by dirtlamb5 on 2009-11-17
...bump...I'd really like to not have to reinstall Ubuntu...

---

### Post by Musicologynut85 on 2009-11-25
I'm having the same problem in Jaunty... everything was fine until I hooked up a second monitor and ran an extended desktop. When I went back to just my laptop screen, compiz stopped working.

Same graphics card, same output.

---

### Post by peih on 2009-12-02
I have other graphic card, but the same problem.
Here is output from compiz-check :

Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Mobility Radeon HD 3400 Series
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

I also tried to disable the fglrx driver, and run the compiz-check, and here is the new output :
Gathering information about your system...

 Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Mobility Radeon HD 3400 Series
 Driver in use: radeon
 Rendering method: AIGLX
......
......

Someone could help !?

---

### Post by misaelrod on 2010-01-10
anyone find the answer for this? I'm having the same issue

---

### Post by bonevg on 2010-01-28
same problem.

But this happens after upgrade from prev version of Ubuntu (in my case from Hardy)
Why I think so?
Because with the same model LapTop and fresh install it work  fine.

Now, If some1 know a way to reset or reinstall the AIGLX thingie which I believe is the rendering that should be used - shoot me.

I found u can enable it from Xorg. But hey - I don`t have /etc/xorg.conf in use anymore after I jumped to 9.10... I used to have when it was hardy.
So I suspect "the new" X-server use another approach to configure itself. (obviously not quite intelligent as they probably anticipated)

any thoughts ?


EDIT:

"dpkg-reconfigure xserver-xorg" helps NOT.

---

### Post by andrea000 on 2010-01-30
Try running compiz in the terminal
Applications->accessories->terminal

> compiz

Your card may be blacklisted

---

### Post by bonevg on 2010-02-01
> **andrea000 said:**
> Try running compiz in the terminal
Applications->accessories->terminal



Your card may be blacklisted

If you are asking me to check if mine is blacklisted - I don`t believe so.
As I mentioned before in my case the problem appears to be only after upgrade from prev version of Ubuntu that uses the old X-server.

Here are some infos:
```

uname -a
Linux bonev-laptop 2.6.31-18-generic #55-Ubuntu SMP Fri Jan 8 14:55:26 UTC 2010 i686 GNU/Linux

lspci
Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

lsmod (with attention to the vga)
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915


```

I don't refuse the possibility that I still might be wrong, but as I said - On the same hardware - clean install appears to do the job - meaning 3d craps, compiz and rendering are working perfectly.

---

### Post by andrea000 on 2010-02-01
I was thinking compiz may have blacklisted your
video card but i am not seeing it in your post.
You can look and see for sure if you would like
type this into the terminal

> sudo gedit /usr/bin/compiz

Then you will need to find were is says blacklisted
based on the pci ids and look and see if your video
card is listed in there i don't think it will be when
you run compiz from the terminal it should show
any errors that compiz is having.

---

### Post by bonevg on 2010-02-04
> **andrea000 said:**
> I was thinking compiz may have blacklisted your
video card but i am not seeing it in your post.
You can look and see for sure if you would like
type this into the terminal



Then you will need to find were is says blacklisted
based on the pci ids and look and see if your video
card is listed in there i don't think it will be when
you run compiz from the terminal it should show
any errors that compiz is having.

No. It is not blacklisted. And it can't be if the clean installation work fine as I mentioned before.
I believe that is the part you wanted me to check.

```
# Driver whitelist
WHITELIST="nvidia intel ati radeon radeonhd i810 fglrx"

# blacklist based on the pci ids 
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
#T="$T 8086:2a02 " # Intel GM965
T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)
BLACKLIST_PCIIDS="$T"
unset T

```

After I reviewed that script you pointed /usr/bin/compiz, I've noticed that it uses xvinfo and greping in the output for "Xgl".
I have checked xvinfo output myself and there isn't "Xgl" string.
So I suspect in this particular case I am missing the Xgl which happens to be the rendering.

And the direct questions I have:
* Is there a packet I can install to satisfy the lack of rendering?
* Or if that Xgl (as it is said: "is distributed with the xserver") is just not started for some reason. Where in the holy tree of files and directories it should be, so I can manually go there VIM the freakin' config and tell em to start doing whatever it is supposed to?

---

### Post by andrea000 on 2010-02-04
looks like the gm965 driver is blacklisted.

> uname -a
Linux bonev-laptop 2.6.31-18-generic #55-Ubuntu SMP Fri Jan 8 14:55:26 UTC 2010 i686 GNU/Linux

lspci
Display controller: [COLOR="Red"]Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller[/COLOR] (rev 0c)

lsmod (with attention to the vga)
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915



> **# blacklist based on the pci ids **
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12" **[COLOR="Red"]# intel 965[/COLOR]**
**#T="$T 8086:2a02 " [COLOR="Red"]# Intel GM965[/COLOR]**
T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)
BLACKLIST_PCIIDS="$T"
unset T

Compiz blacklist drivers all the time if it didn't worked after
a update i would say the update blacklisted it.So just
take the **#** off it and save to unblacklist it.

---

### Post by bonevg on 2010-02-05
Ok lets get this right.
I've followed your suggestions.

1. Removed the "#" comments => saved => even rebooted the whole OS - no effect
2. I put all the "#" comments => saved => rebooted again - no effect
3. tbh I almost got into this compiz thing and even reinstalled after PURGING all the compiz components that I found via dpkg --list | grep compiz

Now on the subject. Why are you insisting on blaming compiz blacklisting my VGA, while I don't need compiz AT ALL to run applications with 3d acceleration..?

For example if I run glxinfo or glxgears it also does not work.

```

# glxgears
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

```

Are you saying compiz is ruling somehow my video settings ?
Imagine if I uninstall THE compiz. Then what? my video will stop running 3Ds ?
C'mooon get me smth better :P

I also tried this:
1) killed gdm
2) reinstalled xorg-xserver-video-intel (deps xorg-xserver-video-all)
Also w/o effect.

Got other ideas ?

---

### Post by bonevg on 2010-02-05
ok. Problem solved.
One guy seems also to had this problem and he just removed some unused video drivers he had additionally installed, which solved his problem.. he mentioned also it was unlikely this is issue.. but just happens it also solved my problem as well.

I had other drivers installed that seemed to interfere with the used one.

..fglrx for ATI and Nvidia-glx-173 or smth like that.. and they seemed to have had installed some kernel modules as well..
After removing them - glxgears, glxheads, glxinfo and every other 3D crap worked including even google-earth..

So compiz had nothing to do with my 3D problems.

Oh wait a sec. You may be pleased to know compiz worked too.
8)
I`m seriously considering using again FreeBSD as costless solution.. to be honest Linux is turning into complete mess.

---

### Post by bonevg on 2010-02-08
However I want to thank you for the effort and the time you put into this, Andrea. I would probably never ever look into the way compiz check for rendering which gave me some directions to think of.

Thx again.
I advice the rest that posted for lack of rendering to check if they have additional unused drivers installed and remove them.
Won't hurt I guess :)

---

### Post by fferreira on 2010-02-09
Thank you for reporting... I just had the same problem.. and it solved... I'd never figure it out.

---

### Post by bmdavis on 2010-03-02
Same issue for me -  studio xps with ati 3670.

compiz works great for other things, cube and special effects.  GLXgears is fine. 

It's just the minimizing of windows and resizing that is extremely slow (alt tab switching as well).  I get the same issues with compiz check (like it's not there!)

any updates?...

---

### Post by bonevg on 2010-03-09
> **bmdavis said:**
> Same issue for me -  studio xps with ati 3670.

compiz works great for other things, cube and special effects.  GLXgears is fine. 

It's just the minimizing of windows and resizing that is extremely slow (alt tab switching as well).  I get the same issues with compiz check (like it's not there!)

any updates?...

Review the whole thread again carefully.

---

### Post by atentik on 2010-03-12
How did you solve this problem? My matlab graphics is not working and from what I gathered, it has something to do with glxinfo. This is the error I got when I typed glxinfo in the terminal.
>  glxinfo
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  16
  Current serial number in output stream:  16


---

