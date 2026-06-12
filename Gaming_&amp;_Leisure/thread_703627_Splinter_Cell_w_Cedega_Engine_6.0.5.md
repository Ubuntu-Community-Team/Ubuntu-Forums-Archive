---
title: "Splinter Cell w/ Cedega Engine 6.0.5"
date: 2008-02-21
forum: Gaming &amp; Leisure
---

### Post by jbaerbock on 2008-02-21
Well I'm trying to play Splinter Cell (The Original Game) via Cedega w/ engine version 6.0.5. The game runs, sound works, but after it goes through the video for a mission etc... and says press fire to continue it messes up. When I click button one on the mouse for fire it goes to a Cedega Error screen that says:

     Critical Error:
           General Protection Fault!

           History:


And that is all it says. Any ideas on what the problem is here (yes it is a legitimate copy, got it from Walmart)? Got my saved game filed from a previous playtime too but never finished the game so wanna get it working in Linux so as to finish it. Any help would be appreciated.

---

### Post by Eddie Wilson on 2008-02-21
There are several of my games that would run with wine and not Cedega. You might try the Cedega web site and see if they can help or you may try wine. Sorry I can't be any help.

Eddie

---

### Post by jbaerbock on 2008-02-21
Ok will do, figured I would give people a chance to answer before i messed with Wine again though.

---

### Post by jbaerbock on 2008-02-21
Bump

---

### Post by jbaerbock on 2008-03-17
Ok I am dualbooting now and tried running splinter cell install on my windows partition via wine whilst in Linux. Works fine including sound, only problem is when in the playable parts of the game the graphics are all wierded up. Any ideas why this may be?

---

### Post by stuart.crouch on 2008-03-18
Not with that vague info.

Did you check the App DB?
Is there a screenshot to explain "weirded up"?
Does the wine wine log say anything useful?
no PC specs? Your not doing something silly like trying to run this on an Intel 955 GPU or something are you?

I dont claim I can help - but no one can help unless you give some more explanation of whats going wrong!

Also there is no guarantee that splinter cell will work on linux

---

### Post by jbaerbock on 2008-03-18
App DB in winehq has no usefull info on the problem. I'll try and post a screenie later. Wine log says nothing usefull but I'll copy and paste it in later when I do screenie. And I have an HP zv6000 1,256 ram and 2ghz AMD64 (running 32-bit). Have ATI 200M dedicated 128mb graphics card which has latest drivers automatically installed via latest Envy (not repo Envy).

---

### Post by jbaerbock on 2008-03-18
....

---

### Post by stuart.crouch on 2008-03-19
When I looked AppDB had loads of useful info!

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9083&iTestingId=15369](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9083&iTestingId=15369)

> 
What works
The installer for splinter cell 1.0 works and the 1.2b update which can be downloaded from Ubi soft.com.The game works well and is fully playable,only a few issues are present.


What does not
Some textures appear buggy as if light was shining on them even though they will be in the shadows.Resolutions above 640x480 does not work and causes the game to mess up in a window when you load it.One level was very slow and was not playable.


What was not tested
Nothing....I loaded every one of the levels at least once.


Additional Comments
In order to get the game to work correctly,you have to edit the registry to:[HKEY_CURRENT_USER\Software\Wine\Direct3D] "OffscreenRenderingMode"="fbo" "VideoMemorySize"="256" 


From that -

Have you patched to v1.2b? 
Have you edited both registry keys?
Are you staying at 640x480 resolution?
Have you played other (native games) to ensure your gfx card works (like warsow)

---

