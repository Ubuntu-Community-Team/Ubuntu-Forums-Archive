---
title: "Suspend Hibernate Button Removal (New Method)"
date: 2010-05-03
forum: Desktop Environments
---

### Post by histographik on 2010-05-03
The old way of doing this in gconf-editor (gnome power settings) is now invalid.

**Here is the new way of doing this!**

================================================================

First install devicekit-power:

#[COLOR=RoyalBlue]aptitude install devicekit-power[/COLOR] [COLOR=Red]**[COLOR=Silver]EDIT[/COLOR]** (aptitude install [COLOR=SeaGreen]upower[/COLOR]) *installed by default on Lucid*[/COLOR]

Then edit the power policy:

#[COLOR=Green]sudo gedit /usr/share/polkit-1/actions/org.freedesktop.upower.policy[/COLOR]


Under the following headings perform the following changes:

**<description>[COLOR=Sienna]Suspend the system[/COLOR]</description>**

Change the following entries:

          > <allow_inactive>**no**</allow_inactive>
          <allow_active>**yes**</allow_active>
      
To:
 
    <allow_inactive>**[COLOR=Red]yes[/COLOR]**</allow_inactive>
          <allow_active>**[COLOR=Black]no[/COLOR]**</allow_active>**<description>[COLOR=DarkSlateBlue]Hibernate the system[/COLOR]</description>**

Change the following entries:

          > <allow_inactive>**no**</allow_inactive>
          <allow_active>**yes**</allow_active>
      
To:
 
    <allow_inactive>**[COLOR=Red]yes[/COLOR]**</allow_inactive>
          <allow_active>**[COLOR=Black]no[/COLOR]**</allow_active>          
All done. Reboot.

Now the Hibernate & Suspend buttons are removed!  :-)

---

### Post by SnickerSnack on 2010-05-03
Whenever I get a new keyboard for a desktop (I avoid such buttons in the first place, but if I get one that does have them), one of the first things I do is open it up and remove the mechanisms from any shutdown/suspend/sleep/etc buttons....

But, for a laptop, this is a good thing to have.

Thanks for posting it!

---

