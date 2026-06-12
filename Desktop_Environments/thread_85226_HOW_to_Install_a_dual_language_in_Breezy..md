---
title: "HOW to: Install a dual language in Breezy."
date: 2005-11-02
forum: Desktop Environments
---

### Post by zechy on 2005-11-02
Is it possible to toggle betwen Eglish and chinese in breezy-Badger?

Can we input Chinese Chararcters?

How do we activate the Chinese Language Format in Breezy?

If So, Can we also encode in Chinese Format? I noticed there is no Chinese Keyboard format in Breezy. What Should I do to activate it?

Hoping for your enlightenment on This. I am a total stranger to Linux. Just acquired the breezy Ubuntu 5.10 through internet download. Had it installed in our Church's computer.

I do not know anything about the line commands of the linux encoding. Please give me a clear guide to solve this problem. Thank you in advance and God Bless you.

---

### Post by Appolusionist on 2005-11-02
[quote=zechy]Is it possible to toggle betwen Eglish and chinese in breezy-Badger?
 
Can we input Chinese Chararcters?
 
How do we activate the Chinese Language Format in Breezy?
 
If So, Can we also encode in Chinese Format? I noticed there is no Chinese Keyboard format in Breezy. What Should I do to activate it?
 
Hoping for your enlightenment on This. I am a total stranger to Linux. Just acquired the breezy Ubuntu 5.10 through internet download. Had it installed in our Church's computer.
 
I do not know anything about the line commands of the linux encoding. Please give me a clear guide to solve this problem. Thank you in advance and God Bless you.[/quote]
 
Please take a look at [http://ubuntuguide.org/#scim]("http://ubuntuguide.org/#scim"). This appear to be what you are looking for? Also you might take a look at [http://www.mrbass.org/linux/ubuntu/scim/]("http://www.mrbass.org/linux/ubuntu/scim/"). Both of these are geared for Hoary 5.04, but should point you in the right direction for Breezy.

---

### Post by zechy on 2005-11-04
Thank you for the quick reply. Those instructions are very interesting... 

I am very sorry, but since I am entirely new with this operating system and has no background whatsoever with the so called "terminal". 

how do I type those "sudo" thing? 

where do I go from my desktop to do those? and should I copy them exactly the way they are written? can I just copy-paste those in the website? 

I notice that those are the codes for 5.04, do they apply to 5.10 also? 

Please be patient with my ignorance. am really very new at this and am willing to learn how i can do this. because I believe, this is a better operating system than my previous system;).

Thank you for your help in advance.

---

### Post by hunteramor on 2005-11-05
it's hard to give step-by-step instructions since i don't know how much (if anything) i can assume you already know how to do.  i'm something of a newbie to this too, but since i've dealt with getting chinese working here too, i thought i'd give the explanation a shot.  anyone more experienced, feel free to jump right in.

first of all, it'd be a good idea to start by reading some of the posts in the absolute beginner talk forum:
[http://ubuntuforums.org/forumdisplay.php?f=73](http://ubuntuforums.org/forumdisplay.php?f=73)

to get to the 'terminal,' choose it in the accessories menu.  you'll be using it quite a bit! you may also be able to get to 'open terminal' by right-clicking on the desktop but i don't remember if that is standard in breezy or not.

sudo stands for "super user do" - many things you'll need to do in ubuntu require super user access.  when you use the sudo command, you'll be prompted for your password and you'll basically be giving permission for the following command to be performed.

in the terminal, paste in the following text:

sudo apt-get install language-pack-gnome-zh language-pack-gnome-zh-base language-pack-zh language-pack-zh-base language-support-zh scim scim-chinese scim-tables-zh zh-autoconvert xfonts-cmex-big5p xfonts-intl-chinese xfonts-intl-chinese-big xpdf-chinese-simplified xpdf-chinese-traditional tfm-arphic-bkai00mp tfm-arphic-bsmi00lp tfm-arphic-gbsn00lp tfm-arphic-gkai00mp ttf2pt1-chinese libtabe-db libtabe2 libzh0 im-switch

enter your password when prompted.

that should be a good base for you to build on, as far as chinese support goes.  when you get to understand things more, i'd recommend you do a search in synaptic for zh and chinese, and add the packages that look appropriate.  (don't do uim and scim at the same time, though!)

now go to system/preferences/sessions in the menu

select the startup programs tab and add the command scim -d

restart and you should be able to switch input languages with ctrl+space or clicking on the keyboard icon.

