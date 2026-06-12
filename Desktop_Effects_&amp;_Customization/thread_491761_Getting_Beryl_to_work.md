---
title: "Getting Beryl to work"
date: 2007-07-04
forum: Desktop Effects &amp; Customization
---

### Post by Vega on 2007-07-04
Everything passed on my card I got to install and it's running

but where are the effects? and how do I enable them?

---

### Post by cwood06 on 2007-07-04
what card do you have?

if its nvidia you should have no problems if its ati you need to install xgl

---

### Post by fjm03 on 2007-07-04
What did you install? Beryl, Compiz or Fusion?
What window manager are you using? Beryl, Compiz or Metacity?.
Assuming your O/S is Ubuntu, probably 7.04(32)?

---

### Post by Vega on 2007-07-04
UbuntuStudio 7.04

Metacity

Ati Radeon X1600XT

Using Beryl

---

### Post by fjm03 on 2007-07-04
"Using Beryl" implies that Beryl core, plus all the numerous, specialized dependencies and the proper ATI drivers have been installed. What method was used for installation.  SPM? An Ubuntu Forum 'howto'? A 'howto' from the Beryl Wiki?

Beryl has three general methods of  initiation depending on how it was installed. It may automatically initiate via a script in 'Sessions', or It may be initiated from the Main Menu under 'Application' >>'System Tools' >> 'Beryl Manager' or it can be commanded from a Terminal window by inputing 'beryl' after the flashing cursor at the default, home directory. 

Which method was used to install and which to initiate?

---

### Post by Vega on 2007-07-04
> **fjm03 said:**
> "Using Beryl" implies that Beryl core, plus all the numerous, specialized dependencies and the proper ATI drivers have been installed. What method was used for installation.  SPM? An Ubuntu Forum 'howto'? A 'howto' from the Beryl Wiki?

Beryl has three general methods of  initiation depending on how it was installed. It may automatically initiate via a script in 'Sessions', or It may be initiated from the Main Menu under 'Application' >>'System Tools' >> 'Beryl Manager' or it can be commanded from a Terminal window by inputing 'beryl' after the flashing cursor at the default, home directory. 

Which method was used to install and which to initiate?

well first I made sure my gpu supported it, on the[ main page of ati cards]("http://wiki.beryl-project.org/wiki/Support_for_ATI_cards")

I got Yes 

So I just followed the commands of that how to and I even manually put it on start up

The app shows it's on and I can configure it like I please but I'm just not seeing any of this goodness.

---

### Post by Vega on 2007-07-04
I tried to search for similar threads like mine and it seemed other users had the effects automatically running after installation

When I right click select window manager it's always stuck on Metacity (Gnome Window Manager) even when I try to switch it to beryl windows keep trying to change but it never goes on beyrl which is maybe why no nice effects..

---

### Post by mark. on 2007-07-04
you have beryl running, right? right click the emerald icon so that the menu thing shows up.

change 'select window manager' from metacity to beryl.
maybe thats it?

---

### Post by cwood06 on 2007-07-04
go to ubuntuguide.org and follow there tut for ati it will work

---

### Post by sailor2001 on 2007-07-04
I have nividea and still have problems going direct from metacity to beryl. I found going in steps from metacity to compiz to beryl works......slowly, not fast steps

---

### Post by fjm03 on 2007-07-04
There are numerous ways to verify if Beryl is the window manager but the easiest is to glance at the right hand corner of the bottom panel.  If there is only one desktop icon to the left of the trash can then Compiz is the manager, two panes and Metacity is in charge and four desktops indicates a default, Beryl management.

Other clues are an icon of a ruby (red beryl) crystal on the right side of the top panel and a deep red top menu bar for all windows.

Might check in 'System' >>'Preferences' and make sure than "Desktop Effects' is turned **off **since they conflict with the Beryl Manager. From the red ruby icon, pull down menu, make sure that 1) Beryl is the widow manager , 2) All 'Advanced Beryl options' are set to automatic,  and 3) That Emerald  (green beryl crystal) is the Beryl Window Decorator. 

None of this guarantees that Beryl will work but at least it's in charge and you can now look toward properly configuring graphics rendering.

---

### Post by Vega on 2007-07-04
I mentioned this before..


I have it on metacity but I can't change it to beryl in "select window manager" It just always gets stuck on metacity.


Everything you described is what I have (settings wise)

---

### Post by czepluch on 2007-07-04
Does it work with Intel GMA 915 too ?

---

### Post by BVStang1967 on 2007-07-05
I'm having the same problem with my laptop with an ATI card.  Someone said that right clicking on the Ruby to bring up the menu that will allow me to change the window manager.  I don't have a ruby icon... anywhere.  I installed Beryl from synaptic (the version for ubuntu).  Does anyone know a command line that will make Beryl take over window management?

---

### Post by cwood06 on 2007-07-05
> **Vega said:**
> I mentioned this before..


I have it on metacity but I can't change it to beryl in "select window manager" It just always gets stuck on metacity.


Everything you described is what I have (settings wise)

Do you have xgl server set up?

---

### Post by BVStang1967 on 2007-07-05
That was my problem, XGL... here's the link I just used and now Beryl WORKS!!!
[http://ubuntuforums.org/showthread.php?t=488385&highlight=download+XGL](http://ubuntuforums.org/showthread.php?t=488385&highlight=download+XGL)

---

### Post by Vega on 2007-07-05
> **BVStang1967 said:**
> That was my problem, XGL... here's the link I just used and now Beryl WORKS!!!
[http://ubuntuforums.org/showthread.php?t=488385&highlight=download+XGL](http://ubuntuforums.org/showthread.php?t=488385&highlight=download+XGL)

that did the trick

thanks allot!

---

