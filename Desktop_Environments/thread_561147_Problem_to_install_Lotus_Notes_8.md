---
title: "Problem to install Lotus Notes 8"
date: 2007-09-27
forum: Desktop Environments
---

### Post by chouf on 2007-09-27
Hi all,

I'm new to Ubuntu (and to Linux). I tried already twice to switch to Ubuntu in the past but never really took the time to start working with the OS, but this time I'm ready to spend some time to understand the ins and outs.
Anyway, I'm now trying to install Lotus Notes 8 client for Linux on my IBM Thinkpad T42 laptop running the latest version of Ubuntu (dual boot with Win XP). Lotus Notes is the official email client in my company.
I managed to get a legal copy of Lotus Notus Client for Linux via the admin of my company.

I followed the two following guides:

[LIST]
[*][HOWTO: Install & setup Lotus Notes for Linux]("http://ubuntuforums.org/showthread.php?t=222492")
[*][How to Install Lotus Notes 8 in Ubuntu Linux]("http://www.glump.net/dokuwiki/howto/notes_8_on_ubuntu")[/LIST]

but am stuck at the beginning of the procedure when I have to run the setup.

```
sudo ./setup.sh
```

The Lotus Notes installation wizard starts ok, but the screen stays blank and no text is displayed. I get the message "*Initializing Wizard........  Extracting Bundled JRE*." then the installation wizard window pops up but is blank (see screenshot enclosed).

I also saw the following remark in the terminal window:

```
/usr/share/themes/Human/gtk-2.0/gtkrc:71: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:241: Priority specification is unsupported, ignoring

```

Would anyone have an idea on what I could do to install Lotus Notes?
Thanks in advance

Chouf

PS: I'm a newbie so if it's very technical, tx to a explain clearly what I 'd have to do.

---

### Post by lucazade on 2007-09-27
I'm interested in installing notes 8 as well... :roll:
Here is a guide for [lotus symphony]("http://www.howtoforge.com/ibm_lotus_symphony_ubuntu_7.04") if you need it on ubuntu.

---

### Post by chouf on 2007-09-28
OK after some research on the Net, it seems that the issue is related neither to Ubuntu nor to Lotus Notes; but to Java and the way some applications are handled. As far as I could see on the forums, other people had the same kind of issue with other programs and other graphical bug (such as progress bar not displayed, windows blank...)

When looking on my PC, I see that I have *Sun Java 6 Web Start*, *Sun Java 5.0 Runtime* and *Sun Java 5.0 Plugin *installed. I do not find any other more recent package available so I suppose my Java installation is fine.

I had a look on the IBM website and found the following articles:

- [Detailed system requirements - Lotus Notes 8.0 for Linux]("http://www-1.ibm.com/support/docview.wss?rs=475&context=SSKTWP&context=SSKTMJ&q1=linux&q2=notes+8+linux&uid=swg27009485&loc=en_US&cs=utf-8&lang=en")
- [What is IBM Lotus Notes client for Linux and what Linux platforms are supported?]("http://www-1.ibm.com/support/docview.wss?rs=475&context=SSKTWP&context=SSKTMJ&q1=linux&q2=notes+8+linux&uid=swg21242594&loc=en_US&cs=utf-8&lang=en")
- [Notes 8 Linux client install setup.sh file will not launch]("http://www-1.ibm.com/support/docview.wss?rs=475&context=SSKTWP&context=SSKTMJ&q1=linux&uid=swg21265763&loc=en_US&cs=utf-8&lang=en")
- [Lotus Notes for Linux FAQs]("http://www-142.ibm.com/software/sw-lotus/products/product4.nsf/wdocs/linuxfaqs")

... but none of them were really able to help me out. So I'm still stuck at the first screen of the installation. It's so frustrating to be blocked by such a stupid problem.

Btw, I've noticed that the error...

```
/usr/share/themes/Human/gtk-2.0/gtkrc:71: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:241: Priority specification is unsupported, ignoring
```

... only appears in the terminal window when I close the Lotus Notes Installation Wizard window.

Anyone who have an idea how to fix this issue?

Thanks

chouf

---

### Post by bikeboy on 2007-09-28
I might be completely wrong here, but part of the notes from the first link you supplied list this:> Video
Windows: Hardware support for OpenGL
Linux:128 MB video RAM with XGL-compatible video driver from hardware OEM for OS; /etc/X11/xgl-hardware-list

It sounds like Lotus Notes wants XGL or a driver with XGL built in. I don't have the best understanding of that, but what sort of graphics card do you have and do you have any restricted drivers installed?

Administration > Restricted Drivers Manager

---

### Post by chouf on 2007-09-28
For info, when changing the theme I get another error message in the terminal. The Lotus Notes Installation Wizard window is still blank.

```
/usr/share/themes/Clearlooks/gtk-2.0/gtkrc:34: error: lexical error or unexpected token, expected valid token
/usr/share/themes/Mist/gtk-2.0/gtkrc:6: error: lexical error or unexpected token, expected valid token
```

---

### Post by chouf on 2007-09-28
> **bikeboy said:**
> I might be completely wrong here, but part of the notes from the first link you supplied list this:

It sounds like Lotus Notes wants XGL or a driver with XGL built in. I don't have the best understanding of that, but what sort of graphics card do you have and do you have any restricted drivers installed?

Administration > Restricted Drivers Manager

Hi there,
Tx for helping.
When going there I received the message "Your hardware does not need any restricted drivers."

When running the command from the IBM website I get the following

```
thomas@CCT41Ubuntu:~$ /etc/X11/xgl-hardware-list
bash: /etc/X11/xgl-hardware-list: No such file or directory
```

Chouf

---

### Post by bikeboy on 2007-09-28
Ok, so you don't have ati or nvidia graphics. Is it an Intel graphics chip by any chance?

---

### Post by chouf on 2007-09-28
> **bikeboy said:**
> Ok, so you don't have ati or nvidia graphics. Is it an Intel graphics chip by any chance?

Thanks for the follow up.
I do have an ATI Readon 9500 video card in the laptop with 128Mb.
I'm sure of it, because I already installed many T41 Thinkpad (with Windows XP)  before and this is the default hardware.

---

### Post by bikeboy on 2007-09-28
Ah ok, so you're probably using the 2d free driver for it (which is generally fine). It doesn't do XGL, hopefully someone with more knowledge can come along and work out whether the propietary ati driver and XGL are needed. I'm not sure so really don't want to suggest anything that could break your currently working (mostly) system.

---

### Post by chouf on 2007-09-28
Ok I found a solution to display the Lotus Notes installer.
I asked some developpers in my company to give me a hand.
Apparently the problem is linked to some installer wizards built on java. There are some incompabilities with the default windows manager. So before staring the program one should switch back to a ligher and more simple interface, with no fancy 3d effects and so on.

before starting the wizard, type the following command in the terminal

```
sudo metacity --replace
```

start the installer and you should now be able to see the text normally (see screenshot enclosed)

to switch back to the "normal" mode, type the following command:

```
sudo compiz --replace
```

hope this helps someone

Chouf

---

### Post by bikeboy on 2007-09-29
Hey chouf, glad you got it working. So it was a graphics related issue, but I was a little off track.

Could you mark the thread as "solved" so other people with Lotus install problems can find a solution?

---

### Post by Silx on 2007-10-08
The company I work at uses Lotus Notes, but I want to try version 8 on Ubuntu. Can someone point me to the installer?

---

