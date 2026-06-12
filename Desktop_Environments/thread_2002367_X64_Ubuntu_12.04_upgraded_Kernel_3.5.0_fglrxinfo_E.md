---
title: "X64 Ubuntu 12.04 upgraded Kernel 3.5.0 fglrxinfo ERRORS ( ATI )"
date: 2012-06-12
forum: Desktop Environments
---

### Post by TorakTu on 2012-06-12
UPDATED QUESTION : How can I get my ATI graphics drivers to work with any kernel above 3.2.0.x ?
( NOTE : Added this question because apparently there is some confusion as to what I am asking )

Installed original AMD64 version of Ubuntu 12.04 ISO image. Burned DVD and installed which shown kernel 3.2.0-23 to begin with. Got 5.1 surround sound working. Got ATI ( Now its AMD ) video drivers installed for my Radeon HD R6870 Video card from AMD's website. fglrxinfo came up and reported as normal.

BUT....

Before, during and AFTER installing all this, I had lots of lockups. No matter what I did it locked up. If I opened FireFox it locked up. If I played a game it would lock up. Keep in mind, it was all random. So there was no way to pin it down. I googled everywhere I could and one guy mentioned upgrading the kernel. I did. No lock ups. In fact I have tested many kernels above 3.2.0-24 and none of them lock up. So that part works. My 5.1 surround card works no matter what kernel I throw at it. I'm happy.. or so I thought...

None of my games work. In fact I get nothing but ( Sorry cannot start ) type of errors. Here is a JAVA example while trying to run any game that is a java game, such as Minecraft or WURM Online :

```

&#65279;Javax.media.opengl.GLException: glXGetConfig failed: error code GLX_NO_EXTENSION
    at com.sun.opengl.impl.x11.X11GLDrawableFactory.glXGetConfig(X11GLDrawableFactory.java:651)
    at com.sun.opengl.impl.x11.X11GLDrawableFactory.xvi2GLCapabilities(X11GLDrawableFactory.java:350)
    at com.sun.opengl.impl.x11.X11GLDrawableFactory.chooseGraphicsConfiguration(X11GLDrawableFactory.java:174)
    at javax.media.opengl.GLCanvas.chooseGraphicsConfiguration(GLCanvas.java:520)
    at javax.media.opengl.GLCanvas.<init>(GLCanvas.java:131)
    at haven.HavenPanel.<init>(HavenPanel.java:68)
    at haven.HavenPanel.<init>(HavenPanel.java:78)
    at haven.MainFrame.<init>(MainFrame.java:182)
    at haven.MainFrame.main2(MainFrame.java:306)
    at haven.MainFrame.access$100(MainFrame.java:34)
    at haven.MainFrame$7.run(MainFrame.java:360)
    at java.lang.Thread.run(Thread.java:722)

```All of them are showing a similar error ( Even though they worked on 3.2.0.x,  Including non-JAVA games ) Now I have tried and tried and tried to get ATI drivers to work correctly on several kernels and the only one that installs it correctly is 3.2.0-23 and 24. All the rest of them crash in the sense that its missing updated dependencies and when you install those dependencies it still gives errors as if those dependencies are not there. So it wont even recreate the DEB packages for the drivers ( No matter what XORG version I use ). I have googled to death this issue and I am seeing articles from all the way back to 2007 on this EXACT issue. But none of them help. Here is the fglrxinfo error that all of us see when it comes to ATI drivers ( and in some posts I see NVidia has same issues, but some posts say that it was solved for NVidia - Not sure if it really is the case or not )

```

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  139 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13

```This is what I have seen since I upgraded any kernel above 3.2.0.x. I have tried kernel 3.3.0, 3.3.4, 3.3.5, 3.4.0, 3.4.2 and Now I am even on 3.5.0-030500rc2. So far, ALL of them show this error no matter what I do. And NONE of the games work. Including Blender 3D for 3D rendering. Now I thought at first this was an ATI driver issue, BUT..  it installs and works for Kernel 3.2.0-34 and 24. If it wasn't for the random lockups I would be sticking with that. But now that I got rid of the lockups, I can't do anything with my Operating System like I want too.

I have gone over this tutorial many times ( [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) ) and it doesn't work on ANY kernel except 3.2.0.x.

So I guess I am at the mercy of waiting to see what kernel can fix this.

By the way, I have tried All Mint 13 Versions ( all 4 meaning MATE and Cinnamon 32 / 64 Bit ), Dreamstudio ( Latest both 32 and 64 Bit ), Zorin.. which would not even boot... so I guess this is irrelevant, as well as Kubuntu. ALL of them have same issue. And if your thought comes out as if its my video card, I thought about that too, and I realized that is not the case because ANY other OS I install works fine with my card. All windows version from XP to Windows 8 work fine with it. Including the Hackintosh. But the only OS I love is Linux. So again, I am at your mercy here. I am stable, but cannot play any 3D software such as games.

Thoughts, ideas ?

EDIT UPDATE  1 : Also am I supposed to post it here ? Or is there somewhere else I am to report this ? Because there seems to be old forums for linux so its a little confusing. 

EDIT UPDATE 2 :  It dawned on me that some of you might ask me if I tried the OpenSource ATI / AMD drivers. Yes I tried many many times on ALL of the kernels and none of them will install. Even on the 3.2.0.x it will not install. Keeps looking for dependencies that are installed. Still no go. It's why I am forced to use the Official ( Restricted ) drivers from the AMD website.  It would at least install on the 3.2.0.x Kernel. Also, I am a newbie to linux, I am coming from a Windows background. I just am tired of Windows so I am going through all this to get away from Windows.


EDIT UPDATE 3 : I'm going to see if I can revert my XORG version back to the 7.6 version since my drivers were only supposed to go up to 7.6. I just realized JUST NOW that I am using Xorg 11. No wonder I am not able to run my ATI drivers.

```

X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-31-server x86_64 Ubuntu
Current Operating System: Linux desktop 3.5.0-030500rc2-generic #201206082235 SMP Sat Jun 9 02:36:22 UTC 2012 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-030500rc2-generic root=UUID=af520f7d-e88f-4bff-bd09-e6d463eb4246 ro quiet splash
Build Date: 07 May 2012  11:43:21PM
xorg-server 2:1.11.4-0ubuntu10.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.24.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.

```I'll post my findings.


EDIT UPDATE 4 : FAIL..  I read the Xorg version wrong. I was hoping I missed something.. apparently I had it installed and just not realized it. 1.76+12 is currently installed. Although the X -version doesn't reflect this that I can find. Either way, I even attempted once more after reinstalling Xorg to get the drivers installed. I got pop ups saying to report errors of which I did. Then it told me to report this to askabuntu's website. So I'm on my way to that site to see what I can do about this.

EDIT UPDATE 5 : Posted the question here : [http://askubuntu.com/questions/149989/x64-ubuntu-12-04-upgraded-kernel-3-5-0-fglrxinfo-errors-ati](http://askubuntu.com/questions/149989/x64-ubuntu-12-04-upgraded-kernel-3-5-0-fglrxinfo-errors-ati)

---

