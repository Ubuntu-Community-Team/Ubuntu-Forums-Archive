---
title: "Remove Top Panel on Second Monitor Only"
date: 2011-05-04
forum: Desktop Environments
---

### Post by bcollier on 2011-05-04
I like Unity so far, but one big complaint/question.  On my second monitor I have the same top panel / menu bar as on my main screen.  I would like / need to be able to remove the top panel on my second monitor only, and run all the global menu / system tray stuff on my main screen.

1) Having the system tray duplicated on both screens is a CLEAR design flaw, there is no reason I need to see the time, my name, and volume level etc. on both screens.

2) Removing the top panel from my second monitor is probably "preference" rather than necessary, but for those of us interested in screen real estate, distraction, and esthetics, being able to remove the panel from the second monitor is a must.

3)  I'm very surprised I have not been able to find anyone else in the forum asking this question, or making this comment, am I the only one noticing this?

I'm running an NVIDEA card with TwinView if that is helpful, see screenshot to see the duplicated top panel / system tray.

---

### Post by MasterShake1441 on 2011-05-04
I have a similar complaint. I would rather it not be there, but since it is, I would like to control whats over there. My little pop-up notifications come up on my second monitor, when I would like them on my main monitor and sometimes the panel moves to the right to the point where some of the buttons aren't accessible. If anyone has an idea how to edit panels in dual monitor configurations, that would be great. :)

---

### Post by _T_ on 2011-05-04
I can't say for sure if this will work for Gnome 3, as I havent used it yet, but you can give this a shot, as it works for me in Gnome 2...

1) Right click an existing panel and select "New Panel"

2) Right click the new panel wherever it appears and select "Properties" then uncheck "Expand" under the "General" tab. (This is really just so you can move it around for now)

3) Drag any icons and *most* applets from the other existing panels onto this new one. I say most because some applets did not want to simply drag over to the new panel in Gnome 2. You can right-click and "Add To Panel" any applets that do not want to play nice. (Don't forget to add the "Window List" applet, as this is the one that gives you the panel buttons for any open windows)  You should now have a pretty much empty panel (the old one) and your new one floating around.

4) Right click the **old** panel and select "Delete This Panel"

5) Drag your new panel to the top or bottom of whichever monitor you're wanting it to be on. It should "snap" onto the edge.

6) Right click it, and select "Properties" and add the check back to "Expand".

*Note* After expanding your new panel you may find the applets and icons need to be moved around. You can right click and make sure "Lock To Panel" is **not** checked then right click the same icon or applet and select "Move" and simply move your mouse left and right to position it as you please. Right click said applet/icon and "Lock To Panel" when you're done.

It's gonna be a shame if G3 is so different that this post was pointless...

---

### Post by Copper Bezel on 2011-05-04
The OP was about Unity, not Gnome 3, and neither one uses editable panels. 

bcollier, don't the menubars from windows on your second display appear on that display's panel?

---

### Post by bcollier on 2011-05-05
The menu bars for applications on the second monitor do show up on the second monitor, but that is not necessary, it could very easily show up in the first monitor.  For example, for a week this bothered my so much I used Ubuntu Classic, and in that I had one panel on my main monitor, and the global menu bar for any application, on the second monitor or first, showed up in the panel on the main monitor.

---

### Post by Copper Bezel on 2011-05-05
Then your best bet would be to continue using Classic, yes. Unity duplicates the panel to keep it accessible, particularly the global Application Menu, and possibly for aesthetic reasons as well (to retain consistency.) There's no option to disable this behavior (or to enable it with the Classic Gnome panel.)

If you would prefer the Classic panel but like the Unity Launcher, look into Docky, which is written by the same developer. It can be installed from the repositories.

---

### Post by bcollier on 2011-05-05
Thanks Copper, that was my solution for a while, but in 6 months they are going to change my option to do that, so I thought I would jump on board the new interface, and ask for changes if possible.

---

### Post by yolongyi on 2011-05-06
I have the exactly same compliant..
I also think it is needless to have duplicated things in both monitors.
actually I've googled for a week to find a way to remove the second top panel ( like you bcollier want )
I wish ur thought will be adopt :o
[]("http://ubuntuforums.org/member.php?u=1251027")

---

### Post by Mynt on 2011-06-08
Same here.

In my case the situation is worse since the options dissapear in my second toolbar and the icons on the first bar are not responding.

Please fix it!

---

### Post by RAMDrive on 2011-08-19
Has a real solution been found for this? aside from not using Unity.

---

### Post by RebelYeller on 2011-10-14
I have came across a way to hide the top panel in the second monitor. It does not exactly get rid of it or the notification windows because you won't be able to close any full screen window unless either right clicking on the application on your default monitor and closing the application that way or using a keyboard shortcut command (which I developed a liking to after using a Mac for years, But the Mac O.S. Crashed and couldn't restore it so I put Ubuntu on it and love it.). So the loop hole that I found;

When clicking on the "Power/Gear Icon" in the top right hand corner click on "Displays...", it should show the monitors you have connected.

The monitor that you want to you use for your secondary move next to but... under the black top bar of your main display like so in the picture that I hopefully posted along with this reply.

This is what worked for me (so far) and I am pretty hopeful this should for you as well.

---

### Post by ciborium on 2011-11-12
This solution may work for me as I only am using the second screen as a presentation projector.

---

### Post by jakobb on 2012-08-19
any solution on this yet??

---

