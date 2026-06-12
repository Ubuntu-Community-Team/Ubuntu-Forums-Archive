---
title: "Gutsy Firefox Profiles Broken?"
date: 2007-11-20
forum: Desktop Environments
---

### Post by erichnewell on 2007-11-20
After dist-upgrading (flawlessly) from Feisty to Gutsy, I can no longer run multiple concurrent Firefox profiles.

My panel shortcut is: "firefox -P PickOne"

"PickOne" doesn't exist which previously would force the profile selection box. After an initial profile was selected and running, subsequent use of the above shortcut would again bring up the selection box, and a second or even third browser session could be started, each under a different profile.

After upgrading this no longer works. I can start any profile I'd like as the INITIAL session, but subsequent execution of the firefox binary simply opens a new window under the already existing profile. I can no longer get the profile selection box nor can I force selection of a different profile directly by: "firefox -P <profilename>"...both have the same result.

---

### Post by kellemes on 2007-11-20
Have you tried "firefox -profilemanager"?

---

### Post by erichnewell on 2007-11-20
Yes, I have tried "firefox -ProfileManager, which has the same effect...none.

However, you inspired me to a different direction which does allow me to spawn a different profile:

"firefox -P <profilename> -a <profilename>"

This does not however address the issue of accessing the profile manager with a session already running.

---

### Post by inhumanbean on 2007-11-22
Here's what I did to get it to work.
Create a bash script called firefox.sh with the contents:
#!/bin/bash
export MOZ_NO_REMOTE=1
/usr/bin/firefox -ProfileManager


Then point my firefox icon on the launch panel to my firefox.sh script (dont forget to make it executeable eg: chmod 755 firefox.sh)

Then when I click the icon, the script is executed and voila!..firefox with profile manager.

Hope this helps.

Inhumanbean

---

