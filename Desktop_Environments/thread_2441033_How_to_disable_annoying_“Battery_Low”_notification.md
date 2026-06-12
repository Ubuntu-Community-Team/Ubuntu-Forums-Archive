---
title: "How to disable annoying “Battery Low” notifications in XFCE desktop environment?"
date: 2020-04-18
forum: Desktop Environments
---

### Post by RockTeam on 2020-04-18
I found that when the battery level is 10% or below popup notifications are appearing on each percent of discharge rate in the right top corner. Clicking on “Battery settings” do nothing. I’m sure that this comes not from xfce4-power-manager. I tried to disable all notifications but this ugly battery notification still appears.

I tried to search for the source of this notification yesterday more then 5 hours and went to bed late after midnight. Please help to find the root of this issue. This is standard Xubuntu 18.04 LTS that I got after dist-upgrade from Xubuntu 14.04 LTS.

Screenshot:

[[ATTACH=CONFIG]285551[/ATTACH]]("https://www.dropbox.com/s/83f8llrpok2ouxj/From10p.png")

---

### Post by ecostato12 on 2020-04-18
you can try sudo apt-get install --reinstall [COLOR=#000000] xfce4-power-manager, and disable notifications.
[/COLOR]

---

### Post by #&amp;thj^% on 2020-04-18
This is still a bug in "Upower". I just disabled UPower by running "systemctl stop upower" and "systemctl mask upower".
However just running "systemctl stop upower", may be enough.
It is not a perfect answer if you have a laptop, but it is fine for a desktop computer.
Also check with "upower --dump"

---

### Post by RockTeam on 2020-04-19
UPower config is pretty simple and there is no configurable options for notifications unfortunately.
  
 ```
[UPower]
 
 EnableWattsUpPro=false
 NoPollBatteries=false
 IgnoreLid=false
 UsePercentageForPolicy=true
 PercentageLow=5
 PercentageCritical=3
 PercentageAction=1
 TimeLow=300
 TimeCritical=180
 TimeAction=60
 CriticalPowerAction=Hibernate
 
```

  	 	 	 	   I can recall one discussion where it was mentioned that if in the org.freedesktop.Upower.conf file remove all content between these <busconfig> </busconfig> tags it will stop notifications from UPpower. Maybe I need to try this also.
 
 
 Thank you for suggestion to try with &#8216;upower -dump&#8217;. Definitely this should be a good start in this case. Discharging battery again for more tests.

---

### Post by #&amp;thj^% on 2020-04-21
> **RockTeam said:**
> UPower config is pretty simple and there is no configurable options for notifications unfortunately.
  
 ```
[UPower]
 
 EnableWattsUpPro=false
 NoPollBatteries=false
 IgnoreLid=false
 UsePercentageForPolicy=true
 PercentageLow=5
 PercentageCritical=3
 PercentageAction=1
 TimeLow=300
 TimeCritical=180
 TimeAction=60
 CriticalPowerAction=Hibernate
 
```

  	 	 	 	   I can recall one discussion where it was mentioned that if in the org.freedesktop.Upower.conf file remove all content between these <busconfig> </busconfig> tags it will stop notifications from UPpower. Maybe I need to try this also.
 
 
 Thank you for suggestion to try with &#8216;upower -dump&#8217;. Definitely this should be a good start in this case. Discharging battery again for more tests.

Keep us posted, funny I did not see your reply till just now but I can confirm by altering upower's config file also works.
My UPconfig on arch works very nice with:
```
# Only the system vendor should modify this file, ordinary users
# should not have to change anything.

[UPower]

# Enable the Watts Up Pro device.
#
# The Watts Up Pro contains a generic FTDI USB device without a specific
# vendor and product ID. When we probe for WUP devices, we can cause
# the user to get a perplexing "Device or resource busy" error when
# attempting to use their non-WUP device.
#
# The generic FTDI device is known to also be used on:
#
# - Sparkfun FT232 breakout board
# - Parallax Propeller
#
# default=false
EnableWattsUpPro=false

# Don't poll the kernel for battery level changes.
#
# Some hardware will send us battery level changes through
# events, rather than us having to poll for it. This option
# allows disabling polling for hardware that sends out events.
#
# default=false
NoPollBatteries=false

# Do we ignore the lid state
#
# Some laptops are broken. The lid state is either inverted, or stuck
# on or off. We can't do much to fix these problems, but this is a way
# for users to make the laptop panel vanish, a state that might be used
# by a couple of user-space daemons. On Linux systems, see also
# logind.conf(5).
#
# default=false
IgnoreLid=false

# Policy for warnings and action based on battery levels
#
# Whether battery percentage based policy should be used. The default
# is to use the time left, change to true to use the percentage, which
# should work around broken firmwares. It is also more reliable than
# the time left (frantically saving all your files is going to use more
# battery than letting it rest for example).
# default=true
UsePercentageForPolicy=true

# When UsePercentageForPolicy is true, the levels at which UPower will
# consider the battery low, critical, or take action for the critical
# battery level.
#
# This will also be used for batteries which don't have time information
# such as that of peripherals.
#
# If any value is invalid, or not in descending order, the defaults
# will be used.
#
# Defaults:
# PercentageLow=10
# PercentageCritical=3
# PercentageAction=2
PercentageLow=10
PercentageCritical=3
PercentageAction=2

# When UsePercentageForPolicy is false, the time remaining at which UPower
# will consider the battery low, critical, or take action for the critical
# battery level.
#
# If any value is invalid, or not in descending order, the defaults
# will be used.
#
# Defaults:
# TimeLow=1200
# TimeCritical=300
# TimeAction=120
TimeLow=1200
TimeCritical=300
TimeAction=120

# The action to take when "TimeAction" or "PercentageAction" above has been
# reached for the batteries (UPS or laptop batteries) supplying the computer
#
# Possible values are:
# PowerOff
# Hibernate
# HybridSleep
#
# If HybridSleep isn't available, Hibernate will be used
# If Hibernate isn't available, PowerOff will be used
CriticalPowerAction=HybridSleep
```
***However on Ubuntu (18.04 to 20.4) had to comment out whole config, leaving empty <busconfig></busconfig> tag.

---

### Post by RockTeam on 2020-04-24
I have tried comment everything  between <busconfig> </busconfig> tags in the org.freedesktop.Upower.conf file but in this case I do not see Power Management indicator in the panel. Indeed this behavior that I mentioned in the beginning looks to be a bug in software. I decided to try with upgrade on Xubuntu 20.04 LTS in a few month.

---

