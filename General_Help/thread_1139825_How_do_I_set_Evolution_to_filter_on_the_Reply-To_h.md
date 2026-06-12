---
title: "How do I set Evolution to filter on the Reply-To header?"
date: 2009-04-27
forum: General Help
---

### Post by DJ_Peng on 2009-04-27
Is there a way to set up a message filer in Evolution 2.26.1 that will filter on the Reply-To header? I thought I had this set up before but I did a fresh install of Jaunty and I forgot to export my settings before I created a new profile (I had issues with my old profile) and now I can't seem to be able to get Epiphany to filter incoming messages based on the Reply-To field. That's how I want to filter messages from subscribed Launchpad bugs.

I understand Thunderbird can do it, but I specifially migrated from Tb to Evo last year so switching back really isn't an option at this point.

---

### Post by DJ_Peng on 2009-05-04
I don't know what happened, but I deleted the original filter I created and made a new one to look for the following conditions:

Specific Header: Reply-To > contains "launchpad.net"
Then: Move to folder > [path/to/my_Launchpad_folder]

I saved the filter and ran it on a message from Launchpad that came in today and it worked like a charm. I'm not sure what changed between when I first created the filter and today (since I had that criteria on the original filter) but it seems deleting the old rule and creating a new one in Evo 2.26.1 (from Ubuntu 9.04) did the trick.

---

