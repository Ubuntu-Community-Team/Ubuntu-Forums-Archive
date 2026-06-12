---
title: "intel graphics, xgl, slow performance in gutsy"
date: 2007-10-28
forum: Desktop Effects &amp; Customization
---

### Post by bingoUV on 2007-10-28
Hi,
    Just migrated from fedora 7 to Gutsy. Beryl used to work fine in fedora with spectacular effects enabled, so my hardware seems capable enough (GMA X3000). But there are problems with desktop effects in gutsy.

1. Just after install, when I try to enable effects, I get an error "Desktop effects could not be enabled" without citing any reason. I learned by searching forums, that I need to install xserver-xgl. Then effects get enabled. Great !!!

2. Now, mplayer and vlc behave as if running on 286 processor. If I press 'f' to go fullscreen, it reacts after 2-3 seconds. mplayer also warns me that I do not have XF86-XVidModeExtension. Even alt-tabbing is slower than I would like.

3. I disable effects. But mplayer and vlc do not improve. 

4. I uninstall xgl. Desktop becomes as snappy as ever, but I am back to 1, no desktop effects.

Any solutions? I could not find many questions being answered for intel graphics. Sorry if this is already covered in some other thread. Thanks a lot.

---

### Post by bingoUV on 2007-10-28
OK, found the solution. I have to somehow force AIGLX. The solution is mainly due to Jigish Gohil a.k.a cyberorg, his Oct 24, 2007 entry in [http://planet.compiz-fusion.org/](http://planet.compiz-fusion.org/). Except that he seems to recommend this for ATI, but for me it has worked for intel graphics also with minor tweaks.

1. Edit xorg.conf (/etc/X11/xorg.conf) : add the sections

```

Section "ServerFlags"
    Option "AIGLX" "true"
EndSection

Section "Extensions"
    Option "Composite" "true"
EndSection

```

2. aiglx seems to be blacklisted for some reason, so do this
```

echo SKIP_CHECKS=yes > ~/.config/compiz/compiz-manager

```

3. log in, and log out. If still desktop effects not enabled, try once more System -> Preferences -> Appearance -> Visual Effects

4. Use x11 output for video playback.
mplayer :
```

echo vo=x11 >> ~/.mplayer/config
echo zoom=yes >> ~/.mplayer/config

```
vlc : Settings -> Preferences -> Video -> Output Modules -> X11 video output

Please put this, or a better HOWTO somewhere more visible. Otherwise compiz is unusable on intel graphics. 

thanks

---

### Post by varkey on 2007-10-28
Thanks. It works but the video quality in VLC is not good. I did make it X11 but still I find the video bad. Any ideas?

---

### Post by bingoUV on 2007-10-28
Is it bad only in vlc? How is it in mplayer?

---

### Post by varkey on 2007-11-02
The prob is only there in VLC! Mplayer its fine

---

