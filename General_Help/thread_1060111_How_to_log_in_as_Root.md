---
title: "How to log in as Root"
date: 2009-02-04
forum: General Help
---

### Post by vamper on 2009-02-04
I have just installed Ubuntu 8.10 desktop edition again, and am trying to login from the main login screen as Root, but am unsure what the default password for Root login is I have tried my own password, and also tried leaving the password space blank and stil no luck, now I am curious what the default password is, or if there is a procedure to installing a password for root login.

Thank you in advance

---

### Post by snowpine on 2009-02-04
Ubuntu doesn't allow you to log in as root. You become root temporarily by using the 'sudo' command followed by your user password. Let us know what you need to do as root, and we can walk you through it.

For example, to install Firefox:

```
sudo apt-get install firefox
```

---

### Post by jerome1232 on 2009-02-04
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

At any rate as stated before, an account that is in the admin group can use sudo (gksu for graphical apps) to escalate their privileges to any user on the system, including root, you use your accounts password to authenticate.

---

### Post by vamper on 2009-02-04
I wanted to change the modem information(telephone#, username, and password) in the /etc/wvdial.conf, I have gone through all the prompts told to me in another thread in the wireless internet connection forum of this site but when I get to the the point where the file pops up and I can change the information I cannot save it I get a message at the top of the screen that says I do not have permission to change this file. So I tried logging in as 'root' to see if I could change it that way, but i can not

---

### Post by jerome1232 on 2009-02-04
Press alt+f2 then type this. sudo and gsku are how you escalate your privileges to the root account.

```
gksu gedit /etc/wvdial.conf
```

---

### Post by snowpine on 2009-02-04
Here's the command to edit that file with root privilages:

```
gksu gedit /etc/wvdial.conf
```

You use gksu instead of sudo because gedit is a graphical application. (If you use a different text editor, substitute that for gedit.)

The tutorial you're following probably tells you to log in as root because it was not specifically written for Ubuntu. Most other Linux distros allow you to log in as root; using sudo only is kind of an Ubuntu thing. ;)

---

### Post by redseventyseven on 2009-02-04
As the other two posters have stated, you don't need to log in as root. You need to temporarily escalate your privileges to "root" status by using the *sudo* command. In your case:

```
sudo gedit /etc/wvdial.conf
```

should do the trick.

EDIT: both "gksu" and "sudo" will work fine - gksu asks for your password using a graphical dialog box; sudo asks for your password in the terminal.

---

### Post by mb_webguy on 2009-02-04
> **redseventyseven said:**
> 
EDIT: both "gksu" and "sudo" will work fine - gksu asks for your password using a graphical dialog box; sudo asks for your password in the terminal.

There's more to [gksu and sudo]("http://www.psychocats.net/ubuntu/graphicalsudo") than that.  You should always run GUI apps with gksu, and command-line apps with sudo.  Most of the time, the results will be the same, but sometimes you'll get unexpected behavior if you're using sudo for a GUI app or gksu for a command-line app.  And on rare occasions, [very bad things]("http://ubuntuforums.org/showthread.php?t=181867") can happpen.  So it's better to make a habit of using the appropriate command for what you're doing .

---

### Post by vamper on 2009-02-04
I have been doing the sudo command - pehaps you should see what I mean

[http://ubuntuforums.org/showthread.php?p=6676315#post6676315]("http://ubuntuforums.org/showthread.php?p=6676315#post6676315")

This may help you understand - I have been tring the sudo thing over and over, I didn't want to get into to different topics in the same thread so I started this one here on basically how to log in as root, as I thought it may help me out, to change the permissioon to save the document for the dial up modem but it seems to be another problem.

---

### Post by snowpine on 2009-02-04
You should use 'gksu' instead of 'sudo' with a graphical application such as gedit. I think that is why you're getting the "** (gedit:576: WARNING **: Could not write gedit state file: Failed to create file '/root/.gnome2/gedit-2.KXHROU': No such file or directory" message.

---

### Post by vamper on 2009-02-04
Ok i got it figured out I didn't need to log in as 'root', the main isuue was that I was running, Ubuntu 8.10 64 AMD version, after some detailed reading on the topic, I discovered that there were dial up issues using an internal pci modem so perhaps there were also issues using external cable modems, second there was no gnome/gnome2 folders included with the 8.10 version and some of the replies using wvdial prompts were about gnome folders, so I replaced the operating system with Ubuntu 8.0.4 i386 32 bit version and the modem took immediately, and is working very well for the v34 mode it is running at, now to gigure out how to activate the 56K mode that is also available with this model of modem. I've made my very first steps into the exiting world of Linux/Ubuntu operating systems, perhaps Kubuntu will be in the near future - LOL

Thank yo u every one fo ryour replies and help on this matter
Cheers - :KS - vamper

---

