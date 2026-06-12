---
title: "XFCE 4.10: Open Windows Sticking Underneath Xfce Panel"
date: 2015-07-30
forum: Desktop Environments
---

### Post by crawf777 on 2015-07-30
Hi,
 
 
 I have been experiencing a problem with my xfce desktop for a while now, that I would like to get resolved if possible.
 
 
 I have the panel at the top. And sometimes when I have windows open, they get stuck underneath the panel. I then have to unlock the panel move it down, so I can get at the open window and move them down the screen. I then have to move the panel back to its place and lock it.
 
 
 This process is getting a bit tiresome and I would like to fix it but cant find anything online about this.
 
 
 Would be grateful for any help or advice

 
 
 Thanks in advance,
 
 
 PC.

---

### Post by howefield on 2015-07-31
Whilst not solving the underlying issue you should be able to (from anywhere inside the window) press the Alt key and left click and drag the window from underneath the panel. Might make it less cumbersome whilst you seek a proper answer to the problem.

---

### Post by Toz on 2015-07-31
In the panel properties, make sure that "Don't reserve space on borders" is unchecked. When unchecked, it enables struts functionality which keeps windows from over/underlapping with the panel.

---

### Post by crawf777 on 2015-07-31
Thanks for the tip howefield, thats very useful to know.

---

### Post by crawf777 on 2015-07-31
Thanks for your reply Toz, I had a look the "Don't reserve space on borders" was already unchecked...

---

### Post by Toz on 2015-07-31
Is it certain specific windows that do this, or all windows?

Try setting and upper margin in Settings Manager >> Workspaces >> Margins tab, to see if that helps.

Also, please post back the results of this command:
```
xfconf-query -c xfce4-panel -p /panels/panel-AAA/disable-struts
```
...where AAA is the panel number. So for example, for panel-0, you would type:
```
xfconf-query -c xfce4-panel -p /panels/panel-0/disable-struts
```

---

### Post by crawf777 on 2015-08-01
command returned string: false

Upper margin didn't have an affect. The problem is occurring with all windows.

---

### Post by Toz on 2015-08-01
Can you post all of your xfce4-panel settings:
```
xfconf-query -c xfce4-panel -lv
```

...as well as the results of:
```
ps -ef | grep xfwm4 | grep -v grep
```

---

### Post by crawf777 on 2015-08-05
Hi Toz, thanks for getting back to me.

xfce-panel settings:

/configver                          2
/panels                             1
/panels/panel-0/autohide            false
/panels/panel-0/background-alpha    80
/panels/panel-0/background-style    1
/panels/panel-0/disable-struts      false
/panels/panel-0/enter-opacity       100
/panels/panel-0/leave-opacity       100
/panels/panel-0/length              100
/panels/panel-0/length-adjust       true
/panels/panel-0/mode                0
/panels/panel-0/plugin-ids          <<UNSUPPORTED>>
/panels/panel-0/position            p=6;x=683;y=13
/panels/panel-0/position-locked     true
/panels/panel-0/size                24
/panels/panel-0/span-monitors       false
/plugins/plugin-1                   whiskermenu
/plugins/plugin-2                   tasklist
/plugins/plugin-2/flat-buttons      true
/plugins/plugin-3                   separator
/plugins/plugin-3/expand            true
/plugins/plugin-3/style             0
/plugins/plugin-4                   systray
/plugins/plugin-4/names-visible     <<UNSUPPORTED>>
/plugins/plugin-4/show-frame        false
/plugins/plugin-4/size-max          22
/plugins/plugin-5                   indicator
/plugins/plugin-5/blacklist         <<UNSUPPORTED>>
/plugins/plugin-5/known-indicators  <<UNSUPPORTED>>
/plugins/plugin-6                   separator
/plugins/plugin-6/expand            false
/plugins/plugin-6/style             0
/plugins/plugin-7                   clock
/plugins/plugin-7/digital-format    %d %b, %H:%M

second command:

user    2329  1972  0 Aug05 ?        00:01:50 xfwm4 --replace

---

### Post by Toz on 2015-08-05
Everything looks fine there. Can you try clearing your sessions cache (manually) to see if that helps:

1. Log out.
2. Press Ctrl+Alt+F1
3. Log in to the console.
4. Enter the following commands:
```
cd .cache
rm -rf sessions
```
5. Press Ctrl+Alt+F7
6. Log in to Xfce and see if the windows behave.


Question: Do you have an autostart entry to run "xfwm4 --replace"?

---

### Post by crawf777 on 2015-08-10
Hi,

 I don't have an entry for xfce--replace in autostart, but clearing the cache seems to have did the trick.

 On bumping the panel, widows now maximize, as opposed to staying small and going underneath it.

 Looks like the problem is resolved.

 Thanks for your help.

---

