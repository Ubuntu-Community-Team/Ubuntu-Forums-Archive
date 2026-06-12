---
title: "Keyboard shortcuts for volume control"
date: 2015-04-03
forum: Desktop Environments
---

### Post by gdi2k on 2015-04-03
I want to use [Windows Key] + [Page Up / Down] to control my volume. 

As per the other million threads out there about this issue, I have assigned the command "amixer set Master 3%+" and "amixer set Master 3%-" to the keyboard shortcut, which works fine for my laptop's built-in audio. 

But when I am docked, I use an external USB sound card, which doesn't respond to that command, even when set as the default audio device in PulseAudio Volume Control. 

I also have dedicated volume controls built on my laptop (not accessible when I am docked) and these work on all my audio devices, including the external USB one when I am docked. 

My question is, what command is being used to effect the volume change when the volume buttons on the laptop keyboard are pressed - there is no application shortcut for that in the Keyboard settings in XFCE.

---

### Post by ajgreeny on 2015-04-03
I had the same problem some time ago and eventually found that the media keys on my keyboard can be set to the following
keyboard shortcuts.

```
<property name="XF86AudioLowerVolume" type="string" value="amixer set Master playback 3dB-"/>
<property name="XF86AudioRaiseVolume" type="string" value="amixer set Master playback 3dB+"/>
<property name="XF86AudioMute" type="string" value="amixer -D pulse set Master toggle"/>
```

You may be able to put those last three lines into your .config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml file with changes to the keys chosen or simply use the command shown (between the quote marks) in your user keyboard shortcuts in settings-manager.

I note that looks very similar to your commands except for the % vs db in them; I have no idea if that will make any difference but it may be worth trying.

---

### Post by gdi2k on 2015-04-03
Thanks ajgreeny!

I had a go with the command you provided:

```
amixer set Master playback 3dB-
```

The outcome is that it changes the volume of the laptop's inbuilt speaker, not the USB sound card, which is set as the "Fallback" device in Pulse Audio Volume Control. 

However, when the volume keys on the laptop are pressed, it always affects the device that is currently set as fallback in Pulse Audio Volume Control, and that's what I would like to achieve with my command. 

I've attached a screenshot to show you what I mean. 

[ATTACH=CONFIG]261079[/ATTACH]

---

