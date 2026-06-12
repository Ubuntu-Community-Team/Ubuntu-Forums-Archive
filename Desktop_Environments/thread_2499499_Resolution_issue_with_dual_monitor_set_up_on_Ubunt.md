---
title: "Resolution issue with dual monitor set up on Ubuntu or Gnome?"
date: 2024-07-29
forum: Desktop Environments
---

### Post by lakshaynasa on 2024-07-29
Hi everyone,
I've been using Ubuntu desktop with a dual monitor setup, currently on Ubuntu 24.04 LTS (though I've had this issue on previous versions as well). The problem is with the resolution on a few applications and the desktop. On the second screen, everything looks bigger (higher resolution), as shown in the attached images.
I am using the settings shown in the attached images for both screens. When I try to use Fractional Scaling, the screens become blurry. This issue occurs with certain apps: for example, the terminal works fine on both screens with no enlargement, and the desktop on the second screen looks large. However, Firefox browser displays correctly on both screens, but Chrome, Brave, and VSCode appear enlarged.
I'm unsure if this is an issue with the Ubuntu desktop, the specific applications, or GNOME. Any assistance with troubleshooting this would be really helpful.
Thanks!




 [IMG]https://ubuntuforums.org/attachment.php?attachmentid=294027&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294025&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294026&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294024&stc=1[/IMG]

---

### Post by slovenskekasina on 2024-08-06
Use xrandr for Manual Configuration. 

xrandr --output HDMI-1 --mode 1920x1080 --scale 1x1
xrandr --output HDMI-2 --mode 2560x1440 --scale 1x1

---

### Post by jjull on 2024-09-04
[INDENT][FONT=arial] 		Apparently this is an electron-specific problem with each app based on electron having difficulty to recognize wayland.

for chrome:

1. go to chrome://flags
2. search for "ozone"
3. in the preferred ozone platform drop down choose "Wayland"

for VS code the trick is to add flags to the launcher. I suggest to use   the .deb from VS code website as I had difficulty locating the launcher  in use for the snap install

for Arch (untested)

[https://gist.github.com/qguv/e592dbe...1d2ae8cfa7ef14]("https://gist.github.com/qguv/e592dbeaeebc4ee7791d2ae8cfa7ef14")

For Others, working on Ubuntu 24.04 with VS code .deb 

[https://github.com/microsoft/vscode/issues/176192](https://github.com/microsoft/vscode/issues/176192)

[/FONT][FONT=arial] 	[/FONT][FONT=arial]
[/FONT]
[FONT=arial] 	```
[/FONT][FONT=arial]Exec=code --force-user-env --enable-features=UseOzonePlatform --ozone-platform=wayland %F[/FONT][FONT=arial] [/FONT]
[FONT=arial]
```

note that the launcher might be located at different places (e.g. for snap in  /snap/code/.../meta/gui/code.desktop)

I finally located the code.desktop file and copied it to ~/.local/share/applications/ (source path may change)

```
[/FONT][FONT=arial] 	 	[/FONT][FONT=arial]cp /usr/share/applications/code.desktop ~/.local/share/applications/[/FONT][FONT=arial] [/FONT]
[FONT=arial]
```

full laucher code in ~/.local/share/applications/ (note the icon path)

```
[/FONT][FONT=arial] 	[/FONT][FONT=arial]
[/FONT]
[FONT=arial] 	[/FONT][FONT=arial][Desktop Entry]
Name=VS Code
Comment=Code Editing. Redefined.
GenericName=Text Editor
Exec=code --force-user-env --enable-features=UseOzonePlatform --ozone-platform=wayland %F
Icon=/usr/share/pixmaps/vscode.png
Type=Application
StartupNotify=false
StartupWMClass=Code
Categories=TextEditor;Development;IDE;
MimeType=application/x-code-workspace;
Actions=new-empty-window;
Keywords=vscode;

[Desktop Action new-empty-window]
Name=New Empty Window
Name[de]=Neues leeres Fenster
Name[es]=Nueva ventana vacía
Name[fr]=Nouvelle fenêtre vide
Name[it]=Nuova finestra vuota
Name[ja]=&#26032;&#12375;&#12356;&#31354;&#12398;&#12454;&#12451;&#12531;&#12489;
Name[ko]=&#49352; &#48712; &#52285;
Name[ru]=&#1053;&#1086;&#1074;&#1086;&#1077; &#1087;&#1091;&#1089;&#1090;&#1086;&#1077; &#1086;&#1082;&#1085;&#1086;
Name[zh_CN]=&#26032;&#24314;&#31354;&#31383;&#21475;
Name[zh_TW]=&#38283;&#26032;&#31354;&#35222;&#31383;
Exec=code --force-user-env --new-window --enable-features=UseOzonePlatform --ozone-platform=wayland %F
Icon=[/FONT]/usr/share/pixmaps/vscode.png[FONT=arial] [/FONT]
[FONT=arial] 	
[/FONT][/INDENT][FONT=arial]  	 	 	[/FONT][INDENT][FONT=arial] 		 	
[/FONT][/INDENT][FONT=arial]
```[/FONT]

---

