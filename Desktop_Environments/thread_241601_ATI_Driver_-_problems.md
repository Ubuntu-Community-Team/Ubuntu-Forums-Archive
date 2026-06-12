---
title: "ATI Driver - problems"
date: 2006-08-22
forum: Desktop Environments
---

### Post by c_x on 2006-08-22
[COLOR="Lime"]**Update:**[/COLOR]
This is probobly the most stupid thing I've ever seen:
First it did report Direct rendering ok, but xv was disabled and everything seemed laggy
Now it is reporting DR no, BUT it feels like it's on, x working

**WHATS WRONG WITH THE ARI DRIVER :|**

Okey, first I installed ATI's driver with help of a post here. can't find it now, but it was like "download stuff from ati.com, dpkg somthing and then it worked" but all the apps that involved 3d rendering (e.g. google earth, xgl/compiz) worked fine, but suddenly they could cause a hard-lock. Cedega showed 3d acceleration failure, but glxinfo showed "direct renedering: ok".
So I went to [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) and tried the second stepp: didn't work, tried the first step, didnt work and disabled ati drivers. Tried the second step again only to see the mesa shit again ](*,) 
How can I fix this?
Any help is welcome!

---

### Post by PathSpace on 2006-08-22
Did you install the update to the x-server earlier today?  If you did, I think that you must re-install the ATI drivers.

---

### Post by c_x on 2006-08-22
Thanks, but i have reinstalled them 4 times already

---

### Post by c_x on 2006-08-22
I removed every fglrx related thing in synaptic and reinstalled the driver by the "second howto at http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide"
Aticonfig didn't work so I manually changed xorg.conf to driver="fglrx".
That gave back "direct rendering: yes", but still no 3d acceleration in cedega and compiz, google earth suffers from hard-locks all the time.
Back to square one, help anyone?

---

### Post by c_x on 2006-08-22
glxgears is running really slow and compiz isnot working at all, even if direct rendering is yes.
What did linux do to piss off ati?

---

### Post by Toxicity999 on 2006-08-22
> **c_x said:**
> glxgears is running really slow and compiz isnot working at all, even if direct rendering is yes.
What did linux do to piss off ati?
I think you have that that wrong way whats hasn't ATi done to piss off Linux... I'm confined to an Ati my self I don't want to start the classic ati nv wars here in a bad place so I'll leave it at this skim through some logs specifically the xorg startup log it will be long for sure but go by the symbol system it uses at the left and look for any warning or fatal errors, certain warnings are considered normal but you may have stumbled on it somehow using mesa yet it reporting direct rendering which surly is odd but given all the oddness I encounter tweaking around with the Ati drivers you never know. Could just be a matter or Xorg.conf settings.Sorry for not offering specific help but I just dont have much to go on and I've been away from my box too long to know what the current hap is in the list of ati's 'screw you's to the end user

---

### Post by c_x on 2006-08-23
Well, my aticonfig (whatever I write the help-thing comes up - yes, i'm "sudoing") decided not to do anything so I had to configure it manually:
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option          "OpenGLOverlay" "off"
	Option          "UseInternalAGPGART" "no"
EndSection
```
Anything worng with it?

---

### Post by c_x on 2006-08-24
Bump.
I've tried to reinstall it 4 more times now, still doesn't work
Tried with older drivers too, but without any luck.

---

