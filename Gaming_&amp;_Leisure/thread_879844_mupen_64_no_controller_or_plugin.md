---
title: "mupen 64 no controller or plugin"
date: 2008-08-04
forum: Gaming &amp; Leisure
---

### Post by bravo331 on 2008-08-04
Hello everyone; 
I am trying to get mupen 64plus running on my gateway t1616 laptop. I run mupen by opening the mupen64 bin32 folder then clicking the mupen 64plus exe. It seems that mupen runs just fine but it does not recognise my controller (saitek p880) Ubu recognises the controller & lets me configure through applications-accessories-joystick calibration. This works fine. When I click on the mupen64 basic input plugin in mupen config window nothing happens. Blights plugin is not listed. Blights plugin is present in the mupen bin32 folder, in the plugins subfolder, but mupen does not show it as an available plugin. I can navigate Conkers Bad Fur Day start menus with the keyboard; this is why I believe that mupen itself runs fine. Hopefully someone can steer me in the right direction. Thanks in advance!!

---

### Post by gigaferz on 2008-08-04
Hello.

That happens some times with some emulators. Most likely you need to edit some configuration file.

with this new ubuntu version I installed mupen64 plus , but I got a "deb" package form getdeb.net

Why dont you download it and double click it wait for it to install  then you will find it in the games section.

However in my pc doesnt perform as good as previous versions, I just found the old one v.05 and looks good.

This one is just a folder and you need to double click the "exe" file (is a .bin file not an actual .exe)

Let me know if I can help you further, but honestly I havent been able to find information about mupen 64, whatever is out there is really outdated.

---

### Post by nadarockyraccoon on 2008-08-10
I had the same problem but with my keyboard, not a controller, none the less it turns out the input plugin was just no good. So I downloaded
[http://mupen64.emulation64.com/files/0.5/mupen64-0.5.tar.bz2]("http://mupen64.emulation64.com/files/0.5/mupen64-0.5.tar.bz2")

This program really doesn't work well, the audio and video are real gltchy, but the controller works great. As the superuser I deleted  /usr/local/share/mupen64plus/plugins/blight_input.so and replaced it with /mupen64-0.5/plugins/blight_input.so. Then I stared mupen64plus and configured my controls without a hitch.

I know that other plugins are available on the web for mupen64plus's audio,video, and controllers, and that is where they go, so if this doesn't work or if you just want to see if there is something better, this is about how it goes. (loading mupen64plus out of terminal will tell you if the plugins are good or not)

---

### Post by bravo331 on 2008-08-10
well i did wha gigaferz said, now i can config my conroller but the roms wont load BLAH!!!

---

