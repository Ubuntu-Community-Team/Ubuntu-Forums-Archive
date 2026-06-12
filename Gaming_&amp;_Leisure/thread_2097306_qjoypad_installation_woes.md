---
title: "qjoypad installation woes"
date: 2012-12-22
forum: Gaming &amp; Leisure
---

### Post by romber on 2012-12-22
Hello everyone,

I am having a heck of a time trying to install qjoypad. As far as I could tell, qjoypad is the best mapping software for xbox controllers. I have downloaded the source from [http://qjoypad.sourceforge.net/](http://qjoypad.sourceforge.net/) and extracted the tar.gz to my desktop, but then the ./configure process is where I get hung up, with this error: bash: ./configure: Permission denied

My issue is that I'm not sure if I am even doing the make install steps properly. I'm assuming I am to do all these commands from the src folder within qjoypad.

Also, I have searched for a deb file, but all have been dead ends.

Any help would be appreciated. I'm getting really frustrated and this kinda stuff makes me want to jump back to windows :(

---

### Post by xREDEMPTIONx on 2012-12-23
Check this link [https://sourceforge.net/projects/qjoypad/?source=dlp](https://sourceforge.net/projects/qjoypad/?source=dlp)
There is a 32 bit deb package there. Getdeb.net is down and that is where you would normally find the packages for qjoypad. Also, what is your controller? 360 or regular xbox? Are you trying to make the controller emulate mouse and keys or remap buttons for a game? You could also try jstest-gtk (run sudo apt-get install jstest-gtk in a terminal) for remapping buttons or [http://sourceforge.net/projects/javajoystick/ ]("http://sourceforge.net/projects/javajoystick/")
for remapping as a keyboard. Try not to get frustrated;)

---

