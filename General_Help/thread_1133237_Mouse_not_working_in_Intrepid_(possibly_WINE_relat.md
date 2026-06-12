---
title: "Mouse not working in Intrepid (possibly WINE related)"
date: 2009-04-22
forum: General Help
---

### Post by GreenfieldMark on 2009-04-22
So recently I was attempting to load a program using wine. The program was stalled, but wasn't slowing down my computer so I let it be for a while to see if it would fix itself. After a while it became clear that the program wasn't going to do anything ever, so I moved my mouse into its window to close it, having safely moved my mouse into the window multiple times before to check on its progress. 

This time however, my mouse ceased to move. It was as if my mouse pointer had become suddenly paralyzed for some reason. Thinking this might just be wine, or the program it was running, acting up I logged out to see if that would solve the problem. 

It didn't. So I rebooted, feeling sure that this would get my mouse working. 

No such luck there either. 

My mouse is plugged in, I haven't upgraded anything recently, and it was working just fine until it moved into that window. I have no idea what the problem could be. Please tell me someone here might.

P.S. I love how it's neigh on impossible to post here now because I can't use my mouse to select a thread prefix.

---

### Post by lovinglinux on 2009-04-22
I'm just guessing, but maybe the program you installed with Wine is configure to start automatically. I don't know if it could launch itself through Wine, but I had a similar problem with a game under Wine. In my case, PunkBuster was loading every time I started any Wine application, because it is a Windows service. Then it was slowing down my machine a lot. Uninstalling the game solved the problem.

So, check if there are any services running related to Wine (winedevice.exe, wineserver and any exe service) and kill them.

---

