---
title: "Firefox freezes on pages with flash"
date: 2009-06-02
forum: General Help
---

### Post by chmacka on 2009-06-02
Firefox freezes on pages pages with flash (most of them). For example, when I want to upload pictures using ImageBam, when I click Upload button it freezes and goes black. I wait for a minute or two and when nothing happens I have to kill it (with system monitor). First I thought it was because of Compiz. I got the Compiz-Switch, but there is no change when I turn the Compiz off. It happens **ONLY on Ubuntu**, not on Windows.

I have the latest Flash Player and the latest FF.

---

### Post by whoop on 2009-06-02
Are you running 64 bit?
```

uname -a

```

---

### Post by wpshooter on 2009-06-02
You say you have the latest Flash, how / from where did you install it ?

---

### Post by chmacka on 2009-06-02
> **whoop said:**
> Are you running 64 bit?
```

uname -a

```
2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

No, but I have x64 processor.

@**[wpshooter]("http://ubuntuforums.org/member.php?u=41796")**: From adobe's website ([http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)).

---

### Post by philinux on 2009-06-02
> **chmacka said:**
> Firefox freezes on pages pages with flash (most of them). For example, when I want to upload pictures using ImageBam, when I click Upload button it freezes and goes black. I wait for a minute or two and when nothing happens I have to kill it (with system monitor). First I thought it was because of Compiz. I got the Compiz-Switch, but there is no change when I turn the Compiz off. It happens **ONLY on Ubuntu**, not on Windows.

I have the latest Flash Player and the latest FF.

Close firefox. Run it from a terminal. The command is firefox.
Do your upload again and see if there are any errors reported in the terminal.

You could try the addon flashblock.

---

### Post by chmacka on 2009-06-02
I tried again and this time this massage poped up:

*A script in this movie is causing Adobe Flash Player 10 to run slowly. If it continues to run, your computer may become unresponsive. Do you want to abort the script?*

I'll now try from the terminal.

**EDIT**: Terminal didn't report any errors.

---

### Post by wpshooter on 2009-06-02
Have you tried re-downloading the tar version of AdobeFlash for Linux and re-installing.  I think you are supposed to install it to /usr/lib/firefox-3.0.10 (but don't quote me on that, since I am not at my Ubuntu computer).

---

### Post by chmacka on 2009-06-02
I download the tar.gz for linux, but I don't know how to install it (I'm new to Linux).

I found this: [http://www.cyberciti.biz/faq/install-tarballs/](http://www.cyberciti.biz/faq/install-tarballs/)

I did everything as they said, but there is no ./config folder (there are only flashplayer-installer and libflashplayer.so files).

---

### Post by wpshooter on 2009-06-02
Once you have extracted the tar file, which it sounds like you have done then the terminal command to do the installation would be:

first move to the directory where you have the flashplayer-installer file (and preferable that would be at the root of /home - actually it would be in the flashplayer directory just under /home) and then issue:

sudo ./flashplayer-installer

make sure you have you browser closed before issuing the command.

---

### Post by chmacka on 2009-06-02
O. K. I did it, but nothing has changed. When I click upload, instead of seeing the progress bar firefox freezes (it seems to happen everywhere were I'm supposed to see a progress bar while uploading - imagebam, mediafire...), but the image gets uploaded in the end.

---

### Post by Wobblybob on 2009-06-02
I had crash issues on flash sites untill I removed the flash plugins and installed the .deb from the adobe site, see my post here, it worked for me on 2 pc both having Firefox crashing on flash. 

[[COLOR="RoyalBlue"]myubuntublog.wordpress.com[/COLOR]]("http://myubuntublog.wordpress.com/2009/05/25/firefox-crashing-on-flash-sites/")

Martin

---

### Post by elliotbeken on 2009-06-02
i was trawling through some torrent files and i came across a download thay you burn to disk and it sets up simple things like flash jave and even the repositories....... easy if you have no experience or lazy like me :P

---

### Post by chmacka on 2009-06-02
> **Wobblybob said:**
> I had crash issues on flash sites untill I removed the flash plugins and installed the .deb from the adobe site, see my post here, it worked for me on 2 pc both having Firefox crashing on flash. 

[[COLOR=RoyalBlue]myubuntublog.wordpress.com[/COLOR]]("http://myubuntublog.wordpress.com/2009/05/25/firefox-crashing-on-flash-sites/")

Martin
I did everything as you said, but before installing flash player from .deb file I checked YouTube to see if it will still play. And it did. I found in Firefox Plugins that there is Shockwave Flash installed. Could this be the problem. I don't know how to uninstall Shockwave plugin ([http://ubuntuforums.org/showthread.php?t=1168959](http://ubuntuforums.org/showthread.php?t=1168959) <<< this isn't working for me, cause I don't have **swfdec-mozilla** installed).

**EDIT: **I uninstalled it (deleted file from FF plugins directory). I installed Adobe Flash Player from deb package but the problem is still there. Has anyone of you tried to upload something with ImageBam or Mediafire so I can know if this is only happening to me or...

---

### Post by garuhhh on 2009-06-03
yes,i'm having the same issues. when i upload files in mediafire, firefox freezes (it turns gray) until all the files have been uploaded (atleast it's uploading). But i can't use firefox while it's uploading, which is burdensome.

I've had this issue since ubuntu 8.04. i'm now using 9.04.

---

