---
title: "Cairo-Dock &amp; Chrome Apps"
date: 2015-12-09
forum: Desktop Environments
---

### Post by bcleveng-0 on 2015-12-09
Hi All,

I'm trying to use Cairo-Dock on Ubuntu 14.04, and using chrome apps. In particular I want to use keep/hangouts/music. I've figured out how to create launchers (I go to the chrome apps page, then right click -> create shortcuts, drag created shortcut onto the bar), and they launch the correct application.

My problem is that the window created gets a chrome icon (rather than the app icon), and gets filed with the main chrome launcher on the taskbar. Clicking the app launcher does cause the correct chrome window to be active, but if chrome isn't already the focused window, it causes the chrome launcher to animate asking for attention rather than actually bringing the window forward.

The Unity launcher doesn't have this problem. It correctly files the app with its own launcher, and will always bring it to the front. 

The *.dekstop file I'm using looks like:
```
#!/usr/bin/env xdg-open


[Desktop Entry]
Version=1.0
Terminal=false
Type=Application
Name=Google Keep - notes and lists
Exec=/opt/google/chrome/google-chrome --profile-directory=Default --app-id=hmjkmjkepdijhoojdojkdfohbdgmmhki
Icon=chrome-hmjkmjkepdijhoojdojkdfohbdgmmhki-Default
StartupWMClass=crx_hmjkmjkepdijhoojdojkdfohbdgmmhki
Name[en_US]=Keep
```

So I think the WM_CLASS is set correctly. Checking with xprop I see: ```
WM_CLASS(STRING) = "crx_hmjkmjkepdijhoojdojkdfohbdgmmhki", "google-chrome"
``` 
So that seems right... And because Unity manages it (even when launched from Cairo-Dock) I'd expect that to be right.

Is there a Cairo-Dock setting I'm missing somewhere? I've currently got v3.3.99.beta1.2.really.3.3.2-0ubuntu2.1 & for Chrome I'm using v47.0.2526.80

I'd appreciate any pointers! Or if someone has a dock application I could use that would get this right, rather than Cairo-Dock I'd be willing to give it a shot. I've already tried Docky, it has the same problem though it does get the icon correct even though it files the window with the chrome launcher.

Thanks!

---

