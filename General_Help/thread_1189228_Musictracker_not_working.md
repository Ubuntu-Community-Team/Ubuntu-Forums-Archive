---
title: "Musictracker not working"
date: 2009-06-16
forum: General Help
---

### Post by CaptainMark on 2009-06-16
Im running Intrepid with Pidgin 2.5.2 with musictracker plugin 0.4.1 installed.
for some reason the plugin doesnt work at all making it useless to have. I dont know if im doing something wrong, i have banshee version 1.4.3 installed. i read online that punching this into terminal fixes it,  ```
sed "s/<pref name='bool_disabled' type='bool' value='1'\/>/<pref name='bool_disabled' type='bool' value='0'\/>/" ~/.purple/prefs.xml > ~/.purple/prefs.xml
```but that hasnt helped, ive checked the pidgin debug window and found this ```
[SIZE=3][COLOR=#000000](20:15:32) **util:** Writing file prefs.xml to directory /home/mark/.purple
(20:15:32) **util:** Writing file /home/mark/.purple/prefs.xml
[/COLOR][COLOR=#666666](20:15:36) **jabber:** Sending (ssl): <iq type='get' id='purple8e36270d'><ping xmlns='urn:xmpp:ping'/></iq>
[/COLOR][COLOR=#000000](20:15:36) **jabber:** Recv (ssl)(86): <iq to="************@googlemail.com/home1771A973" id="purple8e36270d" type="result"/>
(20:15:36) **core-musictracker:** org.gnome.Banshee
(20:15:36) **core-musictracker:** proxy
(20:15:36) **core-musictracker:** call
(20:15:36) **core-musictracker:** Banshee,,,,0
(20:15:36) **core-musictracker:** Formatted status: 
(20:15:36) **core-musictracker:** Status set for all accounts[/COLOR][/SIZE]
``` it seems the two programs are not communicating properly.
Any suggestions?

---

### Post by CaptainMark on 2009-06-16
Any ideas at all? could really use some help with this. very frustrating

---

### Post by Eskobar on 2009-10-01
Sorry know one has helped you yet.  I'm having the same issues running Ubuntu Pidgin 2.68 and banshee.  I'll keep googlin' and if I find something I will post back.

---

### Post by fornix on 2009-10-03
Have you tried a new version of musictracker? musictracker is now pidgin-musictracker and current version is 0.4.20. Here's the site link where you could download latest version. [http://code.google.com/p/pidgin-musictracker/](http://code.google.com/p/pidgin-musictracker/) 
Or you could just try updating it via repositories.

---

