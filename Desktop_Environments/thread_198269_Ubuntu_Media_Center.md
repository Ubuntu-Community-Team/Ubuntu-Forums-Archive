---
title: "Ubuntu Media Center?"
date: 2006-06-16
forum: Desktop Environments
---

### Post by Bright Hammer on 2006-06-16
I am not sure that I am posting in the right place so I apologize in advance if there is a media center post somewhere else. I did a search for media center and I didn’t see one as thread so I thought I would start one. I LOVE Ubuntu it works great and I have to say the new build for me has been trouble free. I have just recently hacked my XBOX to turn it in to a media center. I used a software hack so as not to void my warranty if I didn’t like it I could take it back to the retailer where I purchased it. (You can check it out at [XBMC]("http://www.xboxmediacenter.com/index.php") ) These guys have done a Fantastic job on it and it has almost everything you need in a media center. However since I didn’t want to open my xbox so I don’t have a dvr for cable as an option. So I was considering setting up [MythTV]("http://www.mythtv.org/") but that requires that you put Linux on the xbox as the sole OS and then I would lose my warranty. Plus at this point I can’t think of getting rid of XBMC it is way too awesome. So I was wondering if Ubuntu is considering a media center option in the future. Both OSX and Windows have something similar and are pushing hard for convergence. I hope that Ubuntu is looking into something like this. With all the work that has been done with XBMC and MythTV that is open source I hope it might give Ubuntu head start if they haven’t. Plus I really do feel that it would get more users willing to switch from windows.


If anyone knows of any easy user-friendly open source please software for a media center other than the ones I mentioned please post them.

I also have a request can some one please make an Ubuntu version of MythTV package that is easy to set up?

Also I know I should post this side request in a XBMC forum which I will but as a follow up a XBMC front end or connector to MythTV.

I would appreciate some feed back from others on the topic thanks in advance.

BH :)

---

### Post by x64Jimbo on 2006-06-16
Seconded. I'd love to see Ubuntu add a MythTV package.

---

### Post by HyperY2K on 2006-06-17
I've using mythTV unter Ubuntu. If anyone is interested I can post my sources.lst

---

### Post by Bright Hammer on 2006-06-19
[QUOTE=HyperY2K]I've using mythTV unter Ubuntu. If anyone is interested I can post my sources.lst[/QUOTE]


Yes please do. If you can please post some step by step instructions that would be great. Also if you have a TV card please list your hard ware specs. :D

---

### Post by Maelstrm on 2006-06-19
[QUOTE=x64Jimbo]Seconded. I'd love to see Ubuntu add a MythTV package.[/QUOTE]

.. but they already have?

Package: mythtv
A personal video recorder application (client and server)

Maintainer: Matt Zimmerman <mdz@debian.org>
Section: Graphics (multiverse)
Version: 0.18.1-5ubuntu3

Sure, it's probably not the latest version, but it works fine.

---

### Post by xsupernerdx on 2006-06-20
I set up a Myth box for a friend using Ubuntu. He's had it running for about six months with no real issues. The only thing bad about it (like Maelstrm noted) is that it's not the most recent version of Myth. You can check [here]("http://www.abarbaccia.com") for some info on setting up Myth under Ubuntu.
 Knoppmyth might be another option for you. It is super easy to get up and running. You can download it and browse their forum at [the Knoppmyth homepage]("http://www.mysettopbox.tv"). Their [wiki]("http://www.knoppmythwiki.org") also has some really good info.

Just so you know, even if you installed MythTV directly on your Xbox you wouldn't be able to use it as a dvr. The MythTV installation on the Xbox would only act as a frontend. There is an XBMC script that interfaces with MythTV quite nicely if you have a Myth box already set up. It's called [XBMCMythTV]("http://sourceforge.net/projects/xbmcmythtv/"). I've been using that script for a while and it works fairly well.

---

### Post by Bright Hammer on 2006-06-20
[QUOTE=xsupernerdx]I set up a Myth box for a friend using Ubuntu. He's had it running for about six months with no real issues. The only thing bad about it (like Maelstrm noted) is that it's not the most recent version of Myth. You can check [here]("http://www.abarbaccia.com") for some info on setting up Myth under Ubuntu.
 Knoppmyth might be another option for you. It is super easy to get up and running. You can download it and browse their forum at [the Knoppmyth homepage]("http://www.mysettopbox.tv"). Their [wiki]("http://www.knoppmythwiki.org") also has some really good info.

Just so you know, even if you installed MythTV directly on your Xbox you wouldn't be able to use it as a dvr. The MythTV installation on the Xbox would only act as a frontend. There is an XBMC script that interfaces with MythTV quite nicely if you have a Myth box already set up. It's called [XBMCMythTV]("http://sourceforge.net/projects/xbmcmythtv/"). I've been using that script for a while and it works fairly well.[/QUOTE]



THANKS!! Super

This is exactly what I was looking for. I have a couple of question however.

1.	Does this support live TV?
2.	Does it support more that one XBOX with XBMC for a front-end?
3.	Does it support browsing the web? Linkbooks works as a basic browser but I can’t seem to get it to work with media files.


Thanks for your help I will try out the info you gave me above and try to answer my own questions but if you can answer some time soon that would be great.

:D

---

### Post by redelephant on 2006-06-20
I can answer some of those.

1. Yes, though I don't know how well it works. Never tried it. 
2. Yes. You have to give each Xbox permission in mysql to access the Myth backend. I believe you can have as many as you want (as long as they all have permission from the backend).
3. No, I don't think it does. I think the only way to get half decent web browsing is through a Linux distro on your box - like Xebian. XBMCMythtv is just a script that works inside XBMC to access some Myth functions. You can watch recorded programs, watch live tv, look at the program guide, and maybe a couple other things.

The KnoppMyth suggestion is a pretty good one if you are new to Myth. It does most everything automatically and some pretty helpful functions built in. But it does have a few quirks that I personally don't care for.

---

### Post by redelephant on 2006-06-20
[Here's]("http://www.controlaltdeleted.com/xbox/xbox_tutorials/myth_tv_related_information/how_to_install_mythtv_on_your_xbox.html") a link that might help as well.

---

### Post by Bright Hammer on 2006-06-20
Thanks RED for all the good info from everyone. I have to say this community rocks. I will try all to get MythTV working and report back. But if you have any more info please post it. When I get my Myth TV back end working I will start a blog or some thing documenting how.  However I would really like someone at Ubuntu to develop a package that is up to date and make it standard with the distro. I know this is a long shot but I had to at least try.

:D

---

