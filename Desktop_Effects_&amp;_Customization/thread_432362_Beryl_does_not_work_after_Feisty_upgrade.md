---
title: "Beryl does not work after Feisty upgrade"
date: 2007-05-03
forum: Desktop Effects &amp; Customization
---

### Post by AZcat on 2007-05-03
Hi, Beryl was working in Edgy but is dead in the water after upgrading to Feisty.

Entering glxinfo and fglrxinfo returned the following:

jyf@scuzzy:/usr/local/bin$ glxinfo | grep "render"
direct rendering: Yes
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: RADEON 9700 PRO

jyf@scuzzy:/usr/local/bin$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9700 PRO
OpenGL version string: 2.0.6458 (8.36.5)


Issuing "beryl" in a terminal returned the following:

jyf@scuzzy:/usr/local/bin$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

Followed the instructions given in this link without success:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

Just repeated basically the same steps a second time following the instructions given in the "Beryl Via Synaptic" thread (reply #13) with no success.

Question: Is the xserver status my first problem and the no composite extension my second?
Any help would be much appreciated.

Thanks.
AZcat


THANK YOU ALL.  

revus6, THANK YOU, you've saved the day.  Beryl is now running.

icarius, may I suggest you try the guide I used to reinstall Beryl then at the log in screen do what revus6 said.  Good luck.  -- I have AMD XP2800+ cpu running feisty & XPpro.

all2ez, I could not connect to the ubuntuguide.org links.  Thank you.

---

### Post by AZcat on 2007-05-04
Does anyone know how to switch the xserver status to XGL?   The Load "xgl" line is included in the module section of the xorg.conf file.  Synaptic shows that both the xserver-xgl and the libxcomposite1are installed. I am totally lost.  

Thanks.

---

### Post by icarius on 2007-05-05
I am having the _exact_ same problem. Any help anyone???????

---

### Post by revus6 on 2007-05-05
when in login screen, open the options menu on the lower left part of your screen, then click select session. Then choose GNOME with XGL (if using GNOME) and then login

---

### Post by icarius on 2007-05-05
I found that if I disabled the restricted drivers Beryl worked right away. 

Specs
ati radeon 9700
3.2ghz IV HT
Fiesty and XP
Inspiron 9100 Gen 1

---

### Post by all2ez on 2007-05-05
I got beryl in feisty working on my laptop. I have a thinkpad T60 with ATI Radeon Mobility X1400. I have a triple boot system with XP, Vista and Feisty... I had Edgy and beryl working, then I upgraded to Feisty and beryl was still starting when I logged in, but it wasn't working.

I looked around a few places and found no help, so I just uninstalled all of the beryl stuff through synaptic in System>Administration>Synaptic Package Manager (just search beryl and mark everything that is installed for complete removal).

After that, I basically followed the guide here:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)

and it works!!!

It seems the key was editing the startxgl.sh that I already had. Also I had to disable the universe repository and add the correct repository to install beryl from (deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) feisty main). Oh and the ATI restricted driver had to be checked enabled.

The NVIDIA guide is here:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28Nvidia.29)

Hope this helps someone!

:guitar:

---

