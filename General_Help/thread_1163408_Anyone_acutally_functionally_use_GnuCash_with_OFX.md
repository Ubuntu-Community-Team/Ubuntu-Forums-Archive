---
title: "Anyone acutally functionally use GnuCash with OFX?"
date: 2009-05-18
forum: General Help
---

### Post by mbutash on 2009-05-18
Hi,    I am trying to get GnuCash setup to help my horrible handling of cash, and would really like to see it pull info from my bank.  Apparently the only thing more horrible than my handling of cash is the use ability of this software.  I've tried a few times over the years, and always gave up in frustration with the software.  Call me a glutton for punishment, but I'm trying again.    The OFX setup for online banking seems pretty straight forward, but it simply doesn't seem to work.  On top of that, debugging support seems horrid, so I can't say wtf is really broken.  Going into general options for GC, under online banking, I enable verbose debugging, close out of options, and go back in, and the check for debugging is gone.  Well crap...    Next when I go through AQBanking setup, create an OFX user, and try to download account information, it gets the cert, I accept, and I see a whiz of info fly, and the window closes itself before I can actually read anything.  Real freakin helpful guys...  I can't find any presence of log files around aqbanking, so I'm entirely at a loss as to how to even troubleshoot it.    I suppose I have to ask, does anyone successfully use this software?  Certainly no one seems to do any Q/A on it, so I don't know.  Running gnucash with --debug provides me with nothing useful, so I'm at a loss.  Is it entirely a lost cause?  Just run a stupid windoze box and pay for Quicken?  I suppose I'd rather just not balance my checkbook after all.  Frustration ensues.  -mb

---

### Post by Cuba71 on 2009-08-03
I'm trying to migrate from Quicken 2009 to GnuCash, and I'm at the same point you are, can't get OFX to work.

I have all the parameters from Quicken OFX log that I plug in into GnuCash, and still nothing, getting Error 400 all the time.

I'll keep trying and I'll post any progress.

---

### Post by Cuba71 on 2009-08-04
**_Update:_**

I've been able to us OFX in GnuCash wih Bank of America and American Express, after many iterations of defining Users and Accounts.

I'm still looking whre the OFX.log is in my installation.

Update: To get OFX logs you have to set the environment variable AQOFX_LOG_COMM=1.  Recommended only for debugging purposes since it contains IDs and Passwords.  The logs will show at /tmp/OFX.log

---

