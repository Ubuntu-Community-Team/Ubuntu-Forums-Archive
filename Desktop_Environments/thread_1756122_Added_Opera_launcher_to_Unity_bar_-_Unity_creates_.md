---
title: "Added Opera launcher to Unity bar - Unity creates another one when launched"
date: 2011-05-11
forum: Desktop Environments
---

### Post by TBABill on 2011-05-11
Strange one. I installed Opera just fine and it runs great. Decided to add it to the launcher in Unity and the launcher launches Opera correctly. However, when launched the system doesn't identify Opera as open with the small triangle to the left of it as it would any other application when in use. Instead it creates another instance in the Unity bar that has a different icon than the regular Opera "O" and when Opera is minimized you can click on that new icon in the launcher to maximize it again. When you close Opera, that icon disappears from the launcher. So....once closed, you can still click the first Opera icon (big red "O") in the Unity bar and launch Opera again, but then you get that second icon that actually controls it once opened.

Any ideas on why this happens or how to make the single Opera icon the only one that controls Opera instead of just launching it and handing it off to another unnecessary icon?

---

### Post by mc4man on 2011-05-11
Works fine here, but there was an issue previously where Opera would open using the 'opera widget installer' icon instead of the opera one pinned in the launcher.

If that's the case for you a workaround would be 
```
gksudo gedit /usr/share/applications/opera-browser.desktop
```

The bottom area would show this, remove the line in blue and it's space, save and log out/in
```
Comment=A fast and secure web browser and Internet suite
Icon=opera-browser
TryExec=/usr/bin/opera
Exec=/usr/bin/opera %U
Terminal=false
MimeType=text/html;text/xml;application/xhtml+xml;text/vnd.wap.wml;text/wml;application/x-mimearchive;application/mime;application/xml;application/rss+xml;application/rdf+xml;image/svg+xml;application/x-opera-uniteapplication;application/x-opera-extension;x-scheme-handler/http;x-scheme-handler/https;x-scheme-handler/ftp;x-scheme-handler/mailto;
Categories=Network;WebBrowser;
[COLOR="Blue"]StartupWMClass=opera[/COLOR]
X-AppInstall-Package=opera
```

Ex. after removing
```
Comment=A fast and secure web browser and Internet suite
Icon=opera-browser
TryExec=/usr/bin/opera
Exec=/usr/bin/opera %U
Terminal=false
MimeType=text/html;text/xml;application/xhtml+xml;text/vnd.wap.wml;text/wml;application/x-mimearchive;application/mime;application/xml;application/rss+xml;application/rdf+xml;image/svg+xml;application/x-opera-uniteapplication;application/x-opera-extension;x-scheme-handler/http;x-scheme-handler/https;x-scheme-handler/ftp;x-scheme-handler/mailto;
Categories=Network;WebBrowser;
X-AppInstall-Package=opera

```

---

### Post by TBABill on 2011-05-12
That's exactly what was happening. I'll give it a shot when I get on that machine tonight or tomorrow morning. Much appreciated!

---

### Post by TBABill on 2011-05-13
Worked perfectly! Thank you for the assistance.

---

