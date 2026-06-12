---
title: "PS3 Controller Help!!!!"
date: 2013-01-09
forum: Emulators
---

### Post by nonstick on 2013-01-09
Okay, so I am a noob to Ubuntu and before I switched from Windows 8 to Ubuntu 12.10 I was able to play PlayStation 1 and a few other emulators with a PlayStation 3 controller via USB on my laptop. Now since I have switched I haven't been able to find a program that will let me use my PS3 controller via USB with Ubuntu 12.10. Is there one around and I just haven't found it or is there not one yet?
Thank you for the help.

---

### Post by ntzrmtthihu777 on 2013-01-09
> **nonstick said:**
> Okay, so I am a noob to Ubuntu and before I switched from Windows 8 to Ubuntu 12.10 I was able to play PlayStation 1 and a few other emulators with a PlayStation 3 controller via USB on my laptop. Now since I have switched I haven't been able to find a program that will let me use my PS3 controller via USB with Ubuntu 12.10. Is there one around and I just haven't found it or is there not one yet?
Thank you for the help.

```
sudo apt-get install joystick jstest-gtk qjoypad
```Should do the trick. I have mine blue-toothed, its a bit tricky to do that.
```
jstest /dev/input/js*
```
where * is replaced with 0 or 1, will let you see if it is getting input. (The PS3 controller makes two js devices. One only has 3 axis, the other just about everything else.)

I am assuming you are using an authentic Dualshock3 Playstation 3 controller.

If you prefer a GUI you can use jstest-gtk

---

### Post by nonstick on 2013-01-14
I tried this but it doesnt seem to see my controller when its hooked up via usb.

---

### Post by Lightning Dragon on 2013-01-17
Hello,

What kind of controller is it? I find that only high named brands work, like wired controllers. The official PS3 controller doesn't work, at least not for me and some of my friends. If you have another PS3 controller, try that one instead.

---

### Post by nonstick on 2013-01-17
Okay, all I have are the official play station controllers. Then this is probably why it wont work. Thanks

---

### Post by Lightning Dragon on 2013-01-18
Hello,

We can test that, if you have Windows. If you do, try to download the PSX emulator, plug in your controller and let it install the software/driver for the controller, and then open the emulator and then go to the controller settings and click the drop down menu button and find the controller. If it isn't there, then it is for sure because it is an Official controller.

If you have an Xbox 360 controller, non wireless, it will work too.

---

### Post by ntzrmtthihu777 on 2013-01-26
> **Lightning Dragon said:**
> Hello,

What kind of controller is it? I find that only high named brands work, like wired controllers. The official PS3 controller doesn't work, at least not for me and some of my friends. If you have another PS3 controller, try that one instead.
As I stated earlier, my official PS3 pad works find with a bit of tweaking.

---

### Post by Lightning Dragon on 2013-01-27
Hello,

I didn't see your post at the time, I apologized. Based on personal experience and that of the people I know I came to the conclusion the rechargeable controllers for PS3 hardly ever worked right.

[SIZE=1]But may I can ask you if you can assist this user in trying to set up his controller? I know it is a Xbox controller, but maybe you can help him?

[http://ubuntuforums.org/showthread.php?t=2108865&page=5](http://ubuntuforums.org/showthread.php?t=2108865&page=5)[/SIZE]

---

