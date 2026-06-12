---
title: "Wine + Steam = HELP!"
date: 2005-11-24
forum: Gaming &amp; Leisure
---

### Post by PrincessPeach on 2005-11-24
I followed [this guide from linux-gamers]("http://www.linux-gamers.net/modules/wfsection/article.php?articleid=17") to install wine and steam and I got steam working, kind of.  I still have 2 separate issues that maybe someone can help me on.

I'm using gnome on Ubuntu 5.10 i386, nvidia gf6800.

First, when I load up steam using "wine steam.exe" it logs in fine, but then the steam menu just sits on top of my screen.  If I start a game (DoD), it'll still be on top of my game. There's no way to minimize it because if I press the minimize button, it'll flicker and bring me back to the desktop with DoD running in the background. At that point, I can't get to DoD, but I can still hear the audio from it. The system tray from wine is also a little screwy; it sits on my desktop, but in a super small box so that I can't see any icons in it and there's no way to resize it.

Second, I've installed the nvidia drivers but DoD is still pretty choppy.  It ran fine back in windows, and even with the settings turned a little lower, there's noticable fps drops and the lighting seems kind of off.

Any advice in getting wine+steam to be better friends, or should I just give in to Cedega?

---

### Post by stoffe on 2005-11-24
I'm switching over to XFCE to play steam games, the steam icon works like it should there, unlike in Gnome - the Wine guys says it's a Gnome bug but I don't know. Just install xubuntu-desktop and you'll have the session available on the login screen.

It's probably lighter on the resources too, so it might help with performance. I also disable debugging and set a heapsize, like so:
```
WINEDEBUG="-all" wine Steam.exe -applaunch 10 -heapsize 300000 &
```(-applaunch 10 means go directly to CS). Heapsize should be about half your RAM, if I understood instructions properly.

Still, it runs a bit slower than on Windows, but I can play just fine on a not too new machine. Oh, and I run the latest wine from the winehq repositories, that might also help.

---

### Post by PrincessPeach on 2005-11-24
Thanks, great suggestion on xfce. Steam works like a charm now.  However, I'm still getting wierd jittering when I try to play a game. I went to the video settings and it's set on hardware directx 8 and I can't switch it to 9. Might that be a problem?

---

### Post by stoffe on 2005-11-24
Which wine version?

---

### Post by PrincessPeach on 2005-11-24
Wine 0.9.1

---

### Post by stoffe on 2005-11-24
Then I don't know... Is it possible to run in OpenGL mode instead? If so, how does it behave then?

---

### Post by PrincessPeach on 2005-11-25
There's no option in steam to run in OpenGL or not, unless you're talking about something else?

---

### Post by stoffe on 2005-11-25
No, I meant options inside the game. As I read it, the problems were not out in Steam, but when running the game.

---

### Post by byoon on 2005-11-25
Just wondering what kind of fps everyone is getting by running Steam games with Wine 9.1.

I just bought a 6600gt and want to know what kind of performance I can expect.

---

### Post by PrincessPeach on 2005-11-25
[QUOTE=byoon]Just wondering what kind of fps everyone is getting by running Steam games with Wine 9.1.

I just bought a 6600gt and want to know what kind of performance I can expect.[/QUOTE]

I'm getting about 15-20fps in open spaces and ~30 inside buildings with a 6800.

---

### Post by byoon on 2005-11-30
My fps is still ~1 even with my new 6600 GT.

Running Wine 0.9.1 with Counter Strike Source, everything works fine except I get approximately 1 fps in the stress test and in an actual game.

Any help on how to speed things up would be appreciated.

I am running it with the command:

wine Steam.exe -fullscreen -width 1024 -height 768 -applaunch 240 -heapsize 512000 &

These are my system specs:

AMD XP 2000
1 GB RAM
PNY 128 MB GeForce 6600 GT
Ubuntu Breezy
Wine 0.9.1
glxgears gets approximately 6700 fps (I know this is not a benchmark)

---

### Post by Gray. on 2005-12-01
I have a problem with Steam and Wine. I have installed it but after it finishes updating (or checking for updates whatever), it comes up with this error.

[[IMG]http://img207.imageshack.us/img207/6608/screenshot1jb.th.png[/IMG]](http://img207.imageshack.us/my.php?image=screenshot1jb.png)

Any help appreciated.

---

### Post by vtechstu on 2005-12-05
Is this the correct output after running wine regsvr32 mozctlx.dll?  I can't get this to work!! Even after following the guide about 10 times.  wine 9.2.

```
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
Successfully registered DLL mozctlx.dll
```

Also, Here is a Screen shot of where I keep getting stuck at... I'm almost giving up!  Please help.
Image is too big to view in the thread, so just see it [here]("http://filebox.vt.edu/users/pollock/Screenshot.png")

---

### Post by Gray. on 2005-12-08
Well I finally got CS installed.

vtechstu:
What I did was created a CS.bash file and inside it put:
```
cd /home/<username>/.wine/drive_c/Program\ Files/Steam && wine Steam.exe -applaunch 10
``` making sure you put the appropriate <username>.
then:
```
chmod +x CS.bash && sudo mv CS.bash /usr/bin
```
That way all I have to do is type in terminal:
```
CS.bash
``` and it auto-loads CS.

Heres a pic of me in CS:

---

### Post by vtechstu on 2005-12-09
Thanks for the tip.

I tried your suggestion, and it started Steam.  Got to the log in, and i typed in the password, then it said, could not find storefront.steampowered.com could not be found.

output from Terminal:

err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for for context 0x1
fixme:ole:CoCreateInstance no classfactory created for CLSID {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80040154
fixme:winsock:convert_af_w2u unhandled Windows address family 0
fixme:winsock:convert_proto_w2u unhandled Windows socket protocol 0
fixme:winsock:convert_af_w2u unhandled Windows address family 0
fixme:winsock:convert_proto_w2u unhandled Windows socket protocol 0

---

### Post by Gray. on 2005-12-10
Yeah that happened to me as well and I just clicked OK or No or something like that. It went away after the second day. It doesn't affect the game in anyway as far as I can tell.

ALSO: I read that once you know that the app is running fine under Wine, you can add the WINEDEBUG="-all" to the script before wine so it should now look like this:
```
cd /home/<username>/.wine/drive_c/Program\ Files/Steam && WINEDEBUG="-all" wine Steam.exe -applaunch 10
```
It should give a performance boost.

---

