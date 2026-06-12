---
title: "Workspaces switcher does not unexpose"
date: 2014-11-04
forum: Desktop Environments
---

### Post by monkeybrain20122 on 2014-11-04
I am using Ubuntu with Unity and workspaces activated. In Ubuntu 14.04 if I click the workspaces switcher icon on the unity launcher bar it exposes all the workspaces, if click again (when the workspaces are already exposed), the workspaces are unexposed. But in Ubuntu 14.10 nothing happens if workspaces are alrealy exposed (i.e. second click doesn't unexpose) 

Actually this happens with 14.04 as well after Unity upgraded a few months ago, but since I have pinned the package I am still able to click to unexpose. I thought that this was  a temporary bug and hopefully would be fixed in further upgrades, but it persists in 14.10 so I am now not sure whether it is a bug or a change in design.

Any idea?

---

### Post by grahammechanical on 2014-11-04
I am on vivid Vervet and after some experimentation it is left click to expose and right click to unexpose. It works consistently.

Regards.

---

### Post by monkeybrain20122 on 2014-11-04
I am not on Vivid obviously, which is not even pre alpha. I can attest that doesn't work for Unity > 7.20. Tried on two different machines so has nothing to with hardware.

---

### Post by monkeybrain20122 on 2014-11-05
No one experiences this problem?

---

### Post by Doug S on 2014-11-05
> **monkeybrain20122 said:**
> I am using Ubuntu with Unity and workspaces activated. In Ubuntu 14.04 if I click the workspaces switcher icon on the unity launcher bar it exposes all the workspaces, if click again (when the workspaces are already exposed), the workspaces are unexposed. But in Ubuntu 14.10 nothing happens if workspaces are alrealy exposed (i.e. second click doesn't unexpose)It seems to be working fine for me. I am running an up to date Ubuntu14.10 as a guest VM on an Ubuntu 14.04 server host.

---

### Post by mc4man on 2014-11-06
Have you tried in a guest session on an affected install?
(- no issue here, has never stopped working

---

### Post by monkeybrain20122 on 2014-11-06
Not work in guest session either, it works in 14.04 (any session) if I pin Unity to 7.20, it stops working if I let it upgrade. Never works in 14.10.

For 14.10 it does work in live usb. But not after install to hard drive.

---

### Post by monkeybrain20122 on 2014-11-07
No idea?

---

### Post by mc4man on 2014-11-09
> **monkeybrain20122 said:**
> No idea?
Seems to be a rare & quite  localized issue, can't reproduce whatsoever. (just re-installed 14.04 last night.
Can't see any connect between 14.10 (live, 7.3.1+) works, 14.10 (install, same 7.3.1+) doesn't & 14.04 (release 7.2.0) works & 14.04 (7.2.2 or .3) doesn't.
That makes it seem hardware related if nothing was changed in 14.10 & only updates/upgrades in 14.04
(- if you install 14.10 with internet enabled does same occur if you disable before the install?

small curiosity - can you scroll on the ws icon when expo is active to switch ws's?
does super+ tapping s activate & terminate expo?

---

### Post by monkeybrain20122 on 2014-11-28
> **mc4man said:**
> Seems to be a rare & quite  localized issue, can't reproduce whatsoever. (just re-installed 14.04 last night.
Can't see any connect between 14.10 (live, 7.3.1+) works, 14.10 (install, same 7.3.1+) doesn't & 14.04 (release 7.2.0) works & 14.04 (7.2.2 or .3) doesn't.
That makes it seem hardware related if nothing was changed in 14.10 & only updates/upgrades in 14.04
(- if you install 14.10 with internet enabled does same occur if you disable before the install?

small curiosity - can you scroll on the ws icon when expo is active to switch ws's?
does super+ tapping s activate & terminate expo?

Not sure if having intenet on has any impact on this, but I don't have the time to reinstall without internet at the moment.

It happens in two different laptops of completely different specs so I don't know if hardware has anything to do with it (one dell with intel video card, the other hp with AMD video card)

Scrolling on the launcher doesn't work (press alt + scroll) whether expo is activated or not (works in 14.04 with unity 7.20) If expo is activated scrolling (not pressing alt) just select workspace 

Suoer + tab (when expose is activated) select launcher on the icon but does not terminate expos (this is also true with 14.04 with unity 7.20)

---

### Post by monkeybrain20122 on 2014-12-05
Any thought?

---

### Post by monkeybrain20122 on 2015-01-03
It seems that the culprits is some settings in my home. Did a fresh install of 14.04 on a test partition to test something else and expose works with up to date Unity. In the other installations I always keep the same /home partition. I wonder which config file may be responsible. Can mc4man help? Thanks.

---

### Post by mc4man on 2015-01-04
(- I knew your orig. description made no sense, so keeping an old /home is culprit..
Maybe try dconf dump to compare *similar *non-working &  working installs. I believe it will only dump actual changes to default settings so may not be illuminating. 
Ex.
```
dconf dump / >> dconf_old.txt
```
ect. 
Then compare or diff the files

---

### Post by monkeybrain20122 on 2015-01-05
I think I have figured it out. For unity > 7.20 workspace switcher does not unexpose if the unity launcher is set to autohide. I think this is a bug and can be easily reproduced by others. Can anyone please confirm or unconfirm it?

---

### Post by Doug S on 2015-01-05
> **monkeybrain20122 said:**
> I think I have figured it out. For unity > 7.20 workspace switcher does not unexpose if the unity launcher is set to autohide. I think this is a bug and can be easily reproduced by others. Can anyone please confirm or unconfirm it?Hmmm... I can not seem to make autohide work properly. When I enable it, I can never get it to come out from being hidden. I tried different sensitivities and different reveal locations. Oddly, I can sometimes see only the software updater icon trying to reveal. I am a server guy and only run dekstop as a VM guest on my server and my display is via VNC. I thought your request would be easy to confirm or deny, but it is turning into a saga.

---

### Post by mc4man on 2015-01-05
I'm on the road till late Tuesday but I'll check out when I return  (only take tablets with me.
Haven't been using autohide much lately so can't say I've noticed.
(- also have been backporting all compiz & unity 14.10/15.04 changes to 14.04 so not using the trusty version  per se.

---

### Post by monkeybrain20122 on 2015-01-05
> **mc4man said:**
> 
Haven't been using autohide much lately so can't say I've noticed.
(- also have been backporting all compiz & unity 14.10/15.04 changes to 14.04 so not using the trusty version  per se.

Hi, compiz and unity in 14.10 behave the same way, as does Trusty update to unity > 7.2.0 so I think you would be able to see this behaviour too if my guess is correct. On the other hand unity 7.20 on trusty before offiical upgrade a while back did not exhibit this problem (so I have it pinned on my main Trusty install)

---

### Post by Doug S on 2015-01-06
I learned that for my situation, I can use "ALT F1" to force reveal the hidden launcher.

I confirm your findings, but with a slight difference: The first time works, but thereafter it doesn't.

Detail:
1.) Use "ALT F1" to force reveal the launcher.
2.) Position mouse over the workspace switcher icon and click.
3.) The workspace window comes up.
4.) Click again.
5.) The workspace window goes away, leaving the original desktop window.
6.) Click again.
7.) The workspace window comes up.
8.) Click again, and as many times as desired. The workspace window stays.

As a sanity check, do the same with autohide turned off: It works always.

The above tests were repeated several times.

Note: To get out of the locked up state, move the mouse over and select a workspace and click.

Edit 1: Addendum: There seems to be a correlation between the top most icon and this issue.

Greyed:
[ATTACH=CONFIG]259053[/ATTACH]

Normal:
[ATTACH=CONFIG]259054[/ATTACH]

When the launcher is in auto-hide mode but revealed and that topmost icon is greyed out, then things work normally.
When that topmost icon is normal, then the issue of this thread occurs.
When that topmost icon is greyed out, then it doesn't work either (which is normal for greyed out icons, but I don't think normal for this situation).

