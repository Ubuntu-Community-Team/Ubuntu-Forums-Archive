---
title: "install fonts from sources other than repositories"
date: 2006-09-21
forum: Desktop Environments
---

### Post by xurios on 2006-09-21
I am trying to run mathematica from a server here at my lab. I log in from my Ubuntu 6.06 box using ssh -X user@server. I start mathematica, and get 

```

xset:  bad font path element (#162), possible causes are:
    Directory does not exist or has wrong permissions     
    Directory missing fonts.dir
    Incorrect font server address or syntax
xset:  bad font path element (#162), possible causes are:
    Directory does not exist or has wrong permissions
    Directory missing fonts.dir
    Incorrect font server address or syntax

```

Then, of course, mathamatica complains about missing fonts and doesnt work properly. I grabbed all the mathematica fonts off of the server (as per the recomendation of the admin) but I'm not sure where to put them or what config files or environment variables to modify/create. 

I have had troubles before with this sort of x-tunneling and fonts (using RedHat 9 and enterprise 3 with Mentor Graphics), but just gave up on working remotely. Anyone have experience with this sort of issue?

---

### Post by xurios on 2006-09-21
Answered own question. I just tried making an exact duplicate directory path on my local system, with all the sub-directories with their fonts, of the directory where I grabbed the fonts from the server. Now mathematica finds what it's looking for and works just how it should. When I was done, I typed mkfontdir from the parent directory. I'm too tired now to RTFM for mkfontdir thouroughly, but it didn't break anything as far as I can tell.

---

