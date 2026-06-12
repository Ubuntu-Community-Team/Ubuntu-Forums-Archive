---
title: "enabling punkbuster webtool for Battlefield 2"
date: 2009-02-24
forum: Gaming &amp; Leisure
---

### Post by dblade on 2009-02-24
I've had a BF2 dedicated server running ok for a few days.  I enabled rcon access via an admin/default.cfg file and can authenticate successfully.  sv.punkBuster is set to 1 in serversettings.con.  I also used pbsetup.run for linux and it seen and was able to update both the client and server files in the <bf2>/pb/ folder  [Client Version v2.150 | A1392,  Server Version v1.738 | A1392 | C2.150].

I'd like to get webtool setup for use, but it seems like any pb_sv* commands don't ever do anything.  One of my immediate issues is that if do a "rcon exec pb_sv_writecfg", I never see a pbsv.cfg file created in the <bf2>/pb/ folder.

One thing that i'd like to clear up is how would I tell that punkbuster is truly running?  or is it completely built-in now?

I don't see any log files in the pb folder either.  I manually created a pb/svlogs folder but nothing has been created there.

Are the rcon commands at the BF2 server console supposed to give more feedback than just "recon:" ?

ubuntu intrepid server 64-bit.

---

