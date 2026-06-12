---
title: "Firetray for Unity?"
date: 2013-12-09
forum: Desktop Environments
---

### Post by andy-samandari on 2013-12-09
Hi everyone!

Well, nice to be back - I haven't posted in several months. But anyway, I recently switched from Cinnamon to Unity. Yes, you read that correctly. Cinnamon was giving me compatibility issues, and despite the complaints about Unity being uncustomizable, I really like Unity's look, feel, top bar and eye candy ;) .

**But** my one issue with Unity is Thunderbird integration. In Cinnamon, LXDE and a few other DEs I like and use, I used the Firetray extension for Thunderbird to minimize Thunderbird to the system tray, giving me automated notifications when new mail came in and a useful little icon with the total number of unread messages. But this doesn't work in Unity! (I forgot exactly why, you can Google it and I found some ideas that sadly didn't help.)

Is there any program or extension for Unity that gives me notifications and unread count for Thunderbird even when the program is closed? (Like Firetray?) I have Popper for email notifications, but Popper only works when the Thunderbird window is open. I would like Thunderbird opened and minimized to system tray with an unread count. Any suggestions would be greatly appreciated - I used Firetray every day!

Thanks in advance,
Andy

---

### Post by Confused Computer User on 2013-12-10
> **andy-samandari said:**
> 
I really like Unity's look, feel, top bar and eye candy ;) .

Side note: If Unity turns out not to be your "cup of tea", then KDE has lots of eye candy and works flawlessly with firetray...

> **andy-samandari said:**
> 
I forgot exactly why, you can Google it and **I found some ideas** that sadly didn't help.

Please mention what were these ideas since it will save time in looking for solutions.

> **andy-samandari said:**
> 
Is there any program or extension for Unity that gives me notifications and unread count for Thunderbird even when the program is closed? (Like Firetray?) I have Popper for email notifications, but Popper only works when the Thunderbird window is open. I would like Thunderbird opened and minimized to system tray with an unread count. Any suggestions would be greatly appreciated - I used Firetray every day!

Appart from firetray I'm not aware of any other such program. There was an issue I faced when using unity and that was that a lot of the icons that used to show up in the tray were no longer there. For instance: Skype, Pidgin, Artha (I think) and firetray were not visible.
In this case runing the comand: gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
fixed the issue.
You can find more information at:
[Where are my tray icons in the Unity 2D panel?]("http://askubuntu.com/questions/66579/where-are-my-tray-icons-in-the-unity-2d-panel")
and
[How do I enable the pidgin system tray icon?]("http://askubuntu.com/questions/67312/how-do-i-enable-the-pidgin-system-tray-icon")

---

