---
title: "Eve launcher on Ubuntu keeps crashing."
date: 2017-05-20
forum: Gaming &amp; Leisure
---

### Post by Arminius on 2017-05-20
I followed the instructions over at [https://wiki.eveuniversity.org/Installing_EVE_on_Linux](https://wiki.eveuniversity.org/Installing_EVE_on_Linux)

```
User@Computer:~$ cd evelauncher
User@Computer:~/evelauncher$ chmod u+x evelauncher.sh
User@Computer:~/evelauncher$ ./evelauncher.sh
[0521/070123:WARNING:resource_bundle.cc(291)] locale_file_path.empty() for locale 
Installed Qt WebEngine locales directory not found at location /home/User/evelauncher/translations/qtwebengine_locales. Trying application directory...
Qt WebEngine locales directory not found at location /home/User/evelauncher/qtwebengine_locales. Trying fallback directory... Translations MAY NOT not be correct.
[0521/070123:WARNING:resource_bundle.cc(291)] locale_file_path.empty() for locale 
[S_API FAIL] SteamAPI_Init() failed; SteamAPI_IsSteamRunning() failed.
[S_API FAIL] SteamAPI_Init() failed; unable to locate a running instance of Steam, or a local steamclient.so.
nouveau: kernel rejected pushbuf: No such file or directory
nouveau: ch7: krec 0 pushes 0 bufs 10 relocs 0
nouveau: ch7: buf 00000000 00000002 00000004 00000004 00000000
nouveau: ch7: buf 00000001 00000006 00000004 00000000 00000004
nouveau: ch7: buf 00000002 0000003a 00000002 00000002 00000000
nouveau: ch7: buf 00000003 00000029 00000002 00000002 00000000
nouveau: ch7: buf 00000004 00000007 00000002 00000002 00000000
nouveau: ch7: buf 00000005 00000008 00000002 00000002 00000000
nouveau: ch7: buf 00000006 0000000b 00000002 00000002 00000000
nouveau: ch7: buf 00000007 0000000a 00000002 00000002 00000002
nouveau: ch7: buf 00000008 0000001d 00000002 00000000 00000002
nouveau: ch7: buf 00000009 0000002e 00000002 00000000 00000002
Segmentation fault (core dumped)
User@Computer:~/evelauncher$ 

```

So far every time I've run the launcher a 2nd time the computer has permanently frozen and needed a hard reboot.

---

### Post by Arminius on 2017-05-22
Bump

---

### Post by Perfect Storm on 2017-05-23
[S_API FAIL] SteamAPI_Init() failed; SteamAPI_IsSteamRunning() failed.
[S_API FAIL] SteamAPI_Init() failed; unable to locate a running instance of Steam, or a local steamclient.so.

You properly need steam for this.

---

### Post by Arminius on 2017-05-23
> **Artificial Intelligence said:**
> [S_API FAIL] SteamAPI_Init() failed; SteamAPI_IsSteamRunning() failed.
[S_API FAIL] SteamAPI_Init() failed; unable to locate a running instance of Steam, or a local steamclient.so.

You properly need steam for this.

Can anyone recommend a good steam install for Ubuntu?
I'm sure I can google around for one, install it, but don't want to find out after the fact it was a build that runs EVE either not at all or really slowly.

---

### Post by Perfect Storm on 2017-05-23
You can forget the error of steam, I just tried it. It's not it. Same things happen to me.

---

### Post by Perfect Storm on 2017-05-30
figured it out. You need to switch driver. As it says in the error report the open source is running you need to switch to nvidia propriaty driver. Search for addional driver in ubuntu.

---

### Post by Perfect Storm on 2017-05-31
To fix artificial black squares ingame, turn "post processing" off.

---

### Post by Perfect Storm on 2017-06-01
I'm in to this game, been played for hours.
You may want to create a launcher for the game. You can install **Libremenu** to add launcher to ubuntu.
Simply add this code into the added launcher should make a fine shortcut: **sh -c "cd ~/evelauncher && ./evelauncher.sh"**

And I made an icon (which fit the Pacifica icon theme):
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=275399&stc=1&d=1496339171[/IMG]

---

### Post by roesjka on 2017-08-09
Just for good orders sake. You don't need steam for EVEOnline. It is just a notification. I have been playing for years on Debian + Wine EVEOnline and since may/june 2016 with the evelauncher. Have look at my various posts on EVE Linux forums as they might help also on Ubuntu.
Cheers

---

