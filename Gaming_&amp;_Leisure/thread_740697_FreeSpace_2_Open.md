---
title: "FreeSpace 2 Open"
date: 2008-03-31
forum: Gaming &amp; Leisure
---

### Post by Perk on 2008-03-31
Hi guys, I've been having a lot of trouble getting FreeSpace 2 open to work on my Ubuntu. I downloaded the java installer here: [http://www.hard-light.net/forums/index.php/topic,42854.0.html](http://www.hard-light.net/forums/index.php/topic,42854.0.html)

In the console, I typed: 'java -jar FreeSpaceOpenInstaller.jar'

I get the install menu, and I tell it to install to '/home/me/games/FreeSpace2'. I click 'Next' -> 'Next' and then in the console I receive these errors:

[HTML]
IntroPage(11372121)
DirPage(6504030)
OptionPage(26460367)
SelectPage(22507120)
InstallPage(18055655)
ExitPage(28678543)
[www.fsoinstaller.com](www.fsoinstaller.com)
/files/installer/java/
actionPerformed: next
actionPerformed: next
java.io.FileNotFoundException: /home/me/games/freespace 2/installer/installer_error.log.txt (No such file or directory)
        at java.io.FileOutputStream.open(Native Method)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:179)
        at java.io.FileOutputStream.<init>(FileOutputStream.java:102)
        at OptionPage.activatePage(OptionPage.java:50)
        at InstallerGUI.actionPerformed(InstallerGUI.java:114)
        at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
        at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318)
        at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
        at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
        at javax.swing.plaf.basic.BasicButtonListener.mouseReleased(BasicButtonListener.java:236)
        at java.awt.Component.processMouseEvent(Component.java:6038)
        at javax.swing.JComponent.processMouseEvent(JComponent.java:3265)
        at java.awt.Component.processEvent(Component.java:5803)
        at java.awt.Container.processEvent(Container.java:2058)
        at java.awt.Component.dispatchEventImpl(Component.java:4410)
        at java.awt.Container.dispatchEventImpl(Container.java:2116)
        at java.awt.Component.dispatchEvent(Component.java:4240)
        at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4322)
        at java.awt.LightweightDispatcher.processMouseEvent(Container.java:3986)
        at java.awt.LightweightDispatcher.dispatchEvent(Container.java:3916)
        at java.awt.Container.dispatchEventImpl(Container.java:2102)
        at java.awt.Window.dispatchEventImpl(Window.java:2429)
        at java.awt.Component.dispatchEvent(Component.java:4240)
        at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
        at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
        at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
        at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
        at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)
java.io.IOException: No such file or directory
        at java.io.UnixFileSystem.createFileExclusively(Native Method)
        at java.io.File.createNewFile(File.java:883)
        at OptionPage.activatePage(OptionPage.java:54)
        at InstallerGUI.actionPerformed(InstallerGUI.java:114)
        at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
        at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318)
        at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
        at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
        at javax.swing.plaf.basic.BasicButtonListener.mouseReleased(BasicButtonListener.java:236)
        at java.awt.Component.processMouseEvent(Component.java:6038)
        at javax.swing.JComponent.processMouseEvent(JComponent.java:3265)
        at java.awt.Component.processEvent(Component.java:5803)
        at java.awt.Container.processEvent(Container.java:2058)
        at java.awt.Component.dispatchEventImpl(Component.java:4410)
        at java.awt.Container.dispatchEventImpl(Container.java:2116)
        at java.awt.Component.dispatchEvent(Component.java:4240)
        at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4322)
        at java.awt.LightweightDispatcher.processMouseEvent(Container.java:3986)
        at java.awt.LightweightDispatcher.dispatchEvent(Container.java:3916)
        at java.awt.Container.dispatchEventImpl(Container.java:2102)
        at java.awt.Window.dispatchEventImpl(Window.java:2429)
        at java.awt.Component.dispatchEvent(Component.java:4240)
        at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
        at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
        at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
        at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
        at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)
