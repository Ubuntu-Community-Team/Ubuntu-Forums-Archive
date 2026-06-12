---
title: "Thunderbird fonts and formatting, messed up when autostarted"
date: 2009-02-19
forum: General Help
---

### Post by anlag on 2009-02-19
When I have Thunderbird start automatically on boot, via an added line in ~/.profile, it's formatted is different. The text in e-mails is tiny, and in the folder view there is a lot of space between lines, etc. If I kill Thunderbird and restart it manually, all the formatting is fine. Editing the settings under Preferences doesn't seem to have any effect.

Could it be that at autostart it's not my (default) Mozilla profile file being used (seem to recall there is such a thing) and that this causes the formatting to look different? Mind, I haven't changed any formatting since installing the program (last night) - it should all be default anyway.

Any advice?

---

### Post by anlag on 2009-03-03
Found a solution while solving another problem. By creating a shell script that first sleeps for 20 seconds and then launches Thunderbird, and putting this script in ~/.profile instead, the system has time both to figure out what formatting to use and also to connect to the network so I don't always get a "could not connect to server" to click away first thing.

---

