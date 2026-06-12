---
title: "Firefox profilemanager not working how i want!"
date: 2009-06-14
forum: General Help
---

### Post by Chops II on 2009-06-14
I'm trying to create a launcher that will always display the profile manager regardless of which profiles are running already and still be able to launch any profile from it, so that i can launch from profilemanager a profile that is already running if i want a new window of that profile without bringing up the running instance and creating a new window.
Not having -no-remote makes it so the profilemanager wont come up.
another issue is that i could replace this with having separate launchers for each profile, but the specified profile is ignored without -no-remote (it opens the last opened or the one that is open). If i have -no-remote then it fails if that profile is open.
Anyone have the perfect solution?
The envornment variable MOZ_NO_REMOTE=1 what i'm looking for or does that act like -no-remote? If not does it create a new firefox process for every new time i launch firefox from launcher regardless of profiles already running, and is that a bad thing?

Thanks for your help!

---

### Post by gunksta on 2009-06-14
AFAIK, firefox only allows you to run a single instance of a profile. You can run multiple windows, but you can only run a profile once.

---

### Post by crossedout on 2009-06-15
Hi Chops II,

I believe part of the idea behind setting FF with -no-remote is the assumption a user would want to open a separate profile.  Otherwise, again its assumed, the user would just open a new window from the currently running profile.  So what you are asking, at least with -no-remote I don't believe is possible.

If its only one profile you intend to open multiple times then you could set your shortcut without the -no-remote for that particular profile and then click and open as much as you want.

-Xout

---

### Post by Chops II on 2009-06-15
Thank you for fast responses!
Another issue i don't think i mentioned is that when i close my main profile but leave my email profile running, then all links i click in any application are opened in my email profile.
This is annoying.

Perfection would be telling firefox to open any link that opens a new tab from anywhere with a certain profile, including links in emails that open new tabs, except for links clicked in certain other profiles, like ones i've made for other users.
Obviously that's pretty much impossible atm.

Thanks again

---

### Post by asmoore82 on 2009-06-15
I have this on my Desktop...

```
**$** cat Desktop/firefox\ \(profile\ manager\).desktop 
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Firefox Web Browser (Profile Manager)
Comment=Browse the World Wide Web
GenericName=Web Browser
[COLOR="Red"]Exec=firefox -no-remote -P[/COLOR]
Terminal=false
X-MultipleArgs=false
Type=Application
[COLOR="Red"]Icon=deerpark[/COLOR]
Categories=Application;Network;
MimeType=text/html;text/xml;application/xhtml+xml;application/xml;application/vnd.mozilla.xul+xml;application/rss+xml;application/rdf+xml;image/gif;image/jpeg;image/png;
StartupWMClass=Firefox
StartupNotify=true
GenericName[en_US]=Web Browser
Name[en_US]=Firefox Web Browser (Profile Manager)
```

---

