---
title: "Cube and Desktop Effects in Compiz"
date: 2011-12-08
forum: Desktop Environments
---

### Post by wildmanne39 on 2011-12-08
This is a guide for setting up the cube and effects in Ubuntu, Xubuntu, Lubuntu, Kubuntu and Edubuntu in release 10.04, 10.10, 11.04, 11.10 and 12.04.

[https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager)

Thread closed.

Please ask support questions in the appropriate forum.

1. The guide is intended to get the cube and a few of the well known effects working, it will give you the basics to be able to setup and use other effects as well.

2. Please read all the guide and do not skip around it will make it easier to setup that way.

3. The cube and effects were setup in each version and release of ubuntu listed above in virtualbox meaning the graphics driver used is the 3D driver included in virualbox, many problems that may be in countered will be because of issues with graphic drivers. 

4. Please feel free to discuss all things related to setting up the cube and effects here, also you can edit the wiki with your suggestions or if you do not want to edit the wiki post your suggestion here and I will post it to the appropriate section of the wiki.  

5. If you edit the wiki please remember that we are trying to have a guide that is easy for everyone especially new people to ubuntu to use so be as detailed as possible. 

**[COLOR="Red"]Edit: If you still need help after using the guide please post here for assistance.[/COLOR]**

Thanks to mörgæs for your guidance during the writting of this guide.
Thanks to MG&TL for help in editing the guide.
Thanks to Krytarik for proofing-reading and helping to make the guide more concise.

---

### Post by UltimateCat on 2012-01-14
Dear Wildmanne39::)

I followed the instruction for the cube to the T and it's on my desktop; just what I wanted and that's good. 

I just don't understand, how do I make the cube smaller?:confused:

---

### Post by wildmanne39 on 2012-01-14
Hi, when you have windows open in ubuntu and hold down your mouse wheel or ctrl+alt+left/Mouse button it should zoom out.
Thanks

---

### Post by papibe on 2012-01-14
Dear wildmanne39.

With the intention of making the guide better, I want to point out that there's a little problem with the first instruction (after installation):
> 
Ubuntu 10.04 and 10.10, Edubuntu 10.04, 10.10 and 11.04

1. Right click on the background, then click on "change desktop background" in the window that opens. Click on "visual effects" then choose "extra" and it will attempt to activate desktop effects. 
There's no 'Visual Effects' available following those instructions on 11.04

Any thoughts?

Regards.

---

### Post by wildmanne39 on 2012-01-15
Hi papibe, you are right I was sure when I checked Edubuntu 11.04 there was an appearance tab since it does not use unity in 11.04.

When there is no visual effects tab in Appearance just make sure you have 3D working then use compiz-settings-mangager to set the effects you want.

I will change this on the guide tomorrow when I am more rested.
Thank you it is much appreciated.

---

### Post by papibe on 2012-01-15
Another things that can be improved:

**Warnings should be written as first as possible, but not in step 4 !**
> 4. When you disable Open GL you will be asked if you want to disable several plugins. Click to disable every time it asks. When you disable Open GL it will cause graphical glitches in your windows and menu bar but do not worry, a restart will fix the problem but do not restart until later.
That warning is too late in the process. At some point I lost windows decorations, maximize and minimize buttons, alt+tab functionality, etc. If you are following the guide with a maximized firefox window, at some point you will loose the ability to go back to ccsm, thus continuing the guide.

**Better to separate steps for Unity and Classic Mode.**

There is a section for 11.04, but starts by saying that '...can be used for Ubuntu Classic Mode...", but the numbered steps are for Unity. I have to read it a couple of times to realize what was going on.

I hope this assessments can improve the guide.
Regards.

---

### Post by wildmanne39 on 2012-01-15
Hi papibe, thank you for your input I will look at the guide and see what I can do with it in regards to your suggestions.

---

### Post by UbuntuNerd on 2012-01-16
wildmanne39 thanks for the guide i've been unplugged from ubuntu for some time not by choice but this is just what i need to get back into compiz

---

### Post by wildmanne39 on 2012-01-17
Hi, your welcome please read the guide carefully unity is not very forgiving.
Thanks

---

