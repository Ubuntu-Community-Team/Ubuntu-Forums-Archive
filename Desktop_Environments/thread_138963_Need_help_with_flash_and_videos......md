---
title: "Need help with flash and videos....."
date: 2006-03-02
forum: Desktop Environments
---

### Post by PaintballMan10988 on 2006-03-02
Hello everyone,

First things first, I am a total newbie to Linux and Ubuntu.  I am trying to install a flash player to run Yahoo pool.  Firefox linked my to this site for the plug in I was missing  [http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp)

I chose the second Linux one, as I don't know what RPM is or if I have it.  It downloaded just fine.  The instructions for installations are giving me some trouble.  It says...


1.At the terminal: Type:
su 
2.Enter the root password. 
3.Change to the directory in which you want to install. Type:
cd <directory path name>
For example, to install the software in the /usr/java/ directory, Type:
cd /usr/java/
Already, I have been told to use sudo in place of su.  I still can't seem to install the program, and I have no real idea as to the use of the terminal.  Does anyone have a better/easier choice of flash player?

I am also looking for plug ins for totem.  I cannot play any videos at the moment, no WMV, quick time, or other format.  When i try to play a video it tells me...

 “There were no decoders found to handle the stream, you might need to install the corresponding plugins”

Huh?  I do not know what plug ins I need, or where to find them. Help?

Also, are there any other helpful hints to running flash and or videos on ubuntu?

Thank you so much,

Mike

P.S.  Every time I post a comment, I get logged out of the forums, and logging in again does not work.  When I enter my password, it brings up the “thank you for logging in” page, but the page it directs me to does not show me as logged in.  I have to change my password to stay logged in.  Even checking the little “keep me logged in on this computer” button doesn't work.  Any ideas on this?

---

### Post by akiro.yamamoto on 2006-03-03
Check the first link in my sig for info. Go to the Restricted formats section.
BTW: Welcome to Ubuntu Linux ;)

---

### Post by incubus on 2006-03-03
You can also install Java and Flash as you proceeded, but the traditional Debian (easier) way would be:

sudo apt-get install j2re1.4 flashplayer-mozilla

You probably need to enable some repositories first. Besides Mr. Yamamoto's links, also check:

[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

incubus

---

### Post by akiro.yamamoto on 2006-03-03
Yeah the PLF repo is a nice touch! ;)
## PLF REPOSITORY
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) breezy free non-free 
If you add this to your source.list you can download most of the restricted formats
packages from Synaptic. Cooooooool!

---

