---
title: "Inspiron 1420n, no action taken on battery critical"
date: 2009-12-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by oryan_dunn on 2009-12-01
I've tried several things to get this to work, but nothing has worked so far.  I've got a 1420n with Ubuntu Hardy install that does not take any action on battery critical.  I've modified GnomePowerManager to use percentages instead of time, but that didn't work, then I enabled laptop-mode, but that didn't work either.  Is there anything else I can try?  Looking through the bug reports, seems that this problem isn't limited to myself, but it is quite annoying; I don't want to damage my battery or lose data.  I get all the balloon popups with percentages/times and those all seem to be dead on.

---

### Post by Denny Johnson on 2009-12-02
system/preferences/power mgmt/on battery power/when battery power is critically low

---

### Post by oryan_dunn on 2009-12-02
Yeah, that is set to take action (hibernate), but nothing happens. Hibernate works fine when invoked from the menu.

---

### Post by Denny Johnson on 2009-12-02
I'm not knowledgeable enuf to offer other suggestions, but it seems we have the same set up, hardy on 1420n. If I can help by checking anything on my end, let me know.
I assume mine is working properly, but can't say for sure as I have never run the battery that low.
Good luck

---

### Post by oryan_dunn on 2009-12-04
Well, I got it working, or at least it worked once.  I followed the directions here:
[http://ubuntuforums.org/showthread.php?t=1330805](http://ubuntuforums.org/showthread.php?t=1330805)
This basically changed two things, it set the defaults (which using gconf-editor I don't think did), but I used the values he lists 10, 6, and 5, which are higher than I had set before.

```

sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type bool --set /apps/gnome-power-manager/general/use_time_for_policy false
sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type int --set /apps/gnome-power-manager/thresholds/percentage_action 5
sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type int --set /apps/gnome-power-manager/thresholds/percentage_critical 6
sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type int --set /apps/gnome-power-manager/thresholds/percentage_low 10

```

I also enabled the laptop mode in /etc/laptop-mode/laptop-mode.conf, but I didn't have it hibernate on me like it should have after changing that setting.  Now, after the changes above, it gives me warnings at 10 and and 6 percent it says it is going to hibernate soon, then shortly after the last warning, it hibernates.

---