When the launcher is not in auto-hide mode, then that topmost icon is never greyed out (at least that I have been able to discover) and things work normally.

Edit 2: Actually once the issue from this thread has occurred, I can never get the topmost icon to work properly again. regardless of the auto-hide setting or the workspaces enabled setting. It either doesn't work at all (greyed) or opens but won't let me go it, just disappearing instead. I have to re-boot. (Note: I am not certain of the particular sequence to get into this state, but have ended up there several times now.)

---

### Post by monkeybrain20122 on 2015-01-06
Hi, Doug S, 

Thanks for the tests. Yes, autohide is somewhat broken in that sometimes the unity launcher doesn't reveal itself. When that happens I change workspace and change back and it works again. Since I have edges (for desktop wall) and hot corners (scale and expose) enabled I just move the mouse to the edge or the corner to achieve that. Pressing the super key also reveals the launcher.

---

### Post by mc4man on 2015-01-06
Here it's pretty straightforward - 
auto-hide enabled
left click on icon goes to expo
while in expo a left click on icon does nothing, but a right click works & terminates expo.

auto-hide disabled
A left click opens expo, either a left or right click on icon terminates.

(14.04 w/ unity - 7.3.1+15.04.20141216, compiz - 0.9.12.0+15.04.20141210.2

---

### Post by mc4man on 2015-01-06
> **Doug S said:**
> I learned that for my situation, I can use "ALT F1" to force reveal the hidden launcher.

I confirm your findings, but with a slight difference: The first time works, but thereafter it doesn't.

Detail:
1.) Use "ALT F1" to force reveal the launcher.

