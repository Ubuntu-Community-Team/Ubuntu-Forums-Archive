---
title: "Gnome Favorites Folder?"
date: 2018-01-21
forum: Desktop Environments
---

### Post by scribbler2099 on 2018-01-21
IS it possible to group apps together on the Gnome Favorites dock?  I'm looking for something like Unity Drawers ([http://unity-folders.exceptionfound.com/](http://unity-folders.exceptionfound.com/)).  I installed the app folders management extension that lets me do it in the applications overview, but it would save some space if I could for example group 5 of my music apps together on the favorites dock. (Actually, this is the top rated comment about the app folders management extension [http://www.omgubuntu.co.uk/2017/05/simple-gnome-app-folders-extension](http://www.omgubuntu.co.uk/2017/05/simple-gnome-app-folders-extension)) 

This guy apparently started on something: [https://snippets.webaware.com.au/snippets/drawers-for-gnome-3-gnome-shell/](https://snippets.webaware.com.au/snippets/drawers-for-gnome-3-gnome-shell/)

---

### Post by again? on 2018-01-22
At the moment I think your best method would be to create your own launcher in  ~/.local/share/applications
utilising quicklists.
eg a ~/.local/share/applications/browsers.desktop
```
[Desktop Entry]
Name=Web browsers
Comment=Web browsers
Exec=gnome-www-browser
Icon=web-browser
Type=Application

Actions=[COLOR="#B22222"]firefox[/COLOR];[COLOR="#FF8C00"]firefox-private[/COLOR];[COLOR="#006400"]chrome[/COLOR];[COLOR="#40E0D0"]chrome-private[/COLOR];[COLOR="#0000CD"]spacer[/COLOR];[COLOR="#800080"]edit[/COLOR]


[Desktop Action [COLOR="#B22222"]firefox[/COLOR]]
Name=Firefox
Exec=firefox

[Desktop Action [COLOR="#FF8C00"]firefox-private[/COLOR]]
Name=Firefox Private Window
Exec=firefox --private

[Desktop Action [COLOR="#006400"]chrome[/COLOR]]
Name=Chrome
Exec=/usr/bin/google-chrome-stable

[Desktop Action [COLOR="#40E0D0"]chrome-private[/COLOR]]
Name=Chrome Incognito
Exec=/usr/bin/google-chrome-stable --incognito

[Desktop Action [COLOR="#0000CD"]spacer[/COLOR]]
Name=__________________________
Exec=


[Desktop Action [COLOR="#800080"]edit[/COLOR]]
Name=Edit Launcher
Exec=gedit /home/glen/.local/share/applications/browsers.desktop

```

---

