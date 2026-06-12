---
title: "system sounds, but no sound on webpages?"
date: 2008-09-17
forum: Desktop Environments
---

### Post by lanr01 on 2008-09-17
Hello from a newbie. I have installed ubuntu and things are going fairly well so far with getting things setup, But I am having a little problem figuring out what I am missing. I have system sounds, but any webpage that I go to that has sound, I get nothing on my side. I am new to this as I have been forced to use MS until now. Am I missing some codex or is there something I need to change with how firefox is setup? This is more or less a straight out of the box setup running on an amd 64 machine. I am using the onboard sound, and have system sounds.

Thanks,
Rick

---

### Post by eggdeng on 2008-09-17
System sounds and mutimedia apps use different drivers - ESD and ALSA respectively. If you can play back the multimedia files in /home/your_user/examples, your drivers are OK and you can turn your attention to codecs. On a fresh ubuntu install, you will need codecs for DVD playback, Win32 codecs, a flash plug-in and a few other things. Most people get these from the mediubuntu repository. There are lots of how-tos, you need to shop around a bit. One to get you started: [http://www.zimbio.com/mp4+Converter/articles/165/How+Install+Media+Codecs+Flash+DVD+QuickTime]("http://www.zimbio.com/mp4+Converter/articles/165/How+Install+Media+Codecs+Flash+DVD+QuickTime")

---

### Post by lanr01 on 2008-09-18
Ok, this will be a very stupid question to most of you, but what program do i use to install a bin file with? I downloaded realplayer bin file and I am being asked what application to use to open the file with. This link needs to be opened with an application. Send to: and it gives me a choose an application by Choose... But having never used linux, I don't know what I should look for and choose... an archive manager maybe?


Rick

---

### Post by lanr01 on 2008-09-18
> **eggdeng said:**
> System sounds and mutimedia apps use different drivers - ESD and ALSA respectively. If you can play back the multimedia files in /home/your_user/examples, your drivers are OK and you can turn your attention to codecs. On a fresh ubuntu install, you will need codecs for DVD playback, Win32 codecs, a flash plug-in and a few other things. Most people get these from the mediubuntu repository. There are lots of how-tos, you need to shop around a bit. One to get you started: [http://www.zimbio.com/mp4+Converter/articles/165/How+Install+Media+Codecs+Flash+DVD+QuickTime]("http://www.zimbio.com/mp4+Converter/articles/165/How+Install+Media+Codecs+Flash+DVD+QuickTime")



 Looks like I can't play any multimedia apps at all....  Well I fixed that, I can play multimedia, just nothing from webpages other than the video. I can watch anything from foxnews or youtube, but it has no sound...

---

### Post by ukripper on 2008-09-18
Go to add/remove programs and search for ubuntu-restricted-extras and install.

Then re-open firefox make sure you close it and now try again.

---

### Post by lanr01 on 2008-09-18
> **ukripper said:**
> Go to add/remove programs and search for ubuntu-restricted-extras and install.

Then re-open firefox make sure you close it and now try again.

I tried that, but I get this error msg:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

 When I run from terminal, I get this :

dpkg: requested operation requires superuser privilege
rick@Main:~$

---

### Post by ukripper on 2008-09-18
> **lanr01 said:**
> I tried that, but I get this error msg:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

 When I run from terminal, I get this :

dpkg: requested operation requires superuser privilege
rick@Main:~$

sudo dpkg --configure -a

---

### Post by lanr01 on 2008-09-19
Well it seems that I left my onboard sound active in bios and it didnt like having my creative labs card in that I was using. Once I got rid of one or the other, everything works great now.. 3 days of installing, re-installing and multiple attempts at setup was for not. Well not really, I learned a lot because of it. while I am totally new to the nix world, I dont feel as lost now after the last 3 days,, Thanks for all the help and great advice and links...

Rick

---