That is "Launcher navigation mode", the top icon isn't 'greyed out', it's 'selected'  (use down & up arrow keys to see...
To force the launcher just  hold super key down.

---

### Post by monkeybrain20122 on 2015-01-06
> **mc4man said:**
> Here it's pretty straightforward - 
auto-hide enabled
left click on icon goes to expo
while in expo a left click on icon does nothing, but a right click works & terminates expo.

auto-hide disabled
A left click opens expo, either a left or right click on icon terminates.

(14.04 w/ unity - 7.3.1+15.04.20141216, compiz - 0.9.12.0+15.04.20141210.2

Thanks for checking it out. So I gather this is not expected behaviour and a bug should be filed?

Also wonder if you can reproduce these reported on post #10 
"scrolling on the launcher doesn't work (press alt + scroll) whether expo  is activated or not (works in 14.04 with unity 7.20) If expo is  activated scrolling (not pressing alt) just select workspace 

Suoer + tab (when expose is activated) select launcher on the icon but  does not terminate expos (this is also true with 14.04 with unity 7.20)"

---

### Post by mc4man on 2015-01-06
> **monkeybrain20122 said:**
> Thanks for checking it out. So I gather this is not expected behaviour and a bug should be filed?

Well if a left click should work to dismiss expo then yes. (- does a right click not work for you?
> **monkeybrain20122 said:**
> 
Also wonder if you can reproduce these reported on post #10 
"scrolling on the launcher doesn't work (press alt + scroll) whether expo  is activated or not (works in 14.04 with unity 7.20) If expo is  activated scrolling (not pressing alt) just select workspace 

Suoer + tab (when expose is activated) select launcher on the icon but  does not terminate expos (this is also true with 14.04 with unity 7.20)"
I'm a bit lost here - 
What is alt+scroll supposed to accomplish?

Same for super+tab, how does that relate to expo icon or expo mode? Edit: ok, I see - works fine here, will either open or close if already open

---

### Post by mc4man on 2015-01-06
attached short vid, is this what you mean?
(using super+tab, tab, tab, ect to open then close expo

---

### Post by Doug S on 2015-01-06
> **mc4man said:**
> That is "Launcher navigation mode", the top icon isn't 'greyed out', it's 'selected'  (use down & up arrow keys to see...Ah, I see thank you.> **mc4man said:**
> To force the launcher just  hold super key down.I cann't do that, there is no super key with a VNC desktop to the VM guest, as the super key calls up the start menu on the (dare I mention it) windows 8.1 computer I am physically sitting at.

It must be pretty obvious to you guys that I have no clue when it comes to desktop stuff (as previously mentioned, I am a server guy). I was just trying to help, but think I better leave it to you. As far as I can tell auto-hide mode is pretty broken.

---

### Post by mc4man on 2015-01-06
> **Doug S said:**
> Ah, I see thank you.I cann't do that, there is no super key with a VNC desktop to the VM guest, as the super key calls up the start menu on the (dare I mention it) windows 8.1 computer I am physically sitting at.

It must be pretty obvious to you guys that I have no clue when it comes to desktop stuff (as previously mentioned, I am a server guy). I was just trying to help, but think I better leave it to you. As far as I can tell auto-hide mode is pretty broken.
Not that I think you need it but the function of 'super' can be changed in ccsm > Ubuntu unity.. > Launcher tab to some other keybinding though then it requires a min of 2 keys from a short list of what's not used. (- like maybe ctrl+l as in hold ctrl, tap l

---

### Post by monkeybrain20122 on 2015-01-13
> **mc4man said:**
> attached short vid, is this what you mean?
(using super+tab, tab, tab, ect to open then close expo

Hi, sorry for the late reply. Haven't logged into utopic for a while. I mean scrolling the unity launcher when expose is activated (place cursor on launchet, press alt and then scroll) scroll works with unity 7.2.0 when expose is activated but not above.

I use a laptop with the touchpad so I don't left click right click, I just tab the touchpad. Since it unexpose with 7.2.0 but not above I would think that it is a bug.

---

