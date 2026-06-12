---
title: "Keep different Firefox profile separate in the launcher?"
date: 2013-02-27
forum: Desktop Environments
---

### Post by josm on 2013-02-27
Firefox can be started using different profiles with the option -profile and with -no-remote one can keep sessions with different profiles open at the same time in parallel. 

But how can I tell Unity to keep those sessions seperated? At the moment I start the "default" session from the launcher and the alternate session from the command line but Unity throws all the windows together into one launcher icon. 

What is the best way to keep them completely separated and have Unity group the windows for each session in different launcher icons?

---

### Post by stinkeye on 2013-02-27
Using gedit create a .desktop file for firefox with profile.
eg 
Save as **firefox-profile.desktop** to **~/.local/share/applications**
```
[Desktop Entry]
Type=Application
Version=1.0
Hidden=false
Terminal=false
Icon=[COLOR="Red"]/home/glen/Pictures/firefox2.png[/COLOR]
Name=firefox-profile
Exec=firefox -no-remote -P [COLOR="DarkOrchid"]profile[/COLOR]
Categories=GNOME;GTK;Network;WebBrowser;
```

Search and download a firefox.png using google image search
then [COLOR="Red"]link to your pic [/COLOR].
Change the exec line to your [COLOR="DarkOrchid"]firefox profile name[/COLOR].

firefox-profile will now appear in a dash search.
Drag-n-drop to the launcher.

**_P.S._** You can't open a .desktop file by navigating to it in nautilus and  clicking on it.
So if you need to edit later,
either navigate to the file in nautilus and then drag-n-drop the .desktop file to a gedit window

or

open with the terminal
eg
```
gedit ~/.local/share/applications/firefox-profile.desktop
```

---

### Post by josm on 2013-02-27
Thank you - this will add a new icon to start firefox, but once one or more windows for this firefox are created, these OPEN windows are all shown under the same icon as for my default firefox.
To describe this more clearly: when I start Firefox, the OPEN windows are shown not under the icon from where I started it, but a new icon is created in the Launcher. When I click the start icon, a new window is created, when I click the additional launcher icon, all the active windows are shown.
Now, for the new firefox, the active windows are shown TOGETHER with the windows of the other Firefox session, not with a separate icon.
But this was what my question was about: is there a way to keep the OPEN WINDOWS for the two firefox sessions separate?

What may be related to this question is the fact that when I start Firefox and a window is created, that window is represented by a NEW icon in the launcher, not in the exisiting starter icon (like it is the case with e.g. Thunderbird or the Terminal). Why is this? Is it related to my problem of keeping the open windows separated?

---

### Post by stinkeye on 2013-02-27
Not sure if I'm understanding you correctly but in both Quantal and raring for me,
Opening of firefox normally from my launcher icon shows it running from that firefox icon.
Opening a new window shows it under the same icon.


Clicking the created profile launcher starts a new instance shown from the profile icon.
Creating a new window in either of the profiles shows the new window 
in it's applicable launcher.

---

