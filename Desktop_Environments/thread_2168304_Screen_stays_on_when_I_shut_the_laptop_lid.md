---
title: "Screen stays on when I shut the laptop lid"
date: 2013-08-17
forum: Desktop Environments
---

### Post by rconway on 2013-08-17
Hi,

I'm running Xubuntu 13.04 (xfce4). When I close the lid the screen stays on. I'd like the screen to switch off when shutting laptop lid - how do I configure this?

Many thanks,
Richard

---

### Post by Toz on 2013-08-17
Can you clarify, when you close the lid, do you want the computer to go into suspend/hibernate mode, or do you want the laptop to stay running but just turn off the screen?

What is the make and model of your laptop?

---

### Post by rconway on 2013-08-17
Hi Toz, thanks for your reply.
I want it to just put the display to sleep/off/blank (basically save some power) with the machine still running. I have used the Power Manager to suspend on lid close (which works fine), but this not what I want as the machine will stop processing. Sure I've done this with other distros.

It's a Dell Latitude E6410 laptop (Intel(R) Core(TM) i7 CPU  M 640  @ 2.80GHz).

Richard

---

### Post by Toz on 2013-08-17
> **rconway said:**
> Hi Toz, thanks for your reply.
I want it to just put the display to sleep/off/blank (basically save some power) with the machine still running. I have used the Power Manager to suspend on lid close (which works fine), but this not what I want as the machine will stop processing. Sure I've done this with other distros.

It's a Dell Latitude E6410 laptop (Intel(R) Core(TM) i7 CPU  M 640  @ 2.80GHz).

Richard
In Power Manager, change the "When the laptop lid is closed" action to "do Nothing" for both the "On AC" and "On Battery" sections. This should prevent the laptop from going to sleep. Once that is done, can you confirm that:
1. the system does not go into a suspend state
2. that the screen turns off when the lid is closed.

---

### Post by rconway on 2013-08-17
Yes, this is where I started.
My settings are:
- When laptop lid is closed = Nothing
- Put display to sleep when computer is inactive for = Never
- Switch off display when computer is inactive for = Never

In this case everything remains on (incl. display) when I close the lid.

However, I've just discovered something significant. With the above settings, if I modify the value of 'Put display to sleep when computer is inactive for' and/or 'Switch off display when computer is inactive for', and the close the lid then it goes off. However, if I then reboot, then the problem is the same again after the reboot - I have to go back into the power settings, tweak one of these values and then the 'lid close' function starts working!

So in summary, after a reboot I have to go into the power settings and change some values to get the 'lid close' behaviour to 'turn on'. Feels like a bug to me. I wonder if anyone else has the same problem?

Richard

---

### Post by rconway on 2013-08-17
Some more information...

1. After reboot, but before logging on, i.e. at the login screen, then the lid close is correctly turning off the screen. Only after login does the problem get introduced.
2. I added a new user as an experiment to check the behaviour with a fresh user's environment - The problem is the same for this new user.
3. Once the 'change something in power manager' tweak has been applied to make the lid close function work correctly, then logging out and back in does not cause the problem to occur in the way that rebooting does.

Richard

---

### Post by Toz on 2013-08-17
Can you post the contents of the file **$HOME/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-power-manager.xml** after you've changed those settings (before you log out) _and_ again right after you log in before you make any changes? Lets see if they are the same. Those settings are stored there.

---

### Post by rconway on 2013-08-17
Two versions of file:

- before-reboot.xfce4-power-manager.xml - when it's working
<?xml version="1.0" encoding="UTF-8"?>

<channel name="xfce4-power-manager" version="1.0">
  <property name="xfce4-power-manager" type="empty">
    <property name="power-button-action" type="empty"/>
    <property name="lid-action-on-ac" type="uint" value="0"/>
    <property name="dpms-on-ac-sleep" type="uint" value="0"/>
    <property name="dpms-on-ac-off" type="uint" value="0"/>
    <property name="lid-action-on-battery" type="uint" value="0"/>
    <property name="critical-power-action" type="uint" value="4"/>
    <property name="brightness-on-battery" type="uint" value="9"/>
    <property name="dpms-on-battery-sleep" type="uint" value="0"/>
    <property name="dpms-on-battery-off" type="uint" value="0"/>
    <property name="brightness-level-on-ac" type="uint" value="80"/>
  </property>
</channel>

- after-reboot.xfce4-power-manager.xml - not working
<?xml version="1.0" encoding="UTF-8"?>

<channel name="xfce4-power-manager" version="1.0">
  <property name="xfce4-power-manager" type="empty">
    <property name="power-button-action" type="empty"/>
    <property name="lid-action-on-ac" type="uint" value="0"/>
    <property name="dpms-on-ac-sleep" type="uint" value="0"/>
    <property name="dpms-on-ac-off" type="uint" value="0"/>
    <property name="lid-action-on-battery" type="uint" value="0"/>
    <property name="critical-power-action" type="uint" value="4"/>
    <property name="brightness-on-battery" type="uint" value="9"/>
    <property name="dpms-on-battery-sleep" type="uint" value="0"/>
    <property name="dpms-on-battery-off" type="uint" value="0"/>
    <property name="brightness-level-on-ac" type="uint" value="80"/>
  </property>
