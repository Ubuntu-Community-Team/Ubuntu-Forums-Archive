---
title: "open Firefox from links in Thunderbird email"
date: 2007-08-29
forum: Desktop Effects &amp; Customization
---

### Post by Papillonrus on 2007-08-29
I have looked thru the options, preference and setup in Thunderbird, I want to open links within email in Firefox currently when I click a link in email it opens in Konqueror.  Also I would like for my 7 button mouse to within KDE as it functions in Firefox.  Looking for some help and guidance.  Thanks in advance.
                                                    Darrell

---

### Post by vapore0n on 2007-08-29
I actually had a similar problem. 
Links in thunderbird or pidgin wouldnt open when clicked

I went to System/Preferences/Preferred Applications    and set the correct apps there for email and internet. All fixed

---

### Post by Papillonrus on 2007-08-29
I'm lost.  Where do you find System/preferences/prefered Applications?  I'm using Kubuntu 7.04

---

### Post by michael37 on 2007-08-30
Exit thunderbird.

cd ~/.*thunderbird/*default

gedit prefs.js

Add the following two lines:
```

user_pref("network.protocol-handler.app.http", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox");

```

Exit and save prefs.js

Start thunderbird.

Problem solved.

---

### Post by michael37 on 2007-08-30
> **Papillonrus said:**
> I'm lost.  Where do you find System/preferences/prefered Applications?  I'm using Kubuntu 7.04
That's Gnome (that is Ubuntu 7.04) option.   KDE is different.

---

### Post by FuturePilot on 2007-08-30
> **Papillonrus said:**
> I have looked thru the options, preference and setup in Thunderbird, I want to open links within email in Firefox currently when I click a link in email it opens in Konqueror.  Also I would like for my 7 button mouse to within KDE as it functions in Firefox.  Looking for some help and guidance.  Thanks in advance.
                                                    Darrell

Make sure Firefox is set to the default browser and not Konqueror.

---

### Post by ugm6hr on 2007-09-13
This works for all Ubuntu's....

[http://ubuntuforums.org/showpost.php?p=3033722&postcount=7](http://ubuntuforums.org/showpost.php?p=3033722&postcount=7)

Just use *usr/bin/firefox* as the setting.

---

### Post by michael37 on 2007-09-16
> **ugm6hr said:**
> This works for all Ubuntu's....

[http://ubuntuforums.org/showpost.php?p=3033722&postcount=7](http://ubuntuforums.org/showpost.php?p=3033722&postcount=7)

Just use *usr/bin/firefox* as the setting.

First, this post forget about https protocol which is just as important.

Second, this is effectively identical suggestion to [my post #4 above](http://ubuntuforums.org/showpost.php?p=3278469&postcount=4)

---

### Post by SentientFluid on 2007-09-18
> **michael37 said:**
> Exit thunderbird.

cd ~/.*thunderbird/*default

gedit prefs.js

Add the following two lines:
```

user_pref("network.protocol-handler.app.http", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox");

```

Exit and save prefs.js

Start thunderbird.

**Problem solved.**

It most certainly did solve it for me.  Thanks! Gotta love nice simple solutions! :)

---

