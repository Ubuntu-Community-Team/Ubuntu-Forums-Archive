---
title: "Screenlets Help needed"
date: 2007-07-08
forum: Desktop Effects &amp; Customization
---

### Post by detroit/zero on 2007-07-08
I just installed screenlets and everything was working great. I was checking out all the options it had, and added the "check email" screenlet. It gave some sort of server error (presumably because I hadn't yet set it up), but then it froze the entire screenlet application and froze all the other ones I had running. I can do a force quit and **** the program down, but now whenever I bring it back up it starts that "check email" app and freezes all over again.

How can I stop that particular screenlet from coming up? There has to be a list of apps being used in a config file somewhere, but the Screenlet directory in my Home Folder is empty. I looked in a couple other places but nothing jumped out at me.

Is there a config file to modify and stop that app from starting? Can I delete it and start over with the couple screenlets I want to use? Should I uninstall Screenlets as a whole, wipe all traces of it, and start from scratch?

---

### Post by detroit/zero on 2007-07-08
Well, I sort of figured it out.

Unable to find where a config file containing the selected-to-run screenlets were, I read up on the *MailCheck* screenlet and it's listed as experimental software anyways. I went to **/usr/local/share/screenlets** and deleted the *MailCheck* folder altogether.

Screenlets loaded up without a problem, and my original settings are still there. This wasn't necessarily the route I wanted to go, but it worked, so I'm not complaining.

---

