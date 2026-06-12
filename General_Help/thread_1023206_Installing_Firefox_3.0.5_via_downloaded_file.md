---
title: "Installing Firefox 3.0.5 via downloaded file"
date: 2008-12-27
forum: General Help
---

### Post by Mr_JMM on 2008-12-27
I have installed Firefox from the Add/Remove option in the KMenu but the CSS was screwed up so I'm trying to install Firefox via the downloaded file from the 
[Kubuntnu 8.10, installed from CD with all updates installed]

Mozilla website. I have the .tar.bz2 file on the desktop and have followed various "how to's" to install it with no luck.

The last line I tried was kdesudo tar -C /opt/ -zxvf firefox-3.0.5.tar.bz2 but I got a "Unknown Option 'C'" error.
I took it out and got errors about the zxvf.
Tried changing to the desktop but no joy (cd ~/Desktop).

Any help please on how to install Firefox so that it works properly?

Cheers.

---

### Post by taurus on 2008-12-27
If you want to move firefox-3.0.5.tar.bz2 to /opt before you unpack it, you could do

```
sudo mv firefox-3.0.5.tar.bz2 /opt
cd /opt
sudo tar xvzf firefox-3.0.5.tar.bz2
```

or
```
sudo tar xvzf firefox-3.0.5.tar.bz2 -C /opt
```

---

### Post by Mr_JMM on 2008-12-27
Cheers,

I have moved the file and extracted it to /home/james. I can launch Firefox by clicking the Firefox icon in the folder but the CSS is still screwed up. Could this be a problem with Kubuntu?

Annoyingly, it has got a theme I downloaded in the Firefox version installed via Add/Remove. This is also an issue. I used Add/Remove to remove it before I downloaded the file from Mozilla but obviously this hasn't completely removed it. Couls this be the problem? I wanted a fresh, Mozilla Firefox not a version hashed together by someone (Other than the Mozilla team that is).

Annoyingly, Firefox in Kubuntu 8.04 worked perfectly (unlike FF in Ubuntu 8.10).

---

### Post by Mr_JMM on 2008-12-27
Update:

I deleted all the mozilla and firefox folders then extracted the files again.
This gave me a clean install of Firefox but the CSS was still screwed up.

I can only surmise this is an issue with Kubuntu 8.10

Unless someone can show me how to solve this problem then it's bye bye ubuntu and kubuntu as Firefox doesn't work on 8.10.

Go back to 8.04? No. It took 8.10 to get me back to Ubuntu in the first place.

Firefox woks in Intrepid or it's back to Windoze.

I'm a website developer. I need to know the browser's css is as good as possible.

---

### Post by steveneddy on 2008-12-27
What exactly are you trying to do?

To what website are you referring?

FF 3.0.5 works fine for me.

The version of FF 3.0.5 that is in the repos is not a "hashed together" version. it is a legit version.

Maybe you have some other issue?

---

### Post by Mr_JMM on 2008-12-27
I am trying to get Firefox 3.0.5 to install in Kubuntu 8.10 and have it work as well as it does in 8.04 or Windows XP. Primarily, the CSS.

The igoogle page for example has incorrect CSS. Division widths are not perfect, radio buttons have some bizarre square box around them. Submit buttons are positioned in the wrong place.

I have shown the to ways I have installed Firefox and both have the same issue.

To break down the steps:

KStart -> Add/Remove -> Type in password -> Enter -> Search for "Firefox" -> Select the "Firefox Web Broswer" option -> Apply.

If this is wrong, please do say so.

---

### Post by steveneddy on 2008-12-27
Here is a screen shot of the igoogle page that I just shot - is something out of order here?

Maybe posting a screen shot will be helpful.

---

### Post by Mr_JMM on 2008-12-27
I see you're using Ubuntu!

Hopefully the image has uploaded (of my screenshot)

---

### Post by steveneddy on 2008-12-28
Try changing FF theme, fonts or display options.

---

