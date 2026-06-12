---
title: "Java windows pop up on wrong workspace"
date: 2012-06-28
forum: Desktop Environments
---

### Post by ijbrown on 2012-06-28
I'm running a new 12.04 64 bit desktop with the oracle Java 7 SDK (build 1.7.0_05-b05). Configuration is standard unity with dual head monitors.

I have a problem in that when a java program pops up a dialog box, it appears on workspace 2 with a width of zero. I need to navigate to workspace 2, grab the 1 pixel vertical line and resize it and then move it back to the main window.
This seems to be particular to java because I see it both in my own programs and also with intellij IDEA. For example when I load a recent project, the dialog that asks me whether to open it in a new window appears with 0 width on workspace 2. As I am a java developer, this makes the distribution unusable for any serious work.
Is this a known problem and is there any work-around?

I have tried using the lxde desktop, which solves the problem above but it has a worse issue in that dragging a window (in particular a java window ... but others too) causes the contents to corrupt. I have read somewhere that this is an issue with the ATI driver. I don't see the effect with unity though ... just the bizarre window placement.

Thanks,

Ian

---

### Post by msammels on 2012-07-05
If you drag the window to the desired workspace, then right click the title bar of said window, selecting "Only on This Workspace", it should theoretically fix your problem.

---

