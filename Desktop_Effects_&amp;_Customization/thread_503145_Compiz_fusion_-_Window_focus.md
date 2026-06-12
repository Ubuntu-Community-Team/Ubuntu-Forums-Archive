---
title: "Compiz fusion - Window focus"
date: 2007-07-17
forum: Desktop Effects &amp; Customization
---

### Post by ittiam on 2007-07-17
I installed compiz fusion and after that I have one small problem. Switching of window focus happens only if i click on the title bar. It does not happen when i click on the body of the window or anywhere apart the title bar. Can someone suggest what should i do probably in CompizConfig Manager?

---

### Post by Happy_Man on 2007-07-17
Check the focus stealing prevention options in General Settings.

---

### Post by ArcherB on 2007-07-19
> **Happy_Man said:**
> Check the focus stealing prevention options in General Settings.

I checked it, but I don't   know what options to choose.  Here is what I have under "Focus and Raise behavior":
Click to Focus (checked)
Auto-Raise (unchecked)
Auto-Raise Delay (Zero)
Raise on Click (Unchecked)
Focus Prevention Windows (Blank)

I checked Auto-Raise and Raise on Click, but nothing happens.  When I exit the Compiz-Config Settings Manager and look at the options again, they are set to what I mentioned above (the changes don't stick)

Do you have any other suggestions? 
Normally, I'd just edit the text file by hand, but I can't find any "AutoRaise=1" or anything like it.

Thanx!

---

### Post by Happy_Man on 2007-07-20
> **ArcherB said:**
> I checked it, but I don't   know what options to choose.  Here is what I have under "Focus and Raise behavior":
Click to Focus (checked)
Auto-Raise (unchecked)
Auto-Raise Delay (Zero)
Raise on Click (Unchecked)
Focus Prevention Windows (Blank)

I checked Auto-Raise and Raise on Click, but nothing happens.  When I exit the Compiz-Config Settings Manager and look at the options again, they are set to what I mentioned above (the changes don't stick)

Do you have any other suggestions? 
Normally, I'd just edit the text file by hand, but I can't find any "AutoRaise=1" or anything like it.

Thanx!
Set the focus stealing prevention to "low." That should do it.

---

### Post by joakim2 on 2007-07-20
I have the same problem and tried setting "focus prevention windows" to low but it didn't have any effect for me, still have to click the window borders to raise a window, aaaargh

---

### Post by ArcherB on 2007-07-20
I just tried it out in Gnome, and it works fine.  Could the problem be KDE specific?  Are all of you having the problem running KDE only?

---

### Post by joakim2 on 2007-07-21
> **ArcherB said:**
> I just tried it out in Gnome, and it works fine.  Could the problem be KDE specific?  Are all of you having the problem running KDE only?

I'm running KDE. I played around with it some more and I'm getting fairly inconsistent behavior. Logging out and back in a few times while loading and unloading plugins back and forth the focus issue seemed to fix itself.

---

### Post by crazyhunk on 2007-07-21
try setting the focus prevention to 'NONE'.... it worked for me....

---

### Post by vaxen on 2007-07-21
feisty kubuntu. Same problem, none of the solutions work.

---

### Post by dhaus111 on 2007-07-23
I'm having the same problem, I've tried most of the above things (will try the rest when i'm home) but one thing I did want to point out, there are certain options that use blue text instead of the default black,  i don't know what this signifies, but from my expreiences, it seems to indicate that the option is disabled. because even if I check in autoraise after one second, it doesn't work even if i mouseover just the titlebar.

Also, is there any fix for the adept notifier poping out?  I know about restarting it, I'm sure I could create a script that'll get the desired results, I'm just wondering if there is an easier way.

---

### Post by Spam Banjo on 2007-07-24
I had the same problem after playing with Beryl and Compiz... I eventually fixed it by accedent but luckily remembered exactly what I did. (I was at my wits end... seriously!!!)

[COLOR="Red"][LIST=1]
[*]First I went System>Preferences>Windows and turned on 'Select windows when the mouse moves over them', and set the 'Interval before raising' to 0.5, although I don't think the number is important.
[*]Then I logged-out and back in again to restart the window manager.
[*]Now when I mouse over an inactive window the window is highlited... clicking it focuses the window. This is nice, and I could get used to it, but not what I wanted.
[*]...So I turned it off.
[*]Turning this on and off actually fixed the problem.
[/LIST]
[/COLOR]
Whatever setting is changed by activating/deactivating this feature caused the problem for me. Hopefully this will help a few people out cus this glitch was really annoying me for a while!

...Now if I could only get XGL working right... DAMN YOU ATI!

---

### Post by AlienPlanet on 2007-07-27
I had the same problem - running KDE (Kubuntu Feisty). Just got it to work 5 minutes ago.

My CompizConfigSettingsManager (General Options/"Focus and Raise behavior" tab) has the "Raise On Click" checkbox checked and "Click to Focus" and "Auto Raise" unchecked.

Here's how I got it to work:

[LIST=1]
[*]Opened K->System Settings->Window behavior (Look & Feel section)
[*]Selected Window Behavior (first icon on the left side), clicked "Focus" tab.
[*]Under Focus Policy (dropdown), selected Focus follows mouse (this is what I like)
[*]Checked the "Click to raise window" checkbox and hit Apply button.
[*]Then I quit compiz config settings and KDE window behavior system settings.
[*]Final step: Reloaded compiz to see the new changes (typed "compiz --replace" without the quotes in "run command" window (ALT F2))
[/LIST]

---

### Post by sefs on 2007-08-04
I have Ubuntu system Panel installed.  I just installed compiz fusion.  I had beryl installed before and removed it but i find i had to reinstall emerald for my title bar to appear on windows.  I am once again experience the thing where USP loads behind other windows when clicked upon. In beryl i solved this by setting focus stealing prevention to none as that was a simple task...it had a drop down box.   In compiz fusion how is this done? I dont understand whats going on in the foucus window in the general settings.  How do i turn the focus stealing off all together as i would have done with beryl.

Can this stuff be used without emerald?  If so how do you get back title bars without emerald.

Anyone notice that when multiple tabs in firefox are open that the tabs have a *twitch*?

Thanks

---

### Post by cringous on 2007-09-10
I had the same problem with focus on KDE, with gutsy RC5. And I fixed it in K > System Settings > Window Behavior and set the Policy to Click to Focus and turn on the option Click raise active window. Maybe if not work for you, just change and apply the policy some times. I use the fusion-icon, and after each change I reload the theme manager with it.

---

### Post by szundi on 2007-09-16
Hi!

On my Gutsy RC5 going to KDE's own Window Behavior config page, selecting anything and Click to Focus back worked!

Someone got behind KDE's back 

Szundi

---

### Post by prox2far on 2007-09-28
having the same problem after updating from 7.04 to 7.10

I'm not a developer or anything but it seems like the boxes with blue text indicate the option isn't controlled by compiz.

I had to enter the KDE control panel as mentioned by others before me and deseelct focus on click apply the change and select focus on click and apply again before it worked.

---

### Post by distratios on 2007-10-31
Kubuntu 7.10. Did exactly the same and it works. However, reloading the window manager was not necessary for me.

---

### Post by alphane on 2007-11-06
Just thought I'd confirm that these changes worked for me after 2 hours of intermittent urbuntuforums.org searches.

Just to confirm the process:

The blue settings in Compiz Manager are not available (don't stick).

I had to go to Menu > System Settings > Window Behaviour > Focus

The setting for "Click to raise active window" was already checked, so I toggled it off and on, and applied the settings.  

I can now change window focus as I would expect.  

I just hope this value remains active after a reboot...

---

### Post by nichpakaich on 2008-03-23
> **AlienPlanet said:**
> I had the same problem - running KDE (Kubuntu Feisty). Just got it to work 5 minutes ago.

My CompizConfigSettingsManager (General Options/"Focus and Raise behavior" tab) has the "Raise On Click" checkbox checked and "Click to Focus" and "Auto Raise" unchecked.

Here's how I got it to work:

[LIST=1]
[*]Opened K->System Settings->Window behavior (Look & Feel section)
[*]Selected Window Behavior (first icon on the left side), clicked "Focus" tab.
[*]Under Focus Policy (dropdown), selected Focus follows mouse (this is what I like)
[*]Checked the "Click to raise window" checkbox and hit Apply button.
[*]Then I quit compiz config settings and KDE window behavior system settings.
[*]Final step: Reloaded compiz to see the new changes (typed "compiz --replace" without the quotes in "run command" window (ALT F2))
[/LIST]

This is what I need! Solved my problem with those step, guys!
:D

---