</channel>

I've diff'ed them and they appear the same.

Another discovery - After reboot, login, in the state where its not working, I can get it working by running...

$ xfce4-power-manager --restart

i.e. no need to do some fake edits in power manager, but instead just restart the process.

Makes no sense to me!

---

### Post by rconway on 2013-08-17
This might be a red herring, but it seems I can simulate the 'works' / 'broken' behaviour by right-clicking the battery icon in the indicator area and selecting Mode -> Normal / Presentation - where 'Presentation' is equivalent to the broken state. But the starting state is always Normal, which is the working state, except immediately after reboot.

---

### Post by Toz on 2013-08-17
> **rconway said:**
> Another discovery - After reboot, login, in the state where its not working, I can get it working by running...

$ xfce4-power-manager --restart

i.e. no need to do some fake edits in power manager, but instead just restart the process.

Makes no sense to me!
Try clearing out your sessions cache - maybe somethings not right there:
1. Logout of the gui session and log into the console session on tty1.
2. Execute:
```
cd .cache
rm -rf sessions
```
3. Go back to gui login on tty7
4. Login and check.

---

### Post by rconway on 2013-08-18
Deleted the .cache/sessions as you suggested and then rebooted, but makes no difference I'm afraid.
Seems that when xfce4-power-manager runs for the first time it isn't initialising properly.

I have 3 workarounds:
1. Change something in settings
2. Run xfce4-power-manager --restart
3. Use the indicator icon to set Mode -> Normal

I wonder what these have in common.

I notice (from reading xfce bug 6515) that setting "Nothing" will "send DPMS off signal to the screen if no external monitor is connected". Perhaps, in my case, it thinks I have an external monitor connected first time through. Wonder how I debug this.

---

### Post by Toz on 2013-08-18
To see debugging info:
```
xfce4-power-manager --debug
```

---

### Post by steamer360 on 2013-08-18
If nothing seems to work, a temporary fix could be enabling the screen to do an auto shut off after a couple of minutes of inactivity. This isn't a perfect solution, but it could conserve some more battery.

---

### Post by rconway on 2013-08-18
Using xfce4-power-manager --debug have can see that the case which fails (first time after boot) shows...

--snip--
TRACE[xfpm-manager.c:317] xfpm_manager_lid_changed_cb(): LID close event: ((XfpmLidTriggerAction) LID_TRIGGER_NOTHING)
TRACE[xfpm-dpms.c:302] xfpm_dpms_force_level(): start
TRACE[xfpm-dpms.c:315] xfpm_dpms_force_level(): DPMS is disabled
TRACE[xfpm-power.c:1149] xfpm_power_refresh_adaptor_visible(): Tray icon configuration: : ((XfpmShowIcon) SHOW_ICON_WHEN_BATTERY_PRESENT)
TRACE[xfpm-power.c:1113] xfpm_power_hide_adapter_icon(): Hide adaptor icon
TRACE[xfpm-battery.c:286] xfpm_battery_refresh_icon(): Battery state 2
TRACE[xfpm-power.c:1149] xfpm_power_refresh_adaptor_visible(): Tray icon configuration: : ((XfpmShowIcon) SHOW_ICON_WHEN_BATTERY_PRESENT)
TRACE[xfpm-power.c:1113] xfpm_power_hide_adapter_icon(): Hide adaptor icon
TRACE[xfpm-manager.c:344] xfpm_manager_lid_changed_cb(): LID opened: ((XfpmLidTriggerAction) LID_TRIGGER_NOTHING)
TRACE[xfpm-dpms.c:302] xfpm_dpms_force_level(): start
TRACE[xfpm-dpms.c:315] xfpm_dpms_force_level(): DPMS is disabled
--snip--

...whereas after restarting xfce4-power-manager I see...

--snip--
TRACE[xfpm-manager.c:317] xfpm_manager_lid_changed_cb(): LID close event: ((XfpmLidTriggerAction) LID_TRIGGER_NOTHING)
TRACE[xfpm-dpms.c:302] xfpm_dpms_force_level(): start
TRACE[xfpm-dpms.c:321] xfpm_dpms_force_level(): Forcing DPMS mode 3
TRACE[xfpm-power.c:1149] xfpm_power_refresh_adaptor_visible(): Tray icon configuration: : ((XfpmShowIcon) SHOW_ICON_WHEN_BATTERY_PRESENT)
TRACE[xfpm-power.c:1113] xfpm_power_hide_adapter_icon(): Hide adaptor icon
TRACE[xfpm-manager.c:344] xfpm_manager_lid_changed_cb(): LID opened: ((XfpmLidTriggerAction) LID_TRIGGER_NOTHING)
TRACE[xfpm-dpms.c:302] xfpm_dpms_force_level(): start
TRACE[xfpm-dpms.c:321] xfpm_dpms_force_level(): Forcing DPMS mode 0
--snip--