if you want to change the default language of ubuntu, go to system/administration/language selector and choose chinese.

hope that works for you, post any further questions here!

---

### Post by zechy on 2005-11-05
thank you for the quick reply... I will try to do that right away and get back to you asap. Thanks again. God Bless you.

---

### Post by PeaceMessenger on 2005-11-05
I'm using Ubuntu Breezy 5.10 with KDE installed.
I followed the instructions on the website posted above [http://www.mrbass.org/linux/ubuntu/scim/](http://www.mrbass.org/linux/ubuntu/scim/).


To install via internet (universe repositories must be enabled)
 sudo apt-get install uim anthy scim-gtk2-immodule scim-uim scim-chinese scim-hangul scim-tables-zh scim-tables-ja scim-tables-ko
 
 Add SCIM to startup for X11
 sudo touch /etc/X11/Xsession.d/74custom-scim_startup
 sudo chmod 646 /etc/X11/Xsession.d/74custom-scim_startup
 echo 'export XMODIFIERS="@im=SCIM"' >> /etc/X11/Xsession.d/74custom-scim_startup
 echo 'export GTK_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
 echo 'export XIM_PROGRAM="scim -d"' >> /etc/X11/Xsession.d/74custom-scim_startup
 echo 'export QT_IM_MODULE="scim"' >> /etc/X11/Xsession.d/74custom-scim_startup
 sudo chmod 644 /etc/X11/Xsession.d/74custom-scim_startup 


If you installed kubuntu-desktop (KDE) and plan on logging into KDE session do this in terminal
 sudo touch ~/.kde/Autostart/startscim
 echo '"#!/bin/sh"' >> ~/.kde/Autostart/startscim
 echo "scim -d" >> ~/.kde/Autostart/startscim
 sudo chmod 745 ~/.kde/Autostart/startscim 


> 

I didn't have a problem until the end.  The line   echo '"#!/bin/sh"' >> ~/.kde/Autostart/startscim... I get a bash   Permission Denied error.

When I restart Kubuntu now I get a dialogue asking what program to open scimstart with.  So it seems I've been led to change my startup file to do something that doesn't work.  Can anyone help me to set it right.  Preferably I'd like to be able to input Chinese into Kubuntu.  At the very least, I'd like to get rid of the dialogue box that comes up on startup.

I'm a noob.  Probably over my head here.  I thought this would be simpler.  Please lend me a hand if you can.

Thanks,

---

### Post by hunteramor on 2005-11-07
i've never used KDE, so take everything I say with a grain of salt.

that method seems unnecessarily complicated.  at least in gnome, it's pretty straightforward to add a startup program through menus.  is there a preferences/sessions menu in KDE or its equivalent?  

in gnome, to get scim working yyou just add scim -d as a startup command after installing the packages (or at least that's all i *remember* having done)

for a permission denied error like that, 9 times out of 10 it'll be solved by using sudo.  did you try using

sudo echo '"#!/bin/sh"' >> ~/.kde/Autostart/startscim

instead?

---

### Post by PeaceMessenger on 2005-11-07
Using sudo I still get the permission denied error.  I tried that. 

Thanks for your advice though, I will try to figure out the menu's and see if there is a way there.

I found some other posts that seemed to indicate that SCIM worked in Hoary but was broken in Breezy... so I'm not sure if there is hope or not.  I may have to keep going back into Windows when I need to work in Chinese.

My advice for those using KDE with Ubuntu in Breezy who are new to Linux like me, be a little careful following commands you find posted in forums that were designed for previous versions... especially if you don't know exactly what the commands do as it is then hard to reverse them!

---

### Post by hunteramor on 2005-11-07
it was worth a shot, anyway.  i read a lot of people saying that scim was broken for them in breezy, but it worked okay for me when i upgraded.

you might want to make sure you don't have the uim package installed.  i ran into a lot of problems with scim when i had uim too.  scim-uim is okay though.

---

### Post by PeaceMessenger on 2005-11-08
This link made me think that SCIM isn't going to work in Breezy at all but you give me hope!
[http://ubuntuforums.org/showthread.php?t=75157&highlight=asian]("http://ubuntuforums.org/showthread.php?t=75157&highlight=asian")

I did have both SCIM and UIM installed and so I'm going to try SCIM without UIM, and then UIM with SCIM, and see if I can get either one to work. 

Then I'll be searching for more Chinese fonts.  
Thanks

---

