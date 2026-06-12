---
title: "Want WPA, Only WEP Available..."
date: 2008-04-05
forum: Dell  Ubuntu Support
---

### Post by Gringexican on 2008-04-05
On my laptop (1420n running Fiesty).  I keep getting IP collisions with another computer on my network.  That computer is wired.  I want to set it to a static IP (and avoid letting my "brain-dead" ADSL router make the decision) but unfortunatly it will only allow me to use WEP if setting the fixed IP in wireless.  Is there a work-around or patch?

I prefer to keep using WPA-TSK for the enhanced security, but it's getting annoying to have to reset the IP on one or the other depending on which is the second box to go active.  Right now I have it set to enable roaming on the wireless, because I don't want to downgrade the wireless router to WEP.

Nota Bene:: I will be upgrading the lappie to Gutsy by the end of the month as soon as I have more free time -- is that an issue that was 'fixed' in 7.10?

---

### Post by niteshifter on 2008-04-05
Hi,

I had the same problem (WEP only, no WPA) when I was running Edgy. The fix I used was to install network-manager-gnome from the repository.

I don't know if that is available for Feisty, as I went from Edgy to Gutsy. But it can't hurt to look via Synaptic and give it a try.

Gutsy does wireless different, yes it's fixed.

---

### Post by Gringexican on 2008-04-05
That seems to be doing the trick (at least until I have time to upgrade to Gutsy or Hardy).  Took a lil effort to get the settings happy with key-manager.

---