### Post by nathan soulfly on 2012-01-18
[IMG]http://ubuntuforums.org/images/icons/icon13.gif[/IMG] 				**The unity  has disapear  from the login screen** 			
 			 			 		   		 		 		[SIZE=3]Hi  im using ubuntu 11.10.Yesterday i was trying to make my system have the  effects and the cube  on unity with CCSM, i tried for hours by my self  and with some videos i found on youtube and then i found a page from a  thread here on this site and tryed the instructions it had.Finally i  made only the effects work, it was very helpful.Today i opened my  computer and to the log screen i put my password with out checking the  small gear on the right to see what was selected cause i new from  yesterday i was last checked to UNITY (or UBUNTU as it appears on that  menu) and it loged in GNOME.So i  logout and try to select from the gear  the unity (or ubuntu )but it wasn't there.The options i have left are  GNOME , GNOME classic , GNOME classic with no effects and UBUNTU 2D  which is the UNITY 2D environment.Help please.

THANKS IN ADVANCE[/SIZE]

---

### Post by wildmanne39 on 2012-01-18
Hi, here is a link which is also in the guide for fixing that kind of problem.
[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)
It sounds like you my have removed ubuntu desktop. I would reset unity and compiz since you tried other methods from youtube.

Unity reset will keep running, after about three minutes just reboot by tapping the power button once and it should bring up a shut down window. 
Thanks

---

### Post by s33d3r on 2012-01-20
Thanx wildmanne39...
Awesome Work... I got the Cube Working on My Desktop... :D

---

### Post by fhaddad78 on 2012-01-20
Hi, thank you for this awesome guide! I followed it and everything is working. I only have one question...

I'm using the NVIDIA proprietary driver, and TwinView. When I bring up the cube, it is appearing on both monitors. On the left monitor (the primary), the cube is fine. However, on the right monitor, as I move and rotate the cube, it's not refreshing the screen, so what I'm seeing is a sort of "tiling effect." It's hard to explain, but imagine if you were moving a window around and instead of it moving, it kept making a new copy and until you let go of the mouse button, you would see lots of copies of the window all over the screen.

Can I either...
A) have the animation only appear on the primary monitor, or
B) can I have the animations render properly on both?

Thanks!

---

### Post by wildmanne39 on 2012-01-20
Hi s33d3r, your welcome!
@fhaddad78, I have no experience with two monitors but I searched for the answer and I did not find one that fit exactly, you can do a google search for cube and twinview +ubuntu or put compiz in place of the cube maybe you will find something that I did not.
Thanks

---

### Post by fhaddad78 on 2012-01-20
@wildmanne39, Thanks for the tip. I ended up finding a workable solution. In the CompizConfig Settings Manager, in the Desktop section, if you click on Desktop Cube, you can change the cube to 'One big cube' in the Multi Output Mode setting. That effectively created one big cube (instead of two) and solved the rendering issues. One additional change I made was to scale the cube down some in  the Rotate Cube settings by moving the Zoom slider.

This information might be helpful to others if you or someone wants to add it to the guide.

Thanks again!

---

### Post by wildmanne39 on 2012-01-21
Hi fhaddad78, thank you for sharing your solution I am sure it will help other people.

---

### Post by SsgtSyms on 2012-01-22
Thanks, I've been looking for this for awhile :D

---

### Post by wildmanne39 on 2012-02-01
Hi, your welcome!

---

### Post by LinuXofArabiA on 2012-02-08
I just enabled the cube using your guide and it is working beautifully :)  Just wanted to say thanks!

---

### Post by wildmanne39 on 2012-02-08
Hi, your welcome!
Enjoy

---

### Post by abhilashcs on 2012-02-19
when configuring cube , the Ubuntu Unity Plugin is gone now i canot get the dashboard And application please help me

---

### Post by wildmanne39 on 2012-02-19
Hi here is a link for resetting compiz or unity that will fix your problem.
[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)
Which version of unity are you using?

If you follow the directions exactly you should have no problems the panels they will be disable but when you are done they will be back and you will have a working cube.
Thanks

---

### Post by ortermagic on 2012-02-27
Hi there, I have been fooling around with Ubuntu for some time now thoughi i would recount some of my experiences with compiz and the natty to oneric unity distributions.

My problem started when I loaded natty for the first time, as a regular upgrade from maverick.
Unfortunately I thought that i would casually go for the encrypt your home folder option when i set it up.
After a little while tinkering i installed compiz in order to set up a rotating cube desktop. 

I had no idea that gnome and unity were so different and to my horror i lost control  was unable to fire up the operating system at all. Then forgetting that i had encrypted the home folder i decided to  do a clean reinstall on another hdd i had laying around  then take the lost files out of the problem drive later.