So the problem is that DPMS is initially disabled - how does this get started?

---

### Post by rconway on 2013-08-18
Thanks for the suggestion, but this then causes other annoyances e.g. if watching a movie etc. then the screen goes off.

---

### Post by rconway on 2013-08-18
This workaround seems to work...

Rename /usr/bin/xfce4-power-manager to _xfce4-power-manager

Create /usr/bin/xfce4-power-manager as the following script...

--snip--
#!/bin/bash
function turn_on_dpms()
{
  sleep 5
  xset dpms force on
}
turn_on_dpms &
_xfce4-power-manager "$@"
--snip--

It's a bit ropey, but seems to work. Of course it will get overwritten on the next update.

---

### Post by Toz on 2013-08-18
> **rconway said:**
> Using xfce4-power-manager --debug have can see that the case which fails (first time after boot) shows...

--snip--
TRACE[xfpm-manager.c:317] xfpm_manager_lid_changed_cb(): LID close event: ((XfpmLidTriggerAction) LID_TRIGGER_NOTHING)
TRACE[xfpm-dpms.c:302] xfpm_dpms_force_level(): start
TRACE[xfpm-dpms.c:315] xfpm_dpms_force_level(): DPMS is disabled
TRACE[xfpm-power.c:1149] xfpm_power_refresh_adaptor_visible(): Tray icon configuration: : ((XfpmShowIcon) SHOW_ICON_WHEN_BATTERY_PRESENT)
TRACE[xfpm-power.c:1113] xfpm_power_hide_adapter_icon(): Hide adaptor icon
TRACE[xfpm-battery.c:286] xfpm_battery_refresh_icon(): Battery state 2
TRACE[xfpm-power.c:1149] xfpm_power_refresh_adaptor_visible(): Tray icon configuration: : ((XfpmShowIcon) SHOW_ICON_WHEN_BATTERY_PRESENT)
TRACE[xfpm-power.c:1113] xfpm_power_hide_adapter_icon(): Hide adaptor icon
TRACE[xfpm-manager.c:344] xfpm_manager_lid_changed_cb(): LID opened: ((XfpmLidTriggerAction) LID_TRIGGER_NOTHING)
TRACE[xfpm-dpms.c:302] xfpm_dpms_force_level(): start
TRACE[xfpm-dpms.c:315] xfpm_dpms_force_level(): DPMS is disabled
--snip--

...whereas after restarting xfce4-power-manager I see...

--snip--
TRACE[xfpm-manager.c:317] xfpm_manager_lid_changed_cb(): LID close event: ((XfpmLidTriggerAction) LID_TRIGGER_NOTHING)
TRACE[xfpm-dpms.c:302] xfpm_dpms_force_level(): start
TRACE[xfpm-dpms.c:321] xfpm_dpms_force_level(): Forcing DPMS mode 3
TRACE[xfpm-power.c:1149] xfpm_power_refresh_adaptor_visible(): Tray icon configuration: : ((XfpmShowIcon) SHOW_ICON_WHEN_BATTERY_PRESENT)
TRACE[xfpm-power.c:1113] xfpm_power_hide_adapter_icon(): Hide adaptor icon
TRACE[xfpm-manager.c:344] xfpm_manager_lid_changed_cb(): LID opened: ((XfpmLidTriggerAction) LID_TRIGGER_NOTHING)
TRACE[xfpm-dpms.c:302] xfpm_dpms_force_level(): start
TRACE[xfpm-dpms.c:321] xfpm_dpms_force_level(): Forcing DPMS mode 0
--snip--
Interesting.

> So the problem is that DPMS is initially disabled - how does this get started?
Anything in your xorg.conf file about DPMS? If not, try adding:
```
Option "DPMS" "true"
```
...to the "Monitor" section.

---

### Post by Toz on 2013-08-18
> **rconway said:**
> 
It's a bit ropey, but seems to work. Of course it will get overwritten on the next update.
I believe that /usr/local/bin is searched first (you can verify be checking your $PATH variable). If so, you could put your script there, that way it won't get over-written.

---

### Post by rconway on 2013-08-19
It seems I don't have an xorg.conf, and the man page states that the default value for Option DPMS is enabled.
Also recall that when I run xfce4-power-manager --restart then it works, and it also works at the login screen.
It feels a bit like a timing issue when xfce4-power-manager runs during my login sequence.

---

### Post by rconway on 2013-08-19
OK, good idea, I'll give that a try. I'm at work now, so won't be until I'm at home this evening.

---

