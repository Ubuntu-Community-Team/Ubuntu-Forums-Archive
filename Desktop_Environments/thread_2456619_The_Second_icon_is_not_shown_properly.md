---
title: "The Second icon is not shown properly"
date: 2021-01-15
forum: Desktop Environments
---

### Post by frnmjn on 2021-01-15
Hi folks,


i have one vscode instance for each roject that i need, so i've created many launcher with specific icon






but when i open the second instance, the icon is not shown properly in the multitasking overview




the laucher conf is like this:


```

[Desktop Entry]
X-SnapInstanceName=booking
Name=Visual Studio Code
Comment=Code Editing. Redefined.
GenericName=Text Editor
Exec=env BAMF_DESKTOP_FILE_HINT=/var/lib/snapd/desktop/applications/booking.desktop /snap/bin/code --force-user-env --no-sandbox --unity-launch %F
Icon=/home/ejf/vscode/booking-service.png
Type=Application
StartupNotify=false
StartupWMClass=Code
Categories=Utility;TextEditor;Development;IDE;
MimeType=text/plain;inode/directory;application/x-code-workspace;
Actions=new-window;new-private-window;
Keywords=vscode;




[Desktop Action new-empty-window]
Name=New Empty Window
Exec=env BAMF_DESKTOP_FILE_HINT=/var/lib/snapd/desktop/applications/booking.desktop /snap/bin/code --force-user-env --no-sandbox --new-window %F
Icon=/home/ejf/vscode/booking-service.png





```




Can you help me to show the second icon properly?

---

