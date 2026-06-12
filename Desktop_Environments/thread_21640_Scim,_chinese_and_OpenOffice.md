---
title: "Scim, chinese and OpenOffice"
date: 2005-03-23
forum: Desktop Environments
---

### Post by b33rc4n on 2005-03-23
Hi everyone. 
Ok so here is my little problem. I have gotten scim with scim-chinese and other scim-BLAHBITZ working with gaim and mozilla &#22826;&#22909;&#20102;&#65281; The chinese fonts looks good and everything has been smooth sailing. That is until I tried to use scim with oowriter (or anyother openoffice app for that fact) and the characters I wrote just didnt want to end up on the document page. Is this a known problem or am I just to big a noob here?  :oops: 

Oh yes one more thing: The fonts in mozilla (the english text) looks abit under the weather. Anybody knows why/how this happened. It looks fine without the ~/.gnomerc file.

This is what "locale -a" throws at me:
```

C
POSIX
zh_CN
zh_CN.gb18030
zh_CN.gb2312
zh_HK
zh_HK.big5hkscs
zh_TW
zh_TW.big5
```

and this is what is in my ~/.gnomerc

```
#!/bin/sh

export LANG=zh_CN.gb2312
PATH=$HOME/bin:$PATH

export G_BROKEN_FILENAMES="@locale"
export XMODIFIERS=@im=SCIM
export GTK_IM_MODULE=scim
scim -d&

exec x-session-manager

```

there is NO ~/.xsession or ~/.bashrc

I just want to say that Ubuntu is a great dist and I love it, but I really want this to work.

---

### Post by adrian440 on 2005-03-23
I have it working (oowriter), I don't use .gnomerc, but instead use .xsession. Its contents are:

scim -d
export XMODIFIERS=@im=SCIM
export GTK_IM_MODULE=SCIM
gnome-session

That file (.xsession) is set executable, 

chmod +x .xsession

Then I started a gnome session, picked the language as chinese (utf8), and session as "default system session". I use utf8 day to day, and can still write gb2312 emails in evolution, so maybe that's the key difference between your system and mine.

Hope this helps,
Adrian.

---

### Post by b33rc4n on 2005-03-23
Thank you!
I am now running the same config as you are. The OO suite is running fine with input but some of the characters gets translated into empty squares... very strange

and...

synaptic now crashes whenever I try to install new packages. I saw that synaptic checks the locales and then does something with scim just before it starts. I only got that message once though. 

THNX in advance

---

### Post by adrian440 on 2005-03-24
Make sure you have these fonts:
ttf-arphic-gkai00mp
ttf-arphic-gbsn00lp

You can do this without synaptic by typing
dpkg -l ttf*
and see if they have ii (installed). If they're not installed "sudo apt-get install" them. As for your synaptic problem, could you start it in a terminal (sudo synaptic) and see post what it prints out when you try to install new packages. If you're still having locale issues, you can always reconfigure them thus:
sudo dpkg-reconfigure locales

---

### Post by b33rc4n on 2005-03-24
well synaptic crashes whenever I try to install a selected package. 

This is the only thing that has been spat out into the terminal by synaptic
```

# synaptic
Launching a SCIM daemon with Socket FrontEnd...
GTK Panel of SCIM 1.0.2

Starting as daemon ...
#

```
I dont get any other error message. It is really wierd. Any suggestions??

---

### Post by adrian440 on 2005-03-24
I'm a little confused as to how you can run synaptic without sudo, I guess you've just run sudo -s first. As yourself (not as root), what do you get when you just type locale? I don't get the message you get when running synaptic in a terminal (loading scim daemon &#20160;&#20040;&#30340;). I've checked that when synaptic is running, it is not running an extra version of scim as root. Perhaps your system is and that's the problem. Here's some sample output of my terminal:
[INDENT]adrian@griffon:~ $ locale
LANG=zh_CN.UTF-8
LC_CTYPE="zh_CN.UTF-8"
LC_NUMERIC="zh_CN.UTF-8"
LC_TIME="zh_CN.UTF-8"
LC_COLLATE="zh_CN.UTF-8"
LC_MONETARY="zh_CN.UTF-8"
LC_MESSAGES="zh_CN.UTF-8"
LC_PAPER="zh_CN.UTF-8"
LC_NAME="zh_CN.UTF-8"
LC_ADDRESS="zh_CN.UTF-8"
LC_TELEPHONE="zh_CN.UTF-8"
LC_MEASUREMENT="zh_CN.UTF-8"
LC_IDENTIFICATION="zh_CN.UTF-8"
LC_ALL=
adrian@griffon:~ $ sudo synaptic

[/INDENT]
How did you go with the font thingy?

---

### Post by b33rc4n on 2005-03-26
Hi again!
Well the fonts in openoffice are still screwed up but I can enter characters in gedit so I'm content to leave it like that.
I managed to add hoary repositories in a warty installation. That seemed to create some problems and after I did a complete upgrade of the system synaptic started running again.

I still don't know why the characters aren't recognized in openoffice though.

---

### Post by hunteramor on 2005-11-08
same problem here....  i can type these characters in every other application, but not openoffice.

---

### Post by AiBo on 2006-01-05
I am out of my league here, but I as well am suffering from the same problems.

All other programs seem to be accepting input ok  (firefox, evolution, GAIM...) it seems only that OpenOffice struggles with my input (things like &#36710; which as you can see works fine here).

I have tried different font settings.  The result seems that a bigger blank space is left in place of the character?!?

I did have similar problems in Evolution, especially with Chinese co-workers receiving my Chinese emails, until I switched the font to Chinese Simplified (GB18030).  After that it was smooth sailing.

I am very NEW to Linux and hence also to Ubuntu.  I tried as much of the above as much as I could, but with no siucess.

Chinese input is very very inportant to my work.  I would like to get this sorted out.

Thanks! &#35874;&#35874;

---

### Post by ymeng on 2006-02-23
Sounds like you guys are ahead of me. I am a newbie, just started to use Ubutu5.1. Badger. I can read Chinese. I tried to follow instructions on [http://makuchaku.info/amnesty/#scim](http://makuchaku.info/amnesty/#scim) to set up Chinese input.

When I tried "sudo apt-get install scim", I got
E: "Couldn't find the package scim".

Any ideas?

Thanks for your help.

Here is the screen dump:

ym@latitude:~$ sudo apt-get install scim scim-modules-socket scim-modules-table scim-pinyin scim-tables-zh scim-input-padReading package lists... Done
Building dependency tree... Done
E: Couldn't find package scim
ym@latitude:~$ apt-cache search scim
ym@latitude:~$ sudo apt-get install scim
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package scim
ym@latitude:~$ sudo apt-get install scim-chinese
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package scim-chinese
ym@latitude:~$ sudo apt-get install scim
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package scim
ym@latitude:~$ apt-cache search scim
ym@latitude:~$
ym@latitude:~$ sudo apt-get install scim
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package scim
ym@latitude:~$

---

