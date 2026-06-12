---
title: "Deadly 30 black window"
date: 2013-01-15
forum: Gaming &amp; Leisure
---

### Post by pardalet on 2013-01-15
I've just purchase Deadly 30 at [IndieGala](http://store.indiegala.com/index.php/bundles/the-deadly-30-bundle-295.html) and it doesn't run on 12.10 64bit. When launched from the terminal all I get is a black window and the following messages:

```
$ ./Deadly_30 
Gtk-Message: Failed to load module "overlay-scrollbar"
`menu_proxy_module_load': ./Deadly_30: undefined symbol: menu_proxy_module_load

(Deadly_30:4413): Gtk-WARNING **: Failed to load type module: (null)

Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.1.15) Gecko/20101027 Ubuntu/9.10 (karmic) Firefox/3.5.3
Mozilla/5.0 (X11; U; Linux i686; en-GB; rv:1.9.1.15) Gecko/20101027 Ubuntu/9.10 (karmic) Firefox/3.5.3
onsize
DoResize
onsize
DoResize
onsize
DoResize
onsize
DoResize
onsize
DoResize
onpaint
SetWindowToInstance
socket id = 3a00040
plug_added_cb
```



It's not an unknown issue, as you can see in _[the game's comments](http://www.desura.com/games/deadly-30/page/2#comments)_ _[on Desura](http://www.desura.com/games/deadly-30/page/4#comments)_, but there's no solution posted there. Do you know any way to fix this and be able to play the game?


PS: I installed the ia32-libs package and I checked that I got the 32-bit versions of libgtk2.0-0, libnss3 and libxtst6, as is suggested _[on the Desura comments](http://www.desura.com/games/deadly-30/page/4#comments)_.

---

### Post by pardalet on 2013-01-16
**UPDATE**

I haven't make any real progress, but now I'm almost sure the problem has to do with Flash: since I installed the game, the Steam client isn't able to display any video correctly. When trying to view a video on Greenlight I get a text error message instead: *#text_need_flash_inclient*. And if I try to view a video on the store, I this other message:

```
You need to have a specific Flash Player installed to view video content
in Steam. Please follow [_these directions_](http://store.steampowered.com/gotflash) to get the right version for Steam.

You will need this Flash player even if you already have the latest player for
your default web browser.
```


Even though I have the adobe-flashplugin package installed, I followed this instructions (which by the way seem tailored for Windows users, as I didn't find any *Flash Player 11 for Other Browsers* option) but all I got was a tarball with the same libflashplayer.so that was already installed in my system. :(

The funny thing is that videos on the Steam client worked fine before I installed Deadly 30. Could the game have messed up my flash configuration in any way?

---

### Post by pardalet on 2013-01-20
Problem solved: I'm finally able to play the game (albeit only in windowed mode, I don't know how to play at fullscreen).

After a lot of trial and error I THINK that the problem was Adobe Air, which conflicted with the (outdated) Adobe Flash Player plugin embedded in the game. Uninstalling it finally got the game running.

[s]The donwside is that now my Desura client has ceased to function properly. Oh dear... :([/s]

---

