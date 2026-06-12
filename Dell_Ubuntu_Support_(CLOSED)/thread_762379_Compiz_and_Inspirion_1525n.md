---
title: "Compiz and Inspirion 1525n"
date: 2008-04-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tylersontag on 2008-04-22
Just got my new Dell this morning and i'm about done getting it all tweaked out the way i like it and im down to one bug.

This seems to be a known issue but im hoping theres a work around.   Whenever Compiz is running, all the screensavers seem to flicker and not render properly.  Embedded video seems to work alright, i haven't moved enough movie files to check them out.  my video card is the embedded intel GM965.  anyone know any tweaks that will help?

---

### Post by sdennie on 2008-04-22
You could try setting/unsetting Unredirected Fullscreen Windows in System->Preferences->Advanced Desktop Effects (it's on the first tab).  I don't know if this will help but, it's something to try.  If you don't have that menu option, you could install it via:

```

sudo apt-get install compizconfig-settings-manager

```

---

### Post by notwen on 2008-04-22
Check out this [link]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility") to enable Compiz-Fusion w/ your Intel chipset.  The X3100 chipset is actually blacklisted by Compiz.  You can bypass this blacklisting, but this can affect your ability to playback video.  Some users have been able to correct their video playback by changing the video output to 'No Xv'.  

I have a Inspiron 1420n w/ the Intel X3100 chipset and am using Compiz daily w/ no issues, including video playback.  Post back if you have any issues. =]

---

### Post by tylersontag on 2008-04-22
I have compiz running, its just i think i'm running into the video playback bugs that i've heard some people complain about.  How do i set the playback mode to No Xv?  Is that in the xorg config file?

EDIT: Changed it to no Xv in the video settings, no apparent change.  if i turn off compiz effects video playback works.  This seems to be widely known that this is a problem, i was just wondering if anyone knew a work around?

---

### Post by odin1965 on 2008-04-23
> **notwen said:**
> Check out this [link]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility") to enable Compiz-Fusion w/ your Intel chipset.  The X3100 chipset is actually blacklisted by Compiz.  You can bypass this blacklisting, but this can affect your ability to playback video.  

I've been using the Hardy beta on my 1520 with the intel 965 and video and compiz both work by default. I don't think the 965 is blacklisted with the newer compiz and intel driver in Hardy.

---

### Post by notwen on 2008-04-24
> **odin1965 said:**
> I've been using the Hardy beta on my 1520 with the intel 965 and video and compiz both work by default. I don't think the 965 is blacklisted with the newer compiz and intel driver in Hardy.

Yes, the Compiz-Fusion team was able to remove the blacklisting for the X3100 chipset in Hardy.  I'm glad as I don't generally approve of bypassing blacklisted hardware, but I myself use Expo religiously.  =]  Looking forward to when Dell releases their custom Hardy image.

---

