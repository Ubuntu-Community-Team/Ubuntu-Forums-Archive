---
title: "Unity launcher background issue"
date: 2012-12-11
forum: Desktop Environments
---

### Post by Tornikee on 2012-12-11
Hello,

While going through various Unsettings options, I set the launcher to 'auto hide', but this strip of launcher background remains after the launcher hides itself: [http://bit.ly/RmVAlU](http://bit.ly/RmVAlU)

What can be done about this?

---

### Post by Tornikee on 2012-12-12
No similar issue for anyone?

---

### Post by cmcanulty on 2012-12-12
I had that too when trying to use launcher in classic, never found a fix

---

### Post by LuisGMarine on 2012-12-12
Hello,

I just want to see if this is a Ubuntu or Unsetting problem.  

Have you tried to change the auto-hide feature from **System Setting -> Appearance -> Behavior** ?

This is bypasses using Unsetting.  I'm not sure if it will yield different results, but it is worth a try.

---

### Post by Tornikee on 2012-12-13
Yes, that was one of the steps I thought of and tried, but doesn't solve anything.

---

### Post by CorruptDNA on 2012-12-13
No fix for this bro.. no fix at all..

---

### Post by uzumakifahim on 2012-12-13
Is this problem only occurring with 12.10? Have anyone faced this issue with 12.04?

---

### Post by LuisGMarine on 2012-12-13
> **uzumakifahim said:**
> Is this problem only occurring with 12.10? Have anyone faced this issue with 12.04?

I just tested it on my 12.04 install and could not reproduce the same problem.

The only thing I can recommend and this point is to try another application to tweak unity and see if the problem persists.  If it does then it might be a ubuntu related bug.  If not, then you might have to file a bug report with the unsetting developers.  Considering there are already a few members that are experiencing the same symptom.

---

### Post by cmcanulty on 2012-12-14
I have it on 12.04 running classic with launcher

---

### Post by uzumakifahim on 2012-12-14
Have you guys, tried to hide the launcher after uninstalling Unsettings? It seems this problem is related with Unsettings. I'm using this auto hide feature for a long time but never faced this type of problem and importantly I'm not using Unsettings.

---

### Post by Tornikee on 2012-12-14
> **uzumakifahim said:**
> Have you guys, tried to hide the launcher after uninstalling Unsettings? It seems this problem is related with Unsettings. I'm using this auto hide feature for a long time but never faced this type of problem and importantly I'm not using Unsettings.
That's exactly what I tried now, and it solved the issue. Now I am going to install Ubuntu Tweak and see if it works w/o causing the same problem.

---

### Post by cmcanulty on 2012-12-15
I removed unsettings but now can't get launcher to show at all. Can someone tell me how to make it run in classic. I tried all the google search ideas with no luck 
This is the screen I get in terminal with lots of errors. I do have all the unity apps installed

```
cmcanulty@HPTech:~$ unity-2d-shell
unity-2d-shell: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core pointer 
unity-2d-shell: [DEBUG] bool KeyMonitor::registerEvents(): Could not open device:  Virtual core keyboard 
unity-2d-shell: [DEBUG] static void WindowImageProvider::activateComposite(): Server supports the Composite extension (ver 0.4)
unity-2d-shell: [WARNING] file:///usr/share/unity-2d/shell/launcher/Launcher.qml:224:39: Expected token `}'
unity-2d-shell: [WARNING] Object::connect: No such signal Lenses::roleNamesChanged(QHash<int,QByteArray>) in /build/buildd/unity-2d-5.12.0/libunity-2d-private/src/qsortfilterproxymodelqml.cpp:65
unity-2d-shell: [WARNING] void QSortFilterProxyModelQML::setSourceModelQObject(QObject*): received a sourceModel that does not notify of changes of its roleNames 
unity-2d-shell: [WARNING] file:///usr/share/unity-2d/shell/hud/Hud.qml:145: TypeError: Result of expression 'shellManager.hudShell' [null] is not an object.
unity-2d-shell: [WARNING] file:///usr/share/unity-2d/shell/launcher/LauncherLoader.qml:67: TypeError: Result of expression 'launcherLoader.item' [null] is not an object.
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Alt+F2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+0" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+0" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+1" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+2" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+3" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+3" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+4" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+4" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+5" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+5" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+6" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+6" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+7" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+7" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+8" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+8" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+9" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+Shift+9" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+&#55232;" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+A" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+E" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+F" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+M" 
unity-2d-shell: [DEBUG] virtual void Hotkey::connectNotify(const char*): Grabbing hotkey "Meta+V" 


```

---

### Post by uzumakifahim on 2012-12-15
> **Tornikee said:**
> That's exactly what I tried now, and it solved the issue. Now I am going to install Ubuntu Tweak and see if it works w/o causing the same problem.

Please tell your experience, what's the condition now after uninstalling Unsettings.

---

### Post by cmcanulty on 2012-12-16
I did in post #12

---

### Post by uzumakifahim on 2012-12-16
> **cmcanulty said:**
> I did in post #12

Thanks cmcanulty, for your sharing experience help, but I'm interested to know is Tornikee facing same problem just like you, or not?

---

