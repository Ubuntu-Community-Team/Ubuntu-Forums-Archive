---
title: "Failed Arduino install wrecked my desktop access - help"
date: 2020-03-22
forum: Desktop Environments
---

### Post by watchpocket on 2020-03-22
Earlier tonight I downloaded Arduino 1.8.12, the Linux 64-bit version from [[("]https://www.arduino.cc/en/Main/Software]]("https://www.arduino.cc/en/Main/Software), for use with the Keyboardio Model 01 keyboard.

It downloaded to my Desktop/Downloads folder.  I then applied the commands described at: 
[https://github.com/keyboardio/Kaleidoscope/wiki/Install-Arduino-support-on-Linux](https://github.com/keyboardio/Kaleidoscope/wiki/Install-Arduino-support-on-Linux) 

This is what I did, from my user home directory shell prompt:

```
    $ cd Desktop/Downloads
    $ tar xvf arduino-1.8.12-linux64.tar.xz
    (a long list of stuff opened and installed)    
    $ sudo mv arduino-1.8.12 /usr/local/arduino
    $ cd /usr/local/arduino
    $ sudo ./install.sh
```

Suddenly I noticed that most of the icons in my top panel were now missing. Then I noticed that my desktop icons were all generic icons. So I re-booted. Upon re-boot, I get a blank screen in both my monitors. For one or two quick flashes, I can see my usual interface behind the blank screen (ssh window, browser, etc).

Can anyone help me figure out WHAT JUST HAPPENED?!

This is on Ubuntu-MATE 16.04.  I had already successfully flashed the latest firmware onto my Keyboardio Model 01 the day before.

I am writing now from a separate drive in my desktop workstation where I have the old Ubuntu 14.04 installed. From here I can open the 16.04 drive and I see that in /usr/local/arduino that the arduino components appear to have been installed.  

I can also see that a file named "Arduino IDE" is on my desktop, and that it's a "desktop configuration file," (application/x-desktop) but it will not open.
 
Right now I have no direct normal graphical access to my entire 16.04 system, which is very scary. This sort of thing hasn't happened to me in quite awhile.  ( I did just recently discover that MATE-16.04 is beyond its end-of-life support, but everything else on my MATE 16.04 has been working fine.)

The install.sh script that's in my /usr/local/arduino is on pastebin here:
[https://paste.ubuntu.com/p/WXbQMgQh3R/](https://paste.ubuntu.com/p/WXbQMgQh3R/)


Any tips or suggestions about what went wrong here greatly appreciated.

---