actionPerformed: next
FreeSpace2 Retail Core
FreeSpace2 Voice
FreeSpace2 Music
FreeSpace2 Tech Animations
FreeSpace2 Command Briefing Animations
FreeSpace2 Voice
FreeSpace2 Music
FreeSpace2 Tech Animations
FreeSpace2 Command Briefing Animations
FreeSpace Open 3.6.9 Windows Executables
FreeSpace Open 3.6.10(unofficial) Windows Executables
FreeSpace Open 3.6.9 Linux Executables (32-bit)
FreeSpace Open 3.6.9 Linux Executables (64-bit)
FreeSpace Open 3.6.9 Macintosh (Universal Binary) Executables
FS2_Open Launcher for OS X
Multiplayer Missions
Multiplayer Voice Files
Multiplayer Voice Files
FS2Net Game Viewer
3.6.8 Zeta MediaVPs With 710 Patches
3.6.8 Zeta Advanced MediaVPs With 710 Patches
3.6.8 Zeta Advanced MediaVPs With 710 Patches
.OGG Cutscenes
FreeSpace Modding Tools
Derelict
Derelict Voice Pack
Derelict Voice Pack
FreeSpace 2 Single Player Demo
Just Another Day
Just Another Day 2: Electric Boogaloo
Just Another Day 3: Shivans on a Plane
JAD3 Cutscene Pack
JAD3 Cutscene Pack
FreeSpace Port
FreeSpace 1 Training Missions
1024x768 Interface Art
Ultra-High-Resolution Texture Maps
Glow Maps
Shine Maps
Music
Command Briefing Animations
Voice Files
FreeSpace 1 Cutscenes
Awakenings
Awakenings Voice Pack
Cardinal Spear
Cardinal Spear Voice Pack
Destiny of Peace
Destiny of Peace Voice Pack
FreeSpace 1 Training Missions
1024x768 Interface Art
Ultra-High-Resolution Texture Maps
Glow Maps
Shine Maps
Music
Command Briefing Animations
Voice Files
FreeSpace 1 Cutscenes
Awakenings
Awakenings Voice Pack
Awakenings Voice Pack
Cardinal Spear
Cardinal Spear Voice Pack
Cardinal Spear Voice Pack
Destiny of Peace
Destiny of Peace Voice Pack
Destiny of Peace Voice Pack
java.io.IOException: Server returned HTTP response code: 500 for URL: [http://www.sectorgame.com/goober/dem.txt](http://www.sectorgame.com/goober/dem.txt)
        at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1241](www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1241))
        at FreeSpaceOpenInstaller.download(FreeSpaceOpenInstaller.java:89)
        at SelectPage.activatePage(SelectPage.java:40)
        at InstallerGUI.actionPerformed(InstallerGUI.java:114)
        at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
        at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318)
        at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
        at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
        at javax.swing.plaf.basic.BasicButtonListener.mouseReleased(BasicButtonListener.java:236)
        at java.awt.Component.processMouseEvent(Component.java:6038)
        at javax.swing.JComponent.processMouseEvent(JComponent.java:3265)
        at java.awt.Component.processEvent(Component.java:5803)
        at java.awt.Container.processEvent(Container.java:2058)
        at java.awt.Component.dispatchEventImpl(Component.java:4410)
        at java.awt.Container.dispatchEventImpl(Container.java:2116)
        at java.awt.Component.dispatchEvent(Component.java:4240)
        at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4322)
        at java.awt.LightweightDispatcher.processMouseEvent(Container.java:3986)
        at java.awt.LightweightDispatcher.dispatchEvent(Container.java:3916)
        at java.awt.Container.dispatchEventImpl(Container.java:2102)
        at java.awt.Window.dispatchEventImpl(Window.java:2429)
        at java.awt.Component.dispatchEvent(Component.java:4240)
        at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
        at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
        at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
        at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
        at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
        at InstallerSection.<init>(InstallerSection.java:37)
        at InstallerSection.<init>(InstallerSection.java:25)
        at SelectPage.activatePage(SelectPage.java:41)
        at InstallerGUI.actionPerformed(InstallerGUI.java:114)
        at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
        at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318)
        at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
        at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
        at javax.swing.plaf.basic.BasicButtonListener.mouseReleased(BasicButtonListener.java:236)
        at java.awt.Component.processMouseEvent(Component.java:6038)
        at javax.swing.JComponent.processMouseEvent(JComponent.java:3265)
        at java.awt.Component.processEvent(Component.java:5803)
        at java.awt.Container.processEvent(Container.java:2058)
        at java.awt.Component.dispatchEventImpl(Component.java:4410)
        at java.awt.Container.dispatchEventImpl(Container.java:2116)
        at java.awt.Component.dispatchEvent(Component.java:4240)
        at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4322)
        at java.awt.LightweightDispatcher.processMouseEvent(Container.java:3986)
        at java.awt.LightweightDispatcher.dispatchEvent(Container.java:3916)
        at java.awt.Container.dispatchEventImpl(Container.java:2102)
        at java.awt.Window.dispatchEventImpl(Window.java:2429)
        at java.awt.Component.dispatchEvent(Component.java:4240)
        at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
        at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
        at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
        at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
        at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)
