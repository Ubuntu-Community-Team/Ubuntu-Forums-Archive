---
title: "Beryl not working at all. Help!"
date: 2007-06-14
forum: Desktop Effects &amp; Customization
---

### Post by Jono04 on 2007-06-14
Well I'm really new to Linux but I'm starting to understand most of the commands etc.

I installed Ubuntu 7.04 then downloaded Beryl and installed it fine. I added the Beryl Manager to startup. But no matter what I do no themes will change and nothing will look different. Everything still looks the same as default Ubuntu settings.

I'm running Radeon 9600 with 2gb Ram and 2.04 Ghz.

Any help would be great.

Cheers Jono

---

### Post by wesxohio on 2007-06-15
> **Jono04 said:**
> Well I'm really new to Linux but I'm starting to understand most of the commands etc.

I installed Ubuntu 7.04 then downloaded Beryl and installed it fine. I added the Beryl Manager to startup. But no matter what I do no themes will change and nothing will look different. Everything still looks the same as default Ubuntu settings.

I'm running Radeon 9600 with 2gb Ram and 2.04 Ghz.

Any help would be great.

Cheers Jono

I had this problem a minute ago.. try just typing "beryl" in the terminal

that runs a compatibility test.. which mine didn't work, i got this error ```
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0

``` 
and it made my task bar disappear


I hope this works for you though

---

### Post by kaede on 2007-06-15
u must install ur ATI driver first to be able running beryl i guess. u can find tutorial on beryl site. :D

---

### Post by Jono04 on 2007-06-17
I got this error, any ideas?




jono@Jono:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension
jono@Jono:~$

---

### Post by dkaddict on 2007-06-17
Have you made the necessary additions/amendments to your 'etc/X11/xorg.conf' file?

I know for sure you have to add the relevant options in order to get compositing working with ATI graphics.

There are loads of how 2s and tutorials for getting beryl working. I don't use such 3d rendering apps but think it all looks pretty cool.

I am pretty sure that you will have to make a few amendments to your 'xorg.conf'. 

for example, at the end of xorg.conf, the following have to be present

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

That isn't all, however. There are quite a few more 'options which you will have to add in the correct sections of your xorg.conf. Also, and I am not sure about this so I suggest taking the time to learn all that you can about the subject, I am pretty sure that you will have to find out whether your card works with GLX or AIGLX? Again, you will need to gain some insight into the subject of GLX versus AIGLX.

I suggest having a pretty good look at this site 

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

 This is important!!!!!!!!  Make sure you use 'ctrl+alt+backspace' when you have made the amendments to your xorg.conf directory. If you don't, when you reboot  you will only be able to start Ubuntu in recovery mode and from there you will have to return 'xorg.conf' back to the state it was in when X worked properly. That happened to me a few times when playing about with 3d. You have to be careful when changing xorg.conf so swot up on it m8.

If you still have probs>>

Beryl, Compiz, etc are beta so are not going to work if they are implemented by someone who has absolutely no experience with xorg and/or direct rendering. One of the best things that has happened as a result of my switching to Ubuntu is the fact that I have had to actually teach myself how to use a computer by way of solving problems such as the one you have. I enjoy getting my teeth into a problem and solving it because I learn so much doing so. I have learnt more about comps in a year with Ubuntu than I did in 20 years with MS .

Try doing a Google and you will be overwhelmed with info. Or, start here 

[http://ubuntuforums.org/showthread.php?t=428397](http://ubuntuforums.org/showthread.php?t=428397)

That may cover your problem. There are loads of links to how2s that people have used.

Enjoy the challenge m8.

Hope I may have helped a little.

I have never been beaten by a problem which has arised since installing Ubuntu last year. How? These forums and Google.

peace

dk

---

