---
title: "What would be the consequences of removing ivman? (I HATE CD AUTOPLAY)"
date: 2005-10-25
forum: Desktop Environments
---

### Post by gingermark on 2005-10-25
So, I go to rip my first CD since upgrading, insert the CD in my drive, and KsCD decides to play the CD, and Konqueror decides to open two windows to look at the CD's contents.

Annoying to say the least.

When my computer does something I didn't ask it to do I get very angry (sad, I know). It was one of the reasons I moved away from Windows. After searching the system settings for ages trying to find an option to turn off the autoplay, I found [this thread](http://www.ubuntuforums.org/showthread.php?t=70092) that said it was all down to a new program called ivman.

Can I just get rid of it, or will this affect other settings? I am in the habbit of putting DVDs in the drive that I'll watch 5 mins later when I'm ready to, as well as ripping my music so I have it all to hand, so the autoplay is very irritating, and I'm disappointed to see it has been introduced as a default option.

HELP! (Please :razz: )

---

### Post by goldenboy on 2005-10-25
I totally agree with gingermark!!

Autoplay was annoying with Windows, but at least one knew how to turn it off. This is different from Linux/KDE.

---

### Post by GeneralZod on 2005-10-25
If it's only autplay that bothers you, then you can disable it by editing /etc/ivman/IvmConfigActions.xml amd replacing:

```

<ivm:Match name="hal.volume.disc.type" value="cd_rom">
       <ivm:Match name="hal.volume.disc.has_audio" value="true">
           <ivm:Match name="hal.volume.disc.has_data" value="false">
               <ivm:Option name="exec" value="/usr/bin/kscd -s $hal.block.device$" />
           </ivm:Match>
       </ivm:Match>
   </ivm:Match>

```

with

```

<!--
<ivm:Match name="hal.volume.disc.type" value="cd_rom">
       <ivm:Match name="hal.volume.disc.has_audio" value="true">
           <ivm:Match name="hal.volume.disc.has_data" value="false">
               <ivm:Option name="exec" value="/usr/bin/kscd -s $hal.block.device$" />
           </ivm:Match>
       </ivm:Match>
   </ivm:Match>
-->

```

Upcoming releases of KDE will, I believe, make this more easily configurable via a GUI.

---

### Post by gingermark on 2005-10-25
Thankyou kindly.

---

### Post by skeezer65134 on 2005-12-17
Thank you so much on my end too. Every time I went to rip a CD with KAudioCreator, KsCD and Konqueror would open up the CD as well. Very annoying to say the least. Then the CD would not eject because KsCD was using it.

As an added hack, I checked the line that opens the CD in Konqueror as well...
```

<!-- open konqueror -->
   <ivm:Match name="hal.info.category" value="volume">
                <ivm:Option name="exec" value="MOUNT=$hal.block.device$; kfmclient openURL media:/${MOUNT#/*/}" />
   </ivm:Match>

```

Became
```

<!-- open konqueror -->
   <ivm:Match name="hal.info.category" value="volume">
<!-- Added to stop mounting of audio CDs -->
       <ivm:Match name="hal.volume.disc.has_audio" value="false">
           <ivm:Match name="hal.volume.disc.has_data" value="true">
                <ivm:Option name="exec" value="MOUNT=$hal.block.device$; kfmclient openURL media:/${MOUNT#/*/}" />
           </ivm:Match>
       </ivm:Match>
   </ivm:Match>

```
This way, if a CD is a mixed mode (audio and data, like many audio CDs are), it won't open them. This also should prevent other CDs that don't have data (like blank CDs) from opening up in Konqueror (another thing that was annoying me).

Again, much thanks on the ivman info!

---

### Post by wanger123 on 2005-12-30
Thanks guys, I think this should be stickied. This had been driving me nuts. I also stopped konqueror and kaffeine opening dvd's
wanger

---

### Post by aysiu on 2005-12-30
[QUOTE=wanger123]Thanks guys, I think this should be stickied.[/QUOTE] [It's in  customization: tips and tricks.](http://www.ubuntuforums.org/showthread.php?t=90457)

---

### Post by veloct on 2005-12-30
thanks aysiu

---

### Post by wanger123 on 2005-12-30
Yeah thanks aysiu, the problem is I have so many links I never know where to look for info lol :confused:

wanger

---

