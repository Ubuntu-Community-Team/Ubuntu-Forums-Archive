---
title: "Two mices -&gt; Two pointers"
date: 2010-02-20
forum: Desktop Environments
---

### Post by kn4rF on 2010-02-20
When you plug two mices the operating system let you use both, but both mices move the same pointer. Is it possible in some way to get a second pointer for the second mouse plugged in?

---

### Post by jflaker on 2010-02-20
> **kn4rF said:**
> When you plug two mices the operating system let you use both, but both mices move the same pointer. Is it possible in some way to get a second pointer for the second mouse plugged in?

In my experience, you can have as many keyboards and mice as you can physically connect...You will have a single mouse pointer and keyboard input will be limited to the active application's window.

Now...you can create a virtual machine with virtual box (not the Open Source Edition OSE...download from Sun.) and allow remote desktop to that system and work independently through another system or through your console......

I do that now with XP that can be remotely accessed from another system.

---

### Post by kn4rF on 2010-02-20
> **jflaker said:**
> In my experience, you can have as many keyboards and mice as you can physically connect...You will have a single mouse pointer and keyboard input will be limited to the active application's window.

Now...you can create a virtual machine with virtual box (not the Open Source Edition OSE...download from Sun.) and allow remote desktop to that system and work independently through another system or through your console......

I do that now with XP that can be remotely accessed from another system.
I think we are doing different things: I don't need to remote access my machine, sometimes my pc (who has two monitors) is shared with another person; i have two mices and two keyboards and want to use one monitor, one mouse and one keyboard for me and one for him. 

The idea of using the virtual machine is very smart, because you can disable or enable the input devices you want; I tried with WinXP on VirtualBox but there's a problem: when I disable one usb mouse, this mouse is disabled not only for the virtual machine but for the entire system..

---

### Post by warp99 on 2010-02-20
You can have multiple mice inputs with multiple pointers. You need to setup up a Multi-Point X-Server (MPX) to do this. This is going to be included with Lucid (10.4) and it's already in the Alpha:

[http://ubuntu10-04.blogspot.com/2010/01/mpx-multipointer-in-ubuntu-1004-lucid.html](http://ubuntu10-04.blogspot.com/2010/01/mpx-multipointer-in-ubuntu-1004-lucid.html)

So if you wait about a month you can have what your looking for with a supported release or run the alpha and have it right now without having to compile and rebuild X-Server in Karmic.

---

### Post by kn4rF on 2010-02-21
> **warp99 said:**
> You can have multiple mice inputs with multiple pointers. You need to setup up a Multi-Point X-Server (MPX) to do this. This is going to be included with Lucid (10.4) and it's already in the Alpha:

[http://ubuntu10-04.blogspot.com/2010/01/mpx-multipointer-in-ubuntu-1004-lucid.html](http://ubuntu10-04.blogspot.com/2010/01/mpx-multipointer-in-ubuntu-1004-lucid.html)

So if you wait about a month you can have what your looking for with a supported release or run the alpha and have it right now without having to compile and rebuild X-Server in Karmic.

Thank you, I already tried MPX with no success. There's also a lack of documentation. At [this site]("http://alec.mooo.com/mpx.php")  I found a little howto which explains how to set multiple pointers.. But I don't get the same output as the hotwo's. 

Howto's output

```
  $ xinput list
  &#9121; Virtual core pointer                          id=2    [master pointer  (3)]
  &#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
  &#9116;   &#8627; Touchpad                                  id=6    [slave  pointer  (2)]
  &#9116;   &#8627; Mouse1                                    id=7    [slave  pointer  (2)]
  &#9116;   &#8627; Mouse1                                    id=9    [slave  pointer  (2)]
  &#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
      &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
      &#8627; Keyboard0                                 id=8    [slave  keyboard (3)]
      &#8627; Keyboard0                                 id=10   [slave  keyboard (3)]
    
```

My output

```



fr4nk@debian:~$ xinput list
"Virtual core keyboard" id=0    [XKeyboard]
"Virtual core pointer"  id=1    [XPointer]
"Keyboard0"     id=2    [XExtensionKeyboard]
"Mouse0"        id=3    [XExtensionPointer]


```

I don't get a structure..

---

### Post by Zorael on 2010-02-22
Try it from a Lucid live cd/usb.
```
$ xinput list
&#9484; Virtual core pointer                          id=2    [master pointer  (3)]
&#9474;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9474;   &#8627; "SynPS/2 Synaptics TouchPad"              id=12   [slave  pointer  (2)]
&#9474;   &#8627; "Macintosh mouse button emulation"        id=13   [slave  pointer  (2)]
&#9492; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; "Power Button"                            id=6    [slave  keyboard (3)]
    &#8627; "Video Bus"                               id=7    [slave  keyboard (3)]
    &#8627; "Power Button"                            id=8    [slave  keyboard (3)]
    &#8627; "Sleep Button"                            id=9    [slave  keyboard (3)]
    &#8627; "USB 2.0 Camera"                          id=10   [slave  keyboard (3)]
    &#8627; "AT Translated Set 2 keyboard"            id=11   [slave  keyboard (3)]
```

Daily live images: [Ubuntu](http://cdimage.ubuntu.com/daily-live/current/), [Kubuntu](http://cdimage.ubuntu.com/kubuntu/daily-live/current/), [Ubuntu Netbook](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/), [Kubuntu Netbook](http://cdimage.ubuntu.com/kubuntu-netbook/daily-live/current/), [Xubuntu](http://cdimage.ubuntu.com/xubuntu/daily-live/current/).

You'll find [Unetbootin](http://unetbootin.sourceforge.net/) in the repositories.

---

### Post by warp99 on 2010-02-22
I just confirmed this in Lucid with a Live USB using a touchpad and a Microsoft mouse. It works pretty slick. :D

---

### Post by Rhubarb on 2010-02-22
Ooooooooooooooooooooh yay!

I'm so happy, I've been keeping an eye on MPX over the last few years, wondering how long long it'll take to find its way into more mainstream linux distros, and of course, into the main x.org tree.

Sure there's a lot of apps that don't support MPX just at the moment, but it's good to know that it's finally here :)

---

### Post by warp99 on 2010-02-22
> **Rhubarb said:**
> 
Sure there's a lot of apps that don't support MPX just at the moment, but it's good to know that it's finally here :)


I've been playing with MPX a little and it looks like if one pointer drops down a menu the other can't select that menu or choose anything from the list until the other pointer releases the menu. There's probably going to be some way to rectify this in the future but as of now it's the default behavior. One good thing is that if you unplug the mouse and plug it back in during your session it's recognized immediate as a separate pointer. :biggrin:

---

