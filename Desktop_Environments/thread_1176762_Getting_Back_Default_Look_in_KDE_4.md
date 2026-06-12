---
title: "Getting Back Default Look in KDE 4"
date: 2009-06-02
forum: Desktop Environments
---

### Post by Nir Friedman on 2009-06-02
Hey all,

I recently installed a dark theme (darkPearl) from Kde-look.org. I didn't install any third party programs, I just used the settings in KDE combined with a downloaded colour pack. I've gotten tired of it, so I tried to put things back to default settings. While some things worked, many things do not look right.
Examples: buttons in programs like firefox, pidgin, tabs in pidgin, the background for kicker is black (I don't think it was like that?), background for kate is still black.
My procedure for undoing this was to go to system settings, appearance and make sure everything was set to the Oxygen schemes. Does anybody know a step by step, guaranteed way to get back the original GUI configuration? I'm even willing to do something drastic like delete a config file to force KDE to re-create it if this will go back to the original default settings. (Just to clarify, by default I mean the EXACT appearance of KDE 4 when you first install Kubuntu). thanks in advance!

---

### Post by Nir Friedman on 2009-06-02
Bump. Please, this is really killing me, a lot of my applications are unusable.

---

### Post by krazyd on 2009-06-03
What happens when you go to System Settings > Appearance > Colors, and select 'Default' or 'Oxygen' ?

---

### Post by Nir Friedman on 2009-06-03
it didn't fix everything. I eventually figured out what to do. First, I had to delete my ~/.kde folder. Second, you have to go to appearance and change the settings for all the engines. I didn't understand how that works; I thought it only uses one thing at a time. I went to QtCurve and changed the settings to default and that fixed the last few things. Thanks though for the post.

Cheers

---

### Post by chandra on 2009-07-01
System Settings -> Appearance -> Icons -> Theme and/or Advanced

should have fixed it, although it is too late to test that out now.

---

