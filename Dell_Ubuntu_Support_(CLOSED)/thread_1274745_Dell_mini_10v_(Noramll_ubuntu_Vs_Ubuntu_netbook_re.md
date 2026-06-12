---
title: "Dell mini 10v (Noramll ubuntu Vs Ubuntu netbook remix)"
date: 2009-09-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dj-toonz on 2009-09-24
Hi all, I'm getting the above dell netbook later on today (being delivered) & already got a external USB DVD-RW & ubuntu netbook remix on a 8 gig usb flash drive (going to wiping windows XP straight off the netbook (as I don't want to use the dell ware rubbish it comes with. I've got a few questions before I install either of the 2

1) what's the difference between the UNR (never used it or have a clue what it is) & the normal version

2) I'm going to remove the bottom bar & replace it with  a mac osx launcher, if i do install UNR is that possible & does UNR let you Change to default gnome look to be able use compiz

3) I've been reading the wiki for netbooks for UNR & it says the dell mini 10v has no problems with either Jaunty 9.04 UNR or Karmic 9.10 UNR or the normal version is that true

I'll only be using the netbook to write reports up on, listering to shoutcast streams & surfing the net,facebook,Twitter & chatting over skype & MSN 

The dell I've ordered has 2 gigs of ram , Bluetooth chip , 3.5g Mobile broadband as It comes on a Vodafone contract

---

### Post by lincoln32 on 2009-09-24
net book remix (UNR) has all non needed stuff removed that will not be needed for a netbook computer to keep it small and fast and has a special
desktop designed for small screen so it has a side bar launcher. but you can change it to a normal desktop. you could use a full version also it will just have a lot of unneeded files and programs and would not have the spcial desktop but that can always be added. compiz is default in 9.10 but not in 9.04

---

### Post by mikewhatever on 2009-09-25
UNR has a different interface, modified to better suite smaller netbook screens. That's about all of the difference. Contrary to lincoln32 above, I'd say UNR is virtually identical to Ubuntu proper regarding the programs installed. You get the usual assortment, Open Office, Firefox, Pidgin, Music and Media Player, Gimp, etc.

As for the doc, also known as AWN - Avant Window Navigator, you'll probably need to switch to Desktop mode and install compiz. Personally, I don't think it a good idea, given a relatively low vertical resolution mini 10v has.

---

### Post by Devi 710 on 2009-10-13
Doesn't UNR work better with the hardware? I believe it is supposed to be optimized to work with the Atom processors used in newer netbooks, where the normal Ubuntu distro isn't.

I am also curious as I will be buying a Dell 10v or an A90 (like mini 9) later this week.

Would it be best to install UNR and just switch to the full desktop mode for the best results on the hardware? Anyone tried both?

I've been using Easy Peasy on my eeepc 701 which is a lot like UNR, but if I go to a 10" screen, I might prefer a proper desktop.

Thanks,

Devi

---

### Post by mikewhatever on 2009-10-13
No, UNR is the standard i386 architecture not particularly optimized for an Atom CPU. In other words, UNR and Ubuntu standard are the same under the hood. You can get an LPIA architecture port of Ubuntu standard, but there is no UNR, and you are limited to lpia repositories.
[http://cdimage.ubuntu.com/ports/releases/9.04/release/ubuntu-9.04-alternate-lpia.iso](http://cdimage.ubuntu.com/ports/releases/9.04/release/ubuntu-9.04-alternate-lpia.iso)

In the end, it doesn't really matter what you install. I've used a custom Ubuntu with LXDE first (similar to a regular desktop), then switched to UNR, and liked both.

---

### Post by Devi 710 on 2009-10-13
Interesting. I guess it is just Moblin that is supposed to take advantage of the Atom processor. I thought UNR did as well because an Atom Processor is listed as a requirement. So I guess it's just the interface that is optimized for the small screen and some fat trimmed away from the OS.

That's why I went the Easy Peasy route, as my eepc 701 didn't have the atom p.

I think I'll be going the full 9.04 route, or just wait a bit and see how 9.10 turns out.

---

### Post by mikewhatever on 2009-10-13
Actually, there is a lot of choice these days for the Dell minis. You can get UNR/Ubuntu, Ubuntu Moblin Remix, or Moblin itself. It's rather tempting. As for the architecture, I'd expected UNR to be lpia and not i386, but that's not the case. Regardless, things work well, no complains, besides, lpia doesn't as much take advantage of Atom, as helps save some power, thus extending battery life.

---

### Post by Devi 710 on 2009-10-13
You may want to check out Jolicloud if you haven't already.
[http://www.jolicloud.com/]("http://www.jolicloud.com/")

Yet another option. It's still alpha. I just got my invite today. They are taking a bit of a different approach. More web based.

---

### Post by snowpine on 2009-10-13
The Dell Mini comes with Ubuntu 8.04 pre-installed. This custom "Dellbuntu" is different from any "normal" Ubuntu release. It has a special lpia (low power intel architecture) kernel, special drivers for the hardware, and legal codecs. It also has a different user interface that is a little different from the standard Ubuntu Netbook Launcher. 

Personally, I used Dellbuntu 8.04 for a while on my Mini 9, but eventually switched to Arch for various reasons. For a casual user, however, I would definitely recommend Dellbuntu 8.04 as a sane default option. It runs flawlessly on the hardware and gets good performance/battery life through the lpia architecture.

---

