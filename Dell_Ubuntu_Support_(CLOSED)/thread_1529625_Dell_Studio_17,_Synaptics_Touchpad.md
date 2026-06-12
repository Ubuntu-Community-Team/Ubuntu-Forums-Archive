---
title: "Dell Studio 17, Synaptics Touchpad"
date: 2010-07-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by seventhapollo on 2010-07-12
So I've got a Dell Studio 17 (1747 to be exact, I believe). It's got the Synaptics multi-touch trackpad - which, in Windows 7, anyway, is quite useful. 

However, in Ubuntu it's more than slightly a nuisance. In fact, every time I touch the trackpad in more than one location (whether accidental or otherwise) the cursor will literally jump all over the screen. It's quite ridiculous. I've in fact gotten into the habit of running
```
sudo modprobe -r psmouse
``` every time I boot.

The fix I've seen floating around the forums for Synaptics touchpads involving 'xinput set-int-prop' does *not* work. Is there a way to get my multi-touch back? Even if not, can I at least disable the spaz 'feature'?

---

### Post by toddysean on 2011-02-23
I am also having this problem. Anyone got a fix?

---

### Post by s.orem on 2011-02-25
Have you tried this?

[http://manpages.ubuntu.com/manpages/maverick/man4/synaptics.4.html](http://manpages.ubuntu.com/manpages/maverick/man4/synaptics.4.html)

Not sure if it would help or not. I'm about to check it out and see if I get any benefit from it.

---

### Post by gberar on 2011-06-30
I have a dell studio XPS 16 and I'm running ubuntu 11.04.  

I am surprised that there isn't multiple threads on this.  Very Strange.  Wasting a lot of time on this bizarre behavior.  This is a huge problem for me.  

The following seems to help but I don't think it is optimal.  If anyone has any information that will help with this please let me know.

Where does syndaemon get started?  I wish to change the command line parameters to the daemon.  I cannot find where it starts.  I tried the suggestion in the documentation to put it in .xinitrc but that didn't work.  It starts but there is no clue as to where it starts.

This is what the default is

syndaemon -i 0.5 -k -R


This is what I want


syndaemon -i 1 -k -R

---

### Post by mikewhatever on 2011-07-02
@gberar
Just add the command to the startup programs to make sure it is run every time you login.

---

