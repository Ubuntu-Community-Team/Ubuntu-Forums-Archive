---
title: "Starting 5.10 problem"
date: 2006-01-10
forum: General Help
---

### Post by spock2263 on 2006-01-10
Hello to everyone.
I've installed ubuntu 5.10 on my laptop pc and it boots ok, but after this stage (I don't know how is it called, I've attached a jif file of it) I get a black screen and then nothing at all! What I should do? What is this 6.04 flight cd 2? Is it a complete distro? I thought it would be released on April. Should I download and install this,whould it help me? Thank you

---

### Post by spock2263 on 2006-01-11
I booted again and when it freezed I pressed Ctrl-Alt-F1, I put my username and password and then I got this: jim@ubuntu:~$ (jim is my username). What I should type? Thank you

---

### Post by dabang on 2006-01-11
Seems to me that your X configuration does not work properly as the boot process is OK. Otherwise you couldn't login at console prompt. Maybe the refreshrate isn't compatible with your screen so it goes blank? Just a guess?

---

### Post by lamego on 2006-01-11
On the terminal try:
> sudo dpkg-reconfigure xserver-xorg

---

### Post by lx638 on 2006-01-11
^^this shall be my first post here.:D im new to ubuntu and linux by the way. i have the same problem. i will try what u suggested.thanks.

---

### Post by spock2263 on 2006-01-11
I tried this command, I reconfigured what i was asked to and then i got the same: jim@ubuntu~$ ...

---

### Post by spock2263 on 2006-01-11
Last time I booted I noticed that during the loading screen everything reports ok except 'Starting hotplug subsystem', that doesn't say 'ok'. Does it have something to do with my problem? It's really weird I am prompted to log in the console, isn't it? And then this jim@ubuntu~$... The gnome won't load

---

### Post by gunksta on 2006-01-11
I agree with what others have said here.  It's an Xorg configuration issue.  To help you more, we need to know what kind of video card you have and if you could cut and past your /etc/X11/xorg.conf file, that might help too.  To do this start gedit.  Tell it to open /etc/X11/xorg.conf and then just paste it over to the web here.

I haven't had any coffee yet.  If none of this makes sense.  Blame my coffee machine.

--andy

---

### Post by dabang on 2006-01-11
Without X gedit is hard to use... ;) 
If you have another OS on that computer and mounted its partition, you could copy your xorg.conf to that partition:
```
cp /etc/X11/xorg.conf /path/to/other/os
```
and then post it here.
maybe you need start this command with *sudo*. If you don't have a chance to do that, I guess you have to write it down. To see it's content in a terminal type
```
more /etc/X11/xorg.conf
```

---

### Post by spock2263 on 2006-01-11
I tried to start gedit but I got this: '(gedit:8058):Gtk-WARNING **:cannot open display' Then again jim@ubuntu:~$, so I type anyway /etc/x11/xorg.conf and I get: ' no such file or directory'
My video card is ATI MOBILITY RADEON X700 PCI Express With 128MB VRAM

---

### Post by canadianwriterman on 2006-01-11
[QUOTE=spock2263]Hello to everyone.
I've installed ubuntu 5.10 on my laptop pc and it boots ok, but after this stage (I don't know how is it called, I've attached a jif file of it) I get a black screen and then nothing at all! What I should do? What is this 6.04 flight cd 2? Is it a complete distro? I thought it would be released on April. Should I download and install this,whould it help me? Thank you[/QUOTE]

By the way, I would NOT download and install Flight 2. It is an experimental version of the next Ububtu release and I bound to break.

---

### Post by dabang on 2006-01-11
You forgot "more"...

```
more /etc/X11/xorg.conf
```

---

### Post by spock2263 on 2006-01-11
I tried this: cp /etc/X11/xorg.conf /path/to/other/os and I got: 
cp: cannot stat /etc/x11/xorg.conf: no such file or directory...

---

### Post by Thirsteh on 2006-01-11
Do it with a CLI editor, spock. Like:

sudo nano -w /etc/X11/xorg.conf

---

### Post by spock2263 on 2006-01-11
I've also tried 'more /etc/X11/xorg.conf' but again no luck

---

### Post by lx638 on 2006-01-11
> sudo dpkg-reconfigure xserver-xorg
i tried this one untill i reached the one saying

> Please select your desired default color depth in bits

and i chose 24. what's next?i am a windows user this is giving me a hard time, but it's worth a try. just tell me what to do.:D thanks

---

### Post by Thirsteh on 2006-01-11
[QUOTE=spock2263]I tried this: cp /etc/X11/xorg.conf /path/to/other/os and I got: 
cp: cannot stat /etc/x11/xorg.conf: no such file or directory...[/QUOTE]

Keep in mind that character case matters in Linux, it's X11, not x11.

/etc/X11/xorg.conf

---

### Post by lx638 on 2006-01-11
ok im here again. after typing **sudo dpkg-reconfigure xserver-xorg** i followed instructions and rebooted

it says X failed to start. here are the error details:

**no screens found**

and i also found these

[B](WW) the directory /usr/share/X11/fonts/cyrillic does not exist
(WW) the directory /usr/share/X11/fonts/CID does not exist
(WW) fonts.dir invalid
(WW) open APM failed (dev.apm_bios) (no such file of directory)[/B]

---

### Post by spock2263 on 2006-01-12
I typed 'more /etc/X11/xorg.conf' and I got a list of something like command choices, I have no idea what to do next...
Also with ;sudo nano -w/etc/X11/xorg.conf I got a weird list...

---

### Post by spock2263 on 2006-01-12
Please tell me what I am supposed to do after typing 
'sudo nano -w/etc/X11/xorg.conf' or 'more /etc/X11/xorg.conf' ?

---

### Post by dabang on 2006-01-15
> Please tell me what I am supposed to do after typing
'sudo nano -w/etc/X11/xorg.conf' or 'more /etc/X11/xorg.conf' ?

This command shows the content of your xorg.conf file which is responsible for your X configuration. Pleas post it's content here along with your hardware specs...

---

### Post by spock2263 on 2006-01-19
[QUOTE=dabang]This command shows the content of your xorg.conf file which is responsible for your X configuration. Pleas post it's content here along with your hardware specs...[/QUOTE]
 I finally managed to start the Gnome, but now I don't have the right screen resolution, you see I have a 16:9 widescreen and the resolution now ubuntu gives me is 1024x768 which is a 4:3 screen resolution. You will now tell me to run the xorg.conf file to correct this, but I've done this, it's 1280x800 in the xorg.conf file but I get 1024x768, so everything is streched to fit the widescreen!!! Do you have any ideas?

---

