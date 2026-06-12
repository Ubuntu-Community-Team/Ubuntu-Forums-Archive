---
title: "Desktop Won't Appear"
date: 2006-02-20
forum: Desktop Environments
---

### Post by stevo1328 on 2006-02-20
Hey guys, I am extremely new to Linux, and I have recently installed Ubantu, and it installed successfully, but when i sign into Ubantu, i just get a nice brown screen, and stays like that forever.  If someone could please walk me through stepsto be able to get my desktop, it would be greatly appreciated.  Thanks

---

### Post by Ramses de Norre on 2006-02-20
First of all: why does some people need to re-invent the distro's name? I've seen it a lot allready.. it's just ubuntu you know..

About your problem: does everything hang at the brown screen? If so, do you have an amd 64 in combination with an ati graph card? Because amd doesn't seem to combine very good with the ati driver in some cases.. 
The solution for me was to change the driver to vesa and then apt-get the fglrx drivers for ati.

I can explain how to do it if you think this is the problem.

---

### Post by stevo1328 on 2006-02-20
i have an amd 64, but i dont have a ati graphics card

---

### Post by Ramses de Norre on 2006-02-20
I don't know whether other graph cards have the same problem. But you could try setting the driver to vesa.
To do so you can open a shell by pressing ctrl+alt+F1 at the login screen.
sudo cp /etc/X11/xorg.conf /ect/X11/xorg.conf.bak  will backup your xorg file
sudo vi /etc/X11/xorg.conf    to edit the file
search for something like this: ```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon X600 (RV370)"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"

```
press i to get to insert mode and change the driver to "vesa"
press esc to exit insert mode
shift+q to get a command-line at the bottom
wq! to write and quit
now press ctrl+alt+F7 to get back in the GUI and the press ctrl+alt+backspace to restart it
does it work now? 
It allowed me to log in but sometimes X crashed, vesa is also very basic. But once you can log in you can set up your internet and download better drivers.

Hope this solved your problem!

---

### Post by stevo1328 on 2006-03-07
No, that still won't do it, it actually messed it up more

---

