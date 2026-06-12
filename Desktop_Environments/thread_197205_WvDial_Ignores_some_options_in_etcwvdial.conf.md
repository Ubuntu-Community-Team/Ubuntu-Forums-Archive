---
title: "WvDial Ignores some options in /etc/wvdial.conf"
date: 2006-06-15
forum: Desktop Environments
---

### Post by mudfanatic on 2006-06-15
I'm trying to get a fresh breezy install to connect to the internet. the modem I have is a Smartlink PCI modem... it functioned perfectly under slmodemd with breezy in another computer, and does so in this one as well, but I'm having weird problems with Wvdial. To get Wvdial to work with the slmodem driver you have to tell wvdial to not do a carrier check, since slmodemd insists that there is no carrier. Adding this line to /etc/wvdial.conf:

Carrier Check = no

works fine on my other pc, but not on this one. wvdial simply ignores the command and checks for a carrier, which inevitably fails with slmodemd... any help would be appreciated, this is the last obstacle in the way of yet another working ubuntu system ;)

PS I've also tried enabling "Stupid Mode" - this fails as well.

-mudfanatic
[Discworld]("http://discworld.atuin.net")

---