### Post by josm on 2013-02-27
Hmm something seems to be wrong with how my firefox launcher works (oddly, just the Firefox launcher and not other ones, because invariably, starting a window by clicking on the Firefox icon, will either create a new separate icon (if this was the first window started) or add the window to that separate, second icon.

Is there a way to figure out which .desktop file corresponds to the starter icon and maybe compare it with yours? Could the content of the .desktop file be responsible for this odd behavior?
Is there a documentation about all this anywhere, especially about what the syntax of such a .desktop file is?
Unfortunately it is not possible to figure any of this out by right-clicking as it was the case with the Gnome 2.0 icons in the panel.

EDIT: I think i fixed the odd behavior problem: I started Firefox which created the additional icon, then right-clicked that new icon and chose "lock to Launcher". Then I moved that icon up beside the old starter icon and removed the old starter icon (so the new locked icon took its place). The new locked icon now seems to work as expected.
HOWEVER: the windows of the second firefox starter are still shown under this "original" firefox starter icon. This is even the case if there is no window open for the "original" default Firefox. So if I then start the second Firefox, the little white triangle mark appears at the starter of the original Firefox, not the one I used.

---

### Post by unheeding on 2013-02-27
In order to make it work here I had to change the default Firefox launcher to be:

```
Exec=firefox --no-remote -P default %u
```

Now they appear in different icons.

---

### Post by josm on 2013-02-27
how does one change the default starter? How can I figure out where to find the .desktop file for the default starter? It is not in .local/share/applications.

EDIT: I tried to do this differently: I just created a second .desktop file for the default firefox using -no-remote etc. However that did not have the desired effect either: now the windows for both this and the alternate profile firefox showed up under the original starter icon in the launcher. So I removed the original starter icon to see what happens then. Now, NO icon shows the little white triangle! Also, the two icons can only be used to start a single window, because after the first window, clicking again shows the error message that firefox is already running.

---

### Post by stinkeye on 2013-02-27
If you want to try unheedings method,
copy the system wide launcher to /.local/share/applications then edit that file.
```
cp /usr/share/applications/firefox.desktop ~/.local/share/applications
```

Then edit that file to use unheeding's exec line.
```
gedit ~/.local/share/applications/firefox.desktop
```

May need to remove and then add back firefox launcher.

Deleting **~/.local/share/applications/firefox.desktop** will return you to using
**/usr/share/applications/firefox.desktop**

---

### Post by josm on 2013-02-27
I did all this and the behavior is still the same - clicking any of the different Firefox starter icons creates a new icon below all the starter icons and only that icon can be used to display the open windows - the starter icon will only try to add new windows which fails because of the -no-remote parameter.
No matter which of the many starter icons i have now created i use, the window will be added to the one single firefox icon that is created below all the starter icons for the open windows of any of these firefox sessions.

---

### Post by stinkeye on 2013-02-27
The only other suggestion I have is, try creating a new user and see
how the launcher behaves in that session.

---

### Post by josm on 2013-02-27
Thanks - good suggestion!
I did not try all the rest, but just starting Firefox under the other user does not create a separate icon for the windows. 
So the riddle is: what is going wrong with my user and how can I fix it? :)

It would help to know more about the mechanisms involved here and if there was some good documentation of all this -- is there?

---

### Post by unheeding on 2013-02-27
The problem with your user would be the files in ~/.local/share/applications/

---

### Post by josm on 2013-03-02
> **unheeding said:**
> The problem with your user would be the files in ~/.local/share/applications/

I fear no - I simply removed all the files from ~/.local/share/applications/ and the Firefox icon still shows the same behavior: when Firefox is started, a new separate icon is created that represents the open windows.

---

### Post by josm on 2013-03-02
I think I figured out some relevant information for the issues involved here:

1) if anything is added, deleted or changed in .local/share/applications, one has to log out and log in again so that Unity will see the changes
2) it seems that in order for two different application to show up in the dash, one has to change both the name of the desktop file and the value of the "Name=" parameter within the file.
3) Unity will create a separate icon for a started application when the X11 WM_CLASS information of the Window is different from what Unity expects it to be (supposedly based on the Name in the launcher, but I have not found any documentation that would verify that assumption). The WM_CLASS that Unity should expect can be explicitly specified in the .desktop file with the parameter StartupWMClass. (Setting this parameter to "Firefox" - which it should be anyways - in /usr/share/applications/firefox.desktop solved the problem I had with a second icon appearing for my Firefox, see [http://ubuntuforums.org/showthread.php?t=2120726](http://ubuntuforums.org/showthread.php?t=2120726))
4) In order to keep Firefox sessions separate, on can tell Firefox which WM_CLASS to  use with the parameter --class MYCLASS. I was successful grouping the windows for two different profiles with two different icons by creating a starter that used "Exec=firefox -P myfirefox --class myfirefox %u" and "StartupWMClass=myfirefox".
5) Firefox will always execute commands like e.g. opening a new window against an instance that is already running, even if one specifies a profile name. So there is no way to make the "new window" command work properly from the starter icon (if one uses -no-remote, then am error will occur if an instance is running, if one does not use no-remote, the new window command may go to the wrong instance. This appears to be a Firefox bug). So if one uses two different Firefox starter icons for different profiles, it still does not seem to be possible to make the right-click "Open a new Window" option work properly.

---

