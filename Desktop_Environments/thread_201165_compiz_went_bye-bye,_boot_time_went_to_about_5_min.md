---
title: "compiz went bye-bye, boot time went to about 5 minutes..."
date: 2006-06-21
forum: Desktop Environments
---

### Post by hotani on 2006-06-21
I started up today, and halfway through the process it comes up with 

"you should issue /etc/init.d/sendmail reload"

I do not even want sendmail since it never worked and I'm getting this message every time I boot. I've already tried "uninstall everything sendmail" from synaptic but apparently it is still here. In addition, it hangs on this message for a couple of minutes during the boot process while doing god-only-knows-what.

EDIT: did more cleaning - I seem to have finally gotten rid of sendmail. woo hoo!

Then when I finally get to the desktop, no compiz. Just gone. It was fine when I shut down the computer 2 days ago. What happened? Nothing I do to get it going again seems to work. I didn't even do anything! Bad linux day I guess.... This is with aiglx, BTW - and I used the compiz/aiglx setup howto on this board and have had no problems until now. Fortunately I still have a desktop at least.

I'm getting this message when I try to reload from the repos:
```

W: GPG error: http://xgl.compiz.info dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E

```

and when I try to select 'compiz-vanilla-gnome' in synaptic:
```

compiz-vanilla-gnome:
  Depends: libpango1.0-0 (>=1.12.3) but 1.12.2-0ubuntu3 is to be installed

```

Seriously, this was just working then it stopped.

](*,)

---

