---
title: "How to force PCManFM to launch without the side pane"
date: 2014-06-08
forum: Desktop Environments
---

### Post by robert_frittmann2 on 2014-06-08
Normally I launch PCManFM maximized and with the side pane showing the folder tree, and showing hidden icons. I'm trying to set up a separate LXPanel entry that will allow me to launch an instance of PCManFM with different settings to the defaults. I understand that there are some issues with [how view settings change in one PCManFM window affects other PCManFM windows]("http://wiki.lxde.org/en/PCManFM#How_view_settings_change_in_one_PCManFM_window_affects_other_PCManFM_windows"). To try to get around this, I have tried the following, which didn't seem to work...

1. Create a copy of [FONT=courier new]~/.config/pcmanfm/lubuntu/pcmanfm.conf[/FONT] as [FONT=courier new]nosidepane.conf[/FONT]
2. In [FONT=courier new]nosidepane.conf[/FONT] set [FONT=courier new]side_pane_mode=hidden;dirtree[/FONT]
3. Edit [FONT=courier new]~/.config/lxpanel/lubuntu/panels/panel[/FONT] to create a new action with [FONT=courier new]action=pcmanfm --profile=nosidepane.conf[/FONT]
4. When that didn't work, I tried [FONT=courier new]action=pcmanfm --profile=~/.config/pcmanfm/lubuntu/nosidepane.conf[/FONT]
5. When that didn't work, I tried [FONT=courier new]action=pcmanfm --profile=/home/robert/.config/pcmanfm/lubuntu/nosidepane.conf[/FONT]

I figured that launching an instance of PCManFM from LXPanel's menu, with a command line argument specifying a different profile, should solve the problem, but it didn't seem to work. My LXPanel menu icon shows up fine, and launches PCManFM perfectly, it just doesn't seem to accept the [FONT=courier new]--profile[/FONT] setting and still shows the side pane. I've looked through the available [command line options]("http://wiki.lxde.org/en/LXDE:PCManFM_build_and_setup_guide#Command_line_options") but couldn't find an easier way other than with the [FONT=courier new]-p[/FONT] or [FONT=courier new]--profile[/FONT] argument. Anyone know of a way to do this?

---

### Post by Rex Bouwense on 2014-06-08
You can set PCManFM to launch without the side panel by navigating to View->Side Pane and then untick Show Side Pane.  If you want the side pane you can toggle F9 to show or hide.

---

### Post by robert_frittmann2 on 2014-06-08
Umm, yeah, that's not quite what I was after. I'm trying to set up a computer that will be as familiar to a WinXP user as possible. By default, the My Documents link on the Start Menu opens the folder in a restored (not maximized) window, showing large icons, and no side bar. That's the look I'm trying to achieve. Other links to PCManFM should open normally, maximized, with the side bar.

---

