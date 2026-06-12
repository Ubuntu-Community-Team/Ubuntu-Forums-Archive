---
title: "Set icon image for link via terminal"
date: 2009-04-25
forum: General Help
---

### Post by mpgarate on 2009-04-25
I am looking for the command that will allow me to change or set an icon image for a symbolic link. I am also curious how to (via the command line) tell ubuntu to always run the link, whereas now it prompts me to run, run in terminal, or display its contents.

thanks

---

### Post by geirha on 2009-04-25
As far as I know, you can't set an icon for a particular symbolic link; only the generic icon used for all symbolic links. Make a launcher instead (right click the Desktop and choose Create Launcher).

---

### Post by mpgarate on 2009-04-25
I'd really like to learn how to do this via the terminal, as it is the final step in a how-to I am writing. It would be nice if the reader only had to paste commands, rather than click around.

---

### Post by geirha on 2009-04-25
Make a launcher on your desktop using the GUI. If you name it "test", then you'll find the launcher as ~/Desktop/test.desktop in the terminal. Open it in a text editor and look at the format. It's fairly easy to create a launcher from the terminal by using cat or echo or similar.

EDIT: An example:
```
cat > "`xdg-user-dir DESKTOP`/mylauncher.desktop" << EOF
[Desktop Entry]
Encoding=UTF-8
Type=Application
Terminal=false
Name=The name of the launcher
Exec=/path/to/executable
Icon=apple-red
Comment=Awesome program
EOF

```

---

