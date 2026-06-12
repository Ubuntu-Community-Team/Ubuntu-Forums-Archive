---
title: "EVE Online in (K)ubuntu 18.04"
date: 2018-05-04
forum: Gaming &amp; Leisure
---

### Post by thenailedone on 2018-05-04
Greetings all,

So here is a quick guide on getting EVE Online to work in (K)ubuntu 18.04 (and as the game is free-to-play I would say give it a go :KS)

The main tutorial on which this one is based can be found at: [https://wiki.eveuniversity.org/Installing_EVE_on_Linux]("https://wiki.eveuniversity.org/Installing_EVE_on_Linux")

So we will follow the first 4 steps of the basic setup found in the link above:
```
wget https://binaries.eveonline.com/evelauncher-1104891.tar.gz (Sure there is newer versions but I know this one works and it will auto-update to the latest ;))
tar -xvf evelauncher-1104891.tar.gz
cd evelauncher
chmod u+x evelauncher.sh

```


Now run the following two command within the directory which you extracted that has the evelauncher.sh script if your on Kubuntu 18.04 (**if on another version find where on your system libssl.so.1.0.0 and libcrypto.so.1.0.0 is stored and substitute that location into the code below!!**):
```
ln -s /usr/lib/x86_64-linux-gnu/libssl.so.1.0.0 libssl.so
ln -s /usr/lib/x86_64-linux-gnu/libcrypto.so.1.0.0 libcrypto.so
```
now run ```
./evelauncher.sh
```
It should launch and update to the latest version.

After it quits / crashes re-run the two commands making the links to libssl.so and libcrypo above (you will need to do that every time your launcher updates, check the link to eveuniversity above for a solution to that)

Now run ```
sudo apt install libldap-2.4-2:i386 (not sure what this is and does but it is needed)
sudo apt install libpulse0:i386 (for sound)
```

Lastly run
```
./evelauncher.sh (to install the game. Now log in and hit the play button)
``` 

Fly safe!


PS - If you use the code - [http://secure.eveonline.com/signup/?invc=e93581b9-9053-4cc4-96a6-63a38105808b&action=buddy]("http://secure.eveonline.com/signup/?invc=e93581b9-9053-4cc4-96a6-63a38105808b&action=buddy") you can get a nice boost on your initial training.

---

### Post by oldrocker99 on 2018-05-04
Very nice! I've never played it, but now I may.

---

### Post by thenailedone on 2018-05-06
> **oldrocker99 said:**
> Very nice! I've never played it, but now I may.

Get in!

---

### Post by mastablasta on 2018-05-09
since when is eve online free to play? there was a subscription fee before.

---

### Post by thenailedone on 2018-05-09
> **mastablasta said:**
> since when is eve online free to play? there was a subscription fee before.

For several months now you can play for free and have alpha status (access to the full game but with some limitations on how many ships you can pilot... but there is still to many). If you enjoy it enough and would like to fly the additional ships then you can swith your account to Omega (subscription). And from what I can tell if you later decide not opt out of the subscription you go back to Omega status and vice-versa.

So there is really no reason not to try it :KS

---

### Post by oldrocker99 on 2018-05-09
Hmmm. This is what I got after I tried the second launcher run:

```
[0509/145201:WARNING:resource_bundle.cc(291)] locale_file_path.empty() for locale 
Installed Qt WebEngine locales directory not found at location /home/oldrocker99/evelauncher/translations/qtwebengine_locales. Trying application directory...
Qt WebEngine locales directory not found at location /home/oldrocker99/evelauncher/qtwebengine_locales. Trying fallback directory... Translations MAY NOT not be correct.
[0509/145201:WARNING:resource_bundle.cc(291)] locale_file_path.empty() for locale 
[S_API FAIL] SteamAPI_Init() failed; no appID found.
Either launch the game from Steam, or put the file steam_appid.txt containing the correct appID in your game folder.
^C
oldrocker99@70Maple:~/evelauncher$ ./evelauncher.sh
```
[nothing happened, so CTRL-C]

 What's the deal with Steam?

---

### Post by thenailedone on 2018-05-09
> **oldrocker99 said:**
> Hmmm. This is what I got after I tried the second launcher run:

```
[0509/145201:WARNING:resource_bundle.cc(291)] locale_file_path.empty() for locale 
Installed Qt WebEngine locales directory not found at location /home/oldrocker99/evelauncher/translations/qtwebengine_locales. Trying application directory...
Qt WebEngine locales directory not found at location /home/oldrocker99/evelauncher/qtwebengine_locales. Trying fallback directory... Translations MAY NOT not be correct.
[0509/145201:WARNING:resource_bundle.cc(291)] locale_file_path.empty() for locale 
[S_API FAIL] SteamAPI_Init() failed; no appID found.
Either launch the game from Steam, or put the file steam_appid.txt containing the correct appID in your game folder.
^C
oldrocker99@70Maple:~/evelauncher$ ./evelauncher.sh
```
[nothing happened, so CTRL-C]

 What's the deal with Steam?

The game is available in Steam but it isn't required (ignore those errors)

If you are not running Kubuntu 18.04 the location of the libssl and libcrypto files may differ (I made an edit to the OP, thought I had done so already!). In Ubuntu 18.04 it is somewhere related to snap applications. I typically use catfish to find them. Simply change the step to make links to point to the correct files and you should be good to go!

edit: Oh and after every update to the launcher you have to remake the links as they get overwritten!

---

### Post by ra93 on 2018-05-11
I think EVE Online in long-term goes free 2 play so it worth to play it now. Great possibility for [buy eve ]("https://www.sellersandfriends.com/eve-online/tranquility/isk")[isk]("https://www.sellersandfriends.com/eve-online/tranquility/isk") and huge knowledge need to be pro makes this game very difficult. Only for smart people.

---

### Post by thenailedone on 2018-05-22
Bump to thread as I made an edit to the files needed for sound. Also would love to give any Linux users that want to try the game a boost with my buddy link - [http://secure.eveonline.com/signup/?invc=e93581b9-9053-4cc4-96a6-63a38105808b&action=buddy]("http://secure.eveonline.com/signup/?invc=e93581b9-9053-4cc4-96a6-63a38105808b&action=buddy"). Sign up with it and get a nice boost on training.

---

### Post by zewirus on 2018-06-28
Hi everyone! I have a so strange issue, after choosing a character, when world already loaded, if I click on any camera space (except for the side menu) client crashes with a message(taken from game-log) "X Error of failed request:  BadWindow (invalid Window parameter)"
Any ideas?

---

### Post by arieleoar on 2018-07-12
> **zewirus said:**
> Hi everyone! I have a so strange issue, after choosing a character, when world already loaded, if I click on any camera space (except for the side menu) client crashes with a message(taken from game-log) "X Error of failed request:  BadWindow (invalid Window parameter)"
Any ideas?

Hi zewirus! that can be solved easily changing the version of wine used by the launcher;
Go to options menu in launcher - then settings - then activate "use dev versions" checkbox - then switch the options in the dev branch list, for example i'm using the "winehq-master" version because the one bundled with the launcher never opens a window and throws the exact same error as you.

Regards and enjoy!

---

