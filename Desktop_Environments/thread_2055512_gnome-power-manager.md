---
title: "gnome-power-manager"
date: 2012-09-09
forum: Desktop Environments
---

### Post by ronnystickshift on 2012-09-09
Greetings, folks.  I'm using Ubuntu 12.04, gnome (no effects) desktop environment.  The small icon on the task bar that indicates the battery state is not present.  If I go to the menu -> System Tools -> Preferences, there is no power management option.

I have recently purged and reinstalled gnome-power-manager.  The command gnome-power-statistics works as expected, but there is no binary called gnome-power-preferences, even though there should be one.

Any thoughts on how I can get this binary and change my preferences?  Once in a rare while my laptop accidentally gets unplugged without my noticing and then dies because it runs out of battery very quickly, which is very annoying.  Please help!  :)

---

### Post by ronnystickshift on 2012-09-11
anyone?  not a major issue of course, but the solution could be instructive :)

---

### Post by dozdozez on 2012-09-11
what about gnome-control-center ? 
(you can type it a interminal if you don't find it in menus )

---

### Post by newb85 on 2012-09-11
> **ronnystickshift said:**
> there is no binary called gnome-power-preferences, even though there should be one.

gnome-power-preferences isn't present on my machine, either.  What makes you think it should be?  If it's experience from earlier releases, then it has probably been replaced with something else.

---

### Post by claracc on 2012-09-12
I cannot find any battery gnome applet to add to panel.

But, I have docky installed in my gnome fallback desktop, and you can add a docklet named battery monitor, which shows you its state os charge.

---

### Post by claracc on 2012-09-12
Also, when I unplug my laptop from ca supply, in the complete mini-application indicator which I have in my panel, appears the icon of the battery, saying how much time remain.

---

### Post by newb85 on 2012-09-12
Click the gear icon in the upper-right corner of the screen and select "System Settings".  Then go to "Power".  The last option there should be "Show battery status in the menu bar..."  Make sure "Never" is not selected.

---

### Post by Closetheloop on 2012-09-12
Yes, not sure if I should start a new thread...but I hope my query is applicable here.

I have a Thinkpad notebook and I have just done a clean install of 12.04 LTS server and then installed the GUI using sudo apt-get install --no-install-recommends ubuntu-desktop.

I am familiarising myself with Unity (quite a task...but I like what I see :) ). However when I click the gear icon in the upper-right corner of the screen and select "System Settings". Then go to "Power" I see a nice battery icon which does absolutely nothing when I execute it.

Any idea what I need to load to get the power icon functioning? It is obviously missing files that were not installed by '--no-install-recommends ubuntu-desktop'.

Thanks for any help guys.:)

---

### Post by newb85 on 2012-09-12
> **Closetheloop said:**
> Yes, not sure if I should start a new thread...but I hope my query is applicable here.

I have a Thinkpad notebook and I have just done a clean install of 12.04 LTS server and then installed the GUI using sudo apt-get install --no-install-recommends ubuntu-desktop.

I am familiarising myself with Unity (quite a task...but I like what I see :) ). However when I click the gear icon in the upper-right corner of the screen and select "System Settings". Then go to "Power" I see a nice battery icon which does absolutely nothing when I execute it.

Any idea what I need to load to get the power icon functioning? It is obviously missing files that were not installed by '--no-install-recommends ubuntu-desktop'.

Thanks for any help guys.:)

Not sure I quite understand your situation.  Are you saying that when you Click on "Power", the power options don't come up?

If that's the case, please make sure that both gnome-control-center and indicator-power are installed.

---

### Post by Closetheloop on 2012-09-12
Perfect :popcorn:

Basically:
- gnome-control-center was already installed:
- indicator-power was NOT installed:

So I installed indicator-power and now when I login in on battery:
1) I get a battery image in the top left hand corner which opens up the Power options...
2) When I select "System Settings" then go to "Power" I see the afore-mentioned battery icon and this time when I execute that icon I also get the Power options.

Thats really nice thanks.

---

### Post by ronnystickshift on 2012-09-12
gnome-control-center and indicator-power are both the latest version, at least that's what apt-get tells me when i attempt to install them.

gnome-control-center works fine, when i click on power it opens a window, and by "Show battery status in the menu bar" there is a pull down menu.  this is where it gets a little weird: when i first open the control center, that pull down menu is blank.  when i select another option, like "When battery is present" nothing changes.  when i close the gnome-control-center, nothing happens.  and then when i open it again, the text for the pull down menu is blank again!

---

### Post by newb85 on 2012-09-12
> **Closetheloop said:**
> Perfect :popcorn:

Basically:
- gnome-control-center was already installed:
- indicator-power was NOT installed:

So I installed indicator-power and now when I login in on battery:
1) I get a battery image in the top left hand corner which opens up the Power options...
2) When I select "System Settings" then go to "Power" I see the afore-mentioned battery icon and this time when I execute that icon I also get the Power options.

Thats really nice thanks.

Glad you're back in business.

---

### Post by newb85 on 2012-09-12
> **ronnystickshift said:**
> gnome-control-center and indicator-power are both the latest version, at least that's what apt-get tells me when i attempt to install them.

gnome-control-center works fine, when i click on power it opens a window, and by "Show battery status in the menu bar" there is a pull down menu.  this is where it gets a little weird: when i first open the control center, that pull down menu is blank.  when i select another option, like "When battery is present" nothing changes.  when i close the gnome-control-center, nothing happens.  and then when i open it again, the text for the pull down menu is blank again!

Hmm...I would try reinstalling indicator-power.

Was 12.04 a fresh install, or did you upgrade through the package manager?  If it's an upgrade, what version was the last fresh install?

---

### Post by ronnystickshift on 2012-09-13
> **newb85 said:**
> Hmm...I would try reinstalling indicator-power.

Was 12.04 a fresh install, or did you upgrade through the package manager?  If it's an upgrade, what version was the last fresh install?

thanks for the suggestion - i just tried reinstalling indicator-power now, but the situation is the same unfortunately.

my last fresh install was 8.04.  seriously.  i upgraded from 8.04 to 10.04 when it came out, and then from 10.04 to 10.10 to 11.04 to 11.10 all in the same day, and then from 11.10 to 12.04 a few months after that.

---

### Post by newb85 on 2012-09-13
Okay, here's something else to try.  (I found the info [here]("http://askubuntu.com/questions/68445/no-battery-status-icon").)

In a terminal:

$ gsettings list-recursively | grep settings-daemon.*.power\ active

The line it spits out should end in *true*.  If not, we've found the problem!  Fix it:

$ gsettings set org.gnome.settings-daemon.plugins.power active true

Log out and back in.

---

### Post by ronnystickshift on 2012-09-14
> **newb85 said:**
> Okay, here's something else to try.  (I found the info [here]("http://askubuntu.com/questions/68445/no-battery-status-icon").)

In a terminal:

$ gsettings list-recursively | grep settings-daemon.*.power\ active

The line it spits out should end in *true*.  If not, we've found the problem!  Fix it:

$ gsettings set org.gnome.settings-daemon.plugins.power active true

Log out and back in.

the first line returned true.  so using the second line i set it false, logged out and back in, set it true, logged out and back in again, but still no battery icon.

also, i looked at some of the other suggestions in that link.  dconf-editor shows it as set to present, meaning it should be displayed all the time, so that doesn't help.  and if i try to run gnome-setting-daemon, i get an error message:
** (gnome-settings-daemon:6794): WARNING **: You can only run one xsettings manager at a time; exiting

:(

---

