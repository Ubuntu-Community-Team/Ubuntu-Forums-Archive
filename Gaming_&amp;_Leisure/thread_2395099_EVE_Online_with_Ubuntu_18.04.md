---
title: "EVE Online with Ubuntu 18.04"
date: 2018-06-26
forum: Gaming &amp; Leisure
---

### Post by chrisneedshelp on 2018-06-26
I have never tried to run EVE on any other distro of Ubuntu, only on windows.  

I installed the launcher etc using steps from [here]("https://ubuntuforums.org/showthread.php?t=2390973&highlight=EVE+online") and [here]("https://wiki.eveuniversity.org/Installing_EVE_on_Linux") and I get the following results...
```
chris@Desktop:~/evelauncher$ ./evelauncher.sh
[0626/144524:WARNING:resource_bundle.cc(291)] locale_file_path.empty() for locale 
Installed Qt WebEngine locales directory not found at location /home/chris/evelauncher/translations/qtwebengine_locales. Trying application directory...
Qt WebEngine locales directory not found at location /home/chris/evelauncher/qtwebengine_locales. Trying fallback directory... Translations MAY NOT not be correct.
[0626/144524:WARNING:resource_bundle.cc(291)] locale_file_path.empty() for locale 
[S_API FAIL] SteamAPI_Init() failed; SteamAPI_IsSteamRunning() failed.
[S_API FAIL] SteamAPI_Init() failed; unable to locate a running instance of Steam, or a local steamclient.so.
Segmentation fault (core dumped)
```
visually I can see the launcher open for a moment, then it crashes.

I really have no idea what I can do next, any suggestions?

TIA

---

### Post by thenailedone on 2018-06-26
> **chrisneedshelp said:**
> I have never tried to run EVE on any other distro of Ubuntu, only on windows.  

I installed the launcher etc using steps from [here]("https://ubuntuforums.org/showthread.php?t=2390973&highlight=EVE+online") and [here]("https://wiki.eveuniversity.org/Installing_EVE_on_Linux") and I get the following results...
```
chris@Desktop:~/evelauncher$ ./evelauncher.sh
[0626/144524:WARNING:resource_bundle.cc(291)] locale_file_path.empty() for locale 
Installed Qt WebEngine locales directory not found at location /home/chris/evelauncher/translations/qtwebengine_locales. Trying application directory...
Qt WebEngine locales directory not found at location /home/chris/evelauncher/qtwebengine_locales. Trying fallback directory... Translations MAY NOT not be correct.
[0626/144524:WARNING:resource_bundle.cc(291)] locale_file_path.empty() for locale 
[S_API FAIL] SteamAPI_Init() failed; SteamAPI_IsSteamRunning() failed.
[S_API FAIL] SteamAPI_Init() failed; unable to locate a running instance of Steam, or a local steamclient.so.
Segmentation fault (core dumped)
```
visually I can see the launcher open for a moment, then it crashes.

I really have no idea what I can do next, any suggestions?

TIA

Hmmm... the Steam warnings can be safely ignored as they always come up. The other warnings I am not sure (will have to run it when I am home again and see the output). Perhaps giving some more details of the hardware your running, any other versions of Wine you might have installed etc. could also help (I am aware of an issue with freetype fonts whereby all the new distro's are having 2.8 and the game needs 2.7, but this issue still lets you launch into the game before it crashes so it isn't it).

---

### Post by chrisneedshelp on 2018-06-26
woah, might be something there, my wine version is 3.0...

---

### Post by chrisneedshelp on 2018-06-26
okay, so after what you said I looked into my hardware and it turns out the 'upgraded' video card my buddy gave me was no upgrade at all, so I reinstalled my old one and had to redo all the drivers etc.  After doing that I could open the EVE launcher and it updated, but I cannot get it to launch the online portal.  It gets all the way to starting client and then sometimes the screen goes black and it seems to try and load it, but then that goes away and I'm back to the EVE launcher with 'play' available again.

---

### Post by chrisneedshelp on 2018-06-26
After a few more attempts and reboots it needed to download more info (7.25Gb) and after that it will start to launch and show the progress bar stating that it is logging in and authenticating, and then it quits, same place every time.  I am going to try and replace wine 3.0 with wine 2.7 based on previous feedback.

---

### Post by thenailedone on 2018-06-27
The thing is the file you download is a wine rapper developed by one of the devs of CCP who develop the game. I always have success when I don't have any other wine or wine using software installed. I am not sure why I also sometimes had issues when I install another version of wine. And info online is scarce :/

Oh and the versions numbers in my last post wasn't wine versions but libfreetype font versions... I just re-installed Ubuntu 18.04 and am currently installing EVE.. I want to see what happens if a) it works and b) what happens when I install wine etc...


edit:
For what it is worth here is my current output when I launch the game:

```
nailed@vector-sigma:~/evelauncher$ ./evelauncher.sh 
Gtk-Message: 16:10:58.761: Failed to load module "canberra-gtk-module"
[0627/161058:WARNING:resource_bundle.cc(291)] locale_file_path.empty() for locale 
Installed Qt WebEngine locales directory not found at location /home/nailed/evelauncher/translations/qtwebengine_locales. Trying application directory...
Qt WebEngine locales directory not found at location /home/nailed/evelauncher/qtwebengine_locales. Trying fallback directory... Translations MAY NOT not be correct.
[0627/161058:WARNING:resource_bundle.cc(291)] locale_file_path.empty() for locale 
[S_API FAIL] SteamAPI_Init() failed; SteamAPI_IsSteamRunning() failed.
[S_API FAIL] SteamAPI_Init() failed; unable to locate a running instance of Steam, or a local steamclient.so.

```

Oh and as I just installed Crossover linux my game crashes as soon as I move my mouse in game >.<

---

### Post by chrisneedshelp on 2018-06-29
I was able to get rid of the 'canberra-gtk-module' error by running

```
sudo apt install libcanberra-gtk-module libcanberra-gtk3-module
```

---

### Post by thenailedone on 2018-07-02
> **chrisneedshelp said:**
> I was able to get rid of the 'canberra-gtk-module' error by running

```
sudo apt install libcanberra-gtk-module libcanberra-gtk3-module
```

Good. Still doesn't help the game to run however. If you were able to get the launcher itself to work you could run a logging utility when you launched the game which sometimes yields answers... Very strange :(

On the up side (or is that downside), I have switched the Windows and all works as intended ](*,))

---

