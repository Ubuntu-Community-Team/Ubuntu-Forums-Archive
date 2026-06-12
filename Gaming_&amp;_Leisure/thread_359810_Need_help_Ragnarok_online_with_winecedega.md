---
title: "Need help: Ragnarok online with wine/cedega"
date: 2007-02-12
forum: Gaming &amp; Leisure
---

### Post by n1ppon on 2007-02-12
I'm trying to get Ragnarok Online to run as playable.

I have made it run with Cedega but it only works like every fifth time i try. When I've got 17 fps when I'm playing and it takes one min, to load maps, which usually takes about 5 secs. Another problem with Cedega is that i cant erase anything i write ingame, for example username or password on the loginscreen or chatmessages.

When i try to run it Wine I receive an error message telling "LoadMapInfoTable Failed!".

Please help! Thanks

---

### Post by FenrisAbraxas on 2007-02-12
> **n1ppon said:**
> I'm trying to get Ragnarok Online to run as playable.

I have made it run with Cedega but it only works like every fifth time i try. When I've got 17 fps when I'm playing and it takes one min, to load maps, which usually takes about 5 secs. Another problem with Cedega is that i cant erase anything i write ingame, for example username or password on the loginscreen or chatmessages.

When i try to run it Wine I receive an error message telling "LoadMapInfoTable Failed!".

Please help! Thanks

RO is very well known for problematic under Linux sorry i think Cedega is not interested in making it better and Wine just lack some features of cedega, and i think vmware won't run it as well. 

I once played RO and kept me booting to windows a lot of time :S.

Heres the link with the playability in 0 :( [http://transgaming.org/gamesdb/games/view.mhtml?game_id=3532](http://transgaming.org/gamesdb/games/view.mhtml?game_id=3532)

---

### Post by kherim on 2007-02-21
> **n1ppon said:**
> I'm trying to get Ragnarok Online to run as playable.

I have made it run with Cedega but it only works like every fifth time i try. When I've got 17 fps when I'm playing and it takes one min, to load maps, which usually takes about 5 secs. Another problem with Cedega is that i cant erase anything i write ingame, for example username or password on the loginscreen or chatmessages.

When i try to run it Wine I receive an error message telling "LoadMapInfoTable Failed!".

Please help! Thanks

The same thing happen to me when I tried to run Ro in Cedega, but today i succed playing ragnarok in wine; but the last version (0.9.31) have some problems. 

So search the last version in [http://packages.ubuntu.com/](http://packages.ubuntu.com/) (i use edgy; so i downloaded wine-0.9.30)

Once installed, run in a terminal wincfg. If you want play in windowed mode go to the graphics and select Emulated Virtual Desktop. Then in a terminal (in ro folder); run wine setup.exe and select Full Window. I leave unmarked Fog and Lightmap.

Finally in a terminal (in ro folder): wine ragexe.exe

Now you should erase words and a better performance.

---

