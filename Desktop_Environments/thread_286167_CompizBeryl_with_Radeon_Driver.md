---
title: "Compiz/Beryl with Radeon Driver"
date: 2006-10-27
forum: Desktop Environments
---

### Post by Synikk on 2006-10-27
I've got an ATI Radeon Mobility 7500 (identified as "Radeon Mobility M7 LW" in xorg.conf) running with the open source "radeon" driver. I get the impression from reading several posts on the forum that it's not possible to get Compiz/Beryl running with this card/driver. Is that the case?

---

### Post by Synikk on 2006-10-27
Anyone?

Maybe I should've posted this in a more active part of the forum...

---

### Post by sbentzen on 2006-10-27
> **Synikk said:**
> I've got an ATI Radeon Mobility 7500 (identified as "Radeon Mobility M7 LW" in xorg.conf) running with the open source "radeon" driver. I get the impression from reading several posts on the forum that it's not possible to get Compiz/Beryl running with this card/driver. Is that the case?

sorry, i don't think you'd get it running unless you use aiglx, not xgl because aiglx is indirect rendering and xgl is a system hog, though i think you might be able to work something out.

---

### Post by michael117 on 2006-10-27
It is completely possible and you do not need AIGLX. I have an ATI Radeon 9800 pro in my desktop now and I had Beryl+XGL running just fine until something randomly stopped working (I think I might have not correctly updated my driver). You will first need to get the ATI driver (named fglrx) from the repo, configure xorg.conf to use fglrx, and make sure it has direct rendering enabled by typing glxinfo into the console and seeing if it says "direct rendering: yes". If it says that, you are good to go and start setting it up. I went on to follow a guide on compiz.info which became beryl-project.org.

Just to clear some things up... The ATI driver is not actually open source because ATI will only provide closed source binaries. Also, I wouldn't say that there is any real decrease in performance from what I've noticed on my 3 year old PC. I was actually surprised by the smooth performance for how bloated you would expect an alpha piece of software to be, but it still has its bugs and you will definitely notice a few when using it. I must say, though, that I've found myself using Ubuntu in a different manner when it is working properly and taking advantage of virtual desktops because it is so easy to switch between them. Good luck on installing it!

---

### Post by Synikk on 2006-10-28
> **michael117 said:**
> It is completely possible and you do not need AIGLX. I have an ATI Radeon 9800 pro in my desktop now and I had Beryl+XGL running just fine until something randomly stopped working (I think I might have not correctly updated my driver). You will first need to get the ATI driver (named fglrx) from the repo, configure xorg.conf to use fglrx, and make sure it has direct rendering enabled by typing glxinfo into the console and seeing if it says "direct rendering: yes". If it says that, you are good to go and start setting it up. I went on to follow a guide on compiz.info which became beryl-project.org.

Just to clear some things up... The ATI driver is not actually open source because ATI will only provide closed source binaries. Also, I wouldn't say that there is any real decrease in performance from what I've noticed on my 3 year old PC. I was actually surprised by the smooth performance for how bloated you would expect an alpha piece of software to be, but it still has its bugs and you will definitely notice a few when using it. I must say, though, that I've found myself using Ubuntu in a different manner when it is working properly and taking advantage of virtual desktops because it is so easy to switch between them. Good luck on installing it!

Well the only problem is the fglrx driver isn't supported by my card, hence why I'm using the "radeon" driver (and not the generic "ati" driver).

I'm guessing very few people are running a card with the "radeon" driver, and even fewer are running Compiz/Beryl with it (if any!) But if someone running Compiz/Beryl on the "radeon" driver on an older ATI card does read this, point me in the direction of a tutorial, please!

---

### Post by michael117 on 2006-10-28
Ah, I see... the ATI website suggests using DRI for Radeon 7500 cards, but DRI is only an infrastructure and I don't think they have a full driver out. I remember reading a few months back about some people who wanted to get AIGLX up on their ATI cards and many said that ATI's drivers don't support AIGLX so the only solution was to use the Intel driver which is essentially a generic driver to work with any card. The Radeon open source drivers don't seem to have full 3D support, from what I know, which makes them useless to XGL. The whole issue is just to have "glxinfo" give you "direct rendering: yes". I guess you could Google that topic about getting direct rendering support. Hope this helps!:???:

---

### Post by klato on 2006-10-28
I have the exact same video card in my laptop, and I just ran Beryl on Edgy.  

Edgy uses the open source drivers by default for this card, and I believe xorg has AIGLX built into it. Do a search for "edgy beryl" and you should find what you're looking for.

Performance was good, although it was rather buggy for me (desktop sort of gets cut off so that I can't see the notification area...also my desktop background disappears, and window titlebars disappear too and I can't drag anything around...it sure as hell looks cool though ;)

Update: for this interested, I've fixed the desktop issues by making a file called "drirc" and putting it in /etc

Here's the contents:

<driconf>
    <device screen="0" driver="ati">
        <application name="all">
            <option name="allow_large_textures" value="2" />
        </application>
    </device>
</driconf>

---

### Post by parenp on 2006-11-03
> Update: for this interested, I've fixed the desktop issues by making a file called "drirc" and putting it in /etc

Could you post your xorg.conf file so I can see how you got X to respect your drirc file?

Thanks.

---

### Post by aka5ha on 2006-11-08
I have an IBM T30 with Radeon Mobility 7500 16Mb and I have Compiz / AIGLX working perfectly.  Here is how I did it:

1. fresh install of edgy
2. follow the guide at:
[http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/](http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/)

Hope this works for you.

---

### Post by Synikk on 2006-11-08
> **aka5ha said:**
> I have an IBM T30 with Radeon Mobility 7500 16Mb and I have Compiz / AIGLX working perfectly.  Here is how I did it:

1. fresh install of edgy
2. follow the guide at:
[http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/](http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/)

Hope this works for you.

Thanks, I'll look into this.

---

