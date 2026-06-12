---
title: "[SOLVED] AWN Main Menu Applet"
date: 2007-09-05
forum: Desktop Effects &amp; Customization
---

### Post by Inxsible on 2007-09-05
In the main menu applet in awn, I seem to missing a few of the icons. Please see the screenshot. There are other icons missing too is other parts of the menu.

Is there a solution to this?

---

### Post by Rupertronco on 2007-09-05
Timon (awn developer) said that he's still working on the main menu applet. It's not quite finished. One of the problems most often experienced is the one you're encountering. Right now, if you're using the latest version, you already have the most successful main menu applet. (source = awn forums)

Hopefully by the time they produce the first release most of these annoyances will be cleared up.

---

### Post by Inxsible on 2007-09-05
Alright, Thanks for the info

---

### Post by [Alsharifi] on 2007-09-06
any write up on how to install it,and does it come with that stack option or is that seperate?

it will be appreciated.

---

### Post by whitingx on 2007-09-06
> **'[Alsharifi] said:**
> any write up on how to install it,and does it come with that stack option or is that seperate?

AWN debs containing stacks can be found and installed from here;

[http://syzygy42.tuxfamily.org/]("http://syzygy42.tuxfamily.org/")

Hope this helps.

---

### Post by Inxsible on 2007-09-06
> **'[Alsharifi] said:**
> any write up on how to install it,and does it come with that stack option or is that seperate?

it will be appreciated.

```
gksudo gedit /etc/apt/sources.list
```Add the following lines to the end of the file. Save and close```
deb http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
```Then back in the terminal do this```
sudo apt-get update && sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr
```

---

### Post by [Alsharifi] on 2007-09-06
thanx alot that did it,but its still buggy huh?.

u guys missing some icons on the main menu,and why isnt there a "system" or "places" icons ?

---

### Post by bubuzzz on 2007-12-14
i cannot complete the installation because of errors 

> Get:5 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release [26.9kB]                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources              
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release                               
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Packages       
Hit [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/avant-window-navigator Sources        
Fetched 27.1kB in 11s (2449B/s)                                                
Reading package lists... Done
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package avant-window-navigator-bzr

where i try apt-get update, this error appears again : no_pubkey 3e231ac7f4ecf181
any help, please ? i just start to use ubuntu just a few day ago:guitar:

---

