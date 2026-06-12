---
title: "How to hear songs from Net(RealPlayer problem)"
date: 2006-03-08
forum: Desktop Environments
---

### Post by UltimaGuy on 2006-03-08
Hi Guys,

I have to hear songs from the internet from sites like [www.raaga.com](www.raaga.com) . For example, if I want to hear the following songs from this movie : <a href="raaga.com/channels/tamil/movie/T0000693.html>Click Here</a> then I will select whatever I want and then click "play selected" ... and in windows I generally hear the song after that ...

But in Ubuntu ... first I was getting an error saying that "RealPlayer was not installed" even after I installed Realplayer. Then I copied the mozilla plug-ins in Realplayer and pasted it into the plug-ins directory if firefox ... now I am not getting any error ... nor am I getting any songs ... can anyone please help !

Thanks ...

---

### Post by ronmarley1 on 2006-03-08
Hi,
This probably won't help, but I visited the site and clicked on "Play Slected" and I got a pop-up player that reads "Initializing player.  Please wait..."  It just has a blinking red dot in front of "Loading."  If I click the Play button, nothing happens. So, what is happening to you happens to me also.  Normally, I don't have problems with RealPlayer files.  Have you tried other sites with RealPlayer feeds?  Other sites I visit work fine.  You can use [http://service.real.com/test/](http://service.real.com/test/) to test RelPlayer.  Maybe there's a problem with raaga.com?

---

### Post by arnieboy on 2006-03-08
raaga.com needs some latest realplayer codecs which only come with the windows version. There is no way you can make it work on the ubuntu version of firefox. The only workaround is to install the windows version of firefox with wine and install the flash and realplayer plugins from within firefox. That will let u  listen to music on raaga.com. Here is what u need to do:
```
sudo gedit /etc/apt/sources.list
```
add the following line to the end:
> deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main
save and close.
```
sudo apt-get update
sudo apt-get install wine
```

after wine gets installed, run the following:
```
winecfg
```
choose the defaults and hit OK.
now download and install the latest version of firefox for windows here:
[http://www.mozilla.org/products/firefox/all](http://www.mozilla.org/products/firefox/all)
run the "exe" with "wine" and install firefox. now from firefox go to raaga.com and try to play a song. It will talk about missing plugins (flash and realplayer). Install them both and u will be all set. Please remember that after realplayer gets installed, it will crash at the splash screen when it tries to get launched.
at that moment do the following:
```
sudo killall wineserver
sudo killall wine-preloader
```
this will close all windows apps (though it wont hurt the realplayer installation) and then u can restart firefox and enjoy the music on raaga.com

Hope this helps.

---

### Post by UltimaGuy on 2006-05-03
Hi,

Sorry for the late reply :)

Your suggestion worked like a charm ... except for one small issue .. instead of selecting defaults in winecfg, we have to select ALSA in Audio. Everything else is working as expected ... many many thanks :)

---

### Post by dhruv_1884 on 2006-05-03
Thanks Dudes,
You guys solveda major problem for me.....

Regards
-
Dc

---

### Post by dhruv_1884 on 2006-05-03
Hey Arnie,

You Rock!!!!:KS 

Is there a similar way to play Widows media streams, i think the streams are .asx files.

sites like  [www.ibnlive.com](www.ibnlive.com) have such streams



Regards 
-
Dc

---

### Post by arnieboy on 2006-05-03
[QUOTE=dhruv_1884]Hey Arnie,

You Rock!!!!:KS 

Is there a similar way to play Widows media streams, i think the streams are .asx files.

sites like  [www.ibnlive.com](www.ibnlive.com) have such streams



Regards 
-
Dc[/QUOTE]
u should try using the native version of firefox on ubuntu with the mplayer plugin installed. windows media player 7 upwards is not well supported by wine.

---

### Post by dhruv_1884 on 2006-05-03
Arnie,

From where do i get the plugin......


New to linux
Is it in Synaptic



Regards

-

Dc

---

### Post by arnieboy on 2006-05-03
[QUOTE=dhruv_1884]Arnie,

From where do i get the plugin......


New to linux
Is it in Synaptic



Regards

-

Dc[/QUOTE]
try using [automatix]("http://ubuntuforums.org/showthread.php?t=138405")

---

### Post by dhruv_1884 on 2006-05-03
Arnie,
I installed the xpi from souce forge before i could read ur reply.

it didnt install and neither deoes it un install.

what do i do

i just realised that u created automatix.

u rock even more.

i tried automatix, it said all installations compolete, but i dont see any new extensions.

thanks dude..


regards
-
dc

---

### Post by arnieboy on 2006-05-03
[QUOTE=dhruv_1884]Arnie,
I installed the xpi from souce forge before i could read ur reply.

it didnt install and neither deoes it un install.

what do i do

i just realised that u created automatix.

u rock even more.

i tried automatix, it said all installations compolete, but i dont see any new extensions.

thanks dude..


regards
-
dc[/QUOTE]
mplayer plugin is a plugin, not an extension.. in firefox, type **about:plugins** to get a list of installed plugins.

---

### Post by dhruv_1884 on 2006-05-03
Arnie,

i dont think any Mplayer pluin gto installed.

I think i neer to change my profile of mozilla
i am attaching the screen shots of the insatlled plugins

---

### Post by arnieboy on 2006-05-03
if u are using firefox 1.0.x
try doing the following from terminal:
```
sudo apt-get install mozilla-mplayer
```
and then restart firefox and check your plugins page again

---

### Post by dhruv_1884 on 2006-05-03
HI ARNIE,

THANKS A TONNE!!!!!!!

iT'S WORKING

HOW DO I GET THE OTHER PLUGINS SHOWN IN AUTOMATIX FROM THE COMMAND LINE


tHANKS ALOT 


REGARDS

-
dC

---

### Post by arnieboy on 2006-05-03
if u have flash, java and mplayer plugins installed, u should be all set. make sure u have the w32codecs installed though for mplayer to play certain streams.

---

