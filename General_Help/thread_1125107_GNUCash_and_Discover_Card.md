---
title: "GNUCash and Discover Card"
date: 2009-04-14
forum: General Help
---

### Post by run4flat on 2009-04-14
If anybody wants to get direct connect to work with GnuCash, you can find excellent instructions on the GnuCash wiki here:

[http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2](http://wiki.gnucash.org/wiki/Setting_up_OFXDirectConnect_in_GnuCash_2)

You can find the various parameters for you bank (if they are known) here:

[http://wiki.gnucash.org/wiki/OFX_Direct_Connect_Bank_Settings](http://wiki.gnucash.org/wiki/OFX_Direct_Connect_Bank_Settings)

However, in order to get GnuCash to work with DiscoverCard or Amex (Amex unconfirmed), you will need to enable SSLv3 (as mentioned in this post:
[http://forum.kde.org/ofx-direct-download-problems-t-30488.html](http://forum.kde.org/ofx-direct-download-problems-t-30488.html)).  To do that, in the step **Using AqBanking to set up accounts** from the wiki instructions, you should look for SSLv3 under the *Server Options* of the *OFX* tab for the *User Configuration*.  You'll have that tab open at this point in the procedure anyway, so just look around, or see the attached image for help.

Hope that helps!

---

