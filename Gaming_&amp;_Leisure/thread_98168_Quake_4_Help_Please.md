---
title: "Quake 4 Help Please"
date: 2005-12-02
forum: Gaming &amp; Leisure
---

### Post by tpnerdcore on 2005-12-02
hey everybody. First off, I'm sorta an Ubuntu Newbie. I managed to sucessfully Quake 4!! But, my sound is horrible. Ive seen stuff like "quake4 +set s_device oss" but i dont know where to input this. Does anybody know an easy way to fix the sound problem??? PLEASE HELP

anthony(tpnerdcore)

---

### Post by OptikKnight on 2005-12-02
You might try the "Multimedia Systems Selector" from the Main Menu: System > Preferences > Multimedia Systems Selector...

Also, there may be a reference to that line of code in a configuration file for Quake 4. As OSS is only recently becoming out-of-date, and being replaced by ALSA, Quake 4 may have automatically set that configuration, or it may have derived it from an existing configuration for, say, Gnome's multimedia support.

Good luck, and don't forget to post a response detailing whatever solutions you find!

---

### Post by tpnerdcore on 2005-12-02
well i tried going into the multimedia systems selector and changing that to OSS but it was already set to OSS. I bet i could fix it if i knew where the Quake 4 config file was. I've searched all through the directory and its sub folders trying to find something and no luck. Any advice optik or anyone??


anthony(tpnerdcore)

---

### Post by crane on 2005-12-03
[QUOTE=tpnerdcore]hey everybody. First off, I'm sorta an Ubuntu Newbie. I managed to sucessfully Quake 4!! But, my sound is horrible. Ive seen stuff like "quake4 +set s_device oss" but i dont know where to input this. Does anybody know an easy way to fix the sound problem??? PLEASE HELP

anthony(tpnerdcore)[/QUOTE]

I believe the correct setting is:
quake4 +set s_driver "oss"

---

### Post by Curlydave on 2005-12-03
Do this: Go to the sound driver settings in the Quake 4 game itself, and set it to OSS from there.

---

### Post by tpnerdcore on 2005-12-04
where is exactly do i set the driver to OSS is quake 4. All i see is "default" or "OpenAL" no oss. Please help


anthony(tpnerdcore)

---

### Post by mcrosmar on 2005-12-04
[quote=tpnerdcore]hey everybody. First off, I'm sorta an Ubuntu Newbie. I managed to sucessfully Quake 4!! But, my sound is horrible. Ive seen stuff like "quake4 +set s_device oss" but i dont know where to input this. Does anybody know an easy way to fix the sound problem??? PLEASE HELP

anthony(tpnerdcore)[/quote] 
Open terminal and type quake4 +set s_driver oss

---

### Post by Razvan on 2005-12-04
terminal lives in Applications>>System tools

---

### Post by tpnerdcore on 2005-12-05
well when i do this just in the default directory it says im at(anthony@ubuntu:~$)...it says "bash: quake4: command not found"

and when i do this in the quake4 directory it says the same thing??

any more sugestions??? 

anthony(tpnerdcore)

---

### Post by mcrosmar on 2005-12-06
[quote=tpnerdcore]well when i do this just in the default directory it says im at(anthony@ubuntu:~$)...it says "bash: quake4: command not found"

and when i do this in the quake4 directory it says the same thing??

any more sugestions??? 

anthony(tpnerdcore)[/quote]

How did you install Quake4?

---

### Post by metoo on 2005-12-06
I'm just checking out the demo. Thanks to all the posters to get me going.

To make it permanent (it's with the demo, but likely for the real thing as well):

1) in your home directory there is a hidden directory .quake4-demo (or just .quake4 ?) - enter it
2) dive into q4base
3) open Quake4Config.cfg with an editor gedit or kedit for instance
4) search for: s_driver
5) set the value in "" to "oss" the line now says: seta s_driver "oss"
6) save

---

### Post by vtechstu on 2005-12-12
Thanks metoo.  This worked like a charm for the demo.  I'm assuming it worked for the other guy too, but he forgot to thank you.  Fun game!

---

### Post by tpnerdcore on 2005-12-12
Thanks alot, this worked perfectly!!! Thanks to everybody that answered the same way, i just needed a bit more help actaully finding the directories thanks

anthony(tpnerdcore)

---

### Post by pitr on 2005-12-12
Here is another possible solution

1. Open ~/.quake4/q4base/Quake4Config.cfg
2.    change the line seta s_alsa_lib "libasound.so.2" to       seta s_alsa_lib "libasound.so.0"
3. Save the file

---

### Post by Brynster on 2005-12-21
Thanks Metoo your l33t hacking skills fixed my bad sound too

Many thanks

---

