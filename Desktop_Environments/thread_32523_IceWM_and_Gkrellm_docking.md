---
title: "IceWM and Gkrellm docking"
date: 2005-05-08
forum: Desktop Environments
---

### Post by Gentist on 2005-05-08
Ok, so I'm normally a Fluxbox user, though I thought I'd try out IceWM. For the last few days, I've been messing with the settings, reskinning and adding features which I feel was needed (such as ROX-filer for icons and as filemanager). Now I've come to the point where I'd like to setup some sort of system monitoring tool, and being the Fluxbox user I am, Gkrellm is the only real choice for me.

After a lot of googling, I've managed to dock Gkrellm with IceWM without messing up the ROX-filer setup, however... Gkrellm when in docking mode docks itself to the top left corner of the screen, which isn't really desirable. I would prefer to have it dock in the bottom right corner of the screen, but I've failed to find any documentation on the issue. My guess is that I would either have to pass a command in the winoptions file to tell Gkrellm where it should go, or I have to tell the dock to move. Basically, what I'm asking is: Is this supported by IceWM, and in such case, how do I go about it?

---

### Post by Gentist on 2005-05-08
Since I never managed to find a solution, I solved it by starting Gkrellm with "Gkrellm -w -g +x+y" (where x and y determines where it should be placed), plus the following lines in ~/.icewm/winoptions:

```

# GKrellm settings
gkrellm.layer: AboveAll
gkrellm.allWorkspaces: 1
gkrellm.ignoreWinList: 1
gkrellm.ignoreTaskBar: 1
gkrellm.ignoreQuickSwitch: 1
gkrellm.doNotCover: 1

```

My only problem now is that if I press the "Show Desktop" button, Gkrellm is minimized, and since it's hidden, I have no way of reversing the action. Is there an option that would have it stay where it is even if you press the "Show Desktop" button?

---

### Post by jonrkc on 2005-05-21
Here is the section for gkrellm from an IceWM winoptions file I used recently.  Using this, gkrellm remained visible all the time, even when "Show Desktop" was pushed:

```

gkrellm.Gkrellm.dBorder: 0
gkrellm.Gkrellm.dClose: 0
gkrellm.Gkrellm.dDepth: 0
gkrellm.Gkrellm.dHide: 0
gkrellm.Gkrellm.dMaximize: 0
gkrellm.Gkrellm.dMinimize: 0
gkrellm.Gkrellm.dResize: 0
gkrellm.Gkrellm.dRollup: 0
gkrellm.Gkrellm.dSysMenu: 0
gkrellm.Gkrellm.fClose: 0
gkrellm.Gkrellm.fMaximize: 0
gkrellm.Gkrellm.fResize: 0
gkrellm.Gkrellm.fRollup: 0
gkrellm.Gkrellm.ignoreQuickSwitch: 1
gkrellm.Gkrellm.ignoreTaskBar: 1
gkrellm.Gkrellm.tray: Ignore
gkrellm.Gkrellm.workspace: 2

```

---

### Post by BLTicklemonster on 2006-12-14
Excellent!

---

