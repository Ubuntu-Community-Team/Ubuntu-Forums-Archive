---
title: "Compiz Fusion Not Workig Either Way"
date: 2007-12-16
forum: Desktop Effects &amp; Customization
---

### Post by Fzero on 2007-12-16
I've tried to install Compiz Fusion several times but for some reason when I install it it doesn't work all I can run is the CompizConfig Settings Manager. Here is what happens when I try to run Compiz Fusion

Computer@laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:3150 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald

(emerald:4052): Wnck-WARNING **: Unhandled action type (nil)

(emerald:4052): Wnck-WARNING **: Unhandled action type (nil)

(emerald:4052): Wnck-WARNING **: Unhandled action type (nil)

(emerald:4052): Wnck-WARNING **: Unhandled action type (nil)

(emerald:4052): Wnck-WARNING **: Unhandled action type (nil)

(emerald:4052): Wnck-WARNING **: Unhandled action type (nil)

(emerald:4052): Wnck-WARNING **: Unhandled action type (nil)

(emerald:4052): Wnck-WARNING **: Unhandled action type (nil)

(emerald:4052): Wnck-WARNING **: Unhandled action type (nil)

(emerald:4052): Wnck-WARNING **: Unhandled action type (nil)

(emerald:4052): Wnck-WARNING **: Unhandled action type (nil)

(emerald:4052): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

In other times Compiz Fusion has worked but then the settings manager doesn't.

If anybody can help me fix my problem I would really appreciate it.

---

### Post by Fzero on 2007-12-16
Bump

---

### Post by rayman_3d on 2007-12-16
ok , give me some information :
1- Graphic Card type
2- ubuntu version or the kernel (uname -r)
and i will help u in this

---

### Post by erfahren on 2007-12-16
[Google search - ubuntu Checking for Xgl: not present](http://www.google.com/search?hl=en&q=ubuntu+Checking+for+Xgl%3A+not+present&btnG=Search)

this has been covered many times before

---

### Post by Fzero on 2007-12-16
I have an ATI graphics card.

---

### Post by Ub1476 on 2007-12-16
Post the result of:

```
lspci | grep VGA
```

and

```
lsb_release -a
```

---

### Post by Fzero on 2007-12-16
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty

---

### Post by erfahren on 2007-12-16
enable the restricted driver (System > Admin > Restricted Drivers Manager) and reboot

then in the terminal:
```

sudo apt-get install xserver-xgl

```

restart X (ctrl+Alt+backspace) and enable desktop effects

--- OH, hold up... if you're using feisty the instructions are different -- which version of Ubuntu?

---

### Post by Fzero on 2007-12-16
I'm using Feisty but last time I restarted the Xserver it some how messed up Ubuntu and when I tried to log in it was like terminal.

---

### Post by Ub1476 on 2007-12-16
Alright, it looks like you are using Ubuntu 7.04. Why not use the latest 7.10? It will probably work better for you.

If you want to stick with Feisty Fawn though, [here's]("http://ubuntuforums.org/showthread.php?t=488385&highlight=compiz+ati+howto") a good guide to get Compiz-Fusion up and working. You can drop the "Beryl" part of the guide.

If you decide to use the latest version of Ubuntu, 7.10 Gutsy Gibbon, take a look at [this]("http://ubuntuforums.org/archive/index.php/t-586038.html"), if it doesn't work out of the box already.

---

### Post by Fzero on 2007-12-16
I'll try the guide right now and post again when I finish. Thanks for the help :)

---

### Post by Fzero on 2007-12-16
> 
The first thing we need to do is add the security key, do this by pasting into a terminal:

Code:

sudo wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -



This part of the tutorial doesn't work.

---

### Post by Fzero on 2007-12-16
I finished the tutorial but now I get an error except it must be wrong because I have ran Beryl on my laptop and I have also ran Compiz Fusion 

Here's the error

Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

The CompizConfig Settings Manager doesn't open either.

---

### Post by Fzero on 2007-12-16
Bump

---

### Post by Ub1476 on 2007-12-16
You can give [this guide]("http://www.ubuntu1501.com/2007/08/compiz-fusion-in-fiesty-with-xgl.html") a shot too. If it doesn't work I have no other suggestio than getting the latest Ubuntu.

BTW, remember to remove your .compiz/.beryl (the folder where your settings are stored for compiz) before you attempt to install. It's located in your home directory, but it's hidden. Press alt+h to show hidden files.

---

### Post by Fzero on 2007-12-16
gpg: no valid OpenPGP data found.

I get that message when I go to add the repository key.

I think I'll just give upgrading to 7.10 another go.

---

### Post by Ub1476 on 2007-12-16
I suggest doing a clean install.

---

### Post by Fzero on 2007-12-16
My only problem is when I install 7.10 and then boot up I get an error which doesn't allow me to boot into Ubuntu. I have gotten it to work by using the upgrade feature in 7.04.

---

### Post by Ub1476 on 2007-12-16
> **Fzero said:**
> My only problem is when I install 7.10 and then boot up I get an error which doesn't allow me to boot into Ubuntu. I have gotten it to work by using the upgrade feature in 7.04.

Could you post the error here? If you upgrade you're likely to leave a messy load of config files which might be the reason Visual Effects is not working.


Also check the checksum of the CD, and check it for defects.

---

### Post by Fzero on 2007-12-16
Right now I'm on 7.04 not 7.10. And I have checked for defects.

[The error I have]("http://ubuntuforums.org/showthread.php?t=640860")

---

### Post by Ub1476 on 2007-12-16
That looks like the infamous tty problem. Try using the alternate text-based CD (check it at the download page). Remember to burn at slowest speed possible.

---

### Post by Fzero on 2007-12-16
So the alternate ISO on this page? [Link]("http://releases.ubuntu.com/7.10/")  A text based installer would probably be too difficult for me.

---

### Post by Fzero on 2007-12-16
Bump

---

### Post by erfahren on 2007-12-16
> **Fzero said:**
> So the alternate ISO on this page? [Link]("http://releases.ubuntu.com/7.10/")  A text based installer would probably be too difficult for me.
yes - and using the Alternate CD isn't all that difficult, I don't think it's any more difficult than using the Live CD (maybe even a bit easier in a way).

There is an excellent walk-through guide to using it (with screenshots) here: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Fzero on 2007-12-16
I think I might just stick with 7.04 :(

---

### Post by erfahren on 2007-12-16
> **Fzero said:**
> I think I might just stick with 7.04 :(
I wasn't going to mention this and let you decide for yourself, but I actually used Gutsy for about a month and reverted back to Feisty.

One of the reasons was the suspend/hibernate issue for me among other things. Feisty just works better all around on my notebook.

- you're not alone there, so turn that frown upside down! :)  -- lol
--- sorry, I couldn't resist

---