[/HTML]

It just hangs at the end of that line. Installer stuck at 0%. 

I have java 6 jre and jdk installed.

---

### Post by Perk on 2008-03-31
Okay, so apparently I needed a 'installer' folder inside the folder I installed it to.. I did that and it solved the Exceptions problem.

It runs smoothly until it tried to download 'Destiny of Peace Voice Pack'. It just hangs there.

[HTML]
IntroPage(26460367)
DirPage(18055655)
OptionPage(28678543)
SelectPage(24417480)
InstallPage(13884241)
ExitPage(14927396)
www.fsoinstaller.com
/files/installer/java/
actionPerformed: next
actionPerformed: next
actionPerformed: next
FreeSpace2 Retail Core
FreeSpace2 Voice
FreeSpace2 Music
FreeSpace2 Tech Animations
FreeSpace2 Command Briefing Animations
FreeSpace2 Voice
FreeSpace2 Music
FreeSpace2 Tech Animations
FreeSpace2 Command Briefing Animations
FreeSpace Open 3.6.9 Windows Executables
FreeSpace Open 3.6.10(unofficial) Windows Executables
FreeSpace Open 3.6.9 Linux Executables (32-bit)
FreeSpace Open 3.6.9 Linux Executables (64-bit)
FreeSpace Open 3.6.9 Macintosh (Universal Binary) Executables
FS2_Open Launcher for OS X
Multiplayer Missions
Multiplayer Voice Files
Multiplayer Voice Files
FS2Net Game Viewer
3.6.8 Zeta MediaVPs With 710 Patches
3.6.8 Zeta Advanced MediaVPs With 710 Patches
3.6.8 Zeta Advanced MediaVPs With 710 Patches
.OGG Cutscenes
FreeSpace Modding Tools
Derelict
Derelict Voice Pack
Derelict Voice Pack
FreeSpace 2 Single Player Demo
Just Another Day
Just Another Day 2: Electric Boogaloo
Just Another Day 3: Shivans on a Plane
JAD3 Cutscene Pack
JAD3 Cutscene Pack
FreeSpace Port
FreeSpace 1 Training Missions
1024x768 Interface Art
Ultra-High-Resolution Texture Maps
Glow Maps
Shine Maps
Music
Command Briefing Animations
Voice Files
FreeSpace 1 Cutscenes
Awakenings
Awakenings Voice Pack
Cardinal Spear
Cardinal Spear Voice Pack
Destiny of Peace
Destiny of Peace Voice Pack
FreeSpace 1 Training Missions
1024x768 Interface Art
Ultra-High-Resolution Texture Maps
Glow Maps
Shine Maps
Music
Command Briefing Animations
Voice Files
FreeSpace 1 Cutscenes
Awakenings
Awakenings Voice Pack
Awakenings Voice Pack
Cardinal Spear
Cardinal Spear Voice Pack
Cardinal Spear Voice Pack
Destiny of Peace
Destiny of Peace Voice Pack
Destiny of Peace Voice Pack

[/HTML]

Maybe the server it's downloading from is busy at the moment? I'll leave it one for a few minutes and see what happens.

---

### Post by Perk on 2008-03-31
Okay, it's been almost 40 minutes and it's still stuck. Does anyone know what is going on?

---

