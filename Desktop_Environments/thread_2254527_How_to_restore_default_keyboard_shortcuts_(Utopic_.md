---
title: "How to restore default keyboard shortcuts? (Utopic Unicorn)"
date: 2014-11-27
forum: Desktop Environments
---

### Post by radiognome on 2014-11-27
Today I sort of accidentally changed the shortcut for the HUD to something other then the left ALT key.

Using settings/keyboard I can not seem to get it back. Pressing the ALT key ends up disabeling the HUD shortcut. Seems the ALT key is not registered by the application as a possible shortcut key. I can use all kinds of other combinations, but I want it back the way it was.

Is there a way to revert to default, or is there some config-file I could edit, bypassing the GUI? After two hours of searching and trying, I revert to posting a new thread on this forum.

Thanks for reading,

Martin

---

### Post by CantankRus on 2014-11-27
How did you accidentally change?

Try setting back to default with...
```
dconf reset -f /org/compiz/integrated/show-hud
```

---

### Post by radiognome on 2014-11-28
@CantankRus:

Thanks, just the thing I was looking for, but could not find. Worked perfectly.

Where can I find more about this?

Kind regards,

Martin

---

### Post by CantankRus on 2014-11-28
About dconf you mean?
```
man dconf
```

If I want to change a dconf setting via a command I search for the key in dconf-editor and then use with **dconf write** or  **dconf reset**

eg the 1st attached pic is the show-clock key in dconf-editor.
The key path is the **[COLOR="#FF8C00"]schema[/COLOR]** plus the [COLOR="#008000"]**key Name**[/COLOR]
Start the path with a forward slash then substitute each "." in the Schema with a "/" and append the actual key name, add a space then the [COLOR="#EE82EE"]**key value**[/COLOR]
eg to turn the panel clock off...
```
dconf write [COLOR="#FF8C00"]**/com/canonical/indicator/datetime/**[/COLOR][COLOR="#008000"]**show-clock**[/COLOR] [COLOR="#EE82EE"]**false**[/COLOR]
```

Here's an example script to toggle the clock on/off
```
#!/bin/bash 
#
# Script to toggle visibilty of clock in Unity Panel
#
#

hide="dconf write /com/canonical/indicator/datetime/show-clock false"
show="dconf write /com/canonical/indicator/datetime/show-clock true"
test=$( dconf read /com/canonical/indicator/datetime/show-clock )

if [ $test = "true" ]; then
	eval $hide
else
	eval $show
fi
```

Another handy command is
```
dconf watch /
```
Allows you to watch a key or directory for changes.(2nd pic)
eg if you want to find out the dconf setting a tool like unity-tweak-tool is changing,
run the "dconf watch /" command and make the change in the tweak tool.

---

### Post by radiognome on 2014-11-29
Thanks again for this elaborate explanation.... Learning a lot about how Ubuntu stores its desktop-settings. I mostly use Ubuntu server, so I was expecting some files in /etc/....

Kind regards,

Martin

---

