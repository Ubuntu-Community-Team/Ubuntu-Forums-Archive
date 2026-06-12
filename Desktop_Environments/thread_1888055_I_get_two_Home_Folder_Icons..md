---
title: "I get two Home Folder Icons."
date: 2011-11-28
forum: Desktop Environments
---

### Post by anur.bhargav on 2011-11-28
I tried to add all the 'Favorite Places as Quicklists for Home Icon in Unity'..I followed How-To [http://www.techdrivein.com/2011/10/15-things-i-did-after-installing-new.html](http://www.techdrivein.com/2011/10/15-things-i-did-after-installing-new.html) and I messed up big time.

I have 2 home folders as soon as I open any window (One with favorites, when I clicked it another would open up). Then I deleted the "nautilus-home.desktop" in " ~/.local/share/applications" .
Only thing that changed was I didn't have my favorites in the Home Icon. I still have 2 Home folders as soon as I open any window.

Please see this video [http://youtu.be/oS52pYNFZ6I](http://youtu.be/oS52pYNFZ6I). It explains my problem.

---

### Post by BC59 on 2011-11-28
Maybe you can solve the problem by reseting Unity:

```
unity --reset-icons
```

```
unity --reset
```

---

### Post by anur.bhargav on 2011-11-28
> **anur.bhargav said:**
> I tried to add all the 'Favorite Places as Quicklists for Home Icon in Unity'..I followed How-To [http://www.techdrivein.com/2011/10/15-things-i-did-after-installing-new.html](http://www.techdrivein.com/2011/10/15-things-i-did-after-installing-new.html) and I messed up big time.

I have 2 home folders as soon as I open any window (One with favorites, when I clicked it another would open up). Then I deleted the "nautilus-home.desktop" in " ~/.local/share/applications" .
Only thing that changed was I didn't have my favorites in the Home Icon. I still have 2 Home folders as soon as I open any window.

Please see this video [http://youtu.be/oS52pYNFZ6I](http://youtu.be/oS52pYNFZ6I). It explains my problem.

I solved the problem :D...
This is what I did..

This was my original "nautilus-home.desktop" file's contents
> 
[Desktop Entry]
Name=Home Folder
Comment=Open your personal folder
Exec=nautilus
Icon=user-home
Terminal=false
StartupNotify=true
Type=Application
OnlyShowIn=GNOME;Unity;
Categories=GNOME;GTK;Core;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=3.0.0
X-Ubuntu-Gettext-Domain=nautilus


After some reading, I come to know that the 9th line > OnlyShowIn=GNOME;Unity; causes your 'Home Folder Launcher Icon' will only launch the app, "not control it". A 2nd icon will show up that does that. In my case the second Icon was called "Files" (The one that we see in Gnome-Shell).
I deleted this line and this solved the problem :D.

And I even got the quicklists. This is what I did.

1. Copy 'Home Folder' launcher file to your home directory 
> 
mkdir ~/.local/share/applications
cp /usr/share/applications/nautilus-home.desktop ~/.local/share/applications
2. Open the file in Gedit  > gedit ~/.local/share/applications/nautilus-home.desktop
3. Delete the following line from the file > OnlyShowIn=GNOME;Unity;
4. Add this text to the bottom of the file, then close and save:
> X-Ayatana-Desktop-Shortcuts=Videos;Documents;Music;Pictures;Downloads
[Videos Shortcut Group]
Name=Videos
Exec=nautilus Videos
TargetEnvironment=Unity

[Documents Shortcut Group]
Name=Documents
Exec=nautilus Documents
TargetEnvironment=Unity

[Music Shortcut Group]
Name=Music
Exec=nautilus Music
TargetEnvironment=Unity

[Pictures Shortcut Group]
Name=Pictures
Exec=nautilus Pictures
TargetEnvironment=Unity

[Downloads Shortcut Group]
Name=Downloads
Exec=nautilus Downloads
TargetEnvironment=Unity
5. Hit "ALT+F2" and type > unity --replace

DONE !! :P  For more quicklist visit [http://askubuntu.com/questions/35488/list-of-custom-launchers-quicklists-for-unity](http://askubuntu.com/questions/35488/list-of-custom-launchers-quicklists-for-unity) :popcorn: :D

---

### Post by anur.bhargav on 2011-11-28
> **BC59 said:**
> Maybe you can solve the problem by reseting Unity:

```
unity --reset-icons
```

```
unity --reset
```

I tried ```
unity --reset
``` it didn't work, but hadn't tried ```
unity --reset-icons
``` Thanks for the reply :).. I solved it and have posted the solution :D

---

