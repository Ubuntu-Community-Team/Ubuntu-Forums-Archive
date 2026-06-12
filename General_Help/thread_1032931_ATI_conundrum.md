---
title: "ATI conundrum"
date: 2009-01-06
forum: General Help
---

### Post by onecallednick on 2009-01-06
I have a pretty low end computer mated to a Radeon 9250 PCI card.  I'm currently running off the live cd, because after attempting to install the xorg drivers off the Add/Remove Application, i tried changing the resolution and was greeted with a fubared screen at every startup.

The frustration comes from the fact that now, for some reason, the live cd is much more responsive than the HDD install ever was.  Text actually keeps up when I type, instead of lagging behind a couple of words.  Does anyone have any experience with this card and has made the drivers work, or at least made ubuntu usably quick with it?  And why the hell is the live cd faster than the install?

---

### Post by onecallednick on 2009-01-06
Should i just give up on it?  I'm dreaming about picking this guy up from newegg:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814187041](http://www.newegg.com/Product/Product.aspx?Item=N82E16814187041)
but i'm torn, I was hoping to leave this computer the way it is and start saving up for a laptop.

---

### Post by jocko on 2009-01-07
> **onecallednick said:**
> I have a pretty low end computer mated to a [COLOR=Red]Radeon 9250[/COLOR] PCI card.  I'm currently running off the live cd, because after attempting to install the xorg drivers off the Add/Remove Application, i tried changing the resolution and was greeted with a fubared screen at every startup.

Which driver are you trying to install?
The only driver (open source ati/radeon) that works with your card is already installed and activated by default in ubuntu, so you can't install anything else to improve things.
Ati's proprietary driver (fglrx) only supports radeon 9500 and better cards.
Installing fglrx on a computer that does not have a supported card will only break the open source driver and leave you without a gui (or if you're lucky you'll just end up in safe graphics mode).

---

### Post by onecallednick on 2009-01-07
I was trying to install the fglrx drivers.  I realized that wasn't going to work, and was trying to install the drivers from the ATI website, but i've put that on hold as I noticed the open source ati drivers aren't being used currently; it's still using the VESA drivers.  I'm following the instructions from here: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) .  I haven't finished yet; I'll keep you posted. 

Ok, that didn't work.  I landed in low graphics mode again.  Here's what I sent the last person to edit the ati xorg wiki:

Hi, my name's Nick Chase.  I noticed that you were the last person editing the open source ati driver wiki, and I'd like to ask for your help.  I followed the directions in the site to the best of my ability, and when I restarted I landed in low graphics mode. Here's my xorg.conf:

Section "Device"
	Identifier	"Radeon 9250"
	Driver		"ati"
	BusID		"pci:00:08:0"
	Option          "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Option          "DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Radeon 9250"
	SubSection "Display"
                Depth           24
                Modes           "1280x960"
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

one thing I noticed that I found strange is that my video card was listed twice in lspci:

00:08.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
00:08.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)

Does that mean anything or is that normal?  I know this is presumptuous of me, so thanks for your time if you've bothered to read this far, and any light you can shed on this would be greatly appreciated.

---

### Post by hangfire on 2009-01-07
> **onecallednick said:**
> I have a pretty low end computer mated to a Radeon 9250 PCI card.  I'm currently running off the live cd, because after attempting to install the xorg drivers off the Add/Remove Application, i tried changing the resolution and was greeted with a fubared screen at every startup.

The frustration comes from the fact that now, for some reason, the live cd is much more responsive than the HDD install ever was.  Text actually keeps up when I type, instead of lagging behind a couple of words.  Does anyone have any experience with this card and has made the drivers work, or at least made ubuntu usably quick with it?  And why the hell is the live cd faster than the install?

You could grab a copy of the /etc/X11/xorg.conf off of your liveCD and try using it on your installed system.

I had an ATi 9550 w/ Ubuntu 7 & 8, I could get some things to work on it on DVI, some on analog output, some things with some xorg.conf files and some things with others, some with free drivers and some with ATi's, but never everything at once. I used both the FOSS and several generations of their proprietary driver. I read, and re-read, ATi's/AMD's repeated commitments to improve their drivers, and other's experiences, and concluded that the commitments only applied to their latest and greatest hardware.

Then I installed an old nVidia card and everything just worked, and the ATi card was given to a friend running XP. This sort of thing is why old ATi cards go for less money than equivalent nVidia cards on eBay.

I have no way of charging AMD for the time lost trying to get their card to work, but I do have a way to make my money talk in the future.

-HF

---

### Post by onecallednick on 2009-01-07
> **hangfire said:**
> 

Then I installed an old nVidia card and everything just worked, and the ATi card was given to a friend running XP. This sort of thing is why old ATi cards go for less money than equivalent nVidia cards on eBay.

I have no way of charging AMD for the time lost trying to get their card to work, but I do have a way to make my money talk in the future.

-HF

True that.  There's a local computer reuse/recycling center nearby, I'm thinking I'll see if they've got any GeForces and trade them if I can't get this chingaderas to work.

---

### Post by onecallednick on 2009-01-07
Ok, got the damn driver to "work".  Now the text is choppy again.  At least I can say I learned a bit about linux terminal tinkering with it.  Thanks for your help, everyone!

---

### Post by hangfire on 2009-01-07
sorry double post

---

