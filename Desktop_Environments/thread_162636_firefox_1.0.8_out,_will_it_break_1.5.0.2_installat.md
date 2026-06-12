---
title: "firefox 1.0.8 out, will it break 1.5.0.2 installation?"
date: 2006-04-19
forum: Desktop Environments
---

### Post by towsonu2003 on 2006-04-19
see [http://www.ubuntu.com/usn/usn-271-1](http://www.ubuntu.com/usn/usn-271-1)

did anyone tried an update-upgrade? I'm curious as to whether it breaks the 1.5.0.2 installations (both automatix and wiki.ubuntu.com/FirefoxNewVersion ways).

---

### Post by Ramses de Norre on 2006-04-19
No it doesn't, it only replaces the 1.0.7 one.

---

### Post by towsonu2003 on 2006-04-19
[QUOTE=Ramses de Norre]No it doesn't, it only replaces the 1.0.7 one.[/QUOTE]
we played with a couple of settings (wiki instructions). they don't have any effects? 

instructions in question: 

```

# First, /usr/bin/firefox
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
# Then, /usr/bin/mozilla-firefox, used as the default gnome browser
sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox

```

---

### Post by towsonu2003 on 2006-04-19
it might be creating problems: [http://ubuntuforums.org/showpost.php?p=936817&postcount=15](http://ubuntuforums.org/showpost.php?p=936817&postcount=15)

[quote=poster in the link]I know its breaking something, because I get the message:

"unable to make backup link of /usr/sbin/update mozilla-firefox chrome during install"
Please restart any running Firefoxes, or you will experience problems.

What's going on?[/quote]

---

### Post by 5-HT on 2006-04-19
I moved my profile away, removed the 1.0.7 diversion, made sure nothing in /usr/bin/ was linking to 1.5, and had no problems updating 1.0.7 to 1.0.8.

If people are updating, I'd suggest doing something like above if problems are occuring in the update.

(Though I thought the point of the diversion was not to have problems like this?)

----------------------------------
*EDIT: I installed Firefox 1.5 manually from Mozilla's binaries. 

I'm not sure how Automatix installs it. 
Any users who installed 1.5 via Automatix should adjust how they prepare for the update according to how Automatix installed 1.5.

---

### Post by jariy on 2006-04-19
I just hit the update button and same old 1.5 version seems to be running. I did the original 1.5 installation with [the instructions on the wiki]("https://wiki.ubuntu.com/FirefoxNewVersion"). So no problems here.

---

### Post by towsonu2003 on 2006-04-19
I decided to pin it to 1.0.7 so I don't get the 1.0.8 update. Two reasons:
1. I really don't wanna download it via my slow slow dial up (9MB takes 1 hour)...
2. Will do clean install in two months anyway...

If anyone decides to download 1.0.8 and use it instead of 1.5.x, I'd like to know how the performance compares...

---

### Post by andyf on 2006-04-22
It certainly doesn't seem to here. I've got both 1.0.8 (/usr/bin/firefox) and 1.5.0.2 (/usr/local/bin/firefox) running with no problems.

---

### Post by adamkane on 2006-04-22
If you install firefox 1.5 via swiftfox, you avoid any potential dependency problems.

I've found that firefox 1.5 via automatix leads to install/uninstall issues.

Keep firefox 1.0, and find a version of firefox 1.5 with the least footprint possible. The automatix version creates too many problems for new users.

---

