---
title: "[SOLVED] My font names show up but don't work"
date: 2007-09-30
forum: Desktop Effects &amp; Customization
---

### Post by akarros on 2007-09-30
I am new to all of this, so please accept my apologies if this is duplicate.  I have searched these forums for help in making TTF fonts work.  I finally thought i had it.  The fonts show up in word processor font list, but when I choose one of my fonts, they show up blank.

Also, a web page I built in Windows does not show up with the chosen font.  As a matter of fact, it almost looks like when I donwloaded my page source to ubuntu and edited it and FTP back to my server that some font names were substituted.  That was real weird.

i have them installed in /usr/shared/fonts/truetype/myfonts.

I have done

dpkg -recondigure fontconfig-config

mkfontdir

fc-cache -f -v

Any ideas what I am doing wrong??

Also, how do I know that when I try a bunch of different terminal commands that I am not compounding any problems, Is there any way to go back to a default installation without reinstalling everything???

Thanks for all of you being here.

10/23/07:  I have not gotton fonts to work yet.  But I did not want this issue to carry on.  I think you all have suggested pretty much everything.  I will try again sometime with a clean install.  Thanks.

Art

---

### Post by por100pre1 on 2007-10-01
Try placing your .ttf fonts in the .fonts folder inside your user folder. If there's no such folder make one:

```
mkdir .fonts
```

The .fonts folder should be a hidden folder, press Ctrl+H to see hidden folders. Once done, logout and log back in or just reboot.

Hope it helps. :)

---

### Post by akarros on 2007-10-02
Hi.

No luck.  I tried control H and it did nothing for me.  Do i do this in terminal mode???

Regardless i mkdir .fonts and moved my fonts in here.  Did not work I rerun the cache command and still it did not work.

I am on xubuntu.  Does that make a difference??

My main goal is to have correct fonts show up in FIREFOX browser.

Thanks for your help.

art

---

