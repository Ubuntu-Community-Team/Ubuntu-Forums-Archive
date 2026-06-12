---
title: "[SOLVED] xsane invalid argument"
date: 2012-01-14
forum: Desktop Environments
---

### Post by thinking on 2012-01-14
hi,

just wanted to mention the error i got a few minutes ago and how i solved it
the error from xsane GUI was "invalid argumen"
/var/log/syslog states
Jan 14 23:26:54 host xsane: scan/sane/soapht.c 918: invalid extents: tlx=5918629 brx=416153 tly=5918629 bry=369914 minwidth=3196059 minheight3196059 maxwidth=14149222 maxheight=24969215

what's also worth mentioning is that in the main xsane window, on the bottom
should show the paper geometry used for scanning
in my case it was 0.00cm x 0.07cm
it seems this result's in wrong scanning calculations or such - don't know

anyway - the solution was
1) close xsane
2) open terminal
   cd .sane/xsane
3) there should be a .dlc file corresponding to your printer - e.g in my case Hewlett-Packard:HP__Color__LaserJet__CM2320fxi__MFP.drc
   move the file - e.g. mv [YOURFILE].drc [YOURFILE].drc.old
4) start xsane
the geometry should now be correct
5) if your geometry is now correct and you can scan again, you can remove the .drc.old file

don't know what the problem was - in case it doesn't help try reinstalling xsane too

---

### Post by karansac on 2012-08-02
Thank you so much! Works great here

---

### Post by mastermesh on 2013-02-03
Thanks a million!  You just saved me quite a bit of money since I won't have to buy a new scanner now! :)

---

### Post by kurt18947 on 2013-02-03
That is an excellent point to remember.  I had a similar situation with a Brother MFD where it worked fine for one user and not for another.  The problem was a configuration file.  Delete or rename the configuration file and the problem is magically healed.

---

