---
title: "Installed Picasa - can I use its WINE version now?"
date: 2006-06-05
forum: Desktop Environments
---

### Post by megamania on 2006-06-05
I recently installed Picasa, which I'm quite impressed with.

Now I'm considering trying to install IrfanView under wine, because I need to batch-convert hundreds of pictures saved in PSD format which I can't open with Gimp (and I can't do that manually anyway because they're too many).
I was wondering if I can use the Wine that was installed with Picasa (and if so, how?), or if I have to install the stand-alone version of Wine anyway.

Any advice on this would be very appreciated, since it's going to be my first attempt to run windows programs under linux.

---

### Post by eeclark on 2006-06-05
I would just try typing wine at the command line.
if it recognizes the command then try to run an app by typing wine appname

I believe wine is in /opt/picasa/wine/bin/wine.

So if at the cmd line you cannot just wine to get it to work, try typing the whole path above.

---

### Post by megamania on 2006-06-05
[QUOTE=eeclark]if it recognizes the command then try to run an app by typing wine appname

I believe wine is in /opt/picasa/wine/bin/wine.

So if at the cmd line you cannot just wine to get it to work, try typing the whole path above.[/QUOTE]
Typing "wine" at the command line, won't work, but here's what I get if I enter /opt/picasa/wine/bin/wine:

```

gianfranco@desktop:~$ /opt/picasa/wine/bin/wine
wine: creating configuration directory '/home/gianfranco/.wine'...
/opt/picasa/wine/bin/../lib/../bin/wineprefixcreate: line 205: wine: command not found
wine: wineprefixcreate failed while creating '/home/gianfranco/.wine'.
```
On the other hand, if I enter "wine" from the appropriate directory, here's what I get:
```
gianfranco@desktop:~$ cd /opt/picasa/wine/bin/
gianfranco@desktop:/opt/picasa/wine/bin$ wine
bash: wine: command not found
gianfranco@desktop:/opt/picasa/wine/bin$
```
I'm wondering if there's something obvious that I'm missing (very likely), or if I should just install the official Wine on its own.
Also, I downloaded the "googled" wine (picasa-wine-2.2.2820-5_.0-1_i386). Should I install that?

Thanks a lot for the help so far.

---

### Post by Choad on 2006-06-05
cd to the correct dir and try 

```
./wine
```

---

### Post by lean on 2006-06-05
Why would you like to use the google wine instead of the standard wine?

It has more patches, but is also specialised only to run Picasa. Also everything that google has done, is ending up in the official wine at some point in the future.

It has never been the intend of google to install their own wine for all apps to use. If they had, you could propably do an sudo update-alternatives --config wine, and choose to use Picassa's wine as default.

So just install the normal wine, it should work just as fine.

Also, you have to specify the path to run a file.
So 
cd somedir
wine
does not work, but
cd somedir
./wine does

---

### Post by megamania on 2006-06-05
[QUOTE=lean]Why would you like to use the google wine instead of the standard wine?[/QUOTE]
The only reason was to avoid wasting disk space with a double install of wine, also because at the moment I just need it to run IrfanView for a few days.

But I see it's probably easier (and more logic, especially for the updates) to install the official wine on its own. Thanks for the suggestions!

---

### Post by andy_cowman on 2006-06-05
I dont think official Wine takes up much space, the google version in picasa makes up about 9mb of the install of something. 

I would just install the normal wine  version for Irfanview and keep picasa seperate. Let me know how you get on with IrFranview in linux. I used to use it in windows and it was a good program. 

Thanks

Andy

---

### Post by megamania on 2006-06-05
[QUOTE=andy_cowman]I would just install the normal wine  version for Irfanview and keep picasa seperate. Let me know how you get on with IrFranview in linux. I used to use it in windows and it was a good program. [/QUOTE]
As I said above, I need to convert to TIF hundreds of pictures saved in PSD (photoshop) format which I can't open with Gimp (don't know why).
I thought about using IrfanView because I think I read somewhere that it works in wine, and I remember it handles batch jobs.

As soon as I try it, I'll let you know how things work out.

---

