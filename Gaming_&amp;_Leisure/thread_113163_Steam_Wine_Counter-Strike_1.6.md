---
title: "Steam Wine Counter-Strike 1.6"
date: 2006-01-05
forum: Gaming &amp; Leisure
---

### Post by zappa86 on 2006-01-05
I just installed wine .95 from .94 and steam does not crash and I am happy. However I will join a CS server and play (fine, no sound lag and graphics are respectable) for about 30 seconds then it will freeze up the computer. The keyboard and mouse dont respond becasue the input is locked or something so I had to ssh into my computer from another and kill -9 wine-preloader. And Ive tried to play cs by myself and on many servers and each time it plays for 30 secs and then freezes. Its quite annonying becasue it does work fine and just randomly into the game. Any advise would be helpful? thanks.

---

### Post by fealz on 2006-01-06
Did you have the login problem beforehand?  If you did, how did you fix it?  If I can actually get into my account, maybe I would have the same problem and could search for a fix.  Thanks

---

### Post by FizDev on 2006-01-06
I don't know, it does the same thing to me... =( 
And I didn't have the login problem beforehand.

---

### Post by zappa86 on 2006-01-06
To get where I got I used the tutorials from:
[http://cslinux.hacka.net/](http://cslinux.hacka.net/)
[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=17](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=17)
and most of inportantly: (scroll down on this one)
[http://appdb.winehq.org/appview.php?versionId=1554&iTestingId=753](http://appdb.winehq.org/appview.php?versionId=1554&iTestingId=753)

What do you mean by login problem? if you cant see any text its because you dont have the tahoma font installed.

But does anyone know why it works fine for 30 secs then stops.

---

### Post by fealz on 2006-01-06
[QUOTE=zappa86]To get where I got I used the tutorials from:
[http://cslinux.hacka.net/](http://cslinux.hacka.net/)
[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=17](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=17)
and most of inportantly: (scroll down on this one)
[http://appdb.winehq.org/appview.php?versionId=1554&iTestingId=753](http://appdb.winehq.org/appview.php?versionId=1554&iTestingId=753)

What do you mean by login problem? if you cant see any text its because you dont have the tahoma font installed.

But does anyone know why it works fine for 30 secs then stops.[/QUOTE]


i fixed my login problem by using an emulated desktop in wine.  The problem I was referring to was not being able to type my login and pw, but I got that working now.  However, when I load steam now, it freezes as soon as it logs in.  I'm going to check out the links you posted and hope one of them helps it.  Either way, I'll post again, and if I have the same problem as you, i'll post whatever I do if I get it working.  good luck.

---

### Post by zappa86 on 2006-01-06
What does your console say when it feezes? Mine said something about msvcr70.dll so I copied it into my fake drive_c/windows/system folder and it works. Steam wont ever freeze for me ( I let it sit for an hour to test it) nor will cs1.6 when its open. However as soon as i go to play it it feezes after 30 secs. The tutorial at linux-gamers.net said that it needed that dll.

---

### Post by fealz on 2006-01-06
After checking out those sites, those are the same ones I used to install steam.

Here's my problem now..
I load steam and it connects, I get the license agreement because I'm using a cybercafe account and it freezes.. here's what's in the terminal:

fealz@Fealz-lappy:~/win32/Steam$ wine Steam
fixme:vxd:VXD_Open Unknown/unsupported VxD L"gdperf.vxd". Try setting Windows version to 'nt40' or 'win31'.
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
fixme:ole:CoCreateInstance no classfactory created for CLSID {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80040154
fixme:nls:MultiByteToWideChar MB_USEGLYPHCHARS not supported
fixme:nls:MultiByteToWideChar MB_USEGLYPHCHARS not supported
fixme:nls:MultiByteToWideChar MB_USEGLYPHCHARS not supported
fixme:process:SetProcessWorkingSetSize (0xffffffff,-1,-1): stub - harmless
err:ntdll:RtlpWaitForCriticalSection section 0x7befc524 "loader.c: loader_section" wait timed out in thread 0020, blocked by 0000, retrying (60 sec)

I have no idea what that means... anyone help?

---

### Post by fealz on 2006-01-06
[QUOTE=zappa86]What does your console say when it feezes? Mine said something about msvcr70.dll so I copied it into my fake drive_c/windows/system folder and it works. Steam wont ever freeze for me ( I let it sit for an hour to test it) nor will cs1.6 when its open. However as soon as i go to play it it feezes after 30 secs. The tutorial at linux-gamers.net said that it needed that dll.[/QUOTE]


so yours is working now?  the dll fixed it?

---

### Post by zappa86 on 2006-01-06
I got mine to the point where I can play CS in a network game online for about 30 secs, then it will freeze.

---

### Post by Mr_Grieves on 2006-01-07
About freezes in Steam and in games, I've opened up Bug ID 4139 at WineHQ.
[http://bugs.winehq.org/show_bug.cgi?id=4131](http://bugs.winehq.org/show_bug.cgi?id=4131)

---

### Post by fealz on 2006-01-07
ok, so here's my update...

I got rid of  the following error by telling wine to emulate WindowsXP when it runs steam instead of auto-configuring:

> fixme:vxd:VXD_Open Unknown/unsupported VxD L"gdperf.vxd". Try setting Windows version to 'nt40' or 'win31'.

However, I'm still lost about the rest...  These are registry errors I assume, but I don't know what to do about them...

> err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
fixme:ole:CoCreateInstance no classfactory created for CLSID {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80040154


I have no idea what these errors are:
> fixme:nls:MultiByteToWideChar MB_USEGLYPHCHARS not supported
fixme:nls:MultiByteToWideChar MB_USEGLYPHCHARS not supported
fixme:nls:MultiByteToWideChar MB_USEGLYPHCHARS not supported


Then I'm not sure if these are memory errors or problems my computer has with the steam server:
> 
err:ntdll:RtlpWaitForCriticalSection section 0x7befc524 "loader.c: loader_section" wait timed out in thread 0022, blocked by 0020, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7befc524 "loader.c: loader_section" wait timed out in thread 002c, blocked by 0000, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7d08f9d4 "?" wait timed out in thread 001e, blocked by 0000, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7d08f9d4 "?" wait timed out in thread 001e, blocked by 0000, retrying (60 sec)

One thing I've noticed though is that when I run Steam in wine, wine preloader and wine server combined use up 85-100% of my CPU.   At this point, I don't know what to do.  It seems to run for a second or two longer if I change my sound settings to OSS or off.  I think my computer has a problem with ALSA, and I think i've seen other people say the same thing.  Anyone have any advice?  Anything I can try?  Also, zappa, have you tried running Steam in offline mode?  I saw some people say that fixes some problems.. I'm about to try that, but since I dont have any games installed yet, even if it works, it won't be a very good test..

This is the full terminal when I run Steam...

> fealz@Fealz-lappy:~/win32/Steam$ wine Steam
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
fixme:ole:CoCreateInstance no classfactory created for CLSID {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80040154
fixme:nls:MultiByteToWideChar MB_USEGLYPHCHARS not supported
fixme:nls:MultiByteToWideChar MB_USEGLYPHCHARS not supported
fixme:nls:MultiByteToWideChar MB_USEGLYPHCHARS not supported
fixme:process:SetProcessWorkingSetSize (0xffffffff,-1,-1): stub - harmless
err:ntdll:RtlpWaitForCriticalSection section 0x7befc524 "loader.c: loader_section" wait timed out in thread 0022, blocked by 0020, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7befc524 "loader.c: loader_section" wait timed out in thread 002c, blocked by 0000, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7d08f9d4 "?" wait timed out in thread 001e, blocked by 0000, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7d08f9d4 "?" wait timed out in thread 001e, blocked by 0000, retrying (60 sec)


---

### Post by fealz on 2006-01-07
I just tried, and steam wouldn't even load in offline mode.. it still gave me the error about not being able to connect, even though I didn't want it to anyway... sigh...

---

### Post by dfreer on 2006-01-15
Hello all,
   Semi-n00b with linux. My problem is that everywhere I read about how to install counter-strike, they say i need this tahoma.tff font installed to my x11 font directory (specifically, one site says /usr/X11/lib/X11/fonts/truetype). Problem is, I don't have the specified directory (should I just make it? somehow i don't think that will work)... I asume it exists under another name (BTW, I am running Ubuntu 5.10 "Breezy"). I have tried google, but alas my google m4d skillz are lacking, because I cannot seem to find where I should put this .ttf file. 
    Also, I have tried finding a package containing this font viz synaptic :( Nothing doing.

---

### Post by fealz on 2006-01-15
[QUOTE=dfreer]Hello all,
   Semi-n00b with linux. My problem is that everywhere I read about how to install counter-strike, they say i need this tahoma.tff font installed to my x11 font directory (specifically, one site says /usr/X11/lib/X11/fonts/truetype). Problem is, I don't have the specified directory (should I just make it? somehow i don't think that will work)... I asume it exists under another name (BTW, I am running Ubuntu 5.10 "Breezy"). I have tried google, but alas my google m4d skillz are lacking, because I cannot seem to find where I should put this .ttf file. 
    Also, I have tried finding a package containing this font viz synaptic :( Nothing doing.[/QUOTE]


this is one of the few things I can help you with.  Instead of using that font, open .wine/system.reg in text editor.   If you don't know where that is, it's in your user directory, but it's hidden, so open nautilus, the filesystem navigator, and go to home -> <your user name> -> .wine

It should be in there.  However, to view hidden files, you need to press control + h.  Then it will show up.

So, navigate to that directory and open system.reg.  Find the key "[Software\Microsoft\Windows NT\CurrentVersion\FontSubstitutes]"  There may be more after that.  I have numbers after that key, but i'm not sure what they mean.

under that key, add "Tahoma"="Bitstream Vera Sans" including all quotes.  That should work.  So, instead of valve looking for the tahoma font, it'll substitute it with the bitstream vera sans font, which is very similar, and is already installed in Ubuntu breezy or wine or something.  I'm not sure exactly, but I know it works, so try it out and let us know what happens.  :)

---

### Post by claydoh on 2006-01-15
Does this happen on *all* servers you connect to?
I have a very similar problem, but only on one server (half-Life 1) I try to connect to. I don't get a freeze, steam and the game simply crash after about 30 seconds, though occaisionally it just disconnects from the server. This was happening with both cedega and wine 0.93. Ithought it was a NAT router issue at first, but I seemed to have no trouble with different random servers.

---

### Post by Mr_Grieves on 2006-01-15
[QUOTE=dfreer]Hello all,
   Semi-n00b with linux. My problem is that everywhere I read about how to install counter-strike, they say i need this tahoma.tff font installed to my x11 font directory (specifically, one site says /usr/X11/lib/X11/fonts/truetype). Problem is, I don't have the specified directory (should I just make it? somehow i don't think that will work)... I asume it exists under another name (BTW, I am running Ubuntu 5.10 "Breezy"). I have tried google, but alas my google m4d skillz are lacking, because I cannot seem to find where I should put this .ttf file. 
    Also, I have tried finding a package containing this font viz synaptic :( Nothing doing.[/QUOTE]
1) Download tahoma.tff to <folder-X>. Ask a friend with Windows to send it to you. I'm sure you can figure something out.
2) Type in a terminal:
```

cd /path/to/<folder-X>
cp tahoma.tff ~/.wine/drive_c/windows/fonts/

```

---

