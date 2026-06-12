---
title: "Gnome with Ubuntu"
date: 2016-08-22
forum: Desktop Environments
---

### Post by RogerDavis on 2016-08-22
I want to use Gnome with Ubuntu 16.04.  I understand that it is based on 3.18, but I can't hide the top and bottom bars.  I can hide the Unity sidebar, but I'd really rather just do away with it, but the drop-down menus aren't available.  When I updated from 14.04 I was running Metacity (don't know exact version, but was on the Software Center in 14.04) and that seemed to work ok in 16.04, but the Software Center had disappeared.  I tried unsuccessfully to fix that, but no luck.  I had to revert to my clone backup.

Questions :
1) In Ubuntu 16.04, How can I make the top and bottom bars hide?
2) How to use dropdown menus, and do away with the Unity bar?
3) Is Metacity ok for use with Ubuntu 16.04?  If so, what to do about the missing software center?  Are there any other reasons not to use Metacity?  Other than the Software Center, it seemed ok.  Will Metacity not be supported after a time?
4) Is there another Gnome that works better with 16.04, but will still have clear and easy dropdown menus, be able to hide top and bottom bars, solid desktop color and desktop icons, no Unity sidebar, and have all features of Metacity?
5) How do I uninstall any version of Gnome without it in the Software Center?
6) Can I update my current 14.04 to UbuntuGnome directly from my current 14.04, just like I tried 16.04, keeping all my software, etc.?
7) If so, would Ubuntu Gnome satisfy my needs mentioned in 1,2, and 3 above?
8) Where is a comprehensive documentary of Gnome(s)?
9) Is there a forum, like Ubuntu Forum, for Gnome?  Or is this the best place?

Thanks!

---

### Post by grahammechanical on 2016-08-22
In my opinion it is always better to run an alternative distribution built on Ubuntu than an alternative desktop environment installed on top of Ubuntu. Check out Ubuntu Gnome. It has the Gnome 3 shell. You may be surprised that Gnome 3 shell is very similar to Unity. Both use the same software technology. You would need to do a fresh install.

[https://ubuntugnome.org/](https://ubuntugnome.org/)

Or, if you like that old Gnome 2 panel look you might be interested in Ubuntu Mate.

[URL="https://ubuntu-mate.org/"]https://ubuntu-mate.org/

[/URL]Again it would be best to do a fresh install. It is time to make a decision and bite the bullet and accept the pain.

Regards





In Ubuntu with Unity we can install

---

### Post by RogerDavis on 2016-08-22
I guess I need to try again to explain this complicated situation.

I thought the vertical left sidebar was a mark of Unity.  I guess I might be wrong.  At first, I went from Ubuntu 14.04 with Gnome Metacity (Perfect setup) to Ubuntu 16.04.  It had the vertical sidebar, so I thought that was Unity.  As I also understand, 16-04 is on Gnome 3.18, so I thought the Unity bar had been forced onto Gnome somehow.  Anyway, I could ALSO start in Metacity, so that was almost ok.  Almost because the Software Center got lost.  In trying to fix that, the installation began to screw up, so I reverted to 14.04 by disk clone - back where I started.  

So now, I want to go to 16.04 WITH the features of no sidebar, top and bottom bars can hide, solid color desktop, icons on desktop, drop-down cascading menus, etc.  JUST LIKE METACITY, but in the current OS and software, with or without Gnome.  How can this be done?

However, I understand Metacity is depreciated (What does that mean, will it go away, just not be supported, can / can't be used / be a tax deduction / turn to toadstools ...???)   So, is it possible to use the Metacity that survives after the update to 16.04 in a long term situation?  And how can I get the software center back?  If not, what can I DUPLICATE it with using current OS and front end?

If I go to Ubuntu Gnome, can I then get the features I want (no sidebar, top and bottom bars can hide, solid color desktop, icons on desktop, drop-down cascading menus, etc.  JUST LIKE METACITY.)?

Thanks!

---

### Post by mc4man on 2016-08-23
What you seem to want is from gnome-session-flashback. After install log in to gnome session (metacity

---

### Post by vasa1 on 2016-08-23
> **RogerDavis said:**
> ... depreciated (What does that mean, will it go away, just not be supported, can / can't be used / be a tax deduction / turn to toadstools ...???) ...
I think the preferred term in the context of software is *deprecated*. This link has some useful material: [http://stackoverflow.com/questions/8111774/deprecated-meaning](http://stackoverflow.com/questions/8111774/deprecated-meaning). [From there]("http://stackoverflow.com/a/8111890"), I like> "X is deprecated" means "We would have removed X right away if nobody was using it but we couldn't as of the moment. You should still consider switching to Y or Z to avoid getting caught up on its absence one day".

---

### Post by buzzingrobot on 2016-08-23
> **RogerDavis said:**
> 

I thought the vertical left sidebar was a mark of Unity...


Unity and Gnome 3 are two different environments. Both have "docks" on the left side of the display. Gnome's is not displayed by default but is activated by pushing the mouse cursor into the upper left corner.

Ubuntu running Unity uses some Gnome tools, etc. What you on screen n Unity, however, is not Gnome.

As suggested, it looks like you're after gnome-session-flashback. This provides a look and work something like the old Gnome 2. The different interface/environments installed on a system are available at the login prompt.

---

### Post by claracc on 2016-08-23
I advise to do a clean installation of ubuntu gnome 16.04, after backing up your /home folder. 
After installation you can choose to log in between ubuntu gnome shell (very similar to ubuntu unity) or classical gnome which is similar to fallback gnome desktop, which is what you seem to want ( it has classical menus).

As yo have backed up your /home folder, you can copy to the new installation your preferred configurations (rhythmbox, firefox,...) an also other files you want to maintain. If you use evolution, there is a way to backup your settings, accounts and mails and then restore them to your clean installation at the beginning.

Ubuntu gnome uses metacity and works very well and quick.

---

### Post by kurt18947 on 2016-08-23
> **RogerDavis said:**
> 

If I go to Ubuntu Gnome, can I then get the features I want (no sidebar, top and bottom bars can hide, solid color desktop, icons on desktop, drop-down cascading menus, etc.  JUST LIKE METACITY.)?

Thanks!

You might take a look at gnome extensions, found at extensions.gnome.org.

Must haves for me:
[LIST]
[*]Dash to Dock. I use this to make the launcher behave like I want it to. 
[*]lock keys if I'm using a keyboard without capslock & numlock indicators. 
[*]Suspend button 
[*]Taskbar. 
[*]Quicklaunch 
[/LIST]

There are alternatives to my preferences. Tweak Tools to restore max/min/close buttons, make the clock display like I want, icons on the desktop (though Quicklaunch and .desktop files make this somewhat less important). There are at least a couple extensions to restore 'traditional' menus. There are other packages to restore functions lost or crippled in the Gnome 2 -> Gnome 3 transition.

The risk with using extensions is that they may become unsupported because most are volunteer efforts. Gnome supports a handful but not many that I find useful.

---

