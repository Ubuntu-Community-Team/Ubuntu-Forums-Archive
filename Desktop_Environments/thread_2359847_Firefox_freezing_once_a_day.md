---
title: "Firefox freezing once a day"
date: 2017-04-28
forum: Desktop Environments
---

### Post by azaravicius on 2017-04-28
Hi,
I have clean installed Ubuntu 17.04 not long ago. For web browsing I use Firefox 53.0. Once a day Firefox becomes gray and I can't close it. I go to System Monitor and try to kill it, but it do not work. I try to restart Ubuntu, it will close my user season and stops at empty desktop, but Ubuntu will not turn of. It looks like Ubuntu waits for something. Only reset button on computer will turn of computer.
I have Chromium web browser. If I try to start Chromium when Firefox freezes it will try to start for 5-10 seconds, but will not start. So I thinks it is not the problem with Firefox, but something Firefox and Chromium uses.

---

### Post by Xian on 2017-04-28
Do you have a browser extension that is used by both Firefox and Chromium? 

Try disabling all browser extensions and see if the problem reoccurs.

---

### Post by azaravicius on 2017-04-29
I don't really use Chromium so here are no extension in it.
Firefox have 4 extensions: Adblock Plus; DownThemAll; Ubuntu Modifications and Video DownloadHelper.

Is here a log file to look at?

---

### Post by kjartankg on 2017-05-01
I'm running into the same issue. Firefox has frozen 3 times today. I recently upgraded from 16.04 to 17.04 with a rather clean standard setup. If I try to kill firefox then the terminal just hangs and nothing happens. Firfox is at full CPU usage (200%) when this happens.

---

### Post by strangedata on 2017-05-04
I'm seeing this problem too. Usually when I'm trying to open a video or a gif on Whatsapp Web. The browser freezes, I have to force quit it. The process becomes a zombie, and systemd never collects it.

The zombie process keeps using 100% of CPU for a while. I used to be able to delete .parentlock and lock from Firefox's profile and start a new one, but now when I click the Firefox icon to open a new instance the whole system freezes.

I'm thinking it might be an issue with systemd.

---

### Post by linux-k2 on 2017-05-20
I recently upgraded from 16.10 to 17.04, and since then I have had the same Firefox freeze.
I can't find any common action that I do to cause it.  It doesn't happen every day.

Firefox is running something at a low enough level that the system is effectively stuck, and won't shut down.
Firefox uses 100% of 1 CPU, and kill -9 does not get rid of it.
I would run an strace, but I can't start that once I have hit this problem.

I have not noticed anything other than Firefox causing any problem.

---

### Post by todd-kaehler on 2017-05-31
This is also happening to me.  Ubuntu 17.04 and firefox 53.  Only way to fix is to reboot and the reboot hangs so I need to power cycle.  Until fixed I will be using Chrome.

---

### Post by codeprox on 2017-06-04
Having the same exact issue described. Including what strangedata mentioned

> I used to be able to delete .parentlock and lock from Firefox's profile  and start a new one, but now when I click the Firefox icon to open a new  instance the whole system freezes.

Ubuntu 17.04, cpu ryzen 1700

---

### Post by jaarvidsen on 2017-06-10
ive had these crashes too, im suspecting its these hidden addons mozilla keep adding and disabling all the time. theres some info about one of them here thats been added recently - a telemetry one that i do not want [https://bugzilla.mozilla.org/show_bug.cgi?id=1369832](https://bugzilla.mozilla.org/show_bug.cgi?id=1369832)

**NB! if you follow the suggestions below you do so at your own risk, its entirely experimental**

these addons are not visible to the average user and mozilla can add them, disable them and reenable them at their will.
they get installed in /home/USERNAME/.mozilla/firefox/RANDOM/features/
ive deleted  everything there and made the features dir read only

furthermore each time firefox is installed or a new version arrives via the update manager more can be installed here /usr/lib/firefox/browser/features/
ive deleted everything there as well

then i tried to figure out how these get added, i may be wrong but i think in about:config search for 'systemaddon'
i get 2 entries there
extensions.systemAddonSet which seems to list the installed system addons (ive reset the value to nothing)
extension.systemAddon.update.url which i guess may be the url where these addons come from. ive deleted the value

so far no ill effects and no crashes

---

### Post by mikhailovav on 2017-10-04
The problem persists. Xubuntu 17.04, Firefox 55. It seems that it can be provoked by opening about 10 tabs at once, for example. Also, Chromium caused this once (I don't use it as a rule).

---