Well everything went well, the files got copied ok...but they were completely unreadable and seemingly impossible to decrypt from the dvd. I was so mad.

Well saddened with the Unity thing I reverted back to maverick for a few months...
Just a few days ago I decided to jump back in to the upgrade game and give 11-10 a go. 

I had learned to be wary of what i should not do re compiz so i looked around to see if anyone else had had problems with cube and compiz and it seems there have been quite a few victims.
so i googled around and found a very helpful link here ..  

  [http://askubuntu.com/questions/86977/how-to-correctly-enable-desktop-cube-in-unity-3d](http://askubuntu.com/questions/86977/how-to-correctly-enable-desktop-cube-in-unity-3d)  

I thought i would share, since it was so helpful to me

---

### Post by wildmanne39 on 2012-02-27
Hi, thank you for sharing that link.

---

### Post by peredur on 2012-02-28
Doesn't work for me.

I was messing with the compiz settings and clicked on the cube thingies.  Now when I login (ubuntu) I have a blank desktop with just the top bar with the desktop menu that doesn't allow me to do anything I want.

I tried following the instructions at [http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html), but can't even get to a terminal window.  Atl-F1 does nothing Ctrl-Alt-T does nothing Alt-T does nothing.

Can anyone please tell me what I need to do other than a complete reinstall?

I can get to Ubuntu 2D, by the way, which is how I'm able to send this from anywhere other than an internet cafe.

I really hope someone can suggest something.

Cheers


Peter

---

### Post by Cavsfan on 2012-02-28
> **peredur said:**
> Doesn't work for me.

I was messing with the compiz settings and clicked on the cube thingies.  Now when I login (ubuntu) I have a blank desktop with just the top bar with the desktop menu that doesn't allow me to do anything I want.

I tried following the instructions at [http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html), but can't even get to a terminal window.  Atl-F1 does nothing Ctrl-Alt-T does nothing Alt-T does nothing.

Can anyone please tell me what I need to do other than a complete reinstall?

I can get to Ubuntu 2D, by the way, which is how I'm able to send this from anywhere other than an internet cafe.

I really hope someone can suggest something.

Cheers


Peter

About all I can think of is try pressing ALT and F2 - that should bring up a Run Application box.
HTH

---

### Post by 23dornot23d on 2012-02-28
What graphics card are you using and are you sure that they are installed and working.

If Unity 2d is working ok ..... then can you do a screenshot showing the screen with your

graphics setup too ...... system settings - display ..... or if Nvidia - Nvidia settings

---

### Post by MG&amp;TL on 2012-02-28
> **peredur said:**
> Doesn't work for me.

I was messing with the compiz settings and clicked on the cube thingies.  Now when I login (ubuntu) I have a blank desktop with just the top bar with the desktop menu that doesn't allow me to do anything I want.

I tried following the instructions at [http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html), but can't even get to a terminal window.  Atl-F1 does nothing Ctrl-Alt-T does nothing Alt-T does nothing.

Can anyone please tell me what I need to do other than a complete reinstall?

I can get to Ubuntu 2D, by the way, which is how I'm able to send this from anywhere other than an internet cafe.

I really hope someone can suggest something.

Cheers


Peter

Hi, logging into Unity2d, re-ticking the "Ubuntu Unity" plugin in CCSM, then logging back into Unity should work. If not, 

```
unity --reset
``` in a terminal from anywhere (unity2d, tty), should do the trick.

---

### Post by peredur on 2012-02-28
> **MG&TL said:**
> Hi, logging into Unity2d, re-ticking the "Ubuntu Unity" plugin in CCSM, then logging back into Unity should work. If not, 

```
unity --reset
``` in a terminal from anywhere (unity2d, tty), should do the trick.

Oh, that was neat.  Thank you so much.

Do you think the Compiz Settings ought to come with a health warning?

Cheers


Peter

---

### Post by Krytarik on 2012-02-28
> **peredur said:**
> Do you think the Compiz Settings ought to come with a health warning?
Actually, it *will* :P ; in the upcoming Precise 12.04:

[LIST]
[*][https://code.launchpad.net/~andrewsomething/compizconfig-settings-manager/first_run_warning/+merge/92880]("https://code.launchpad.net/%7Eandrewsomething/compizconfig-settings-manager/first_run_warning/+merge/92880")
[/LIST]
Plus these further safeguards:

[LIST]
[*][https://code.launchpad.net/~alanbell/unity/removelargedesktopdependency/+merge/93687]("https://code.launchpad.net/%7Ealanbell/unity/removelargedesktopdependency/+merge/93687")
[/LIST]

[LIST]
[*][https://code.launchpad.net/~andrewsomething/compizconfig-settings-manager/disable_unity_checkbox/+merge/92879]("https://code.launchpad.net/%7Eandrewsomething/compizconfig-settings-manager/disable_unity_checkbox/+merge/92879")
[/LIST]
Thanks to the threat by Jorge Castro to remove CCSM from the official repos altogether.

> **peredur said:**
> Atl-F1 does nothing Ctrl-Alt-T does nothing Alt-T does nothing.
It's *Ctrl*+Alt+F1 for switching to the console/tty1, as correctly stated in that guide; in case that wasn't just a typo here. ;-)

---

### Post by laserator on 2012-04-05
I didnt think you had to change anything before you login to get the cube to work. When I did it I was able to spin the cube right after I was done. Or are you saying your desktop environment is changed now?

---

### Post by wildmanne39 on 2012-04-05
Hi laserator, some people do have to log out and back in after setting up the cube to get it to work.

I am not sure what you are asking here
> Or are you saying your desktop environment is changed now? what do you mean changed?
Thanks

---

### Post by RvShaitan on 2012-04-14
This worked great for me! Thanks wildmanne39. Btw, I had to relog for it to kick in as well on 11.10

---

### Post by wildmanne39 on 2012-04-15
Hi RvShaitan, your welcome!

---

### Post by dbombtek on 2012-04-27
Thanks for the help!

---

### Post by wildmanne39 on 2012-04-27
Hi, glad the wiki was of use to you.
Enjoy

---

### Post by cthom on 2012-04-29
i've upgraded to precise and compiz still works... except photowheel for some reason. any ideas? :/

---

### Post by wildmanne39 on 2012-04-29
Hi, no not at the moment I am still working the kinks out of 12.04 myself.

---

### Post by ricardo072 on 2012-05-01
Hi All,

I have installed vers 12.04 and, so far so good,.. but,.. I have a question,.. what is exactly the configuration I need to have in order to see the 3D-Cube ?

Actually, I have Compiz-Fusion running fine, I already have some efects, but I can't see the cube on 3D and to be honest, I'm not sure what I need to configure from the CompizSettingsManager,.. the checkBox for the 3D-Cube is already checked and is not working..

I can't turn/rotate the cube, and besides that,.. what I need to do to make it transparent?

Thanks,
Best regards,

---

### Post by cthom on 2012-05-01
photowheel just doesn't want to work for me in 12.04, i miss that effect :/

---

### Post by wildmanne39 on 2012-05-03
> **ricardo072 said:**
> Hi All,

I have installed vers 12.04 and, so far so good,.. but,.. I have a question,.. what is exactly the configuration I need to have in order to see the 3D-Cube ?

Actually, I have Compiz-Fusion running fine, I already have some efects, but I can't see the cube on 3D and to be honest, I'm not sure what I need to configure from the CompizSettingsManager,.. the checkBox for the 3D-Cube is already checked and is not working..

I can't turn/rotate the cube, and besides that,.. what I need to do to make it transparent?

Thanks,
Best regards,
Hi, here is the link to the wiki read it very carefully and it tells you what you need to do, if you have done all of that then it may be a problem with your video card driver.
[https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager)
Thanks

---

### Post by AleCes on 2012-05-05
Hello there.

I'm running Ubuntu 12.04 with an NVIDIA 8400 GS with working up-to-date drivers. My problem is that the Minimize effect doesn't appear on CompizConfig, even though I installed all of the extra plug-ins. I can see the following effects:

[LIST]
[*]3D Windows
[*]Animations
[*]Animations Add-On
[*]Bicubic filter
[*]Blur windows
[*]Cube gears
[*]Cube Reflection and Deformation
[*]Fading windows
[*]Login/Logout
[*]Motion blur
[*]Paint fire on screen
[*]Reflection
[*]Trailfocus
[*]Water effect
[*]Window Decoration
[*]Wobbly windows
[/LIST]

Technical data:

**compiz --version**
> Compiz 0.9.7.6

**X -version**
> X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-23-generic x86_64 Ubuntu
Current Operating System: Linux bureau 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic root=UUID=720aae67-a0a2-44d2-a23a-c19aeee23595 ro quiet splash vt.handoff=7
Build Date: 20 April 2012  05:12:02AM
xorg-server 2:1.11.4-0ubuntu10.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.24.4


**nvidia-settings -q NvidiaDriverVersion**
> Attribute 'NvidiaDriverVersion' (bureau:0.0): 295.40

Thanks you for your help.

---

### Post by wildmanne39 on 2012-05-05
Hi,in my screenshot is this where the minimize effect is missing?
If so see if clicking on the arrow beside the tabs at the top makes it come into view.
Thanks

---

### Post by wildmanne39 on 2012-05-05
Here is the screenshot I missed it in the last post.

---

### Post by AleCes on 2012-05-05
Hi [wildmanne39]("http://ubuntuforums.org/member.php?u=508533"),

No, actually, it's a stand-alone effect, indipendent from animations. See here: [http://wiki.compiz.org/Plugins/Minimize.]("http://wiki.compiz.org/Plugins/Minimize") 

Thanks for your help. Bye

---

### Post by wildmanne39 on 2012-05-05
Hi, I do not use the zoom effect, but it is in compiz by default, I showed it to you in the screenshot.

The link you gave me has not been updated in 4 years, I recommed you do not use it.

Did you use the link in the first post to setup compiz? There is also a zoom feature in compiz you just type zoom into the filter box and you will see an option to enable it, but I do not believe that is the one you are looking for, I belive it is the one in the screenshot.
Thanks

---

### Post by AleCes on 2012-05-06
> **wildmanne39 said:**
> Hi, I do not use the zoom effect, but it is in compiz by default, I showed it to you in the screenshot.

The link you gave me has not been updated in 4 years, I recommed you do not use it.

Did you use the link in the first post to setup compiz? There is also a zoom feature in compiz you just type zoom into the filter box and you will see an option to enable it, but I do not believe that is the one you are looking for, I belive it is the one in the screenshot.
Thanks
This effect used to be available back when I still ran 11.04, I don't know about 11.10 because I never checked. But now that I updated to 12.04, I cannot see it anymore. Is it possible it's a deprecated package, since you told me the link has not been updated in four years?

If you scroll down on this page [http://ubuntuguide.net/some-cool-3d-effects-in-ubuntu-with-compiz](http://ubuntuguide.net/some-cool-3d-effects-in-ubuntu-with-compiz) at one point you'll see a comprehensive list of effects containing the "Minimize Effect". This is the one I'm missing.

Thanks

---

### Post by wildmanne39 on 2012-05-06
Hi, click on animations as stated in the link at in the first post of this thread and the minimize effect is in there, it will be a tab at the top of the page unless you have a bug that is preventing it from showing.
Thanks

---

### Post by AleCes on 2012-05-06
> **wildmanne39 said:**
> Hi, click on animations as stated in the link at in the first post of this thread and the minimize effect is in there, it will be a tab at the top of the page unless you have a bug that is preventing it from showing.
Thanks
Hi, yeah, I can see it very well, I turned the zoom on, and it now gives me the effect I was looking for. It's just that I was accustomed to the old way, I didn't know it could be activated that way.

Thanks for your help.

---

### Post by wildmanne39 on 2012-05-06
Hi, your welcome! 
Enjoy

---

### Post by AleCes on 2012-05-06
Hi, I've just noticed Opacify doesn't seem to work, it is reportedly on by default, but I'm hovering over lots of windows and I don't see any effect.

Some relevant data:
Reset opacity to original values when toggling: ON
Delay until opacification: 700
Toggle Opacify on by default: ON
Window Match: Normal | Dialog | ModalDialog | Utility | Toolbar | Fullscreen
Opacity Levels:
Active Opacity: 100
Passive Opacity: 10

Thanks

---

### Post by AleCes on 2012-05-06
Actually, to be precise, it works only if I toggle Opacify through the shortcut SUPER+O but this **only **with windows that were already opened when I pressed it. Windows that are opened after I pressed the key, won't opacify when I hover over them.

---

### Post by node8472 on 2012-05-08
Hello everyone

UPDATE:
Well I feel dumb all I had to do was set the Horizontal & Vertical Virtual Sizes to 4 as well as the # of Desktops

Original:
I'm using Lubuntu 11.10 with compiz as the default window manager. I'd like to use the cube plugin. I used the General Settings>Desktop Size, to set 4 desktops. When I rotate my "cube" I only have two desktops visible, in other words not a cube but a really flat rectangle. This is a default Lubuntu 11.10 install with all packages updated and proprietary drivers. Any Ideas on how to get a cube going or what the problem could be?

---

### Post by Sumaxi on 2012-05-14
Hello! ( Thanks in advance)
Having trouble in 12.04 with Compiz. I originally used Compiz in 11.04 ( Where the problem originates) and can't get it to fully work with 12.04. I'm talking about the Compiz Fusion one, I used to adore that sphere effect, and I don't believe it's added. I did try to install the fusion one but it simply doesn't work. Any help?

---

### Post by HappySmack on 2012-05-15
> **node8472 said:**
> Hello everyone

UPDATE:
Well I feel dumb all I had to do was set the Horizontal & Vertical Virtual Sizes to 4 as well as the # of Desktops

Original:
I'm using Lubuntu 11.10 with compiz as the default window manager. I'd like to use the cube plugin. I used the General Settings>Desktop Size, to set 4 desktops. When I rotate my "cube" I only have two desktops visible, in other words not a cube but a really flat rectangle. This is a default Lubuntu 11.10 install with all packages updated and proprietary drivers. Any Ideas on how to get a cube going or what the problem could be?
@node8472 
  Install CompizConfig Settings Manager from the Software Center. From the dash, open ccsm. Click on General options > Desktop size. There you should choose 4 for horizontal, 1 for vertical and, 1 for desktops. Close and all should be well.

  There are other ways to do this but, this should work fine.

---

### Post by egeezer on 2012-05-15
> **Sumaxi said:**
> Hello! ( Thanks in advance)
Having trouble in 12.04 with Compiz. I originally used Compiz in 11.04 ( Where the problem originates) and can't get it to fully work with 12.04. I'm talking about the Compiz Fusion one, I used to adore that sphere effect, and I don't believe it's added. I did try to install the fusion one but it simply doesn't work. Any help?

To use the sphere effect, you need to install compiz-plugins-extra, which you'll find in Synaptic.  That will give you lots of stuff that the plain vanilla Compiz from the Software Center won't.

---

### Post by ublintu on 2012-05-31
Hi,
I need some help please. Until now I used ubuntu. This is the first release 12.04 when I changed to xubuntu. I like it, but when I want to use compiz, the window borders disappear. I need to run xfwm4 --replace to get back the borders. How to use normal, xubuntu window borders?

---

### Post by wildmanne39 on 2012-05-31
Hi, did you do this? > 5. Right-click Compiz Fusion Icon, highlight "Select Window Decorator" and click on "GTK Window Decorator" or you will not have the close, maximize, minimize buttons on your windows. 
also in ccsm make sure window decorator is checked.
Thanks

---

### Post by ublintu on 2012-05-31
Thank you for your quick answer.
Now I have different window border (from the normal xubuntu) with bottoms, but I can't grab the window and move it. How can I use the original xubuntu window border?

---

### Post by wildmanne39 on 2012-05-31
Hi, for window to move make sure you have windows move checked in ccsm it is in the guide.

Go to the bottom of the guide to window decorators and see if kde window decorator will work, if so you can add it in window decorators in ccsm, but I found in earlier versions that gtk worked the best and the windows decorator is not why the window do not move.
Thanks

---

### Post by Cavsfan on 2012-05-31
I tried Xubuntu 12.04 out and could only control the windows when xfwm4 was selected as the window manager.
But, then I had no cube effects or rotation. With Compiz selected as the window manager, I could rotate the cube but, I could not control windows. Terminal would go to the top of the screen and I could not move it.
I deleted that partition and installed Ubuntu 12.04 with Unity and have a learning curve but, the windows work (a bit differently than anything I am used to I might add).

---

### Post by wildmanne39 on 2012-05-31
Hi, as I said in the other post to the other poster you have to make sure that move windows in ccsm is enabled sometimes it gets unchecked, also it is in the wiki.
Thanks

---

### Post by Cavsfan on 2012-06-01
> **wildmanne39 said:**
> Hi, as I said in the other post to the other poster you have to make sure that move windows in ccsm is enabled sometimes it gets unchecked, also it is in the wiki.
Thanks
Thanks! That may have fixed it but, I already re-installed plain Ubuntu 12.04. Xubuntu kept hanging so there were more problems than just the windows.
+1 Good thread!

---

### Post by nll on 2012-06-02
[Daniel van Vugt has set a ppa]("https://launchpad.net/%7Evanvugt/+archive/compiz-preproposed") to test  a proposed version of Compiz with fixes for glitches while switching workspaces with the desktop wall and cube plugins. There currently is a problem with Nvidia cards making non-focused windows white, but for other cards it's working.

---

