---
title: "Internet Explorer 6.0 4 linux (easy installer with wine)"
date: 2006-09-28
forum: Desktop Environments
---

### Post by sanone on 2006-09-28
I saw this link on OSNews ([http://www.osnews.com/story.php?news_id=16001]("http://www.osnews.com/story.php?news_id=16001")) 
and thought that Ubuntu users may find this useful. 

It's about an installer script which installs IE6 (and optional IE 5.5 and IE 5.0) with flash 9. It configures wine and creates a desktop icon. It's very easy to install, just run a script. And best of all it works very well!

If you have some websites that still require IE, please make the webdesigner change this, but in the mean time use this script to still visit these website. Or if you develop websites, like myself, this is extremly useful.

Well for more info check:
[http://www.tatanka.com.br/ies4linux/page/Main_Page]("http://www.tatanka.com.br/ies4linux/page/Main_Page")

Or for the direct link to the install guide:
[http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu]("http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu")

Have phun,
San

---

### Post by Kilz on 2006-09-28
Its a great script and I have it installed myself. But a word of warning to those that may not realize it. Using IE as your main browser is not safe even on Ubuntu. Its ok if you need it for one or 2 sites(like one from work), or to check the page your working on to see how it looks. But use Firefox as your main browser.

---

### Post by jdunn on 2006-09-28
Why would anyone want to use Internet Explorer?...Even on Windows?  I only use it for Windows updates.

---

### Post by skip910 on 2006-09-28
Just use the Firefox extension, IETab.

---

### Post by aysiu on 2006-09-28
> **jdunn said:**
> Why would anyone want to use Internet Explorer?...Even on Windows?  I only use it for Windows updates.
For website design purposes, mainly. That's what the creator of the script uses it for. That's what I use it for.

By the way, I have a step-by-step, Ubuntu-specific tutorial on IEs4Linux with screenshots:
[http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)

---

### Post by GadgetsGuy on 2006-09-30
IETab does not come in a Linux Flavor .... and that's a real shame!

---

### Post by blackmh on 2006-09-30
Ofcourse it doesn't. It actually uses IE so how can it work when there is no IE installed on system?

---

### Post by pgroover on 2006-10-10
Thanks for the link, I don't like IE but unfortunately some programs find it to be a necessity and this has me up and running great!!

---

### Post by aysiu on 2006-10-10
> **blackmh said:**
> Ofcourse it doesn't. It actually uses IE so how can it work when there is no IE installed on system?
Except with IEs4Linux... it *is* installed on your system.

---

### Post by xunshirine on 2006-12-07
> **Kilz said:**
> Its a great script and I have it installed myself. But a word of warning to those that may not realize it. Using IE as your main browser is not safe even on Ubuntu. Its ok if you need it for one or 2 sites(like one from work), or to check the page your working on to see how it looks. But use Firefox as your main browser.
Hi. Could you explain why do you think in this way .How can ntfs malwares can harm etx3 files? Are Ubuntu users in danger of being infected with windows malwares?
> **aysiu said:**
> Except with IEs4Linux... it *is* installed on your system.

What is the differ between openin up web page via IE and IETab? Does FF prevents the exploits of IE, if IETab used? Thanks

---

### Post by aysiu on 2006-12-07
IETab uses IE--actual IE, not just the appearance of Internet Explorer.

The only difference between IETab and normal IE is that IETab *appears* to be a tab within your Firefox browser (even though it's really IE) and normal IE appears to be a completely separate application.

Normal IE - is a separate application and appears to be separate
IETab - is a separate application but appears to be integrated with Firefox

---

### Post by shane2peru on 2006-12-19
I installed this IEs4Linux and it was easy.  However I'm curious how can I get this linked to my wine installation?  I know it runs via wine, however when I try and install ACT!6.0 by Symantec, it refuses to install saying that IE5.5 or higher is required.  However it is already installed.  How can I link it?  Thanks.  

Shane

Ps.  I have installed it from the CD before too, but no luck there either.  IE6 is on this disk.

---

### Post by shane2peru on 2006-12-19
Ok, never mind.  I got re-installed it from the CD, and seems to be working.  Some minor errors, but fitting of a new thread.

Shane

---

### Post by john_spiral on 2006-12-19
Nice easy install, just followed the instructions on the site. 

I'm sure this software will give windows -> linux migration projects an extra push.

---

### Post by dorcssa on 2006-12-20
I can't install java using wine+firefox, or ie. A dialog box appear: An unknown error has been encountered: HTTP status code=302. What should I do? I only wanted to see the new transformermovie trailer, and my boyfriend said, that I must not erase windows, cos I can only see it with that. I didn't believe him, but I'm starting to..

The link to the trailer: [http://uk.promotions.yahoo.com/transformers/](http://uk.promotions.yahoo.com/transformers/)

---

### Post by dorcssa on 2006-12-20
Now I'm under windows, and it was to clicks with java, and no frustration. This video player causing the problem: [http://vividas.com/support/streamingsupport.html](http://vividas.com/support/streamingsupport.html)

Under linux, it can be viewable under wine only. But I can't install java...should I make up a VMw server to solve this kind of problem in the future? Or it wouldn't help? Do I really have to keep win because all of this? (Or maybe I'll watch it on my boyfriends machine..but that case, it is proven that I can't live without windows. This is frustating.)

---

### Post by shane2peru on 2006-12-20
> **dorcssa said:**
> Now I'm under windows, and it was to clicks with java, and no frustration. This video player causing the problem: [http://vividas.com/support/streamingsupport.html](http://vividas.com/support/streamingsupport.html)

Under linux, it can be viewable under wine only. But I can't install java...should I make up a VMw server to solve this kind of problem in the future? Or it wouldn't help? Do I really have to keep win because all of this? (Or maybe I'll watch it on my boyfriends machine..but that case, it is proven that I can't live without windows. This is frustating.)

FYI,  no, you don't need Windows to view this.  I was able to open it up and play it in Linux, not using wine.  You really don't need wine to run this or IE.  [ ]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox") is the guide to installing Java with Firefox.  You can search this guide and find out how to setup a lot of things if you are using Ubuntu Edgy.  Remember BACKING UP is very important, in case you mess something up.  Chances are if you are new, you will mess things up.  If you need help, search the forums for how to do these things, and if you can't find what you are looking for start a new thread.  

Shane

---

### Post by dorcssa on 2006-12-21
I'm using Dapper.. So you're saying, that I need the latest java, and the one that's in the repos is not enough? And when I installing this new version manually, do I have to uninstall the installed one, wich I installed through synaptic?

---

### Post by shane2peru on 2006-12-21
Do a search on 'Dapper customization guide'   I know there is one of them around too, it should have the same info and help you be able to get Java installed for Dapper.

Shane

---

### Post by dorcssa on 2006-12-24
Well, I installed the latest jre using [this]("http://ubuntuforums.org/showthread.php?t=319138") guide, and the java webpage verify it, but I still cannot view it, it redirects me to the vividas support side. Now what can I do?

Maybe I forgot to mention it, that I want to see the full screen high definition trailer? :) Coz when I click to see full screen, that's when I'm being redirected.

---

### Post by shane2peru on 2006-12-24
Ok, here is a link [here]("http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox") to an easier guide.  I would go all the way down through the Flash part and install the flash part.  I think it is more a flash issue, but I'm not sure.  This guide will help.  The one you found looked a little complex.  You may want to book mark this guide I gave you and refer to it often for getting your computer all setup.  Enjoy!

Shane

---

### Post by dorcssa on 2006-12-24
I know this guide(and yes, in the early days when I was confused, it was very useful), and I have the latest flash and java (what's availabe in dapper), and it's still redirects me when I click full screen.(And the site tells me the only way to see the video is under wine.) By the way, if I hadn't have flashplayer, than I couldn't see the two faces, and choose to click one of them. I'm hopeless, so I have to watch all the hd videos at my boyfriends on his windows. :(

---

### Post by shane2peru on 2006-12-24
Well, your other option is upgrade to Edgy :D   I really can't be of much more help to you since I'm not on Dapper.  Search around the forums a little more, or start a new thread and maybe someone out there with more knowledge than myself, and a Dapper system can be of help to you.  I really don't believe that wine is the answer.  It is good for somethings, but I don't really consider this one of them.

Shane

---

### Post by dorcssa on 2006-12-24
Tell me one thing. When you on the transformer trailer site, and click on the full screen option, what do you get? You get the full screen movie?

I'm not considering of upgrading(although my friend who use ubuntu tell me to do so), I'm fine with dapper at the moment. And just reinstalled it, so I've got enough of installing systems and programs. :D I'll try asking around with a new thread than. Thx for helping though.

---

### Post by shane2peru on 2006-12-24
> **dorcssa said:**
> Tell me one thing. When you on the transformer trailer site, and click on the full screen option, what do you get? You get the full screen movie?

I'm not considering of upgrading(although my friend who use ubuntu tell me to do so), I'm fine with dapper at the moment. And just reinstalled it, so I've got enough of installing systems and programs. :D I'll try asking around with a new thread than. Thx for helping though.

I can understand that! :D   When I click on the full screen I get the same support screen that you were getting before.  When I click on the smaller version, it plays fine.  So I guess there is no real need to upgrade. :D  

Shane

---

### Post by dorcssa on 2006-12-24
> **shane2peru said:**
> I can understand that! :D   When I click on the full screen I get the same support screen that you were getting before.  
Shane

So the whole process of upgrading my java and flash was useless... :( So wine is really needed, and we end up where we started, that I can't install java to firefox or ie under wine. I hope that this vividas something will stand up for the linux challenge soon. :)

---

### Post by rykel on 2006-12-28
Hi,

Just wanted to let you all know that ies4linux works perfectly on Edgy... HOWEVER, it seems like the default installation places IE6 into /home/me/.ies4linux, rather than /home/me/.wine, the place where the WINE Drive_C is actually set up.

This causes a bit of a problem because programs which require IE will NOT find it... is there a way to install ies4linux into the Ubuntu-set WINE folders?

Thanks for viewing!

---

