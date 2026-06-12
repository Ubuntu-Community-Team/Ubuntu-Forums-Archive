---
title: "Ubuntu 13.04 launcher icons problem."
date: 2013-05-09
forum: Desktop Environments
---

### Post by cmoud94 on 2013-05-09
Hi, I have a problem with launcher icons. For example, I have a 'Files' app locked to the launcher, but when I launch the Files app it sometimes put the new icon to the launcher, as if I haven't locked the icon to the launcher.
There is screenshot:
[ATTACH=CONFIG]242369[/ATTACH]

---

### Post by mc4man on 2013-05-09
There maybe several reasons, if it's "sometimes" concerning nautilus that would be a bit odd. (always would be easier to figure

What does this show - (should be 'application://nautilus.desktop'
```
gsettings get com.canonical.Unity.Launcher favorites
```
Do you have any nautilus desktop folders in /usr/local/share/applications or ~/.local/share/applications ?

---

### Post by cmoud94 on 2013-05-09
There is a output of : 'gsettings get com.canonical.Unity.Launcher favorites'
> 
['application://nautilus.desktop', 'application://firefox.desktop', 'application://filezilla.desktop', 'application://gedit.desktop', 'unity://running-apps', 'application://libreoffice-writer.desktop', 'application://libreoffice-calc.desktop', 'application://libreoffice-impress.desktop', 'application://banshee.desktop', 'application://gcalctool.desktop', 'application://gnome-system-monitor.desktop', 'application://ubuntu-software-center.desktop', 'application://gnome-control-center.desktop', 'unity://expo-icon', 'unity://devices', 'unity://desktop-icon']


In /usr/local/share there is no applications folder and in ~/.local/share/applications is only file called Mimeapps.list which contains:
> 
[Added Associations]
application/x-shellscript=gedit.desktop;
x-scheme-handler/http=firefox.desktop;
x-scheme-handler/https=firefox.desktop;
x-scheme-handler/mailto=thunderbird.desktop;
text/calendar=gedit.desktop;
audio/x-vorbis+ogg=rhythmbox.desktop;
video/x-ogm+ogg=totem.desktop;
image/jpeg=eog.desktop;

[Default Applications]
application/x-shellscript=gedit.desktop
x-scheme-handler/http=firefox.desktop
x-scheme-handler/https=firefox.desktop
x-scheme-handler/mailto=thunderbird.desktop
text/calendar=gedit.desktop
audio/x-vorbis+ogg=rhythmbox.desktop
video/x-ogm+ogg=totem.desktop
image/jpeg=eog.desktop

[Removed Associations]
application/x-shellscript=file-roller.desktop;


And the problem isn't only with nautilus, but with LibreOffice Writer too. Only these two apps are doing this type of 'bug'. If I find another app that have the same problem I will post it there.

PS: Thanks for reply.

---

### Post by mc4man on 2013-05-09
You could try this for nautilus - ( to revert just delete the newly created .desktop, log out/in

```
cp /usr/share/applications/nautilus.desktop  ~/.local/share/applications/
```
```
gedit  ~/.local/share/applications/nautilus.desktop
```

On the Exec= line remove --new-window, as in 
```
Exec=nautilus %U
```
Also for the moment change the display name so on the Name= line,  make it 
```
Name=File Manager
```
Save the file, close gedit, log out/in
The icon in your launcher should now tooltip to "File Manager", **if so** then see if it behaves any better, if not, ( not showing File Manager),  then post back

---

### Post by cmoud94 on 2013-05-10
The icon is now showing 'File Manager', but when I launch nautilus, it adds new icon for nautilus to the launcher each time, not only sometimes, as before.

---

### Post by mc4man on 2013-05-10
> **cmoud94 said:**
> The icon is now showing 'File Manager', but when I launch nautilus, it adds new icon for nautilus to the launcher each time, not only sometimes, as before.

(You probably could go back to sometimes by deleting the newly created .desktop, log out /in.if you want)

If not yet...
Was this an upgrade from previous Ubuntu release or fresh install?
What happens if you log into the guest account or a newly created additional user?

Try unlocking the nautilus icon from launcher, log out/in, then go ALT+F2 and enter - 
```
gtk-launch nautilus
```
Lock that launcher - does it work any better?

There are 2 commands you can run, one resets compiz to default, the other resets unity icons to default - I'd try the above things first.

---

### Post by Shansie on 2013-05-10
I've been having a similar problem. However, my issue is with Libre Writer opening an extra icon every time I open it. It hasn't happened since I started using it, only for the past few days. To the best of my knowledge, nothing has changed to cause it to happen.

Locking it to the launcher has made no difference to me. The original Libre Writer icon also has a "lock to launcher" option (that does nothing), and no "unlock" option.

---

### Post by cmoud94 on 2013-05-10
**mc4man**:
It was a fresh install of 13.04 64-bit. It started after few days of using it, and after some updates. I've restored compiz to default and of course the unity icons too, but no effect.

**Shansie**:
> **Shansie said:**
> I've been having a similar problem. However, my issue is with Libre Writer opening an extra icon every time I open it. It hasn't happened since I started using it, only for the past few days. To the best of my knowledge, nothing has changed to cause it to happen.

Locking it to the launcher has made no difference to me. The original Libre Writer icon also has a "lock to launcher" option (that does nothing), and no "unlock" option.

Same problem for me, but it doesn't happen each time, only sometimes.

---

### Post by Shansie on 2013-05-10
> **cmoud94 said:**
> 
It was a fresh install of 13.04 64-bit. It started after few days of using it, and after some updates. I've restored compiz to default and of course the unity icons too, but no effect.

I'm using 12.10 and still have this problem.

---

### Post by arm-c on 2013-07-05
I am having the exact same problem.  At one point, I "unlocked" Files (gnome files / nautilus) icon from the launcher.  I decided I wanted to add it back; however, after I did that, when "Files" opens, it adds another icon to the launcher as if it was not locked on the launcher to begin with.

Any recommendations?  I did not see an actual solution posted here.

Thanks

---

