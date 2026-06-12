---
title: "GnuCash finally working with Wachovia"
date: 2008-12-16
forum: General Help
---

### Post by celem on 2008-12-16
I finally got GnuCash to work correctly with Wachovia. 

There appears to be a problem with the AqBanking Wizard, at least as it pertains to Wachovia. Pressing the AqBanking wizard's User Configuration Get Accounts  always indicates a successful download from the bank but fails with a Parse error.

1. I have a WinXP box with QUICKEN working well with Wachovia.
2. I tried MoneyDance and it worked well with Wachovia - just don't like MoneyDance's interface, otherwise I would consider using it.

The ofx.py script ( [http://www.jongsma.org/gc/](http://www.jongsma.org/gc/) ) had no problem downloading the accounts data from Wachovia and examination of the resultant OFX file indicated that my CHECKING account was listed.
Thus I knew that problem was in AqBanking's wizard.
In order to get Wachovia working, I had to manually install my account info in AqBanking's Accounts tab with my checking account number and the other, well publized relevant Wachovia data, such as Bank ID = 053000219. In Ofx Configuration, FID = 4309, Org = Wachovia, Broker ID is blank, Server URL = "https://pfmpw.wachovia.com/cgi-forte/fortecgi?servicename=ofx&pagename=PFM", APPID=QWIN, APPVER=1600, Header Version=102.

With a manual account setup GnuCash works fine for Wachovia Online Banking. Obviously the  AqBanking Wizard is partially broken.

---

