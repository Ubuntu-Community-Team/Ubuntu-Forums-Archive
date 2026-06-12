---
title: "Call of Duty??"
date: 2006-07-19
forum: Gaming &amp; Leisure
---

### Post by Blacktalon on 2006-07-19
Hello,

I have a Call of Duty windows CD, and i was wondering if there is a way to get it onto my linux computer?

Any assistance is appreciated

---

### Post by der_joachim on 2006-07-19
You can download the CoD client from [Loki Games]("http://liflg.org"). Just follow the instructions and you should be fine. With the correct drivers installed, it runs somewhat better than the Windows version.

---

### Post by skirkpatrick on 2006-07-19
I ran CoD under Wine using the Loki installer.  Slightly better FPS and I didn't have that annoying PunkBuster lag when I first get into a server.

CoD2, on the other hand, doesn't work.

---

### Post by crane on 2006-07-20
Yea CoD and CoD|UO both worked great for me. I have not tried CoD2 though.

---

### Post by jediborger on 2006-09-04
Hey I have Call of Duty 1 and I've tried both the native installer and the loki installer and keep getting the same errors. Con you guys tell me what exactly you're running, verison of Ubuntu, and wine version and possibly what other programs do you have installed like winetools and stuff.

---

### Post by crane on 2006-09-05
I have not tried to play CoD in a while. At least not in  Dapper. What errors are you getting? Did you get it installed?

---

### Post by jediborger on 2006-09-07
Here's what I get:

ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1734c0) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x16e740)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:keyboard:RegisterHotKey ((nil),0,0x00000001,9): stub
fixme:keyboard:UnregisterHotKey ((nil),0): stub

I think it's a problem with the detection of my video card, when I reinstalled it again I got a message saying my hardware might not be good enough. I know it is though and I'm able to run Battlefront under wine as well as all these games under windows with the same hardware. So any suggestions?

---

### Post by jediborger on 2006-09-07
Note: the smiley's are not supposed to be there, I guess the error syntax matches the smily syntax.

---

### Post by Josh_b on 2006-09-07
is Call Of Duty native or do you need wine/cedega/whatever to play it?

---

### Post by jediborger on 2006-09-07
You need wine/cedega to play to play the game. 

Just a note Cedega is just the current wine preconfigured with the fixes/hacks that you need to get some games working. I wish some people would just say waht you need to do to get things working, but on the other hand that wouldn't make them any money.;)

---

### Post by crane on 2006-09-07
I am running Dapper, but the Game was installed in Breezy or earlier. I noticed the 1st error is for sound.
 What sound card and vid card are you using?
 Also if you keep getting errors try checking you wine settings or even try a previos version of wine.

---

### Post by dawg on 2006-09-08
just installed on my laptop, you do need cedega to run it.  if you're using cod1.5, you must use it, i remember about 10 months or so ago, i installed it, and it ran off of wine, thats not the case this time.  let me install cedega, and i'll get back to you

---

### Post by dawg on 2006-09-08
sorry it took me so long to reply, was too busy looking at pictures of kate, katesplayground girl.  hottie with a hoof, anyways, cod runs ok, at least the intro does, i get a black screen after it is done, i will figure it out... BTW im running Kubuntu6.06 and i did have to install cedega.

---

### Post by azathothx on 2006-09-08
using the loki installer and wine (not cedega) i have CoD running perfectly, easily as good as in windows. a couple of dsound errors here and there, but nothing drastic. i just ran the installer, mounted my iso images and ran it away. i'm using wine 0.9.20 and everything proceeded without a hitch. are youusing the latest wine?

---

### Post by dawg on 2006-09-08
don't know what version it is, got it from automatix 3 days ago.  what copy of COD do you have, is it the recent one, the one with the 1.5 patch? are you using k or u BUNTU?  what version?

---

### Post by jediborger on 2006-09-08
I'm running a fresh install of wine .9.20 and my COD says under the readme that it's version 1.4b, so should I look for a version 1.5 update?

I used the native installer since it works fine but I'll try the loki one next time.

---

### Post by jediborger on 2006-09-08
I tried installing the patch and it said I already had the lastest version, so I checked the readme file again and it does say 1.5b. So should I try uninstalling and installing with loki?

---

### Post by Hemmer on 2006-11-13
> **skirkpatrick said:**
> 
CoD2, on the other hand, doesn't work.

do you know if their planning on releasing an installer for CoD2?

---

### Post by lithium06 on 2006-11-21
I get punkbuster errors when i join MP servers.  Any 1 get this working? 1st I had 'blocked O/S priv.' error but i got that fixed. not i get 'unknown windows API function' errors. i've tried google'n it but there's not much out there. COD SP works fine tho. But i hate having to dual boot to play COD MP.

---

### Post by Jonathan2007 on 2006-11-22
I'd love to get Call of Duty 2 installed if possible. I'm going to try to get it running in Cedega CVS later this week. Hopefully I can get it going so I can dump Windows.

---

